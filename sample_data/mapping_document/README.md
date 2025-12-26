Mapping document from legacy fields to Guidewire ClaimCenter entities
| Term        | Meaning                     | Why it matters                  |
| ----------- | --------------------------- | ------------------------------- |
| Loss Date   | Date when incident occurred | Drives coverage applicability   |
| Report Date | Date claim was reported     | Affects timeliness & compliance |
| Coverage    | What policy covers          | Controls payments               |
| Deductible  | Amount insured pays         | Must reduce payment             |
| Reserve     | Expected future payout      | Impacts financials              |
| Payment     | Actual money paid           | Financial accuracy              |

| Legacy Table.Column   | ClaimCenter Entity.Field | Rule                              |
| --------------------- | ------------------------ | --------------------------------- |
| LEGACY_CLAIM.CLAIM_ID | Claim.ClaimNumber        | 1–1                               |
| LOSS_DATE             | Claim.LossDate           | 1–1                               |
| REPORT_DATE           | Claim.ReportedDate       | Default = LossDate if NULL        |
| CLAIM_STATUS          | Claim.State              | Lookup (OPEN→Open, CLOSED→Closed) |
| DEDUCTIBLE            | Exposure.Deductible      | Default 0 if NULL                 |
| RESERVE.AMOUNT        | ReserveSet.Amount        | Sum by Claim                      |
| PAYMENT.PAID_AMOUNT   | Transaction.Amount       | Validate ≤ Reserve                |
