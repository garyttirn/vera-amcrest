# Vera-Amcrest

Amcrest camera implementation files for Vera home automaton system integration

Test with Amcrest IP2M-841, IP4M-1051 & IP3M-943 (no PTZ)

Upload I*.xml files to Vera via Vera Web UI, seletion Apps->Develop apps->Luup files->Upload

Create Camera device via LUUP call from Browser or curl	   
	http://VERA_IPADDRESS:3480/data_request?id=action&serviceId=urn:micasaverde-com:serviceId:HomeAutomationGateway1&action=CreateDevice&deviceType=urn:schemas-upnp-org:device:DigitalSecurityCamera:2&internalID=&Description=Amcrest%20Camera&UpnpDevFilename=D_DigitalSecurityCamera2.xml&UpnpImplFilename=I_Amcrest_ProHD.xml&MacAddress=&RoomNum=0&Reload=1&IpAddress=CAM-IPADDRESS

Create Motion sensor device
http://VERA_IPADDRESS:3480/data_request?id=action&serviceId=urn:micasaverde-com:serviceId:HomeAutomationGateway1&action=CreateDevice&deviceType=urn:schemas-micasaverde-com:device:MotionSensor:1&internalID=&Description=Camera%20motion%20sensor&UpnpDevFilename=D_MotionSensor1.xml&UpnpImplFilename=&IpAddress=&MacAddress=&RoomNum=0&Reload=1&DeviceNumParent=CAMERA-DEVICE-ID*

Force set camera credentials
	http://VERA_IPADDRESS:3480/data_request?id=variableset&DeviceNum=CAMERA-DEVICE-ID&Variable=username&Value=USERID
	http://VERA_IPADDRESS:3480/data_request?id=variableset&DeviceNum=CAMERA-DEVICE-ID&Variable=password&Value=PASSWORD

Delete device
	http://VERA_IPADDRESS:3480/data_request?id=device&action=delete&device=SENSOR-DEVICE-ID

Set as implementation file for a exting camera :
	Camera->Advanced Settings->Extra Parameters->impl_file
