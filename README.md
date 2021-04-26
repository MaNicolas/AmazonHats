# Automation testing on Amazon

Hi,

Here's a test I created using Selenium webdriver and Java.
I am using a Maven project structure with TestNG plugin to run my tests.
The design pattern is Page Object Model.

I will be testing the website “amazon.com” following a very simple scenario.
The idea is to search for some hats, add them to the cart and check that the number of items and total price are both correct.
The trick here is that the result of the search is dynamic (amazon is changing the results according to their own criteria), so the result will be different at every test run and cannot be foreseen in advance.

Here’s the steps to reproduce I will follow:
1. Go to https://www.amazon.com
2. Search for "hats for men"
3. Add first hat to the cart with quantity 2
4. Open the cart and make sure that total price and quantity are correct
5. Search for "hats for women"
6. Add first hat to the cart with quantity 1
7. Open the cart and make sure that total price and quantity are correct
8. Change the quantity for item selected at step 3 from 2 to 1 item in the cart
9. Make sure that total price and quantity are changed correctly

Here is a small documentation regarding the setup required and how to launch the tests.

In order to run the test, you'll need the following setup:
- Java version 1.8.0
- jdk-11.0.6
- Chrome browser version 88.0.4324.182
- Firefox browser version 86.0 (64-bit)
- Eclipse IDE

You will find 3 test suites XML files under "src\test\resources\TestSuites":
- AutomationExerciseTestSuite.xml (which basically run my test on Chrome and Firefox in parallel using parameters)
- WithCsvTestSuite.xml (The same but using a CSV file present in "src\test\resources\dataproviders")
- AllTests.xml (Which is running the 2 XML files)

To run the tests:
- Right click on one of those files
- "Run as"
- TestNG Suite

As for the report, you can find it in the console or under "amazon-hats\test-output\emailable-report.html",
"amazon-hats\test-output\index.html" or finally "amazon-hats\test-output\testng-results.xml"

Please note that throughout my code, you will find those 2 lines:
log.info("This line is for the console");
Reporter.log("This one is for the report in html");

I usually only use the "log.info", but I left both of them for your convenience so you can see the logs wherever you want.

Finally, if you wish to run the test many times automatically, I left the "@Test(invocationCount = X)" parameter available above the test method's name.
Just edit this parameter to your liking.

That's it! Thanks for reading me :)
Nicolas
