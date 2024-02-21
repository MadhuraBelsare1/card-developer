# Dispute Release Note

Dispute API enables users to manage dispute cases for multiple or a single transaction.

**Platform Support**: Debit Enhanced EPOC, Credit Gateway

### Features


**Dispute Details** enables users to manage dispute cases.

  * Search by Card Number: Retrieves dispute case details for a given card number. 
  * Search by Case Id: Retrieves dispute case details for a given case.
  * Search Case Item details: Returns dispute case Item details for a disputed transaction.
  * Retrieve document by Case Item Id: Retrieves a document or image attached to a give case item id. 
  * Retrieve Questionnaire by Case Item Id: Retrieves the completed questionnaire answers for a given case item. 
 

**Dispute Update** enables users to add notes and upload documents to dispute cases.

  * Upload Document by Case Item Id: Allows to attach a document or image to a dispute case. 
  * Add Note: Update a given dispute case with notes.
  * Delete by Case Id: Cancels dispute case.
  * Delete by Case Item Id: Cancels dispute case Items for a given case id.
 

**Dispute Create** enables users to initiate and finalize a new claim and delete a Case Id in draft status.

  * Create Case: Creates a dispute case for given transactions of a particular card number.
  * Submit Case Questionnaire: Submits the questionnaire for a case item.
  * Finalize Case: Finalize the case intake for a case.
