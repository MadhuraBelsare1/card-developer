# Card Dispute
## Event is generated when the user raises a Dispute
#### Version: 1.0.0

## Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": "This event is generated when the user raises a Dispute",
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
          "description": ""
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
          "description": "Decrypted card number provided in place of the true PAN as additional level of security"
        },
        "nonTransToken": {
          "type": "string",
          "description": "NTT card number provided"
        },
        "originalClaimNumber": {
          "type": "string",
          "description": "The Dispute Expert generated unique Case Identifier. "
        },
        "claimNumber": {
          "type": "string",
          "description": "The Dispute Expert-generated unique Case Item Identifier used throughout the internal workflow, on UI and reports. "
        },
        "transactionDateAndTime": {
          "type": "string",
          "description": "The date of this case event as recorded by AdjustmentHub's current date/time clock. "
        },
        "lastEventDate": {
          "type": "string",
          "description": "The date of the preceding case status change. "
        },
        "caseOpenDate": {
          "type": "string",
          "description": "The date the Case Item was initially opened. "
        },
        "caseCloseDate": {
          "type": "string",
          "description": "The date the Case Item was closed. "
        },
        "caseOpenUserID": {
          "type": "string",
          "description": "The UserID who opened the Case. "
        },
        "caseCloseUserID": {
          "type": "string",
          "description": "The UserID who closed the Case Item. "
        },
        "openCode": {
          "type": "string",
          "description": "The AdjustmentHub-standard reason code assigned at the time of Case Item opening. "
        },
        "stateCode": {
          "type": "string",
          "description": "The AdjustmentHub-standard Case status. "
        },
        "closeCode": {
          "type": "string",
          "description": "The AdjustmentHub-standard status code assigned at the time of Case Item closing."
        },
        "initiatedBy": {
          "type": "string",
          "description": "Indicates if this exception item is being initiated by or on behalf of the Acquirer or Issuer. "
        },
        "initiationSource": {
          "type": "string",
          "description": "Indicates if this exception item is being initiated by an automated method. "
        },
        "networkReasonCode": {
          "type": "string",
          "description": "The network- / card-brand result / reason code for the approval or denial of a claim. "
        },
        "issuerDebitCreditcard": {
          "type": "string",
          "description": "Indicates if this case event is an issuer/cardholder Credit, Debit, or non-financial. "
        },
        "adjustmentAmount": {
          "type": "string",
          "description": "The financial amount of this case event to be used by the settlement system. "
        },
        "adjustmentInterChangeFee": {
          "type": "string",
          "description": "The MasterCard-supplied interchange fee. "
        },
        "comments": {
          "type": "string",
          "description": "The case analyst-supplied comments, notes or additional data entered on AdjustmetnHub. "
        },
        "dateSent": {
          "type": "string",
          "description": "The date the document was delivered into AdjustmentHub. "
        },
        "deliveryMethod": {
          "type": "string",
          "description": "2-character Fiserv-assigned code identifying the method used to deliver the document noted within the Date Document Sent field. "
        },
        "transactionId": {
          "type": "string",
          "description": "A unique record identifier for the original transaction as inserted into the TJF. "
        },
        "actionType": {
          "type": "string",
          "description": "Identifies the type of the original transaction. "
        },
        "networkId": {
          "type": "string",
          "description": "Identifies the Fiserv-assigned EPOC branded network/card scheme governing the transaction. "
        },
        "settlementDate": {
          "type": "string",
          "description": "The settlement date of the original financial transaction as reported by the card scheme / network settlement date. "
        },
        "settlementAmount": {
          "type": "string",
          "description": "The Authorized Amount, plus or minus any related authorization fees. "
        },
        "acquirerFIID": {
          "type": "string",
          "description": "The Fiserv-assigned ATM/POS terminal owner or merchant acquirer FIID. "
        },
        "acquirerFILogo": {
          "type": "string",
          "description": "The Fiserv-assigned ATM/POS Acquirer Logo. "
        },
        "arn": {
          "type": "string",
          "description": "The card scheme assigned Acquirer Reference Number associated with this case event. "
        },
        "cardAcceptorId": {
          "type": "string",
          "description": "Identifies the merchant name in a short string-format. "
        },
        "merchantId": {
          "type": "string",
          "description": "The Merchant Identifier assigned by the card scheme, and used to govern all aspects of KYB, settlement account identification, etc. "
        },
        "merchantType": {
          "type": "string",
          "description": "The 4-character card scheme-assigned Merchant Category Code. "
        },
        "originalTransactionDateTime": {
          "type": "string",
          "description": "The date/time of the original transaction as reported by the acquiring network, ATM, POS terminal, etc. "
        },
        "terminalId": {
          "type": "string",
          "description": "The ATM, POS or similar terminal / card-present device ID. "
        },
        "sequenceNumber": {
          "type": "string",
          "description": "The ATM, POS terminal sequential transaction sequence number as journaled electronically or printed by the source device. "
        },
        "terminalDescription": {
          "type": "string",
          "description": "The ATM/POS terminal or other transaction identification information governed by Reg E, suitable for cardholder statement description purposes. "
        },
        "posType": {
          "type": "string",
          "description": "A 1-character code indicating whether the source transaction was an ATM or POS/eCommerce transaction. "
        },
        "pin": {
          "type": "string",
          "description": "A 1-character Y/N (boolean) flag indicating if this is a PINed transaction. "
        },
        "pointOfServiceCode": {
          "type": "string",
          "description": "3-character code indicating the service type of the originating transaction channel. "
        },
        "cardPresent": {
          "type": "string",
          "description": "A 1-character Fiserv-assigned code indicating if the transaction is CNP or card-present. "
        },
        "issuerFIID": {
          "type": "string",
          "description": "The Fiserv-assigned card Issuer FIID. "
        },
        "issuerFILogo": {
          "type": "string",
          "description": "The Fiserv-assigned card Issuer Logo. "
        },
        "fromAccountType": {
          "type": "string",
          "description": "Deposit or credit account FROM type that was financially impacted/authorized/declined by the original transaction. "
        },
        "toAccountType": {
          "type": "string",
          "description": "Deposit or credit account TO type that was financially impacted/authorized/declined by the original transaction. "
        },
        "accountNumber": {
          "type": "string",
          "description": "Deposit or credit account number that was financially impacted by the original transaction. "
        },
        "accountCode": {
          "type": "string",
          "description": "The issuer/authorizer-generated code identifying the authorized or declined transaction. "
        },
        "amount1": {
          "type": "string",
          "description": "For Dispute Expert processing, the actual Settlement Amount is the amount subject to dispute processing. "
        },
        "txnDuid": {
          "type": "string",
          "description": "A unique record identifier in TJF. "
        },
        "uniqueIdentifier": {
          "type": "string",
          "description": "A unique value used to ensure idempotence, guaranteeing the Kafka subscriber processes the message only once. "
        }
      },
      "required": [
        "financialInstitutionId",
        "cardNumber"
      ]
    }
  }
}

```
## Example
```
{
    "header": {
        "id": "325b87f9-11ec-41e1-9875-bf6b32da366a",
        "eventTitle": "Card Dispute",
        "eventType": "Card",
        "eventCode": "Dispute",
        "operationType": "Update",
        "eventDateTime": "2023-05-23T14:47:34Z",
        "eventVersion": "1.0.0"
    },
    "data": {
        "financialInstitutionId": "65555800",
        "cardNumber": "4000100020003477",
        "nonTransToken": "WUPIL5DQTZGM3477",
        "originalClaimNumber": "13122503",
        "claimNumber": "13122503",
        "transactionDateAndTime": "20231016065928",
        "lastEventDate": "20231016065928",
        "caseOpenDate": "20231016065509",
        "caseCloseDate": "null",
        "caseOpenUserID": "ALNWTKAN11",
        "caseCloseUserID": "null",
        "openCode": "",
        "stateCode": "201",
        "closeCode": "null",
        "initiatedBy": "A",
        "initiationSource": "M",
        "networkReasonCode": "4853",
        "issuerDebitCreditcard": "C",
        "adjustmentAmount": 90153,
        "adjustmentInterChangeFee": 0,
        "comments": "Chargeback sent",
        "dateSent": "20231020",
        "deliveryMethod": "07",
        "transactionId": "MPLN2F6EW",
        "actionType": "44",
        "networkId": "655100",
        "settlementDate": "10-Oct-2023 00:00:00",
        "settlementAmount": 90153,
        "acquirerFIID": "65555800",
        "acquirerFILogo": "MCR3",
        "arn": "22223003282000249612548",
        "cardAcceptorId": "R-5411-USA",
        "merchantId": "MC Mandate",
        "merchantType": "5411",
        "originalTransactionDateTime": "20231005085857",
        "terminalId": "12345678",
        "sequenceNumber": "000736",
        "terminalDescription": "NY Short Hills MC Mandate ",
        "posType": "P",
        "pin": "N",
        "pointOfServiceCode": "007",
        "cardPresent": "1",
        "issuerFIID": "84008984",
        "issuerFILogo": "IFSL",
        "fromAccountType": "31",
        "toAccountType": "00",
        "accountNumber": "Test123456",
        "accountCode": "040577",
        "amount1": 90153,
        "txnDuid": "5734745120231011",
        "uniqueIdentifier": "EPOC131225034"
    }
}

```
