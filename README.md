# Paystation payment module for Ubercart

This integration is currently only tested up to Drupal 7.31 with Ubercart 3.6

## Requirements
* An account with [Paystation](https://www2.paystation.co.nz/)
* An HMAC key for your Paystation account, contact our support team if you do not already have this <support@paystation.co.nz>

## Installation

These instructions will guide you through installing the module and conducting a test transaction. 

After you have correctly installed Drupal and Ubercart:

1. Login into your Drupal site as the administrator.

2. Select the Modules tab, and click "Install new module". If the Install new module link is not present, first enable the 'Update manager' module.

3. In the box labelled "Upload a module or theme archive to install", select the name of this ZIP file, and click "Install". 

4. On the Update Manager page, select a connection method (SSH or FTP). The username and password required are those for your SSH or FTP account on the server your Drupal site is on. These are NOT the same username and password you used in Step 1 to login into the administration pages of your drupal site. 

5. If the installation is successful, the message "Installation was completed successfully" will appear after 
installation.

6. Click "Enable newly added modules"

7. Find 'Paystation three-party payment module' under the 'UBERCART - PAYMENT' heading.

8. Check the Enabled box, scroll to the bottom of the page, and click 'Save configuration'. It may take a few moments to enable the module, and when this is completed "The configuration options have been saved" will appear at the top of the page.

9. Select the Store tab. 

10. Click Payment Methods (under Configuration).

11. In the Operations Column, next to 'Paystation Payment Gateway', click on 'settings'.

12. On the Paystation Payment Gateway settings page, set 'Paystation ID' to the Paystation ID provided. 

13. Set 'Gateway ID' to the Gateway ID provided. 

14. Set 'HMAC key' to the HMAC key provided.

15. We strongly suggest checking the "Enable Postback" box, as it will allow the cart to capture payment results even if your customers re-direct is interrupted. However, if your development/test environment is local or on a network that cannot receive connections from the internet, you must disable Postback.

Your Paystation account needs to reflect your Ubercart settings accurately, otherwise order status will not update correctly.

16. Check the 'Enable test mode' check box. 

17. Optionally, you can change 'Payment method title'. This is the text that the Paystation Payment Gateway method is
labelled as on the checkout page.

18. Click 'Save Configuration'

19. The URL for both return and postback is: [host + drupal directory]/cart/paystation_cc/complete

For example - www.yourwebsite.co.nz/drupal/cart/paystation_cc/complete
- send this to support@paystation.co.nz with your Paystation ID and request your Return URL  and Postback URL to be updated.

20. Go to your online store.

21. To do a successful test transaction make a purchase where the final cost will have the cent value set to .00, for example $1.00, this will return a successful test transaction.  To do an unsuccessful test transaction make a purchase where the final cost will have the cent value set to anything other than .00, for example $1.01-$1.99, this will return an unsuccessful test transaction. 

Important: You can only use the test Visa and Mastercards supplied by Paystation for test transactions. They can be found here Visit the Test Card Number page.

22. When you go to checkout - make sure you choose Paystation Payment Gateway in the Payment method section.

23. Once the site is working as expected you will need to fill in the form found on https://www2.paystation.co.nz/go-live so that Paystation can test and set your account into Production Mode.

24. Once Paystation have confirmed the Paystation account is live, go back to the Payment Payment Gateway settings, and uncheck the 'Enable test mode' check box in the Paystation method settings.

25. Congratulations - you can now process online credit card payments!

Notes: 
Orders with successful payments will have a status of 'Payment received'.
Orders with unsuccessful payments will have a status of 'Paystation payment unsuccessful'.
