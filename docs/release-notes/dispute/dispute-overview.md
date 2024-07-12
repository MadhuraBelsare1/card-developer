# Dispute overview

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
    
    #### Case details
    
   View status, case history and transactions of an existing dispute case.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/ease-of-access.png)

    #### Ease of access
    
    Retrieve dispute case information of a cardholder.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/access-card.png)
    
    #### Reduce operational expenses
    
   Reduces time to dispute servicing by eliminating “swivel chair” process.
    
</div>
</div>



<span style="color:#ff6600;">**Dispute details**</span> feature helps manage dispute cases. 
* **Search by card number**: retrieve dispute case details for a specifiedcard number.  
* **Search by case ID**: retrieve dispute case details for a specified case.
* **Search case item details**: retrieve dispute case items details for a specified transaction.
* **Retrieve document by case Item ID**: retrieve  a document or image attached to a specified case item ID.
* **Retrieve questionnaire by case item ID**: retrieve  the completed questionnaire answers for a given case item.
 

<span style="color:#ff6600;">**Dispute update**</span> feature can add notes and upload documents to dispute cases.
* **Upload document by case item ID**: attach a document or image to a dispute case.
* **Add note**: Add notes to a specified dispute case.
* **Delete by case ID**: Cancels dispute case.
* **Delete by case item ID**: Cancels dispute case items for a specified case ID.
 

<span style="color:#ff6600;">**Dispute Create**</span> feature can initiate and finalize a new claim and delete a Case Id in draft status.
* **Create case**: create a dispute case for a card number's specified transactions.
* **Submit case questionnaire**: submit a questionnaire for a case item.
* **Finalize case**: finalize case intake.
