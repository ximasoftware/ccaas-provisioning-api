# Xima CCaaS License Provisioning API - Reseller Documentation

This documentation provides comprehensive information for authorized Xima Software resellers on how to effectively use the CCaaS License Provisioning API. This API enables resellers to programmatically manage and update customer licenses, ensuring efficient and accurate license administration.

## Key Features

* **API Reference:** Detailed Swagger documentation with interactive testing capabilities, covering all available endpoints, parameters, request bodies, and response formats.
  * [View API Reference](https://ximasoftware.github.io/ccaas-provisioning-api/api.html)
* **Secure Authentication:** JWT-based authentication with payload hashing and anti-replay protection using JTI (JWT ID) and expiration timestamps.
  * [Authentication Guide](https://ximasoftware.github.io/ccaas-provisioning-api/authentication.html)
* **Interactive Code Examples:** Practical, ready-to-use code examples in a Google Colab notebook for rapid integration.
  * [Open in Google Colab](https://colab.research.google.com/github/ximasoftware/ccaas-provisioning-api/blob/main/xima_api_jwt_auth_example.ipynb)

## Security Implementation

The API implements several security measures to ensure secure and reliable license management:

* **JWT Authentication:** All requests require JWT tokens signed with your private key
* **Payload Hashing:** The entire request payload is hashed and included in the JWT
* **Anti-Replay Protection:** Each request must include:
  * A unique JTI (JWT ID) in the request body
  * An expiration timestamp (exp) in the request body (max 30 minutes)
* **Strict Serialization:** Request payload must be serialized with specific parameters for verification

## Getting Started

1. **Explore the API:** Review the [API Reference](https://ximasoftware.github.io/ccaas-provisioning-api/api.html) to understand available endpoints and parameters
2. **Understand Authentication:** Follow the [Authentication Guide](https://ximasoftware.github.io/ccaas-provisioning-api/authentication.html) to learn how to create properly signed requests
3. **Try the Code Examples:** Use our [Interactive Notebook](https://colab.research.google.com/github/ximasoftware/ccaas-provisioning-api/blob/main/xima_api_jwt_auth_example.ipynb) to see working examples of:
  * CSR and private key generation
  * JWT creation with payload hashing
  * License update requests with proper authentication

## Common Errors and Troubleshooting

| Error Code | Description | Solution |
|------------|-------------|----------|
| `INVALID_SIGNATURE` | The JWT signature verification failed | Check serialization parameters and ensure you're using the correct private key |
| `DUPLICATE_JTI` | The JTI has already been used | Generate a new UUID for each request |
| `INVALID_JTI` | The JTI format is incorrect | Ensure JTI is a valid UUID string |
| `EXPIRED_TOKEN` | The request's expiration time has passed | Check your server's clock synchronization |
| `VALIDATION_ERROR` | License parameters don't meet requirements | Review validation rules for seat quantities |

## Important Considerations

* **License Validation:** The API enforces minimum values for certain license parameters:
  * `workforceOptimizationSeats` and `workforceManagementSeats` require at least 10 seats
  * `speechAnalyticsSeats` and `dialerSeats` require at least 5 seats
  * `additionalAiMessages` requires at least one `eliteSeats`

## API Base URL

For sandbox testing: `https://licensing.api.ximadev.cloud/v1`

## Support

For questions or assistance with the Xima CCaaS License Provisioning API, please contact Xima Software support at [support@ximasoftware.com](mailto:support@ximasoftware.com).

© 2025 Xima. All rights reserved.