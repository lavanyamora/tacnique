//TEST ANALYSIS

TASK 1

TC-01 · Employee (6 months' tenure) submits FMLA request → Expected: status "Submitted"
Requirement Given : Eligible after 12 months AND 1,250 hours worked.
What is wrong :
1.Employee in the first place should not be able to submit the request(any error message :Not eligible for this FMLA request)
2.Status should not be changed to "submitted"(Either it should throw an error or like status should be rejected)
Correct Behaviour : It should check eligibility according to the requirements

TC-02 · Manager approves FMLA request → Expected: status "Approved," employee notified
Requirement Given : Approve/reject leave for direct reports only — not skip-level
What is wrong :
1.It is not checking eligibility / authorization manaher can only approve/reject for direct reportees
2.Based on that the status can be changed and notified to employee
Correct Behaviour : It should check eligibilty of manager /Authorization

TC-03 · FMLA request approved; employee had 3 sick days → Expected: sick balance −5, FMLA balance −5
Requirement Given : FMLA does not auto-deduct from sick leave — this is an optional employer setting, default off.
What is wrong :
1.FMLA and sick leave cant be combined.
2.FMLA should not decuct from sick leaves also the calculation needs to be checked independently
3.By default configuration is set to off. So we need to check how the system caluculates leave balances - both conditions when the flag is set on and also off
Correct Behaviour : It should check first the configuration settings. Based on the flag enabled, disabled and according to requirements leave balances should eb calculated

TC-04 · Employee already used 10 weeks FMLA this calendar year, submits 3 more weeks → Expected: system blocks the request
Requirement Given :FMLA(Family and Medical Leave Act): US federal law giving eligible employees up to 12 weeks of unpaid, job-protected leave per rolling 12-month period.
What is wrong :
1.As per requirement, employee has already availed 10 weeks and only 2 weeks can be provided.
2.Duration must be calculated for 12 months not just the calendar year.
eg : JULY 2026- JUNE 2027
3.Instead of just blocking, show a clear message why the system behaves like that and can redirect the employee to FMLA policies
Correct Behaviour : It should check the calculations correctly and duration of entitled leave

TC-05 · Manager is on leave; Payroll Processor approves the pending request → Expected: request approved
Requirement Given : Payroll processor : Read-only — no approvals, no submissions
What is wrong
1.Violates permissions/ Security issues Payroll processor can only read and not supposed to do any other edits
2.If Manager is on-leave, who can take the reponnsibility - If we should redirect to hr admin (full access) or any other substitue approver that needs to be clarified.
3.Request should not be approved
Correct Behaviour : It should check the permissions, roles, Read write polocies and all security related aspects

TC-06 · Manager approves 3-day annual leave request; balance was 10 days → Expected: balance updates to 7 immediately
Requirement Given :
What is wrong :
1.Here Ai generated test cases for sick leave scenarios which it should not
2.The test case is correct but under sick leave type scenarios
Correct Behaviour : It should check relevant information, does this test belong here, Correctness and completeness

TASK 2
Missing Scenarios :
1.Should check eligibility of the employee of both conditions (Requirement Given : Eligible after 12 months AND 1,250 hours worked.)
employee worked 12 months but doesnt fulfill 1250 hrs - Ineligible
Employee worked 11 months but completed 1300 hrs - Still In-eligible
Employee worked 12 months fulfilled 1250 hrs - Only eligible
Boundary cases 1249 hrs, 1250hrs, 1251 hrs, 11 months 27 days, 12 months, 12 months 10 days

2.Should check manager authorization
Manager should only able to approve / reject direct reportees

3.Should check Configuration settings
By default flag is set to off, but it was not mentioned how the system behaves when the flag is enabled

TASK 3 :
severity :
TC-01 (eligibility), TC-05, TC-02 (Security / Authorization issues) TC-03 (Configuration issues) TC-03, TC-06 (Incorrect calculations)

TASK 4 :
AI PROMPT : Verify the rquirements, Validate the correct incorrect test cases, identify the gaps, missing tests, without hallucinations
OUTPUT :
| TC | Result | Reason  
| **TC-01** | ⚠️ **Incorrect / Needs clarification** | Employee has only 6 months tenure, so they are **not FMLA eligible**. Requirement doesn't say whether they should be blocked from submitting or allowed to submit. |
| **TC-02** | ✅ **Correct** | Manager can approve leave for a **direct report**. Notification is not clearly defined in the requirements, so that part needs confirmation. |
| **TC-03** | ❌ **Incorrect** | FMLA **does not deduct sick leave by default**. Sick balance should not reduce. |
| **TC-04** | ⚠️ **Needs correction** | FMLA limit is **12 weeks in a rolling 12-month period**, not calendar year. The blocking logic is correct if 10 + 3 = 13 weeks within the rolling period. |
| **TC-05** | ❌ **Incorrect** | Payroll Processor is **read-only** and cannot approve requests, even if the manager is on leave. |
| **TC-06** | ✅ **Correct** | 10 days − 3 days = **7 days**. Manager can approve for a direct report. |

Final: TC-02 and TC-06 are correct; TC-03 and TC-05 are incorrect; TC-01 and TC-04 need clarification/correction.

Its says 2 and 6 are correct based on the anaalysis but for test case 2 also it should mark need more info, TC-06 is also correct but its not checking if the test cases falls under the correct sceanrio
