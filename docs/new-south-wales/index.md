# Parliamentary Services Public API - New South Wales #

The following API's allow the user to consume Hansard documents and metadata.

```
https://api.parliament.nsw.gov.au/api/hansard/search/year
https://api.parliament.nsw.gov.au/api/hansard/search/bydate
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment/html
https://api.parliament.nsw.gov.au/api/hansard/search/daily/pdf
https://api.parliament.nsw.gov.au/api/hansard/search/daily/searchablepdf
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontents
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontentsbydate
https://api.parliament.nsw.gov.au/api/hansard/search/daily/bySpeaker
https://api.parliament.nsw.gov.au/api/hansard/search/daily/byBill
https://api.parliament.nsw.gov.au/api/sittingdate
https://api.parliament.nsw.gov.au/api/sittingdatetype
```

#Read Data

Pick a simple read interface such as ```/api/hansard/search/year/2016``` to retrieve all of the published hansard transcripts for 2016.

For example:
```
curl https://api.parliament.nsw.gov.au/api/hansard/search/year/2016
```
which will return you a JSON object of:
```json
[{
	"date": "2016-03-22",
	"style": "",
	"tooltip": "",
	"Events": [{
		"Chamber": "Legislative Assembly",
		"PdfDocId": "HANSARD-1323879322-69495",
		"TocDocId": "HANSARD-1323879322-69359",
		"Uncorrected": false
	}, {
		"Chamber": "Legislative Council",
		"PdfDocId": "HANSARD-1820781676-64623",
		"TocDocId": "HANSARD-1820781676-64511",
		"Uncorrected": false
	}]
}, {
	"date": "2016-03-21",
	"style": "",
	"tooltip": "",
	"Events": [{
		"Chamber": "Legislative Assembly",
		"PdfDocId": null,
		"TocDocId": null,
		"Uncorrected": false
	}, {
		"Chamber": "Legislative Council",
		"PdfDocId": "HANSARD-1820781676-64622",
		"TocDocId": "HANSARD-1820781676-64460",
		"Uncorrected": false
	}]
}]
```

### Get Hansard By Year
This function allows a user to get all hansards by year
*METHOD*: GET
*PARAMETERS*: year (integer)
```
https://api.parliament.nsw.gov.au/api/hansard/search/year/{year}
```
### Get Hansard By Date
This function allows a user to get detailed hansard by date

*METHOD*: GET

*PARAMETERS*: date (date in UTC format) e.g. 2016-04-21
```
https://api.parliament.nsw.gov.au/api/hansard/search/bydate?date={date}
```
### Get Hansard By Document Id
This function allows a user to get a specific Hansard fragment raw XML file

*METHOD*: GET

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment/{documentId}
```
### Get Hansard HTML By Document Id
This function allows a user to get a specific Hansard fragment JSON Payload

*METHOD*: POST

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment/html/{documentId}
```
### Get Hansard PDF By Document Id
This function allows a user to get a specific Hansard Daily PDF (post-1991)

*METHOD*: GET

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/pdf/{documentId}
```
### Get Hansard PDF By Document Id
This function allows a user to get a specific Hansard Daily PDF File (pre-1991)

*METHOD*: GET

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/searchablepdf/{documentId}
```
### Get Hansard Table of Contents XML By Document Id
This function allows a user to get a specific Hansard Table of Contents raw XML File

*METHOD*: GET

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontents/{documentId}
```
### Get Hansard Table of Contents JSON By Document Id
This function allows a user to get a specific Hansard fragment XML File

*METHOD*: POST

*PARAMETERS*: documentId (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontentsbydate/{documentId}
```
### Get Hansard By Speaker
This function allows a user to get specific Hansard's by speaker

*METHOD*: GET

*PARAMETERS*: speakerName (string), parliamentSessionId (integer), startDate (string), endDate (string), houseCode (string), memberId (integer), rowLimit (integer)

* speakerName can be either a last name or a name in the format "LastName, Title, Preferred or FirstName". E.g. "Doe", "Doe, Mr, John" or "Doe, Mr, Johnny". If providing only a last name you can provide a wildcard "\*" at the end of the name to match more than one name. E.g. providing "Smit\*" will match "Smit", "Smith", "Smithy" and so on.
* parliamentSessionId is the database Id of a parliament session.
* startDate/endDate must be in the format yyyy/mm/dd. Search is inclusive.
* houseCode is either "LH" or "UH".
* memberId is the database Id of a Member.
* rowLimit is used to limit the number of records returned.

All parameters are optional subject to the following restriction:
* You must provide *either* a parliamentSessionId *or* a startDate and endDate *or* a memberId.

**The most straightforward query provides only a start and end date and a speaker name. For example:**
* `https://api.parliament.nsw.gov.au/api/hansard/search/byspeaker?startDate=2019/01/01&endDate=2019/06/01&speakerName=Smith, Mr, John`

```
https://api.parliament.nsw.gov.au/api/hansard/search/byspeaker?
```
### Get Hansard By Bill
This function allows a user to get specific Hansard's by Bill

*METHOD*: GET

*PARAMETERS*: billName (string)
```
https://api.parliament.nsw.gov.au/api/hansard/search/daily/bybill?billName=""
```
### Get Sitting Days
This function allows a user to get a list of sitting days

*METHOD*: GET
```
https://api.parliament.nsw.gov.au/api/sittingdate
```
### Get Sitting Day Types
This function allows a user to get a list of sitting day types

*METHOD*: GET
```
https://api.parliament.nsw.gov.au/api/sittingdatetype
```