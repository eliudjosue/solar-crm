# Solar CRM/ERP Platform

> End-to-end management platform for solar energy companies — built to handle the full commercial and operational cycle, from lead acquisition to invoicing.

**Status:** Active development &nbsp;·&nbsp; **Stack:** Angular · NestJS · PostgreSQL · Docker

---

## The problem it solves

Solar energy companies typically manage their pipeline across disconnected tools: spreadsheets for leads, separate software for quoting, and manual processes for electric invoices. This creates data loss, delays, and zero visibility across the funnel.

This platform centralizes the entire workflow in a single system — built specifically for the operational reality of solar energy businesses.

---

## Core modules

### Lead management
- Full pipeline with status tracking and follow-up history
- Lead source attribution and conversion metrics
- Site information capture (`LeadSite` entity: address, grid connection type, consumption data)

### Quoting
- Configurable line items with live pricing and formatting (es-AR locale)
- Soft delete with audit fields (`activo`, `deleteFecha`)
- PDF quote generation from structured templates
- REST endpoints: create, update, list, soft-delete

### Electric invoice processing
- Import and parse electric invoices from utility providers
- Extract consumption data to feed quoting and sizing calculations
- Alignment between frontend display and backend data model

### Document generation
- PDF output for quotes and reports using structured HTML templates
- Template system with header/footer zone support
- Configurable per document type

---

## Architecture decisions

**Frontend — Angular 17+**
- Standalone components with `ChangeDetectionStrategy.OnPush` throughout
- Angular Signals for reactive state (replacing `@Input`/`@Output` chains)
- `takeUntilDestroyed` for subscription lifecycle — zero memory leaks
- TailwindCSS for utility-first styling with responsive breakpoints
- `Intl.NumberFormat` for locale-aware number formatting

**Backend — NestJS**
- Modular architecture: one module per business domain
- TypeORM with PostgreSQL — repository pattern, typed entities
- JWT authentication with `JwtStrategy`, `JwtAuthGuard`, and `CurrentUser` decorator
- DTO validation with `@Transform` and `@IsEnum` for safe enum normalization
- Swagger/OpenAPI docs auto-generated from decorators

**Infrastructure**
- Docker Compose for local development (app + database)
- Environment-based configuration with `.env` per stage
- Prepared for CI/CD pipeline integration

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | Angular 17+, TypeScript, TailwindCSS, RxJS |
| Backend | NestJS, TypeScript, Swagger |
| Database | PostgreSQL, TypeORM |
| Auth | JWT (access tokens, guards, decorators) |
| Infrastructure | Docker, Docker Compose |
| Dev workflow | Cursor, AI-assisted development with human review |

---

## Development approach

This project is designed and built end-to-end by a single developer. Architecture decisions prioritize:

- **Maintainability** — strict TypeScript, ESLint rules, modular structure
- **Incremental delivery** — each module ships independently without breaking existing logic
- **AI-augmented workflow** — AI coding agents (Cursor, Codex) used for implementation, with structured prompts and expert review at every step

---

## Repositories

This platform is split into two repositories:

| Repo | Description | Stack |
|---|---|---|
| solar-crm-frontend | Angular application — UI, components, state management | Angular 17+, TypeScript, TailwindCSS, RxJS |
| solar-crm-backend | NestJS REST API — business logic, database, auth | NestJS, PostgreSQL, TypeORM, JWT |

> Access available on request.

---

## Status & roadmap

- [x] Authentication (JWT)
- [x] Lead management with site data
- [x] Quoting module (CRUD + PDF)
- [x] Electric invoice module (frontend + backend)
- [ ] Dashboard with conversion metrics
- [ ] Multi-user roles and permissions
- [ ] Client-facing quote portal

---

## About the developer

Built by **Eliud** — Full-Stack Developer based in Buenos Aires, specializing in Angular frontends and NestJS backends for business management platforms.

Available for remote freelance projects with European companies.

→ [LinkedIn](https://www.linkedin.com/in/eliudjosue/) &nbsp;·&nbsp;·&nbsp; [Contact](+5491123885307)
