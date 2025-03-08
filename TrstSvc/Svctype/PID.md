# PID Issuer (URI-based Identifier)

## Description
A trust service issuing and signing **Person Identification Data (PID)** based on verified identity attributes provided by an accredited registration authority. The issuer ensures the integrity and authenticity of issued PID credentials and supports verification through relevant status information services (e.g., revocation lists, validity checks) in compliance with **Regulation (EU) No 910/2014 (eIDAS)**. This may include **secure storage or management** of associated private keys on behalf of the holder.

## Requirements

The issuer must comply with **[EU Regulation 2024/2977](https://eur-lex.europa.eu/eli/reg_impl/2024/2979/oj)**, ensuring:

- Trust framework alignment for PID issuance and verification.
- Secure and auditable identity verification processes.
- Cryptographic key management following recognised security standards.
- Transparent validity status reporting (e.g., OCSP, CRL).
- Interoperability with **EU Digital Identity Wallets** aligned with EWC RFC012, published at https://ewc-consortium.github.io/eudi-wallet-rfcs/.
