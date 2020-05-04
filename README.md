# nrf52-how-to-reject-bonding-from-central

Demo code how to accept/reject the bonding request from BLE Central

## Example

* Press the button 3 to toggle the accept/reject for the bonding request

```
        case BSP_EVENT_KEY_3:
                if (m_allow_bonding)
                {
                        m_allow_bonding = false;
                        NRF_LOG_DEBUG("Force to reject bonding");
                }
                else
                {
                        m_allow_bonding = true;
                        NRF_LOG_DEBUG("Allow bonding");
                }
```

```
static void pm_evt_handler(pm_evt_t const * p_evt)
{
        pm_handler_on_pm_evt(p_evt);
        pm_handler_flash_clean(p_evt);

        NRF_LOG_DEBUG("%s, evt_id = %02x", __func__, p_evt->evt_id);
        ret_code_t err_code;

        switch (p_evt->evt_id)
        {
        case PM_EVT_CONN_SEC_PARAMS_REQ:               
        {
                // pm_conn_sec_params_reply(m_conn_handle, )
                NRF_LOG_DEBUG("PM_EVT_CONN_SEC_PARAMS_REQ");
                if (m_allow_bonding == false)
                {
                        err_code = sd_ble_gap_sec_params_reply(m_conn_handle, BLE_GAP_SEC_STATUS_PAIRING_NOT_SUPP, NULL, p_evt->params.conn_sec_params_req.p_context);
                        APP_ERROR_CHECK(err_code);
                }
        }
```

## Requirement
* NRF52840 DK Board x 1
* Mobile / nRF Connect Desktop
* SDK 16.0 / S140v7.0.1
* IDE Segger Embedded Studio

## Details
You can find all the details information at [URL](https://jimmywongiot.com/2020/05/04/how-to-allow-reject-the-ble-bonding-request-from-central/).

## Location
The project may need modifications to work with later versions or other boards.
To compile it, clone the repository in the /nRF5_SDK_XX.x.0/examples/ directory.
The application is built to be used with the official nRF5 SDK that can be downloaded from developer.nordicsemi.com
