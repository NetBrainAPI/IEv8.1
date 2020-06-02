
## GET /ServicesAPI/API/V1/CMDB/SharedDeviceSettings

This API is used to get devices shared device settings in current domain. The response of this API will return a list in JSON format.<br>

## Detail Information

>**Title:** Get shared device settings API

>**Version:** 05/27/2020

>**API Server URL:** http(s)://IP Address of NetBrain Web API Server/ServicesAPI/API/V1/CMDB/SharedDeviceSettings

>**Authentication:**

|**Type**|**In**|**Name**|
|------|------|------|
|Bearer Authentication|Headers|Authentication token|

## Request body (*required)

>No request body.

## Query Parameters (*required)

|**Name**|**Type**|**Description**|
|------|------|------|
|hostname|string OR list of string|A list of device hostnames|
|ip|string OR list of string|A list of device management IPs|
|||If provided both of hostname and ip, hostname has higher priority. If any of the devices are not found from the provided query parameter, return the found devices as a list in response and add another json key "deviceNotFound", the value is a mixed list of hostnames and IPs that are not found. If both of hostname and ip are as empty, response would depends on the "skip" and "limit" values customer insert. |
|skip|integer|The amount of records to be skipped. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'skip' cannot be negative"}. No upper bound for this parameter.|
|limit|integer|The up limit amount of device records to return per API call. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'limit' cannot be negative"}. No upper bound for this parameter. If the parameter is not specified in API call, it means there is not limitation setting on the call.|
|||If only provide skip value, return the device list with 50 devices information start from the skip number. If only provide limit value, return from the first device in DB. If provided both skip and limit, return as required. Error exceptions follow each parameter's description.<br>Skip and limit parameters are based on the search result from DB. The "limit" value valid range is 10 - 100, if the assigned value exceeds the range, the server will respond error message: "Parameter 'limit' must be greater than or equal to 10 and less than or equal to 100."  |


## Headers

>**Data Format Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|Content-Type|string|support "application/json"|  
|Accept|string|support "application/json"|

>**Authorization Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|token|string|Authentication token, get from login API.|

## Response

|**Name**|**Type**|**Description**|
|------|------|------|
|statusCode|integer|Code issued by NetBrain server indicating the execution result.|
|statusDescription|string|The explanation of the status code.|
|shareDeviceSettings|object list| A list of device setting object.|
|shareDeviceSettings.LiveHostName| string | Device hostname. |
|shareDeviceSettings.ManageIp | string | Device management IP address. |
|shareDeviceSettings.ApplianceId | string | Name of front server. |
|shareDeviceSettings.Locked| bool | Whether the device setting has been locked. |
|shareDeviceSettings.LiveStatus| integer | live status of current device. |
|shareDeviceSettings.CLI_setting| object | CLI setting of current device. |
|shareDeviceSettings.CLI_setting.mode| string | mode for cli access. |
|shareDeviceSettings.CLI_setting.access_mode| string | access mode. |
|shareDeviceSettings.CLI_setting.access_mode_port| string | port number of access mode. |
|shareDeviceSettings.CLI_setting.CLI_credential_username| string | usename for CLI credential. |
|shareDeviceSettings.CLI_setting.privilege_username| string | device privilege username. |
|shareDeviceSettings.CLI_setting.jumpbox_for_FS| string | whether a front server jumpbox is needed. |
|shareDeviceSettings.CLI_setting.jumpbox_for_CLI| string | whether a CLI jumpbox is needed. |
|shareDeviceSettings.CLI_setting.prompt_settings| object | object for CLI prompt settings. |
|shareDeviceSettings.CLI_setting.prompt_settings.non_privilege_prompt| string | non_privilege_prompt. |
|shareDeviceSettings.CLI_setting.prompt_settings.privilege_prompt| string | privilege_prompt. |
|shareDeviceSettings.CLI_setting.prompt_settings.login_prompt_username| string | login_prompt_username. |
|shareDeviceSettings.CLI_setting.prompt_settings.privilege_login_prompt_username| string | privilege_login_prompt_username. |
|shareDeviceSettings.CLI_setting.advenced_setting| object | object for CLI advanced settings. |
|shareDeviceSettings.CLI_setting.advenced_setting.ForceTimeout| integer | force time out for CLI access |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting| object | object for CLI SSH finger print settings. |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting.checkSSHFingerprint| bool | enable or not for SSH Fingerprint key. |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting.SSHFingerprintKey| string | SSH fingerprint key value. |
|shareDeviceSettings.CLI_setting.advenced_setting.LoginScript| object | haven't decide whether should be opened to customer. |
|shareDeviceSettings.SNMP_setting| object | SNMP setting of current device. |
|shareDeviceSettings.SNMP_setting.roString| string  | value of device snmp RO.  |
|shareDeviceSettings.SNMP_setting.rwString| string | value of device snmp RWq. |
|shareDeviceSettings.SNMP_setting.snmpID| string | value of SNMP ID if there is one for this device |
|shareDeviceSettings.SNMP_setting.snmpPort| integer | SNMP port number. |
|shareDeviceSettings.SNMP_setting.snmpVersion| integer | version number of snmp version for current device |
|shareDeviceSettings.SNMP_setting.UseCustomizedManagementIp| bool | whether current device using the customized management IP.|
|shareDeviceSettings.SNMP_setting.v3| object | v3 SNMP setting. |
|shareDeviceSettings.SNMP_setting.v3.contextName| object | v3 SNMP context name. |
|shareDeviceSettings.SNMP_setting.v3.encryptPro| object | v3 SNMP encryptPro??. |
|shareDeviceSettings.SNMP_setting.v3.userName| object | v3 SNMP username. |
|shareDeviceSettings.SNMP_setting.v3.authMode| object | v3 SNMP authentication mode. |
|shareDeviceSettings.SNMP_setting.v3.authPro| object | v3 SNMP authentication pro???. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp| object | SNMP customized management IP setting . |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.retrieve_CPU| string | value of customized management IP retrieve CPU. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.retrieve_memory| string | value of customized management IP retrieve memory. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.ManageIp| string | value of customized management IP. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.snmpVersion| string | customized SNMP version. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.LiveStatus| integer | SNMP setting of current device. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.ro| string | value of customized management IP RO. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.rw| string | value of customized management IP RW. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.v3| object | same with shareDeviceSettings.SNMP_setting.v3 |
|shareDeviceSettings.API_setting| object list | API servers applied to current device. |
|shareDeviceSettings.API_setting.API_plugin| string | name of applied API plugin. |
|shareDeviceSettings.API_setting.API_server| object | applied API server. |
|shareDeviceSettings.API_setting.API_server.name| string | applied API servers name. |
|shareDeviceSettings.API_setting.API_server.front_server| string | front server connect with applied API server. |


***Example***


```python
{  
    "Shared device setting" : {
        "Locked" : False,
        "LiveStatus" : 1,
        "LiveHostName" : "CP-SW1",
        "ApplianceId" : "FS1",
        "ManageIp" : "192.168.0.58",
        "CLI_setting" : {
            "mode":"string",
            "access_mode":"string",
            "access_mode_port":"string"/int,
            "CLI_credential_username":"string",
            "privilege_username":"string",
            "jumpbox_for_FS":"string",
            "jumpbox_for_CLI":"string",
            "prompt_settings":{
                "non_privilege_prompt":"string",
                "privilege_prompt":"string",
                "login_prompt_username":"string",
                "privilege_login_prompt_username":"string"
            },
            "advenced_setting":{
                "ForceTimeout" : int,
                "SSH_key_setting":{
                    "checkSSHFingerprint" : true,
                    "SSHFingerprintKey" : "xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx"
                }
                #############################
                "LoginScript": {
                    "enable" : True/False,
                    "Private" : {      #???
                        "ExpectItems" : []
                    },
                    "UseLoginScript" : true,
                    "NonePrivate" : {    #???
                        "ExpectItems" : []
                    },
                    "cliModes" : [{
                        "name" : "Non-privilege Mode",
                        "basedOn" : "",
                        "content" : {
                            "ExpectItems" : [],
                            "supportPingTraceFrom" : false,
                            "couldEnterCmMode" : false,
                            "relatedBuiltinCmd" : [],
                            "relatedCustomizeCmd" : []
                          }
                        }, 
                      {
                        "name" : "Privilege Mode",
                        "basedOn" : "",
                        "content" : {
                            "ExpectItems" : [],
                            "supportPingTraceFrom" : false,
                            "couldEnterCmMode" : false,
                            "relatedBuiltinCmd" : [],
                            "relatedCustomizeCmd" : []
                         }
                      },
                      .
                      .
                      .
                  ]
                },
                ##########################
            }
        },
        "SNMP_setting" : {
                  "roString": "=",
                  "rwString": "=",
                  "snmpID": null,
                  "snmpPort": 161,
                  "v3": {
                    "contextName": "",
                    "encryptPro": 0,
                    "userName": "=",
                    "authMode": 0,
                    "authPro": 0,
                  },
                  "snmpVersion": 2,
                  "UseCustomizedManagementIp": false,
                  "CustomizedManagementIp": {
                    "retrieve_CPU":"string",
                    "retrieve_memory":"string",
                    "ManageIp": "",
                    "LiveStatus": int,
                    "snmpVersion": "string",
                    "ro": "string",
                    "rw": "string",
                    "v3": {
                      "contextName": "",
                      "encryptPro": 0,
                      "userName": "=",
                      "authMode": 0,
                      "authPro": 0,
                    }
                  }  
            },
        "API_setting" : {[
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }     
                },
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }  
                },
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }     
                },
                .
                .
                .
            ]
        }
    }
}
```

## GET /ServicesAPI/API/V1/CMDB/SharedDeviceSettings/CLISetting

This API is used to get device CLI settings in current domain. The response of this API will return a list in JSON format.<br>

## Detail Information

>**Title:** Get device CLI settings API

>**Version:** 05/27/2020

>**API Server URL:** http(s)://IP Address of NetBrain Web API Server/ServicesAPI/API/V1/CMDB/SharedDeviceSettings/CLISetting

>**Authentication:**

|**Type**|**In**|**Name**|
|------|------|------|
|Bearer Authentication|Headers|Authentication token|

## Request body (*required)

>No request body.

## Query Parameters (*required)

|**Name**|**Type**|**Description**|
|------|------|------|
|hostname|string OR list of string|A list of device hostnames|
|ip|string OR list of string|A list of device management IPs|
|||If provided both of hostname and ip, hostname has higher priority. If any of the devices are not found from the provided query parameter, return the found devices as a list in response and add another json key "deviceNotFound", the value is a mixed list of hostnames and IPs that are not found. If both of hostname and ip are as empty, response would depends on the "skip" and "limit" values customer insert. |
|skip|integer|The amount of records to be skipped. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'skip' cannot be negative"}. No upper bound for this parameter.|
|limit|integer|The up limit amount of device records to return per API call. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'limit' cannot be negative"}. No upper bound for this parameter. If the parameter is not specified in API call, it means there is not limitation setting on the call.|
|||If only provide skip value, return the device list with 50 devices information start from the skip number. If only provide limit value, return from the first device in DB. If provided both skip and limit, return as required. Error exceptions follow each parameter's description.<br>Skip and limit parameters are based on the search result from DB. The "limit" value valid range is 10 - 100, if the assigned value exceeds the range, the server will respond error message: "Parameter 'limit' must be greater than or equal to 10 and less than or equal to 100."  |


## Headers

>**Data Format Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|Content-Type|string|support "application/json"|  
|Accept|string|support "application/json"|

>**Authorization Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|token|string|Authentication token, get from login API.|

## Response

|**Name**|**Type**|**Description**|
|------|------|------|
|statusCode|integer|Code issued by NetBrain server indicating the execution result.|
|statusDescription|string|The explanation of the status code.|
|shareDeviceSettings|object list| A list of device setting object.|
|shareDeviceSettings.LiveHostName| string | Device hostname. |
|shareDeviceSettings.ManageIp | string | Device management IP address. |
|shareDeviceSettings.ApplianceId | string | Name of front server. |
|shareDeviceSettings.Locked| bool | Whether the device setting has been locked. |
|shareDeviceSettings.LiveStatus| integer | live status of current device. |
|shareDeviceSettings.CLI_setting| object | CLI setting of current device. |
|shareDeviceSettings.CLI_setting.mode| string | mode for cli access. |
|shareDeviceSettings.CLI_setting.access_mode| string | access mode. |
|shareDeviceSettings.CLI_setting.access_mode_port| string | port number of access mode. |
|shareDeviceSettings.CLI_setting.CLI_credential_username| string | usename for CLI credential. |
|shareDeviceSettings.CLI_setting.privilege_username| string | device privilege username. |
|shareDeviceSettings.CLI_setting.jumpbox_for_FS| string | whether a front server jumpbox is needed. |
|shareDeviceSettings.CLI_setting.jumpbox_for_CLI| string | whether a CLI jumpbox is needed. |
|shareDeviceSettings.CLI_setting.prompt_settings| object | object for CLI prompt settings. |
|shareDeviceSettings.CLI_setting.prompt_settings.non_privilege_prompt| string | non_privilege_prompt. |
|shareDeviceSettings.CLI_setting.prompt_settings.privilege_prompt| string | privilege_prompt. |
|shareDeviceSettings.CLI_setting.prompt_settings.login_prompt_username| string | login_prompt_username. |
|shareDeviceSettings.CLI_setting.prompt_settings.privilege_login_prompt_username| string | privilege_login_prompt_username. |
|shareDeviceSettings.CLI_setting.advenced_setting| object | object for CLI advanced settings. |
|shareDeviceSettings.CLI_setting.advenced_setting.ForceTimeout| integer | force time out for CLI access |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting| object | object for CLI SSH finger print settings. |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting.checkSSHFingerprint| bool | enable or not for SSH Fingerprint key. |
|shareDeviceSettings.CLI_setting.advenced_setting.SSH_key_setting.SSHFingerprintKey| string | SSH fingerprint key value. |
|shareDeviceSettings.CLI_setting.advenced_setting.LoginScript| object | haven't decide whether should be opened to customer. |

***Example***


```python
{  
    "Shared device setting" : {
        "Locked" : False,
        "LiveStatus" : 1,
        "LiveHostName" : "CP-SW1",
        "ApplianceId" : "FS1",
        "ManageIp" : "192.168.0.58",
        "CLI_setting" : {
            "mode":"string",
            "access_mode":"string",
            "access_mode_port":"string"/int,
            "CLI_credential_username":"string",
            "privilege_username":"string",
            "jumpbox_for_FS":"string",
            "jumpbox_for_CLI":"string",
            "prompt_settings":{
                "non_privilege_prompt":"string",
                "privilege_prompt":"string",
                "login_prompt_username":"string",
                "privilege_login_prompt_username":"string"
            },
            "advenced_setting":{
                "ForceTimeout" : int,
                "SSH_key_setting":{
                    "checkSSHFingerprint" : true,
                    "SSHFingerprintKey" : "xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx"
                }
                #############################
                "LoginScript": {
                    "enable" : True/False,
                    "Private" : {      #???
                        "ExpectItems" : []
                    },
                    "UseLoginScript" : true,
                    "NonePrivate" : {    #???
                        "ExpectItems" : []
                    },
                    "cliModes" : [{
                        "name" : "Non-privilege Mode",
                        "basedOn" : "",
                        "content" : {
                            "ExpectItems" : [],
                            "supportPingTraceFrom" : false,
                            "couldEnterCmMode" : false,
                            "relatedBuiltinCmd" : [],
                            "relatedCustomizeCmd" : []
                          }
                        }, 
                      {
                        "name" : "Privilege Mode",
                        "basedOn" : "",
                        "content" : {
                            "ExpectItems" : [],
                            "supportPingTraceFrom" : false,
                            "couldEnterCmMode" : false,
                            "relatedBuiltinCmd" : [],
                            "relatedCustomizeCmd" : []
                         }
                      },
                      .
                      .
                      .
                  ]
                },
                ##########################
            }
        }
    }
}
```

## GET /ServicesAPI/API/V1/CMDB/SharedDeviceSettings/SNMPSetting

This API is used to get device SNMP settings in current domain. The response of this API will return a list in JSON format.<br>

## Detail Information

>**Title:** Get device SNMP settings API

>**Version:** 05/27/2020

>**API Server URL:** http(s)://IP Address of NetBrain Web API Server/ServicesAPI/API/V1/CMDB/SharedDeviceSettings/SNMPSetting

>**Authentication:**

|**Type**|**In**|**Name**|
|------|------|------|
|Bearer Authentication|Headers|Authentication token|

## Request body (*required)

>No request body.

## Query Parameters (*required)

|**Name**|**Type**|**Description**|
|------|------|------|
|hostname|string OR list of string|A list of device hostnames|
|ip|string OR list of string|A list of device management IPs|
|||If provided both of hostname and ip, hostname has higher priority. If any of the devices are not found from the provided query parameter, return the found devices as a list in response and add another json key "deviceNotFound", the value is a mixed list of hostnames and IPs that are not found. If both of hostname and ip are as empty, response would depends on the "skip" and "limit" values customer insert. |
|skip|integer|The amount of records to be skipped. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'skip' cannot be negative"}. No upper bound for this parameter.|
|limit|integer|The up limit amount of device records to return per API call. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'limit' cannot be negative"}. No upper bound for this parameter. If the parameter is not specified in API call, it means there is not limitation setting on the call.|
|||If only provide skip value, return the device list with 50 devices information start from the skip number. If only provide limit value, return from the first device in DB. If provided both skip and limit, return as required. Error exceptions follow each parameter's description.<br>Skip and limit parameters are based on the search result from DB. The "limit" value valid range is 10 - 100, if the assigned value exceeds the range, the server will respond error message: "Parameter 'limit' must be greater than or equal to 10 and less than or equal to 100."  |


## Headers

>**Data Format Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|Content-Type|string|support "application/json"|  
|Accept|string|support "application/json"|

>**Authorization Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|token|string|Authentication token, get from login API.|

## Response

|**Name**|**Type**|**Description**|
|------|------|------|
|statusCode|integer|Code issued by NetBrain server indicating the execution result.|
|statusDescription|string|The explanation of the status code.|
|shareDeviceSettings|object list| A list of device setting object.|
|shareDeviceSettings.LiveHostName| string | Device hostname. |
|shareDeviceSettings.ManageIp | string | Device management IP address. |
|shareDeviceSettings.ApplianceId | string | Name of front server. |
|shareDeviceSettings.Locked| bool | Whether the device setting has been locked. |
|shareDeviceSettings.LiveStatus| integer | live status of current device. |
|shareDeviceSettings.SNMP_setting| object | SNMP setting of current device. |
|shareDeviceSettings.SNMP_setting.roString| string  | value of device snmp RO.  |
|shareDeviceSettings.SNMP_setting.rwString| string | value of device snmp RWq. |
|shareDeviceSettings.SNMP_setting.snmpID| string | value of SNMP ID if there is one for this device |
|shareDeviceSettings.SNMP_setting.snmpPort| integer | SNMP port number. |
|shareDeviceSettings.SNMP_setting.snmpVersion| integer | version number of snmp version for current device |
|shareDeviceSettings.SNMP_setting.UseCustomizedManagementIp| bool | whether current device using the customized management IP.|
|shareDeviceSettings.SNMP_setting.v3| object | v3 SNMP setting. |
|shareDeviceSettings.SNMP_setting.v3.contextName| object | v3 SNMP context name. |
|shareDeviceSettings.SNMP_setting.v3.encryptPro| object | v3 SNMP encryptPro??. |
|shareDeviceSettings.SNMP_setting.v3.userName| object | v3 SNMP username. |
|shareDeviceSettings.SNMP_setting.v3.authMode| object | v3 SNMP authentication mode. |
|shareDeviceSettings.SNMP_setting.v3.authPro| object | v3 SNMP authentication pro???. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp| object | SNMP customized management IP setting . |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.retrieve_CPU| string | value of customized management IP retrieve CPU. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.retrieve_memory| string | value of customized management IP retrieve memory. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.ManageIp| string | value of customized management IP. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.snmpVersion| string | customized SNMP version. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.LiveStatus| integer | SNMP setting of current device. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.ro| string | value of customized management IP RO. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.rw| string | value of customized management IP RW. |
|shareDeviceSettings.SNMP_setting.CustomizedManagementIp.v3| object | same with shareDeviceSettings.SNMP_setting.v3 |

***Example***


```python
{  
    "Shared device setting" : {
        "Locked" : False,
        "LiveStatus" : 1,
        "LiveHostName" : "CP-SW1",
        "ApplianceId" : "FS1",
        "ManageIp" : "192.168.0.58",
        "SNMP_setting" : {
          "roString": "=",
          "rwString": "=",
          "snmpID": null,
          "snmpPort": 161,
          "v3": {
            "contextName": "",
            "encryptPro": 0,
            "userName": "=",
            "authMode": 0,
            "authPro": 0
          },
          "snmpVersion": 2,
          "UseCustomizedManagementIp": false,
          "CustomizedManagementIp": {
            "retrieve_CPU":"string",
            "retrieve_memory":"string",
            "ManageIp": "",
            "LiveStatus": int,
            "snmpVersion": "string",
            "ro": "string",
            "rw": "string",
            "v3": {
              "contextName": "",
              "encryptPro": 0,
              "userName": "=",
              "authMode": 0,
              "authPro": 0
            }
          }  
        }
    }
}
```

## GET /ServicesAPI/API/V1/CMDB/SharedDeviceSettings/APIServerSetting

This API is used to get device API server settings in current domain. The response of this API will return a list in JSON format.<br>

## Detail Information

>**Title:** Get device API server settings API

>**Version:** 05/27/2020

>**API Server URL:** http(s)://IP Address of NetBrain Web API Server/ServicesAPI/API/V1/CMDB/SharedDeviceSettings/APIServerSetting

>**Authentication:**

|**Type**|**In**|**Name**|
|------|------|------|
|Bearer Authentication|Headers|Authentication token|

## Request body (*required)

>No request body.

## Query Parameters (*required)

|**Name**|**Type**|**Description**|
|------|------|------|
|hostname|string OR list of string|A list of device hostnames|
|ip|string OR list of string|A list of device management IPs|
|||If provided both of hostname and ip, hostname has higher priority. If any of the devices are not found from the provided query parameter, return the found devices as a list in response and add another json key "deviceNotFound", the value is a mixed list of hostnames and IPs that are not found. If both of hostname and ip are as empty, response would depends on the "skip" and "limit" values customer insert. |
|skip|integer|The amount of records to be skipped. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'skip' cannot be negative"}. No upper bound for this parameter.|
|limit|integer|The up limit amount of device records to return per API call. The value must not be negative.  If the value is negative, API throws exception {"statusCode":791001,"statusDescription":"Parameter 'limit' cannot be negative"}. No upper bound for this parameter. If the parameter is not specified in API call, it means there is not limitation setting on the call.|
|||If only provide skip value, return the device list with 50 devices information start from the skip number. If only provide limit value, return from the first device in DB. If provided both skip and limit, return as required. Error exceptions follow each parameter's description.<br>Skip and limit parameters are based on the search result from DB. The "limit" value valid range is 10 - 100, if the assigned value exceeds the range, the server will respond error message: "Parameter 'limit' must be greater than or equal to 10 and less than or equal to 100."  |


## Headers

>**Data Format Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|Content-Type|string|support "application/json"|  
|Accept|string|support "application/json"|

>**Authorization Headers**

|**Name**|**Type**|**Description**|
|------|------|------|
|token|string|Authentication token, get from login API.|

## Response

|**Name**|**Type**|**Description**|
|------|------|------|
|statusCode|integer|Code issued by NetBrain server indicating the execution result.|
|statusDescription|string|The explanation of the status code.|
|shareDeviceSettings|object list| A list of device setting object.|
|shareDeviceSettings.LiveHostName| string | Device hostname. |
|shareDeviceSettings.ManageIp | string | Device management IP address. |
|shareDeviceSettings.ApplianceId | string | Name of front server. |
|shareDeviceSettings.Locked| bool | Whether the device setting has been locked. |
|shareDeviceSettings.LiveStatus| integer | live status of current device. |
|shareDeviceSettings.API_setting| object list | API servers applied to current device. |
|shareDeviceSettings.API_setting.API_plugin| string | name of applied API plugin. |
|shareDeviceSettings.API_setting.API_server| object | applied API server. |
|shareDeviceSettings.API_setting.API_server.name| string | applied API servers name. |
|shareDeviceSettings.API_setting.API_server.front_server| string | front server connect with applied API server. |


***Example***


```python
{  
    "Shared device setting" : {
        "Locked" : False,
        "LiveStatus" : 1,
        "LiveHostName" : "CP-SW1",
        "ApplianceId" : "FS1",
        "ManageIp" : "192.168.0.58",
        "API_setting" : {[
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }     
                },
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }  
                },
                {
                    "API_plugin" : "string",
                    "API_server" : {
                        "name" : "string"/null,
                        "front_server" : "string"/null
                    }     
                },
                .
                .
                .
            ]
        }
    }
}
```