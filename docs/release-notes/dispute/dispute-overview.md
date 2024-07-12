# Dispute Overview

Dispute API gives financial institutions and cardholders a way to manage dispute cases for single or multiple transactions.

**<span style="color:#ff6600;">Availability:</span>** Debit Enhanced EPOC, Credit Gateway

 <h3 style="text-align: center">Features</h3>

<style>
.col-md-4 ul li {
    list-style: none;
}
</style>

<div class="row" style="text-align:center;" markdown=1>
<div class="col-md-4" markdown=1>

*   ![](assets/images/case-details.png)
    
    #### Case Details
    
   View status, case history and transactions of an existing dispute case.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/ease-of-access.png)

    #### Ease of Access
    
    Retrieve dispute case information of a cardholder.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/access-card.png)
    
    #### Reduce Operational Expenses
    
   Reduces time to dispute servicing by eliminating “swivel chair” process.
    
</div>
</div>



<span style="color:#ff6600;">**Dispute Details**</span> for dispute cases. 
* **Search by Card Number**: Retrieves dispute case details for a specifiedcard number.  
* **Search by Case ID**: Retrieves dispute case details for a specified case.
* **Search Case Item details**: Retrieves dispute case items details for a specified transaction.
* **Retrieve document by Case Item ID**: Retrieves  a document or image attached to a specified case item ID.
* **Retrieve Questionnaire by Case Item ID**: Retrieves  the completed questionnaire answers for a given case item.
 

<span style="color:#ff6600;">**Dispute Update**</span> adds notes and upload documents to dispute cases.
* **Upload Document by Case Item ID**: Can attach a document or image to a dispute case.
* **Add Note**: Add notes to a specified dispute case.
* **Delete by Case ID**: Cancels dispute case.
* **Delete by Case Item Id**: Cancels dispute case items for a specified case ID.
 

<span style="color:#ff6600;">**Dispute Create**</span> enables users to initiate and finalize a new claim and delete a Case Id in draft status.
* **Create Case**: Creates a dispute case for a card number's specified transactions.
* **Submit Case Questionnaire**: Submits a questionnaire for a case item.
* **Finalize Case**: Finalize the case intake for a case.
