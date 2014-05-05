Login Screen
============

Overview
--------

This spec is for the login screen of the application. The overall design of
the screen is in the file 'mockup.png'.

The Controls
------------

* The 'username' box accepts alphanumeric characters.
* The limit of the 'username' box is 120 characters.
* The tooltip for the username box is 'Enter Username'.
* The password box accepts any characters and is limited to 120 characters.
* The tooltip for the password box is 'Enter password'.

Logging In - Happy Path
-----------------------

If the controls are filled in correctly as stated above, the
successful login process is:

1. The 'login' button is enabled by default.
2. User enters a username.
3. User enters a password.
4. When 'login' is pressed, the button immediately becomes disabled
   and a spinner is shown to the left of the button caption.
5. When login succeededs, the application immediately moves to the 'profile'
   page.

Logging In - First Time Validation
----------------------------------

The login form will only show validation messages AFTER a click of the login
button. Rather than confusing the user with lots of red boxes with warning messages
such as 'the password field is mandatory', we'll give them a chance to key everything
in right first. If there's anything wrong, *then* we show the validation messages.
 
Logging In - Bad Credentials
----------------------------

If the controls are filled in correctly, but the credentials
are wrong, the login process is:

1. User enters a (bad) username.
2. User enters a (bad) password.
3. The 'login' button becomes enabled.
4. When 'login' is pressed, the button immediately becomes disabled
   and a spinner is shown to the left of the button caption.
5. When login fails:
   * The spinner disappears
   * The caption becomes 'login'
   * The password box is cleared.
6. Finally, an alert above the login box is shown with the title 'Login Failed'
   and the message 'Your username or password is incorrect'.