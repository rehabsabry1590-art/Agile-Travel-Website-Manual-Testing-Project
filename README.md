# Agile Travel Website - Manual Testing Project

## Project Overview
This project focuses on manual testing for the Agile Travel website, including test case design, execution, and defect reporting to ensure system quality and functionality.

I started this project while learning manual testing. My goal was to go beyond theory and run a complete testing cycle end to end: analyse the application, design test cases, execute them, log defects with evidence, and report the results the way it is done on a real team.

**Application under test:** [Agile Travel](https://travel.agileway.net) – a publicly available demo application used for software-testing practice
**Environment:** Google Chrome
**Testing type:** Manual – functional, negative, and input-validation testing

## Website Screenshot
![Agile Travel Website](images/Screenshot%202026-05-17%20102128.png)

## Testing Activities
- Exploratory Testing
- Test Case Design
- Positive & Negative Testing
- Validation Testing
- Bug Reporting
- Defect-to-test-case traceability

## Repository Contents

| File | Description |
|---|---|
| [`Test Cases.pdf`](Test%20Cases.pdf) | 41 test cases with steps, test data, expected and actual results, and execution status |
| [`Bug Report.pdf`](Bug%20Report.pdf) | 26 defects with steps, expected vs. actual result, severity, priority, and the linked test case |
| [`Summary.pdf`](Summary.pdf) | Test summary report |
| [`images/`](images/) | Screenshot of the application under test |

## Scope

| Module | What was tested |
|---|---|
| **Select Flight** | Trip type (one-way / return), origin and destination, departure and return dates, required fields, date logic |
| **Passenger Details** | First and last name: valid input, upper/lower case, special characters, numbers, very long values, empty values, non-English (Unicode) input |
| **Payment** | Card type, card number, card holder name, expiry date, valid Visa/MasterCard payments, invalid and empty inputs, repeated clicks on *Pay now* |

## My Approach

1. **Explored the application** and identified the main user flow: select flight → passenger details → payment.
2. **Designed test cases** covering both positive (valid) and negative (invalid) scenarios, including boundary-style cases such as today's date, a past date, the same departure and return date, and over-length input.
3. **Wrote the test cases in Jira**, each with a clear objective, steps, test data, and expected result.
4. **Executed every test case** and recorded the actual result and pass/fail status.
5. **Logged a defect in Jira for every failure**, linked it to its test case for full traceability, and attached a screenshot showing where the problem appears in the application.
6. **Documented everything in Excel** (test cases, bug report, and summary) and exported it to PDF, so the results can be reviewed without Jira access.
7. **Reviewed the documents for consistency** and corrected errors such as copy-paste mistakes in actual results, unclear test data, and inconsistent severity ratings.

## Results

| Module | Total | Passed | Failed |
|---|:---:|:---:|:---:|
| Select Flight | 12 | 4 | 8 |
| Passenger Details | 16 | 9 | 7 |
| Payment | 13 | 2 | 11 |
| **Total** | **41** | **15** | **26** |

**26 defects** were reported, one for each failed test case:

| Severity | Count |
|---|:---:|
| High | 11 |
| Medium | 12 |
| Low | 3 |

## Key Findings

- **Payment accepts invalid data.** Payments were processed with an expired card date, an empty card number, letters or special characters in the card number, and card numbers that were too short or too long (e.g. Bug_Reg_016, 017, 020–023).
- **No protection against duplicate payments.** Clicking *Pay now* repeatedly was not blocked, which could lead to double charges (Bug_Reg_026).
- **Booking rules are not enforced.** The application accepted a return date earlier than the departure date, a past departure date, and identical origin and destination (Bug_Reg_002, 003, 005).
- **Required fields are not validated on the flight page.** Missing return date, departure date, origin, or destination did not produce an error message (Bug_Reg_001, 006, 007, 008).
- **Name fields lack validation.** Numbers, special characters, and over-length values were accepted. The empty *Last name* field was validated correctly, but the empty *First name* field was not (Bug_Reg_009–015).
- **What works as expected:** valid one-way and return bookings, same-day return trips, valid Visa and MasterCard payments, upper/lower-case names, and non-English (Arabic) names.

## Sample Defect

| Field | Details |
|---|---|
| **ID** | Bug_Reg_016 |
| **Title** | Payment → Error message does not appear when selecting an expiry date in the past |
| **Linked test case** | TC_Reg_029 |
| **Steps** | 1. Select card type 2. Enter valid card holder name 3. Enter valid card number 4. Select an expiry date in the past (01/2025) 5. Click *Pay now* |
| **Expected** | Error message is displayed and payment is not processed |
| **Actual** | Error message is not displayed and payment is processed |
| **Severity / Priority** | High / High |

## Tools Used
- Jira
- Microsoft Excel
- Google Chrome

## Notes

- The application is a demo site, so some missing validations may be intentional. The findings show how I evaluate a form against standard expected behaviour, not a claim about a production system.
- Expected results are based on common, standard behaviour for booking and payment forms, since no formal requirements document was available.
- Bug_Reg_004 (booking multiple flights at the same time) is based on an assumed business rule and would need confirmation against real requirements.

## Skills Demonstrated

- Test case design (positive, negative, boundary-style scenarios)
- Manual test execution and result tracking
- Defect reporting with clear steps, expected vs. actual results, severity, priority, and screenshots
- Requirement-to-defect traceability (every bug linked to its test case)
- Working with Jira and Excel
- Reviewing and improving QA documentation for accuracy and consistency
