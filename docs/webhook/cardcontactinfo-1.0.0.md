# Card Contact Info Event
 Event is generated when the Contact Info of the card is updated.
#### Version: 1.0.0

### Schema
```
{
	"$schema": "http://json-schema.org/draft-04/schema#",
	"type": "object",
	"description": "This event is generated when the Contact Info of the card is updated.",
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
						"contactInfo": {
							"type": "object",
							"properties": {
								"phone": {
									"type": "object",
									"properties": {
										"homePhone": {
											"type": "string",
											"description": "Home phone number of the cardholder"
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
									"description": "Indicates the language preference for EnFact Notifications. Values:E=English, S=Spanish (<spaces> = default to BIN level setting)",
									"enum": [
										"",
										"S"
									]
								}
							}
						},
						"contactIndicator": {
							"type": "object",
							"properties": {
								"text": {
									"type": "object",
									"properties": {
										"homePhone": {
											"type": "string",
											"description": "Home phone number of the cardholder",
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
						}
					}
				},
				"new": {
					"type": "object",
					"properties": {
						"contactInfo": {
							"type": "object",
							"properties": {
								"phone": {
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
        "eventCode": "ContactInfo",
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
            "contactInfo": {
                "phone": {
                    "homePhone": "854578457",
                    "workPhone": "124523124",
                    "cellPhone": "854214215"
                },
                "email": "test@gmail.com",
                "sms": "8457454124",
                "language": ""
            },
            "contactIndicator": {
                "text": {
                    "homePhone": "N",
                    "workPhone": "Y",
                    "cellPhone": "N"
                },
                "sms": "N",
                "email": "N"
            }
        },
        "new": {
            "contactInfo": {
                "phone": {
                    "homePhone": "8545124578",
                    "workPhone": "2352452123",
                    "cellPhone": "8956895623"
                },
                "email": "test123@gmail.com",
                "sms": "8747412456",
                "language": "S"
            },
            "contactIndicator": {
                "text": {
                    "homePhone": "Y",
                    "workPhone": "N",
                    "cellPhone": "Y"
                },
                "sms": "Y",
                "email": "Y"
            }
        }
    }
}
```
