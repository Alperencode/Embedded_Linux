# Week 3

## Week 3 Plan

- <u>[Webhook Get-Post requests](#webhook-get-post-requests)</u>
  - [Process of Using HTTP(S) AT Commands](#process-of-using-https-at-commands)
  - [To-Do](#to-do)
- <u>[Improving Python AT Library](#improving-python-at-library)</u>

<hr>

# Webhook Get-Post requests

## Process of Using HTTP(S) AT Commands

- **STEP 1:** Configure `<APN>`, `<username>`, `<password>` and other parameters of a PDP context by AT+QICSGP. Please refer to Quectel_EC2x&EG9x&EM05_TCP(IP)_AT_Commands_Manual for details. If QoS settings need to be updated, configure them by AT+CGQMIN, AT+CGEQMIN, AT+CGQREQ and AT+CGEQREQ commands. For more details, please refer to Quectel_EC25&EC21_AT_Commands_Manual, Quectel_EG9x_AT_Commands_Manual and Quectel_EM05_AT_Commands_Manual.

- **Step 2:** Activate the PDP context by AT+QIACT, then the assigned IP address can be queried by AT+QIACT?. Please refer to Quectel_EC2x&EG9x&EM05_TCP(IP)_AT_Commands_Manual for details.

- **Step 3:** Configure the PDP context ID and SSL context ID by AT+QHTTPCFG command.

- **Step 4:** Configure SSL context parameters by AT+QSSLCFG command. For more details, please refer to Quectel_EC2x&EG9x&EM05_SSL_AT_Commands_Manual.

- **Step 5:** Set HTTP(S) URL by AT+QHTTPURL command.

- **Step 6:** Send HTTP(S) request. AT+QHTTPGET command can be used for sending HTTP(S) GET request, and AT+QHTTPPOST or QHTTPOSTFILE command can be used for sending HTTP(S) POST request.

## To-do

- Add hyperlinks for all documents references in [Process of Using HTTP(S AT Commands)](#process-of-using-https-at-commands) ❌
  - Gather up all command descriptions if necessary
- Try 3.2 (Access to HTTPS Server) in [HTTP(S) document](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf) ✔️
  - Log errors ❌
- Try different `apn` names ✔️
  - Log errors ❌

##### Sources

- [Sixfab HTTP(S) AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_HTTPS_AT_Commands_Manual_V1.0.pdf)
- [Sixfab AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC25EC21_AT_Commands_Manual_V1.2.pdf)
- [Sixfab TCP/IP AT Commands Manual](https://sixfab.com/wp-content/uploads/2018/09/Quectel_EC2xEG9xEM05_TCPIP_AT_Commands_Manual_V1.0.pdf)
- [Sixfab GSM HTTP AT Commands Manual](https://sixfab.com/wp-content/uploads/2019/10/Quectel_GSM_HTTP_AT_Commands_Manual_V1.4.pdf)

<br><hr>

# Improving Python AT Library


> [!NOTE]
> ***Will be updated***
