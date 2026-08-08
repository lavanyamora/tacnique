CASE A :

Title : Leave balance is not properly updating after annual leave approval even after multiple refreshes
Severity : Medium beacuse its not blocking the employee or manager to submit or approve the leave
Preconditions
Test data:
Environment :
Description:
Steps to Reproduce :
1.login to Meridian corp as priya
2.Check the leave balance
3.Submit the 5 days leave request
4.Approved by manager on the same day
5.After one hour check the leave balance
6.Refresh the screen and try to fetch updated leave balance

Expected Behaviour : Once leave is approved by manager, leave balance should be updated correctly
Actual Behaviour : Leave balance is not updated properly

CASE B :
1.Log a defect, with need more info status for tracking purpose
2.Check the roles, permissions, network calls, timestamp, environment, error message details, screenshots
3.Try to reproduce the issue in other environments with similar data setup

CASE C :
According to me, the bug is not a genuine , because as leaves are already approved, the system says "its finalized" and would like to rquest a new one, This is how generally any leave request (AGAIN DEPENDS ON REQUIREMENTS)
1.Need to refer existing test cases on how system behaves for already approved leaves
2.Check the rquirements , documents, user stories and and still if the information is not clear, i would like to check with PRODUCT OWNER and BUSINESS ANALYST
3.I will not directly loa a defect rather i would check with existing info and clearly explain if the behaviour is intended
4.As HR have full access will redirect the bug reporter to the policies
