# Access Control & Roles Hardening

## Common Issues

- Overpowered `owner` / admin.
- Missing access control on sensitive functions.
- Forgotten test functions left in production.

## Best Practices

- Use `AccessControl` or well-audited role patterns.
- Separate roles:
  - `ADMIN_ROLE`
  - `TREASURY_ROLE`
  - `PAUSER_ROLE`
  - `UPGRADER_ROLE`
- Use multisig for admin roles where possible.
- Log all privileged actions via events.

## Invariants

- No single EOA should be able to irreversibly brick or drain a system.
- Privileged actions should be:
  - Limited in scope.
  - Transparent.
  - Justified by protocol design.
