Validation and reconciliation queries and checks

Record Count Check
SELECT COUNT(*) FROM LEGACY_CLAIM;
SELECT COUNT(*) FROM CC_CLAIM;

Financial Reconciliation
SELECT 
  SUM(PAID_AMOUNT) AS LegacyPayments
FROM LEGACY_PAYMENT;

SELECT 
  SUM(Amount) AS ClaimCenterPayments
FROM CC_TRANSACTION;

Defect Detection
SELECT CLAIM_ID
FROM LEGACY_PAYMENT p
JOIN LEGACY_RESERVE r ON p.CLAIM_ID = r.CLAIM_ID
WHERE p.PAID_AMOUNT > r.AMOUNT;



