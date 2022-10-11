# Parliamentary Services Public API - South Australia #

<div style="font-size:1.2.rem;color:red">
The following APIs have been retired and are not being maintained. A new set of APIs will be made available in the future. Please check back for updates.
</div>


The following API's are available.

```
https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetYearlyEvents
https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetByDate
https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetFragmentHtml
```

#Read Data

Pick a simple read interface such as ```/_vti_bin/Hansard/HansardData.svc/GetYearlyEvents/2016``` to retrieve all of the published hansard transcripts for 2016.

For example:
```
curl https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetYearlyEvents/2016
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
		"Chamber": "House of Assembly",
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
		"Chamber": "House of Assembly",
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
https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetYearlyEvents/{year}
```
### Get Hansard Table of Contents By Id
This function allows a user to get a specific Hansard table of contents
*METHOD*: POST
*PARAMETERS*: DocumentId (string)
```
curl "https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetByDate" -H "Content-Type: application/json; charset=UTF-8" -H "Accept: */*" --data-binary "{""DocumentId"" : ""HANSARD-11-22597""}"
```
### Get Hansard Fragment by Document Id
This function allows a user to get a specific fragment
*METHOD*: POST
*PARAMETERS*: DocumentId (string)
```
curl "https://hansardpublic.parliament.sa.gov.au/_vti_bin/Hansard/HansardData.svc/GetFragmentHtml" -H "Content-Type: application/json; charset=UTF-8" -H "Accept: application/json, text/javascript, */*; q=0.01" -H "X-Requested-With: XMLHttpRequest" --data-binary "{""DocumentId"" : ""HANSARD-11-22542""}"
```
