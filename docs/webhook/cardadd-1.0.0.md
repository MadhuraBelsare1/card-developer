## Card Add Event

Event is generated when a Card is Added.

#### Version: 1.0.0

## Schema
```
{
	"$schema": "http://json-schema.org/draft-04/schema#",
	"type": "object",
	"description": "This event is generated when a card is added.",
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
					"cardType": {
						"type": "string",
						"description": "Indicates the type of card associated with this card class. Values: A = Admin card,D = Demo card,P = Proprietary card,M = MasterCard,V = Visa,X = Discover",
						"enum": [
							"A",
							"D",
							"P",
							"M",
							"V",
							"X"
						]
					},
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
					},
					"expirationDate": {
						"type": "string",
						"description": "Required. Month and year the card record is set to expire. If you enter a date in this field that is less than the old expiration date, a confirmation message displays, enabling you to continue or cancel. If this date is changed, an Account Updater Service (AUS) update record is sent to the networks, unless the option is selected, indicating the cardholder has opted out of AUS.",
						"format": "MM/YY"
					},
					"digitalExpDate": {
						"type": "string",
						"description": "Expiration Date for an instant virtual card. Month and year the virtual card record is set to expire."
					},
					"cardClass": {
						"type": "string",
						"description": "5-character alphanumeric identifier for the card class associated with the card. It represents a client-defined group of cardholders with common characteristics such as card stock, withdrawal limits, or processing days."
					}
				},
				"cardholderInfo": {
					"type": "object",
					"properties": {
						"cardholderName": {
							"type": "string",
							"description": "Cardholder's name. Total length of the Name and Suffix fields does not exceed 26 characters"
						},
						"personalizedEmbossingText": {
							"type": "string",
							"description": ". Displays based on your card class setup and can be left blank. Information is embossed on the front of the card below the cardholder name and is used along with the primary cardholder name. It is primarily used for business cards and contains the business names. Important! Do not use this field for the cardholder name. The data entered into the Additional Emboss Line is not encoded on track 1 of the card.",
							"length": ": Maximum 22 characters are printed on a debit card."
						},
						"primaryDob": {
							"type": "string",
							"description": "Date of birth of the cardholder.",
							"Format": "YYYY-MM-DD",
							"example": "1986-10-25"
						},
						"ssnOrTaxId": {
							"type": "string",
							"description": " Tax identifier (Tax ID) or Social Security number (SSN) of the cardholder. Length: Maximum 20 characters"
						}
					}
				},
				"primaryAddress": {
					"type": "object",
					"properties": {
						"addressLine1": {
							"type": "string",
							"description": "First line of the cardholder's address."
						},
						"addressLine2": {
							"type": "string",
							"description": "Second line of the cardholder's address."
						},
						"city": {
							"type": "string",
							"description": "City of the cardholder's address."
						},
						"state": {
							"type": "string",
							"description": "State code of the cardholder's address.",
							"format": "Format - 2 characters",
							"example": "NJ"
						},
						"country": {
							"type": "string",
							"description": "Country associated with the cardholder's address."
						},
						"zip": {
							"type": "string",
							"description": "Postal code of the cardholder's address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
							"example": "30004 or 30004-0895"
						}
					}
				},
				"alternateAddress": {
					"type": "object",
					"properties": {
						"addressLine1": {
							"type": "string",
							"description": " First line of the cardholder's alternate address."
						},
						"addressLine2": {
							"type": "string",
							"description": "Second line of the cardholder's alternate address."
						},
						"city": {
							"type": "string",
							"description": "City of the cardholder's alternate address."
						},
						"state": {
							"type": "string",
							"description": "State code of the cardholder's alternate address.",
							"format": "Format - 2 characters",
							"example": "NJ"
						},
						"country": {
							"type": "string",
							"description": "Country associated with the cardholder's alternate address."
						},
						"zip": {
							"type": "string",
							"description": "Postal code of the cardholder's alternate address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
							"example": "30004 or 30004-0895"
						}
					}
				},
				"activation": {
					"type": "object",
					"properties": {
						"activationCreateDate": {
							"type": "string",
							"description": "Date when the activation is created",
							"format": "YY-MM-DD"
						},
						"lastAttemptActivationStatus": {
							"type": "string",
							"description": "Displays a card's last activation attempt status. Values: 000-Card not activated,001-Card activated,002-Actvn before available date,003-Card record not found,004-Card status is Lost/Stolen,005-Card status is closed,006-No activation required,007-Exp. date doesn't match,008-Card already activated,009-Attempt after deadline,010-Max attempts exceeded,011-Caller ID invalid,012-Activation code invalid,013-PIN check not performed,014-Invalid Actvn method,015-IVR Auth Failed",
							"enum": [
								"000",
								"001",
								"002",
								"003",
								"004",
								"005",
								"006",
								"007",
								"008",
								"009",
								"010",
								"011",
								"012",
								"013",
								"014",
								"015"
							]
						}
					}
				},
				"accounts": {
					"type": "array",
					"items": [{
						"type": "object",
						"properties": {
							"number": {
								"type": "string",
								"description": "Checking or savings account number linked to the selected cardholder record."
							},
							"type": {
								"type": "string",
								"description": "Account type for the associated account number. Values : 10 = Savings,11 = IRA,14 = Commercial deposit account,20 = Checking (DDA),21 = NOW,23 = Money market,30 = Credit line,31 = Credit card,32 = Check Plus,41 = Installment loan,42 = Mortgage loan",
								"enum": [
									"10",
									"11",
									"14",
									"20",
									"21",
									"23",
									"30",
									"31",
									"32",
									"41",
									"42"
								]
							},
							"status": {
								"type": "string",
								"description": "Status of the account. Values : 0 = No relationship,1 = Open,2 = Restricted to deposits,3 = Open lastary acct,4 = Restricted primary acct,8 = Super primary acct,9 = Closed",
								"enum": [
									"0",
									"1",
									"2",
									"3",
									"4",
									"8",
									"9"
								]
							}
						}
					}]
				},
				"contactIndicator": {
					"type": "object",
					"properties": {
						"text": {
							"type": "object",
							"properties": {
								"homePhone": {
									"type": "string",
									"description": "Home phone number of the cardholder.",
									"enum": [
										"Y",
										"N"
									]
								},
								"workPhone": {
									"type": "string",
									"description": "Work phone number of the cardholder.",
									"enum": [
										"Y",
										"N"
									]
								},
								"cellPhone": {
									"type": "string",
									"description": "Cell phone number of the cardholder.",
									"enum": [
										"Y",
										"N"
									]
								}
							}
						},
						"sms": {
							"type": "string",
							"description": "Cardholder's phone number specified for fraud text messaging.",
							"enum": [
								"Y",
								"N"
							]
						},
						"email": {
							"type": "string",
							"description": "Cardholder's email address to receive messages.",
							"enum": [
								"Y",
								"N"
							]
						}
					}
				},
				"emailAndSms": {
					"type": "object",
					"properties": {
						"email": {
							"type": "string",
							"description": "Cardholder's email address to receive messages."
						},
						"sms": {
							"type": "string",
							"description": "Cardholder's phone number specified for fraud text messaging."
						},
						"language": {
							"type": "string",
							"description": "Indicates the language preference. Values:E=English, S=Spanish (<spaces> = default to BIN level setting)",
							"enum": [
								"",
								"E",
								"S"
							]
						}
					}
				},
				"contactInfo": {
					"type": "object",
					"properties": {
						"homePhone": {
							"type": "string",
							"description": "Home phone number of the cardholder."
						},
						"workPhone": {
							"type": "string",
							"description": "Work phone number of the cardholder."
						},
						"cellPhone": {
							"type": "string",
							"description": "Cell phone number of the cardholder."
						}
					}
				},
				"securityInfo": {
					"type": "object",
					"properties": {
						"mothersMaidenName": {
							"type": "string",
							"description": "Primary cardholder's mother's maiden name."
						},
						"verificationText": {
							"type": "string",
							"description": "Verification data as requested by the primary cardholder for identification. example: Driver's license number"
						}
					}
				},
				"additionalAttributes": {
					"type": "object",
					"properties": {
						"cardFeature": {
							"type": "string",
							"description": "Functionality assigned to the card",
							"format": "8-EMV, 9-ARES, 10-Account Updater Service, 11-EMC Dual Interface, 12-Static Virtual Card, 13-Digital Card"
						}
					}
				},
				"required": [
					"financialInstitutionId",
					"cardNumber",
					"memberNumber"
				]
			}
		}
	}
}
```
## Example

```
{
    "header": {
        "id": "832340f1-ac70-4d72-906b-af3a3719a4b9",
        "eventTitle": "New Card",
        "eventType": "Card",
        "eventCode": "New",
        "operationType": "Add",
        "eventDateTime": "2023-05-15T15:09:50Z",
        "eventVersion": "1.0.0",
        "source":"C"
    },
    "data": {
        "financialInstitutionId": "65200397",
        "cardNumber": "4000100020003477",
        "nonTransToken": "WUPIL5DQTZGM3477",
        "memberNumber": "0",
        "cardType": "A",
        "cmCardStatus": "Active",
        "cmReasonCode": "None",
        "expirationDate": "05/26",
        "digitalExpDate": "06/26",
        "cardClass": "ADMIN",
        "cardholderInfo": {
            "cardholderName": "MADHAVAN,PREMKUMAR",
            "personalizedEmbossingText":"Home Team",
            "primaryDob": "1982-10-30",
            "ssnOrTaxId": "xxxxx5678"
        },
        "primaryAddress": {
            "addressLine1": "ADRLINE1",
            "addressLine2": "ADRLINE2",
            "city": "EDISON",
            "state": "NY",
            "zip": "08834",
            "country": "USA"
        },
        "alternateAddress": {
            "addressLine1": "ALTADRLINE1",
            "addressLine2": "ALTADRLINE2",
            "city": "EDISON",
            "state": "NY",
            "zip": "08824",
            "country": "USA"
        },
        "activation": {
            "activationCreateDate": "23-05-15",
            "lastAttemptActivationStatus": "000"
        },
        "accounts": [
            {
                "number": "123456",
                "type": "20",
                "status": "3"
            },
            {
                "number": "7286102",
                "type": "10",
                "status": "1"
            },
            {
                "number": "ABC18364",
                "type": "31",
                "status": "9"
            }
        ],
        "contactIndicator": {
            "text": {
                "homePhone": "Y",
                "workPhone": "Y",
                "cellPhone": "Y"
            },
            "sms": "Y",
            "email": "Y"
        },
        "emailAndSms": {
            "email": "test@gmail.com",
            "sms": "8545785425",
            "language": ""
        },
        "contactInfo": {
            "homePhone": "6532356895",
            "workPhone": "2325325689",
            "cellPhone": "2325356897"
        },
        "securityInfo":{
          "mothersMaidenName": "Test",
          "verificationText": "passw0rd"
      	},
        "additionalAttributes": {
            "cardFeature": "0"
        }
    }
}
```
