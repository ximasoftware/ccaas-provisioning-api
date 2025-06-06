# Changelog

All notable changes to the CCaaS Provisioning API will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2023-08-10

### Changed

- **Removed obsolete additionalAiMessages field**: Completely removed the deprecated `additionalAiMessages` field from all API schemas, documentation, and code examples.
  - Removed from LicenseUpdateRequest schema and examples
  - Removed from all documentation references
  - Removed from code examples

- **Clarified AI Messaging licensing rules**: Updated descriptions to accurately reflect how the Standard and Advanced tiers work.
  - Clarified that Standard bundles can be stacked for more messages AND knowledge bases
  - Emphasized that the primary reason to purchase the Advanced tier is for 3rd-party integrations
  - Updated all documentation to consistently reflect these rules

### Why these changes?

1. The `additionalAiMessages` field was redundant after the introduction of the tiered system in v1.1.0 and was causing confusion.
2. The previous documentation didn't clearly explain that Standard bundles provide additional knowledge bases when stacked.
3. The value proposition of the Advanced tier (3rd-party integrations) needed to be more prominently highlighted.

These changes ensure the API documentation accurately reflects the product's actual behavior and licensing model, reducing confusion for integrators and customers.

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
