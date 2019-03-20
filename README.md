# Samvera CircleCI Orb

This repository contains a set of shared configuration for CircleCI deploys in
the Samvera organization.

## Deploying

1. Install the CircleCI Client -
   [https://circleci.com/docs/2.0/local-cli/#installation](https://circleci.com/docs/2.0/local-cli/#installation)
2. `circleci setup`
3. `circleci config pack src > src/orb.yml`
4. `circleci orb validate src/orb.yml`
5. `circleci orb publish src/orb.yml samvera/circleci-orb@dev:alpha`
6. If Ready for permanent version bump: `circleci orb publish promote
   samvera/circleci-orb@dev:alpha [major/minor/patch]`
