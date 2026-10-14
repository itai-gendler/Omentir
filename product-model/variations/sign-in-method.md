---
kind: configuration
of: capability-scenario
takesEffect: When the install starts; the install's mode and its access settings are read at startup.
stability: Fixed for the life of the running install. Changing the session secret signs everyone out.
alternatives:
- id: sign-in-with-account
  selectedWhen: 'The hosted service: the install does not run in self-hosted mode.'
- id: sign-in-with-access-password
  selectedWhen: A self-hosted install with an access password set. A password stays required even when open access is also allowed. With neither a password nor open access the install refuses to start.
- id: continue-without-password
  selectedWhen: A self-hosted install whose operator explicitly allowed open access and set no access password.
---

# Sign-in method

The hosted service and self-hosted installs run the same code, and the install's mode decides how a Visitor signs in.
