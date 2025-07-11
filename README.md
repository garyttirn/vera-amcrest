# Vera-Amcrest

Amcrest camera implementation files for Vera home automation system integration

Tested with Amcrest IP2M-841, IP4M-1026, IP4M-1051, IP3M-943 (no PTZ), IP5M-B1186EW-28 & IP5M-B1276EB-AI lastest firmware available at https://amcrest.com/firmwaredownloads

## Installation ##

Upload I*.xml files to Vera via Vera Web UI, seletion Apps->Develop apps->Luup files->Upload
https://support.getvera.com/hc/en-us/articles/360021950473-Apps-Tab-Plug-Ins

## Camera Integration ##

### Set as implementation file for an exting camera ###
Set approriate I*.xml in Camera->Advanced Settings->Extra Parameters->impl_file

#### Pan Tilt Zoom (PTZ) Camera ####
`I_Amcrest_ProHD-PTZ.xml`
#### Fixed Camera ####
`I_Amcrest_ProHD.xml`
#### Fixed AI Camera with audio dection ####
`I_Amcrest_IVS-AI.xml`
#### Fixed AI Camera without audio dection ####
`I_Amcrest_IVS-AI-No-Audio.xml`

### Create new camera device via LUUP call from browser or curl ###

#### Pan Tilt Zoom (PTZ) Camera ####
  `http://VERA_IPADDRESS:3480/data_request?id=action&serviceId=urn:micasaverde-com:serviceId:HomeAutomationGateway1&action=CreateDevice&deviceType=urn:schemas-upnp-org:device:DigitalSecurityCamera:2&internalID=&Description=Amcrest%20Camera&UpnpDevFilename=D_DigitalSecurityCamera2.xml&UpnpImplFilename=I_Amcrest_ProHD-PTZ.xml&MacAddress=&RoomNum=0&Reload=1&IpAddress=CAM-IPADDRESS`

#### Fixed Camera ####
  `http://VERA_IPADDRESS:3480/data_request?id=action&serviceId=urn:micasaverde-com:serviceId:HomeAutomationGateway1&action=CreateDevice&deviceType=urn:schemas-upnp-org:device:DigitalSecurityCamera:2&internalID=&Description=Amcrest%20Camera&UpnpDevFilename=D_DigitalSecurityCamera2.xml&UpnpImplFilename=I_Amcrest_ProHD.xml&MacAddress=&RoomNum=0&Reload=1&IpAddress=CAM-IPADDRESS`

### Force set camera credentials, if needed ###
  `http://VERA_IPADDRESS:3480/data_request?id=variableset&DeviceNum=CAMERA-DEVICE-ID&Variable=username&Value=USERID`

  `http://VERA_IPADDRESS:3480/data_request?id=variableset&DeviceNum=CAMERA-DEVICE-ID&Variable=password&Value=PASSWORD`

### Create Motion sensor device, if needed ###
  `http://VERA_IPADDRESS:3480/data_request?id=action&serviceId=urn:micasaverde-com:serviceId:HomeAutomationGateway1&action=CreateDevice&deviceType=urn:schemas-micasaverde-com:device:MotionSensor:1&internalID=&Description=Camera%20motion%20sensor&UpnpDevFilename=D_MotionSensor1.xml&UpnpImplFilename=&IpAddress=&MacAddress=&RoomNum=0&Reload=1&DeviceNumParent=CAMERA-DEVICE-ID*`

Useful with https://github.com/garyttirn/dahua-watch

### Delete devices ###
  `http://VERA_IPADDRESS:3480/data_request?id=device&action=delete&device=SENSOR-DEVICE-ID`

## Other Information ##
Discussion in Vera/Ezlo forums :
https://community.ezlo.com/t/amcrest-prohd-1080p/193000/52

