# Onboarding to EWC Trust List

This document describes how to onboard a new organisation to the EWC Trust List by submitting a pull request (PR) to the [ewc-consortium/ewc-trust-list](https://github.com/ewc-consortium/ewc-trust-list) GitHub repository.

The EWC Trust list is based on ETSI TS 119 475 (EU Trust List).

## Requirements before submission

Make sure you have the following:

- ✅ Legal entity and trade name
- ✅ Complete postal and electronic address
- ✅ A valid **X.509 Certificate** with Subject Key Identifier (SKI)/Distinguished Name or DID or JWK
- ✅ Public endpoints (wallet URLs or verifiable credential APIs)
- ✅ Correct **Service Type Identifier** from [supported types](#supported-service-types)

## 🔖 Supported Service Types

| Identifier | Description                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `NPWP`     | Non-Personal Wallet Provider                                                                                                                     |
| `PID`      | Person Identification Data Issuer                                                                                                                |
| `EAA`      | Electronic Attribute Authority                                                                                                                   |
| `LPWP`     | Legal Person Wallet Provider                                                                                                                     |
| …          | See full list [in repo](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc012-trust-mechanism.md#32-list-of-service-type-uris) |


## How to add your company to EWC Trust List

### Step 1: Fork the Repository

Fork [`ewc-consortium/ewc-trust-list`](https://github.com/ewc-consortium/ewc-trust-list) to your organisation's GitHub account.

### Step 2: Clone and create a new branch

```bash
git clone https://github.com/<your-org>/ewc-trust-list.git
cd ewc-trust-list
git checkout -b add-your-org-to-tl
```

### Step 3: Edit the XML Trust List

Update `EWC-TL.xml` with the following XML snippet added under `<TrustServiceProviderList>`:

```xml
<TrustServiceProvider>
  <TSPInformation>
    <TSPName><Name xml:lang="en">Your Org Name</Name></TSPName>
    <TSPTradeName><Name xml:lang="en">Your Legal Name</Name></TSPTradeName>
    <TSPAddress>
      <PostalAddresses>
        <PostalAddress xml:lang="en">
          <StreetAddress>Street</StreetAddress>
          <Locality>City</Locality>
          <PostalCode>12345</PostalCode>
          <CountryName>SE</CountryName>
        </PostalAddress>
      </PostalAddresses>
      <ElectronicAddress>
        <URI xml:lang="en">mailto:contact@example.org</URI>
      </ElectronicAddress>
    </TSPAddress>
    <TSPInformationURI>
      <URI xml:lang="en">https://example.org</URI>
    </TSPInformationURI>
  </TSPInformation>
  <TSPServices>
    <TSPService>
      <ServiceInformation>
        <ServiceTypeIdentifier>https://ewc-consortium.github.io/ewc-trust-list/TrstSvc/Svctype/NPWP</ServiceTypeIdentifier>
        <ServiceName><Name xml:lang="en">Example Wallet</Name></ServiceName>
        <ServiceDigitalIdentity>
          <DigitalId>
            <X509Certificate>YourBase64EncodedCertificate</X509Certificate>
          </DigitalId>
          <DigitalId>
            <X509SKI>YourSubjectKeyIdentifier</X509SKI>
          </DigitalId>
        </ServiceDigitalIdentity>
        <ServiceStatus>https://uri.etsi.org/TrstSvc/TrustedList/Svcstatus/granted/</ServiceStatus>
        <StatusStartingTime>2025-03-15T22:00:00Z</StatusStartingTime>
        <ServiceSupplyPoints>
          <ServiceSupplyPoint>https://example.org/wallet</ServiceSupplyPoint>
        </ServiceSupplyPoints>
      </ServiceInformation>
    </TSPService>
  </TSPServices>
</TrustServiceProvider>
```


### Step 4: Commit and push changes

```bash
git add EWC-TL.xml
git commit -m "Add <Your Org> as Trust Service Provider"
git push origin add-your-org-to-tl
```

### Step 5: Create a pull request

Go to your fork on GitHub and click **"Compare & pull request"**.

In the PR description:

- Mention your organisation's name
- Provide a link to your documentation or public site
- Confirm that your certificate is valid and public

## Review and Merge

The EWC Consortium team will review:

- Format compliance
- Validity of certificate
- Accessibility of endpoints

If all checks pass, the PR will be approved and merged into the Trust List.

## Support

For questions or verification support, use EWC slack channel [#wallet-support](https://eudigitaliden-gax7504.slack.com/archives/C063LNT4L4R)