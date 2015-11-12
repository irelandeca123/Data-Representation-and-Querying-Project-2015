# Data Representation and Querying Project 2015
## Stoyan Rizov

## Introduction
This project provides the design and documentation for the dataset "Roscommon Sports Facilities" which is available at [data.gov.ie](https://data.gov.ie/dataset/roscommon-sports-facilitiesbbc82).
This message may display while trying to access this dataset   
"{"status":"Processing","processing_time":0,"count":0}".

## About the data
This dataset was received in Comma Separated Values (CSV) format,it was downloaded from the following source: [Roscommon Facilities](https://data.gov.ie/dataset/roscommon-sports-facilitiesbbc82/resource/216a5b61-3ef0-429d-b6c9-5c272f23d9b8).

The CSV file contains 97 rows and 12 columns.
There are twelve values on each line, which are as follows:

Field | Description
------|------------
X | the x coordinates of the location of the clubs on the map.
Y | the y coordinates of the location of the clubs on the map.
OBJECTID | the unique identification number for each club.
Name | the names of the clubs located on the dataset.
Type| the type of the sports on the dataset.
Address | the address of each club.
Telephone | whether the club has a contact number or not.
Website | contains the web urls for the clubs depending if the club has one.
Streetview_Link | displays the google street view of the location of the club.
WGS84Longitude | shows the longitude of the location of the club basically the x coordinates.
WGS4Latitude | shows the latitude of the location of the club basically the y coordinates.
Eircode | to locate address in the state.

## Get Methods: 

####List of names for a given club
You can get list of names of the clubs by using the following GET method:
<em> *http://sports.com/Name/[NAME]* </em>
where [NAME] is the name of the club which returns the club names of the club.
An example would be (url):
<em> *http://sports.com/Name/[ClannaGael]* </em>
That would return the clubs named Clan na Gael which will be returned in JSON format with the following properties for each club:
- **OBJECTID**: Unique object ID of the club.
- **Type**: Type of sport that the club is.
- **Telephone**: That will return whether the club has a phone number or not.

An example of a response would be:
```json
 [ {"OBJECTID": 4, "TYPE": "GAA", "Telephone": "NA"} ]
 ```

#### List of locations for given clubs
You can get list of names of the clubs found in the address by using the following GET method:
<em> *http://sports.com/Address/[address]* </em>
where [address] is the club address your looking for.
An example would be (url):
<em> *http://sports.com/Address/[Tulsk,Co-Roscommon]* </em>
That would return the club located at Tulsk, Co Roscommon which will be returned in JSON format with the following properties for each club:
- **X**: x coordinates of the club. 
- **Y**: y coordinates of the club.
- **Name**: the name of the club.
- **TYPE**:Type of sport that the club is.

An example of a response would be:
```json
 [ {"X": -8.02051310392344, "Y": 53.3687496538591, "Name": "Clan na Gael", "TYPE": "GAA"
 } ]
 ```
 
#### Find a given club by the type of sport
 You can get list of names of the clubs found in that sport by using the following GET method:
<em> *http://sports.com/Type/[Type]* </em>.
Where [Type] is the sport type your looking for.
An example would be (url):
<em> *http://sports.com/Type/[GAA]* </em>
That would return the clubs associated with the sport GAA which will be returned in JSON format with the following properties for each club:
- **Name**: the name of the club.
- **Address**: Showing the addresses associated with the club.

An example of a response would be:
```json
 [ {"Name": "Clan na Gael", "Address": "Johnstown, Cornafulla, Athlone, Co Roscommon"} ]
 ```

#### Find contact information for a given club
You can get list of contact information of the clubs by using the  following GET method:
<em> *http://sports.com/Telephone/[Name]* </em>.
Where [Name] is the club name which then will show the contact information.
An example would be (url):
<em> *http://sports.com/Telephone/[Boyle-GAA-Club]* </em>
That would return the contact information associated with the club entered on the GET method which will be returned in JSON format with the following properties for each club:
- **Name**: The name of the club.
- **Address**: Showing the addresses associated with the club.
- **Telephone**: That will return whether the club has a phone number or not.
- **Web**: The website associated with the club.

An example of a response would be:
```json
 [ {"Name": "Clan na Gael", "Address": "Johnstown, Cornafulla, Athlone, Co Roscommon", "Telephone": "NA", "Web": " www.fuerty.roscommon.gaa.ie"} ]
 ```
#### List of clubs using eircode
You can get list of names of the clubs that have eircode by using the following GET method:
<em> *http://sports.com/Eircode/[EIRCODE]* </em>
where [EIRCODE] is the eirocde of the club/address which returns the club names that have that eircode as specified.
An example would be (url):
<em> *http://sports.com/Eircode/[F45KP93]* </em>
That would return the club named Castlerea Open Air Swimming Pool which will be returned in JSON format with the following properties for each club:
- **OBJECTID**: Unique object ID of the club.
- **Name**: The name of the club.
- **Address**: Showing the addresses associated with the club.

An example of a response would be:
```json
 [ {"OBJECTID": 81, "Name": "Castlerea Open Air Swimming Pool", "Address": "The Demesne, Castlerea, Co Roscommon" } ]
 ```

### Post Method:
The post method is used in order to send data to a server, for example file update and form data.
The following is an example use of the POST method:

```http
POST / request HTTP/1.1
Host: www.sports.com
Content-Type: application/jsonrequest
Content-Length: 88
Connection: Keep-Alive

{"OBJECTID": "2", "Name": "Ballinameen GAA", "Web": "www.Ballinameen.ie"}
```
This request will basically update the website ("Web") for the given ID "2" and will return in JSON format.

##Summary

This is my simple API Design for Apps4gaps.The data is made available through a set of URLs,
using a variety of HTTP methods.Thank you for reading !
