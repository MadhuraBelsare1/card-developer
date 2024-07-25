# Card Status Event
Event is generated when a card status is updated.
#### Version: 1.0.0

### Schema
```
{
	"$schema": "http://json-schema.org/draft-04/schema#",
	"type": "object",
	"description": "This event is generated when a card status is updated.",
	"properties": {
		"header": {
			"type": "object",
			"properties": {
				"id": {
					"type": "string",
					"description": "Generic identifier that contains no sensitive data and represents a unique value for the event being presented"
				},
				"eventTitle": {
					"type": "string",
					"description": "Indicates the title of event"
				},
				"eventType": {
					"type": "string",
					"description": "Indicates the type of event"
				},
				"eventCode": {
					"type": "string",
					"description": "Indicates the card functionality"
				},
				"operationType": {
					"type": "string",
					"description": "Indicates the type of change"
				},
				"eventDateTime": {
					"type": "string",
					"description": "Date/time when change occured"
				},
				"eventVersion": {
					"type": "string",
					"description": "Version of the event (starts at \"1.0.\")"
				},
				"source": {
					"type": "string",
					"description": "The source to add/update the card record Values :  1 = External API,2 = Card Console,3 = Card Hub,4 = ECHO,5 = Test API,6 = Domain Services,A = Admin (not currently used),B = Batch Processing,C = CWSi,D = CM2 Conversion or Kit,E = CM2 Remote Card Maintenance,F = CM2 FHM (ISO or HISO),F = FUN server,G = CM2 Conversion (Internal RCM),H = Card Alert Tracking,I = Integrated Desktop,J = Case Tracker (reserved),k = HOT requestor,L= PIN activation server,M = Pin By Phone (Unix),N = RuleManager,O = Reissue (Tandem),P = Reissue (Unix),Q = AlertBroker Gateway,R = Refresh,V = VRU,U  = Unknown",
					"enum": [
						"1",
						"2",
						"3",
						"4",
						"5",
						"6",
						"A",
						"B",
						"C",
						"D",
						"E",
						"F",
						"G",
						"H",
						"I",
						"J",
						"K",
						"L",
						"M",
						"N",
						"O",
						"P",
						"Q",
						"R",
						"V",
						"U"
					]
				}
			}
		},
		"data": {
			"type": "object",
			"properties": {
				"financialInstitutionId": {
					"type": "string",
					"description": "Financial institution identifier - FIID"
				},
				"cardNumber": {
					"type": "string",
					"description": "Decrypted/masted card number"
				},
				"nonTransToken": {
					"type": "string",
					"description": "NTT card number provided"
				},
				"memberNumber": {
					"type": "string",
					"description": "Unique number associated with each member of the card",
					"format": " 1 digit; depending on card prefix, values include 0 (zero) or 1–9"
				},
				"old": {
					"type": "object",
					"cmCardStatus": {
						"type": "string",
						"description": "Current status of the selected card",
						"enum": [
							"Active",
							"Capture",
							"Deactivate",
							"Issued",
							"Restricted"
						]
					},
					"cmReasonCode": {
						"type": "string",
						"description": "Reason for the current status of the selected card",
						"enum": [
							"None",
							"Abused",
							"Closed",
							"Customer Request",
							"Damaged",
							"Lost",
							"Revoked",
							"Stolen"
						]
					}
				},
				"new": {
					"type": "object",
					"cmCardStatus": {
						"type": "string",
						"description": "Current status of the selected card",
						"enum": [
							"Active",
							"Capture",
							"Deactivate",
							"Issued",
							"Restricted"
						]
					},
					"cmReasonCode": {
						"type": "string",
						"description": "Reason for the current status of the selected card",
						"enum": [
							"None",
							"Abused",
							"Closed",
							"Customer Request",
							"Damaged",
							"Lost",
							"Revoked",
							"Stolen"
						]
					}
				}
			},
			"required": [
				"cardNumber",
				"memberNumber"
			]
		}
	}
}
```

### Examnple
```
{
    "header": {
        "id": "325b87f9-11ec-41e1-9875-bf6b32da366a",
        "eventTitle": "Card Status Changes",
        "eventType": "Card",
        "eventCode": "Status",
        "operationType": "Update",
        "eventDateTime": "2023-05-23T14:47:34Z",
        "eventVersion": "1.0.0",
        "source":"C"
    },
    "data": {
        "financialInstitutionId": "65200397",
        "cardNumber": "4000100020003000",
        "nonTransToken": "WUPIL5DQTZGM3000",
        "memberNumber": "0",
        "old": {
            "cmReasonCode": "None",
            "cmCardStatus": "Active"
        },
        "new": {
            "cmReasonCode": "Closed",
            "cmCardStatus": "Deactivated"
        }
    }
}
```
