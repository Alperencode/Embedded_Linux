# Week 3

## Week 3 Plan

- <u>[Webhook Get-Post requests](#webhook-get-post-requests)</u>
  - [Process of Using HTTP(S) AT Commands](#process-of-using-https-at-commands)
  - [To-Do](#to-do)
  - [Input-Outputs](#input-outputs)
- <u>[Improving Python AT Library](#improving-python-at-library)</u>
  - [Minor-Updates](#minor-updates)

<hr>

# Webhook Get-Post requests

## Process of Using HTTP(S) AT Commands

- **STEP 1:** Configure `<APN>`, `<username>`, `<password>` and other parameters of a PDP context by AT+QICSGP. Please refer to [TCP(IP)_AT_Commands_Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_TCPIP_AT_Commands_Manual_V1.0.pdf) for details. If QoS settings need to be updated, configure them by AT+CGQMIN, AT+CGEQMIN, AT+CGQREQ and AT+CGEQREQ commands. For more details, please refer to [AT_Commands_Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC25EC21_AT_Commands_Manual_V1.2.pdf).

- **Step 2:** Activate the PDP context by AT+QIACT, then the assigned IP address can be queried by AT+QIACT?. Please refer to [TCP(IP)_AT_Commands_Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_TCPIP_AT_Commands_Manual_V1.0.pdf) for details.

- **Step 3:** Configure the PDP context ID and SSL context ID by [AT+QHTTPCFG](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf) command.

- **Step 4:** Configure SSL context parameters by AT+QSSLCFG command. For more details, please refer to [SSL_AT_Commands_Manual](https://usermanual.wiki/Document/QuectelEC2x26EG9x26EM05SSLATCommandsManualV10.1735503669/view).

- **Step 5:** Set HTTP(S) URL by [AT+QHTTPURL](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf) command.

- **Step 6:** Send HTTP(S) request. [AT+QHTTPGET](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf) command can be used for sending HTTP(S) GET request, and AT+QHTTPPOST or QHTTPOSTFILE command can be used for sending HTTP(S) POST request.

## To-do

- Add hyperlinks for all documents references in [Process of Using HTTP(S AT Commands)](#process-of-using-https-at-commands) ✔️
  - Gather up all command descriptions if necessary
- Try 3.2 (Access to HTTPS Server) in [HTTP(S) document](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf) ✔️
  - Log errors ❌
- Try different `apn` names ✔️
  - Log errors ❌

## Input-Outputs

> [!NOTE]
> ***Will be updated***

##### Sources

- [Sixfab HTTP(S) AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf)
- [Sixfab AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC25EC21_AT_Commands_Manual_V1.2.pdf)
- [Sixfab TCP/IP AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_TCPIP_AT_Commands_Manual_V1.0.pdf)
- [Sixfab GSM HTTP AT Commands Manual](https://sixfab.com/wp-content/uploads/2019/10/Quectel_GSM_HTTP_AT_Commands_Manual_V1.4.pdf)
- [Quectel SSL AT Commands Manual](https://usermanual.wiki/Document/QuectelEC2x26EG9x26EM05SSLATCommandsManualV10.1735503669/view)

<br><hr>

# Improving Python AT Library

## Minor Updates

- Add `Empty response` check
  - Reference [here](https://github.com/Alperencode/AT-Lib/commit/0baa2ac691312461cc242cc6701e0d312f5957b4#diff-225e7cfc4be956dfc27a380f6db386cdd5c88abc9482236efcfc1b5dfa79f198R98)
- Add `CONNECT` response check
  - Reference [here](https://github.com/Alperencode/AT-Lib/commit/0baa2ac691312461cc242cc6701e0d312f5957b4#diff-225e7cfc4be956dfc27a380f6db386cdd5c88abc9482236efcfc1b5dfa79f198R109-R112) (Updated due testcases later [here](https://github.com/Alperencode/AT-Lib/commit/3a609c24e69418bdf78edfea4b78a8770458303c#diff-225e7cfc4be956dfc27a380f6db386cdd5c88abc9482236efcfc1b5dfa79f198R109-R112))
- Add return response to `Unexpected AT response`
  - Reference [here](https://github.com/Alperencode/AT-Lib/commit/0baa2ac691312461cc242cc6701e0d312f5957b4#diff-225e7cfc4be956dfc27a380f6db386cdd5c88abc9482236efcfc1b5dfa79f198R115)