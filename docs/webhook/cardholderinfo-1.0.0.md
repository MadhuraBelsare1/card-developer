# Card Holder Info
Event is generated when the cardholder Info is updated.
#### Version: 1.0.0

### Schema
```
{
	"$schema": "http://json-schema.org/draft-04/schema#",
	"type": "object",
	"description": "This event is generated when the cardholder Info is updated.",
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
					"properties": {
						"name": {
							"type": "string",
							"description": "Cardholder's name. Total length of the Name and Suffix fields does not exceed 26 characters"
						},
						"personalizedEmbossingText": {
              				"type": "string",
              				"description": ". Displays based on your card class setup and can be left blank. Information is embossed on the front of the card below the cardholder name and is used along with the primary cardholder name. It is primarily used for business cards and contains the business names. Important! Do not use this field for the cardholder name. The data entered into the Additional Emboss Line is not encoded on track 1 of the card.",
							"length": ": Maximum 22 characters are printed on a debit card."
						},
						"ssnOrTaxId": {
							"type": "string",
							"description": " Tax identifier (Tax ID) or Social Security number (SSN) of the cardholder. Length: Maximum 20 characters"
						},
						"primaryDob": {
							"type": "string",
							"description": "Date of birth of the cardholder.",
							"Format": "YYYY-MM-DD",
							"example": "1986-10-25"
						}
					}
				},
				"new": {
					"type": "object",
					"properties": {
						"name": {
							"type": "string",
							"description": "Cardholder's name. Total length of the Name and Suffix fields does not exceed 26 characters"
						},
						"personalizedEmbossingText": {
              				"type": "string",
              				"description": ". Displays based on your card class setup and can be left blank. Information is embossed on the front of the card below the cardholder name and is used along with the primary cardholder name. It is primarily used for business cards and contains the business names. Important! Do not use this field for the cardholder name. The data entered into the Additional Emboss Line is not encoded on track 1 of the card.",
             				 "length": ": Maximum 22 characters are printed on a debit card."
           			 	},
						"ssnOrTaxId": {
							"type": "string",
							"description": " Tax identifier (Tax ID) or Social Security number (SSN) of the cardholder. Length: Maximum 20 characters"
						},
						"primaryDob": {
							"type": "string",
							"description": "Date of birth of the cardholder.",
							"Format": "YYYY-MM-DD",
							"example": "1986-10-25"
						}
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
### Example
```
{
    "header": {
        "id": "af892545-194b-433d-9aa0-8231994b6f17",
        "eventTitle": "Demographic Updates",
        "eventType": "Card",
        "eventCode": "CardholderInfo",
        "operationType": "Update",
        "eventDateTime": "2023-05-09T18:04:46Z",
        "eventVersion": "1.0.0",
		"source":"C"
	},
    "data": {
        "financialInstitutionId": "65200397",
	    "cardNumber": "4000100020005487",
	    "nonTransToken": "WUPIL5DQTZGM5487",
        "memberNumber": "0",
	    "old": {
	      "name": "RAMKUMAR,RAJESH",
	      "personalizedEmbossingText":"Home",
	      "primaryDob": "1984-10-30",
	      "ssnOrTaxId": "xxxxx5678"
	    },
	    "new": {
	      "name": "KUMAR,RAMESH",
	      "personalizedEmbossingText":"Home Team",
	      "primaryDob": "1986-12-20",
	      "ssnOrTaxId": "xxxxx5124"
	    }
  	}
}

```
