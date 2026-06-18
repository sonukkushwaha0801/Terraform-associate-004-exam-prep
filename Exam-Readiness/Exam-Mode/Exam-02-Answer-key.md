# Terraform Associate (004) Exam 02 - Answer Key

## Answer Summary

| Q   | Ans | Q   | Ans | Q   | Ans | Q   | Ans |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | C   | 16  | B   | 31  | D   | 46  | C   |
| 2   | B   | 17  | A   | 32  | B   | 47  | B   |
| 3   | C   | 18  | C   | 33  | B   | 48  | C   |
| 4   | C   | 19  | A   | 34  | B   | 49  | A   |
| 5   | B   | 20  | B   | 35  | D   | 50  | A   |
| 6   | A   | 21  | C   | 36  | B   | 51  | B   |
| 7   | C   | 22  | B   | 37  | B   | 52  | C   |
| 8   | B   | 23  | B   | 38  | C   | 53  | C   |
| 9   | C   | 24  | C   | 39  | C   | 54  | A   |
| 10  | A   | 25  | A   | 40  | A   | 55  | A   |
| 11  | B   | 26  | A   | 41  | B   | 56  | C   |
| 12  | A   | 27  | C   | 42  | C   | 57  | A   |
| 13  | A   | 28  | B   | 43  | A   | 58  | A   |
| 14  | C   | 29  | C   | 44  | B   | 59  | B   |
| 15  | A   | 30  | C   | 45  | C   | 60  | C   |

---

## Detailed Answer Key

### Q1-Q10

1. C - terraform import
2. B - Variable Sets
3. C - depends_on
4. C - terraform init -upgrade
5. B - module
6. A - default
7. C - replace_triggered_by
8. B - required_providers
9. C - terraform version
10. A - variable

### Q11-Q20

11. B - module
12. A - output
13. A - output
14. C - locals
15. A - terraform show
16. B - terraform validate
17. A - count
18. C - locals
19. A - provider
20. B - terraform providers

### Q21-Q30

21. C - terraform fmt
22. B - dynamic
23. B - terraform init -upgrade
24. C - terraform state show
25. A - terraform apply *(Mock Exam Answer)*
26. A - terraform validate
27. C - Workspaces
28. B - count
29. C - terraform.tfvars
30. C - terraform destroy

### Q31-Q40

31. D - for_each
32. B - terraform output
33. B - provider
34. B - variable
35. D - data
36. B - terraform apply
37. B - terraform providers
38. C - terraform plan
39. C - terraform state rm
40. A - terraform plan

### Q41-Q50

41. B - depends_on
42. C - locals
43. A - backend.tf
44. B - terraform import
45. C - Workspaces
46. C - prevent_destroy
47. B - terraform init
48. C - data
49. A - variable
50. A - terraform plan -json

### Q51-Q60

51. B - terraform state list
52. C - replace_triggered_by
53. C - terraform state rm
54. A - terraform graph
55. A - terraform state rm
56. C - prevent_destroy
57. A - terraform state list
58. A - output
59. B - terraform refresh
60. C - output

---

## Score Sheet

| Score | Readiness              |
| ----- | ---------------------- |
| 54-60 | Exam Ready             |
| 48-53 | Likely Pass            |
| 42-47 | Needs Revision         |
| <42   | More Practice Required |

---

## Notes

### Technically Debatable Mock Answers

#### Q25

Mock Answer: `terraform apply`

Terraform automatically acquires a state lock when supported by the backend. There is no explicit lock command used during normal operations.

#### Q29

Mock Answer: `terraform.tfvars`

Variable values are commonly stored in `terraform.tfvars`, but Terraform does not require this specific filename.

#### Q43

Mock Answer: `backend.tf`

Backend configuration can exist in any `.tf` file. `backend.tf` is a common convention.
