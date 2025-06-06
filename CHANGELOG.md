# Changelog

All notable changes to the CCaaS Provisioning API will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2023-07-15

### Changed

- **Refactored AI Messaging licensing model**: Replaced the ambiguous `aiMessaging.additionalMessageBundles` structure with a new explicit tiered system that supports "Standard" and "Advanced" license bundles.
  - Added new component schemas: `AiMessagingStandard` and `AiMessagingAdvanced`
  - Updated the `LicenseUpdateRequest` schema to use `oneOf` to enforce the "either/or" relationship between tiers
  - Updated all examples and documentation to reflect the new structure
  
### Why this change?

The previous model used a single `additionalMessageBundles` property which was ambiguous and didn't clearly communicate the differences between service tiers. The new model:

1. Clearly separates Standard and Advanced tiers
2. Makes it explicit that tiers cannot be combined (enforced through schema validation)
3. Provides better documentation about what each tier includes:
   - Standard: 5,000 AI messages and 2 knowledge bases per bundle
   - Advanced: 5,000 AI messages and 5 knowledge bases per bundle, plus 3rd party integrations

This change improves the API's usability by making the licensing options more transparent and reduces potential confusion for integrators.