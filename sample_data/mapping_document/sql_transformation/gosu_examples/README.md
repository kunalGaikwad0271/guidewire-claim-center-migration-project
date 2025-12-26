Gosu examples used for ClaimCenter migration
if (claim.ReportedDate == null) {
  claim.ReportedDate = claim.LossDate
}

Validation Rule

if (payment.Amount > claim.TotalReserves) {
  throw new ValidationException("Payment exceeds reserve")
}

Transformation

claim.State = claim.LegacyStatus == "OPEN" ? "Open" : "Closed"


