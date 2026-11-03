# Microserv52

Microserv52 is a microservices platform for buying and selling products. The
project combines APIs for products, orders, accounts, authentication and
currency exchange with cloud deployment, CI/CD, observability and performance
testing.

[Read the complete documentation on GitHub Pages](https://microsserv52.github.io/platform/)

## Platform

The platform uses a gateway as the public entry point. Authenticated requests
are routed to independent services, while Order integrates with Product for
prices and Exchange for currency conversion.

## Main repositories

| Repository | Description |
| --- | --- |
| [platform](https://github.com/Microsserv52/platform) | Integration repository, architecture, Docker Compose and documentation |
| [gateway](https://github.com/Microsserv52/gateway) | Public API gateway and request routing |
| [order](https://github.com/Microsserv52/order) | Java Order API |
| [order-service](https://github.com/Microsserv52/order-service) | Order service integration layer |
| [product](https://github.com/Microsserv52/product) | Product catalogue API |
| [exchange](https://github.com/Microsserv52/exchange) | Currency exchange API |
| [account](https://github.com/Microsserv52/account) | Account management service |
| [auth](https://github.com/Microsserv52/auth) | Authentication and authorization service |

The `platform` repository integrates service repositories as Git submodules when
they are part of the current deployment.

## Technology and operations

- Java and Spring Boot for the Order service.
- Python and FastAPI for the Exchange service.
- Docker Compose for local integration.
- AWS and Amazon EKS for cloud deployment.
- GitHub Actions for documentation delivery.
- Metrics, logs and traces for observability with Grafana.

