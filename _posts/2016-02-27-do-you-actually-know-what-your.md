\-\-- layout: post title: \'Do You Actually Know What Your Automated
Test Is Doing? \' date: \'2016-02-27T14:04:00.002-05:00\' author: T.J.
Maher tags: - logging - test framework modified\_time:
\'2016-04-29T07:34:06.251-04:00\' blogger\_id:
tag:blogger.com,1999:blog-3868566217808655382.post-2186748731439972252
blogger\_orig\_url:
http://www.tjmaher.com/2016/02/do-you-actually-know-what-your.html \-\--
When it comes to automated tests for your software application, what is
more important?\
\

-   Knowing that a test passed or failed
-   Knowing *how* a test passed or failed 

\
Without adequate reporting, you will never be able to tell what is being
tested, how it is being tested, and whether the test is being thorough
enough.\
\
When I was a manual tester, I *always* made sure to write up a test
case.\
\

-   **Summary Heading** : What I am hoping the test is going to
    accomplish
-   **Steps to Reproduce**: A bullet pointed list of the specific
    parameters I am using to test the application, and where I am
    entering them.
-   **Results**:  What did I expect the results to be? What were the
    actual results? Did it (PASS) or (FAIL)? 

\
The Steps to Reproduce were quite important. When investigating the
possible failure, they might pass with a similar set of parameters, but
only fail with the exact parameters you used.\
\
[]{#more}\
\
Or, the problem might be between the keyboard and the chair: The results
might be correct, but my assumptions about how the product is supposed
to work is not.\
\
Or the test might only skim the surface of the application, and it does
not go deep enough to reach a trouble spot.\
\
Or the test might be mistakenly listing completely invalid data as being
perfectly valid.\
\
\... Without an audit trail, you can never truly be sure.\
\
I carried these habits into my new role as an automation developer.\
\

-   When my Selenium WebDriver test opens a web application, logs into
    the system, selects a link, enters text into a textbox, chooses a
    radio button or an item from a dropdown listbox, or clicks a button,
    I keep a record of it. 
-   When there is a unique ID such as an Order ID or a Confirmation
    Number, I keep a record of it. 
-   When my test goes to a unique page like the Order Summary Page for
    an order, a manual tester can use to go to the exact page than has
    the error, I keep a record of the url. 

<div>

That recording of the results can then can be archived by name and a
date/ timestamp, printed out in the Jenkins log files, or into an
application such as TestRail, storing what passed, what failed, and how
the tests were performed. 

</div>

\
\
Take a look at the following test. Without knowing anything about the
application, you can see exactly how the test was performed.\
\
**Verify Customer Service can process a Full Refund for ARIA \|
US-NON-TAX \| Free Shipping**\

\

``` {.CICodeFormatter}
 [ LOGIN: Going to the Commerce Admin Tool (CAT) Login page.  
   ,   
   , LOGIN: Entering Username.  
   , LOGIN: Enter Password.  
   , LOGIN: SUCCESS!  
   ,   
   , Navigating to the Service Home page...  
   ,   
   , SERVICE_HOME: Creating an Order:  
   ,      * Order Type: Standard Order  
   ,      * Clicking the 'SELECT_STORE_CONTAINER'.  
   ,      * Entering into the textbox: 'United States'  
   ,      * Selecting ProductFamily: 'Aria'  
   ,      * Selecting SKU Dropdown: 'Aria (White)'  
   ,      * Selecting [CREATE ORDER] button.  
   , SERVICE_HOME: Checking for errors...  
   , SERVICE_HOME: ... Errors Found: NONE.  
   , SERVICE_HOME: Proceeding to the Edit Order page.  
   ,   
   , EDIT_ORDER: Edit Order QA1-ABCD1234  
   ,   
   , EDIT_ORDER: Getting appropriate shipping levels for UNITED_STATES.  
   , EDIT_ORDER: Selecting Shipping Level radio button: Free  
   , EDIT_ORDER: Shipping and Billing Address are same. Entering Billing Address.  
   ,      * Country: United States  
   ,      * Name: Stripe70731 Test  
   ,      * Address1: 2445 E Old Penitentiary Rd  
   ,      * Address2:   
   ,      * City: Boise  
   ,      * PostalCode: 83712  
   ,   
   , EDIT_ORDER: The following credit card details were entered:   
   ,      * Credit Card Number: 5555555555554444  
   ,      * Expiration Month: 02  
   ,      * Expiration Year: 2018  
   ,      * CSC: 123  
   ,   
   , EDIT_ORDER: Entering Contact Info:  
   ,      * EMAIL: *** EMAIL ****  
   ,      * Phone: 6175555555  
   , EDIT_ORDER: Selecting REVIEW_BUTTON.  
   , EDIT_ORDER: Checking for page errors.  
   , EDIT_ORDER: Proceeding to the ORDER_CONFIRM_CHANGES page.  
   ,   
   ,   
   , ORDER_CONFIRM_CHANGES: Selecting [CONFIRM CHANGES] button.  
   , ORDER_CONFIRM_CHANGES: Verifying 404, 503 and other errors do not appear.  
   , EDIT_ORDER: Checking for highlighted errors on the top of EDIT_ORDER.  
   ,   
   ,   
   , Proceeding to SUMMARY_PAGE:   
   , *** SAMPLE LINK TO ORDER ***  
   ,   
   , SUMMARY_PAGE: Closing Flag: PendingFraudCheck  
   , SUMMARY_PAGE: Closing Flag: FailedFraudCheck  
   , SUMMARY_PAGE: Selecting [CHARGE_AND_FULFILL] button.   
   ,      * Acquiring the ORDER_ID.  
   ,      * ORDER_ID: *** ORDER ID ***  
   ,   
   , REFUND_ACTION: Attempting to Capture Payments to Process Refunds:  
   ,      * Update RefundID: *** SQL CODE used to get Charge IDs ***  
   ,      * Update CaptureID: *** SQL CODE to Capture a Charge ***  
   ,      * Update FulfillmentStatus: *** SQL CODE to Fulfill an Order ***  
   ,      * Update PaymentCapture: *** MORE SQL Code so manual testers can check results ***  
   , REFUND_ACTION: Processing CAPTURE_STATUS.  
   ,   
   , SUMMARY_PAGE: Refreshing the page.  
   ,      * Acquiring the ORDER_ID.  
   ,      * ORDER_ID: *** ORDER ID ***  
   , SUMMARY_PAGE: Selecting [REFUND_SELECTED_ITEMS] button.  
   ,   
   , REFUND: SELECTED_ITEMS: Page Header: Refund Information  
   , REFUND: SELECTED_ITEMS: Appearance of Page Elements are not currently being verified.  
   , REFUND_ACTION: Selecting Unit Price Refunding Rate: 100.00  
   , REFUND: SELECTED_ITEMS: UNIT_PRICE_REFUNDING_RATE: 100.00  
   , REFUND_ACTION: Charging a Restocking Fee: false  
   , REFUND_ACTION: Refunding Shipping: false  
   , REFUND: SELECTED_ITEMS: Message entered into REASON_FOR_REFUND textbox:   
   ,      * Message: This is a sample message  
   , REFUND: SELECTED_ITEMS: Selecting CONTINUE_TO_REVIEW button.  
   ,   
   , REFUND: SELECTED_ITEMS: Page Header: Refund Information  
   , REFUND_REVIEW: Selecting [CONFIRM REFUND] button.  
   ,   
   , REFUND_CONFIRM: Page Header: Refund Confirmed!  
   , REFUND_CONFIRM: Selecting BACK_TO_ORDER_SUMMARY button.  
   ,   
   , SUMMARY_PAGE: Refunded Amounts: [-129.95]  
   , SUMMARY_PAGE: Verify the amount refunded matches the refund listed on the page  
   ,      * Expected Value: 129.95  
   ,      * Actual Value: 129.95  
   ,      * The Expected and Actual Values match. (PASS)  
   ,   
   ]  
```

\
What if the audit trail was not there? If it passed, would you know if
it truly passed? If it failed, would you know what exactly failed?\
\
With an audit trail such as this, you know *exactly* what your automated
test is doing!\
\
\
-T.J. Maher\
 Sr. QA Engineer, Fitbit-Boston\
*// Software Quality Assurance Engineer for 15+ years*\
*// Automation Developer for \[ 1 \] year and counting*\
\
