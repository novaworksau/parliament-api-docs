# Parliamentary Services Public API - New South Wales #

The following API's are available.

```
https://api.parliament.nsw.gov.au/api/hansard/search/year/{year}
https://api.parliament.nsw.gov.au/api/hansard/search/bydate
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment
https://api.parliament.nsw.gov.au/api/hansard/search/daily/fragment/html
https://api.parliament.nsw.gov.au/api/hansard/search/daily/pdf
https://api.parliament.nsw.gov.au/api/hansard/search/daily/pdf/historic
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontents
https://api.parliament.nsw.gov.au/api/hansard/search/daily/tableofcontentsbydate
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
https://api.parliament.nsw.gov.au/api/hansard/search/daily/pdf/historic/{documentId}
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