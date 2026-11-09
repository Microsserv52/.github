# Microsserv52

[![Java](https://img.shields.io/badge/Java-ED8B00?style=flat)](https://dev.java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-149ECA?style=flat&logo=react&logoColor=white)](https://react.dev/)
[![MUI](https://img.shields.io/badge/MUI-007FFF?style=flat&logo=mui&logoColor=white)](https://mui.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white)](https://github.com/features/actions)

Microsserv52 is an educational microservices platform for browsing products and
creating demo orders. **This is a mock store: no real payments or transactions
take place, and no goods are shipped.**

[Read the project documentation](https://microsserv52.github.io/platform/)

## Web applications

Three public repositories are integrated as Git submodules in the platform.
Each is an independent Next.js/TypeScript static export, served under one domain.

| Repository                                         | Platform path | Public path | Experience                                                                           |
| -------------------------------------------------- | ------------- | ----------- | ------------------------------------------------------------------------------------ |
| [landing](https://github.com/Microsserv52/landing) | `web/landing` | `/`         | Demo introduction, catalog preview, privacy/diagnostics and project documentation    |
| [store](https://github.com/Microsserv52/store)     | `web/store`   | `/store/`   | Public catalog search/sort, guest cart, login/register and authenticated demo orders |
| [admin](https://github.com/Microsserv52/admin)     | `web/admin`   | `/admin/`   | Restricted product creation/deletion, account details and observability links        |

The English UI uses shared branding, MUI/Emotion and Tailwind CSS, with TanStack
Query/Table and React Hook Form/Zod. The store has an online-only PWA manifest.
Grafana Faro and Umami are integrated and disabled until collection values and
hosting are agreed. antislop is applied during implementation with real UI
reference research.

Each app has a Dockerfile for local testing. A separate, explicitly labeled
fixture Compose environment permits UI testing without Product/Exchange images.
Production frontends will use CDN hosting with per-app environment values;
provider and configuration are deferred, as is frontend Kubernetes deployment.
The initial implementation is merged and is not a production deployment.
The image extension uses URL-based catalog rendering and admin upload/replace/
remove controls. S3 + CloudFront is selected; the required backend changes are
saved for the future Product repository. Uploads stay disabled in normal
environments until that service is implemented and accepted.

See the [frontend documentation](https://github.com/Microsserv52/platform/blob/main/docs/frontend/index.md)
for scope, package versions, routing, browser sessions, local testing and evidence.
All ten Microsserv52 repositories are public; no organization membership is
required to read or clone the source.

## Backend repositories

| Repository                                                     | Responsibility                                                                |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [platform](https://github.com/Microsserv52/platform)           | Git submodules, integration, Compose/Kubernetes, deployment and documentation |
| [gateway](https://github.com/Microsserv52/gateway)             | Business API routing, browser sessions, JWT/CSRF and public access boundary   |
| [account](https://github.com/Microsserv52/account)             | Registration, authenticated own profile and admin-restricted account reads    |
| [auth](https://github.com/Microsserv52/auth)                   | Login and JWT issuance                                                        |
| [order](https://github.com/Microsserv52/order)                 | Reusable Java Order API contract                                              |
| [order-service](https://github.com/Microsserv52/order-service) | Demo order persistence, ownership and service-calculated totals               |

Product and Exchange remain external integration prerequisites in the current
platform checkout. The current order implementation supports USD totals.

## Engineering and operations

- Java/Spring Boot services, Docker Compose and Kubernetes/AWS EKS for the backend.
- Independent repository checks, tests, CodeQL configuration and immutable
  `sha-<commit>` container publishing; platform-owned integration validation.
- Zensical documentation and recorded verification evidence.
- Secrets stay out of source. Local values belong in `.env`; CI values in
  repository Actions secrets/variables; backend cluster values in the configured
  secret store. Public frontend build variables must never contain secrets.

See the [platform configuration guide](https://github.com/Microsserv52/platform#cicd-and-environment-variables).
