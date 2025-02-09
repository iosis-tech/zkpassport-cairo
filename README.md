# DSC Verification Algorithm in Cairo ZKVM

## Passport Verification Overview

Modern e‑Passports use a multi‑layered cryptographic process to ensure that the data stored on the chip is both authentic and untampered. The key components are:

### 1. MRZ (Machine Readable Zone)
- **Purpose:** The MRZ is a printed area on the passport that contains essential personal data (passport number, date of birth, expiration date, etc.).
- **Role in Cryptography:** The data read from the MRZ is used to derive symmetric session keys (via hashing) in protocols like Basic Access Control (BAC) or Password Authenticated Connection Establishment (PACE). These keys “unlock” the passport’s chip so that its data can be accessed only when the physical document is present.

### 2. CSCA (Country Signing Certification Authority)
- **Purpose:** The CSCA is the root of trust in a country’s Public Key Infrastructure (PKI) for e‑Passports.
- **Role in Cryptography:** A self‑signed CSCA certificate contains the country’s public key and is used to sign Document Signer Certificates (DSCs). This signature binds the DSC to the trusted root and ensures that only the issuing state can generate valid DSCs.

### 3. DSC (Document Signer Certificate)
- **Purpose:** The DSC is an intermediate certificate used to digitally sign the passport’s data.
- **Role in Cryptography:** During passport personalization, the DSC’s corresponding private key is used to sign a collection of data (usually stored in the Document Security Object or SOD) that includes biometric and personal information. Verification involves checking:
  - The digital signature on the SOD using the DSC’s public key.
  - The DSC’s signature itself, which is validated against the CSCA.
  
Together, these steps establish a **chain of trust** that ensures the data on the chip is authentic and has not been altered.

---

## Contributing

Contributions and guidance are very welcome!