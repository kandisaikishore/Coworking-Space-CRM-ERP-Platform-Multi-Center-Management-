# Development, QA, and Operations Guide

This repository describes a multi-center coworking CRM/ERP concept. The actual implementation determines which modules and workflows are available; do not assume that every domain area below is already implemented.

## Setup and configuration

```bash
git clone https://github.com/kandisaikishore/Coworking-Space-CRM-ERP-Platform-Multi-Center-Management-.git
cd Coworking-Space-CRM-ERP-Platform-Multi-Center-Management-
```

Inspect manifests, environment examples, and source to identify the runtime, startup command, data store, and external services. Use project-defined scripts and keep credentials out of commits.

## Multi-center data isolation

If the application supports multiple centers or tenants, every protected read and write must be scoped to the authorized center on the server. Test attempts to access another center's memberships, bookings, billing records, or reports by changing resource identifiers. UI filters alone are not a security boundary.

## Domain validation

For implemented workflows, test:
- Membership creation, changes, expiry, and duplicate submissions
- Desk/room availability and overlapping reservations
- Billing totals, currency rounding, and payment status transitions
- Missing identifiers, invalid dates, negative amounts, and malformed requests
- Administrative changes and audit history, if implemented

Failed operations should not partially update membership, booking, or billing state.

## Audit and privacy

Record attributable audit events for supported high-impact administrative changes. Keep passwords, payment credentials, and unnecessary personal information out of audit logs. Restrict access to customer and billing records by role and center.

## Pull-request checklist

- [ ] Add tests for allowed and denied cross-center access.
- [ ] Test validation boundaries and failed-write behavior.
- [ ] Run the repository's declared test/build commands.
- [ ] Document data persistence and external-service requirements.
- [ ] Distinguish intended domain features from implemented features.
