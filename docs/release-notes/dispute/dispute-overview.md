# Dispute Overview

Dispute API enables users to manage dispute cases for multiple or a single transaction.

 

**<span style="color:#ff6600;">Availability:</span>** Debit Enhanced EPOC, Credit Gateway

### Features

<style>
.col-md-4 ul li {
    list-style: none;
}
</style>

<div class="row" style="text-align:center;" markdown=1>
<div class="col-md-4" markdown=1>

*   ![](assets/images/case-details.png)
    
    #### Case Details
    
   View the status, case history and transactions of an existing dispute case.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/ease-of-access.png)

    #### Ease of Access
    
    Enable users to easily retrieve dispute case information for a cardholder.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/access-card.png)
    
    #### Reduce Operational Expenses
    
   Reduce time allocated to dispute servicing by eliminating “swivel chair” process.
    
</div>
</div>



<span style="color:#ff6600;">**Dispute Details**</span> enables users to manage dispute cases. 

* **Search by Card Number**: Retrieves dispute case details for a given card number.  
* **Search by Case ID**: Retrieves dispute case details for a given case.
* **Search Case Item details**: Retrieves dispute case items details for a disputed transaction.
* **Retrieve document by Case Item ID**: Retrieves  a document or image attached to a given case item id. <br>
* **Retrieve Questionnaire by Case Item ID**: Retrieves  the completed questionnaire answers for a given case item.
 

<span style="color:#ff6600;">**Dispute Update**</span> enables users to add notes and upload documents to dispute cases.

* **Upload Document by Case Item ID**: Allows to attach a document or image to a dispute case.
* **Add Note**: Update a given dispute case with notes.
* **Delete by Case ID**: Cancels dispute case.
* **Delete by Case Item Id**: Cancels dispute case Items for a given Case Id.
 

<span style="color:#ff6600;">**Dispute Create**</span> enables users to initiate and finalize a new claim and delete a Case Id in draft status.

* **Create Case**: Creates a dispute case for given transactions of a particular card number.
* **Submit Case Questionnaire**: Submits the questionnaire for a case item.
* **Finalize Case**: Finalize the case intake for a case.
