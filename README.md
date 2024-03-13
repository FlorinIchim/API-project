# API-project
The application allows you to connect to the ESP32 board using Bluetooth Classic. The app requires the Bluetooth module and location services to be enabled on the smartphone, as well as several permissions to access Bluetooth specific functions, such as scanning for devices, connecting and advertising. The requests and responses are detailed in the following sections.

getNetworks

The getNetworks request is the first request sent by the app and is used for obtaining the list of available WiFi networks available to the ESP32 device, as well as setting the teamId parameter, which will be a required parameter for all responses. The teamId value must be saved in the ESP32 program. Without it, the app will not allow further actions. The expected response is a JSON encoded object for each WiFi network

connect

The connect request is used to connect to a specified network with the WiFi password (if required). Notice that the teamId parameter is no longer sent in this request or any other subsequent request, but the previously stored value will have to be included in all responses, matching the initial value the was sent by the getNetworks request

getData

The getData request is used for querying the list of records from the API. Each API returns a different set of attributes. The ESP32 program should send only the relevant response to the app. The required response is a JSON encoded object for each list record

getDetails

The getDetails request is used for querying a single record. The id attribute represents the id of the item from the previous list. Since each API returns different attributes for the records, the description attribute must be constructed in the ESP32 program, using the relevant attributes returned by the API. The required response is a JSON encoded object
