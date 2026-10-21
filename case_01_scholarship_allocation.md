# Case Study 01: University Scholarship Allocation

## 1. Problem Statement
Design a rule-based system that determines scholarship eligibility and estimates the award amount from a student's CGPA, annual family income, and category. The rules are illustrative academic rules, not official university policy.

## 2. Objectives
- Validate student inputs
- Apply multiple eligibility conditions
- Calculate an award using a percentage cap
- Explain why an applicant qualifies or does not qualify

## 3. Assumptions
- CGPA is between 0 and 10 inclusive.
- Annual family income cannot be negative.
- Eligibility requires CGPA >= 8.0 and annual family income <= ₹300,000.
- Eligible students receive 50% of the annual fee, capped at ₹40,000.

## 4. Algorithm
1. Read CGPA, annual family income, and annual fee.
2. Reject invalid values.
3. Check the CGPA and income conditions.
4. If eligible, calculate min(50% of fee, ₹40,000); otherwise award zero.
5. Return eligibility, reason, and amount.

## 5. Flowchart
```mermaid
flowchart TD
    N0[Start] --> N1
    N1[Validate CGPA, income and fee] --> N2
    N2[CGPA >= 8.0?] --> N3
    N3[Income <= ₹300,000?] --> N4
    N4[Award = min(50% fee, ₹40,000)] --> N5
    N5[Return eligibility and award] --> N6
    N6[End]
```

## 6. Pseudocode
```text
FUNCTION allocate(cgpa, income, fee)\n  VALIDATE 0 <= cgpa <= 10 AND income >= 0 AND fee >= 0\n  IF cgpa < 8.0: RETURN not eligible, reason\n  IF income > 300000: RETURN not eligible, reason\n  award = MIN(fee * 0.50, 40000)\n  RETURN eligible, award\nEND
```

## 7. Python Source Code
See [`../programs/scholarship_allocation.py`](../programs/scholarship_allocation.py).

## 8. Test Cases with Solutions
| Test | Input / scenario | Expected solution |
|---|---|---|
| 1. Eligible student | CGPA=8.6, income=250000, fee=70000 | Eligible; award ₹35,000.00 |
| 2. CGPA below threshold | CGPA=7.5, income=200000, fee=70000 | Not eligible; award ₹0.00 |
| 3. Income above limit | CGPA=9.2, income=350000, fee=70000 | Not eligible; award ₹0.00 |
| 4. Maximum award cap | CGPA=9.0, income=100000, fee=100000 | Eligible; award ₹40,000.00 |

## 9. Execution Output
Screenshot: `../screenshots/case_01_output.png`.

```text
UNIVERSITY SCHOLARSHIP ALLOCATION
Eligible, fee ₹70,000: eligible=True, award=₹35000.00 (All criteria satisfied)
Low CGPA: eligible=False, award=₹0.00 (CGPA below 8.0)
Income too high: eligible=False, award=₹0.00 (Income exceeds ₹300,000)
Award cap: eligible=True, award=₹40000.00 (All criteria satisfied)
```

## 10. Test Execution
Automated test file: [`../tests/test_case_01.py`](../tests/test_case_01.py).

```text
test_01_primary (rerun_test_case_01.TestCase01.test_01_primary) ... ok
test_02_boundary (rerun_test_case_01.TestCase01.test_02_boundary) ... ok
test_03_alternate (rerun_test_case_01.TestCase01.test_03_alternate) ... ok
test_04_edge (rerun_test_case_01.TestCase01.test_04_edge) ... ok

----------------------------------------------------------------------
Ran 4 tests in 0.000s

OK

```

## 11. Conclusion
The program implements the specified rules and was checked against the listed test scenarios. Thresholds and rates are illustrative academic assumptions and should be replaced with official requirements if provided by faculty.
