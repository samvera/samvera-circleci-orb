# Samvera CircleCI Orb

The Samvera CircleCI Orb is meant to make testing Samvera and Samvera-based projects easier.

The orb provides executors that include common Samvera dependencies, and commands to help set up and run your tests.

More information about orbs in general is available in [CircleCI's docs](https://circleci.com/docs/),
and up-to-date documentation about the Samvera orb exists on [the orb's CircleCI page](https://circleci.com/orbs/registry/orb/samvera/circleci-orb)

## Using the orb

Since using the orb depends on Circle's configuration API, this section will attempt to point you to the latest
documentation rather than copying docs that may become outdated quickly.

If you are not yet using CircleCI, please start with their [introduction documentation](https://circleci.com/docs/2.0/first-steps/)

The canonical documentation for setting up the orb is in the [Quick Start Guide](https://circleci.com/orbs/registry/orb/samvera/circleci-orb)
on the orb's CircleCI page.

Once you have finished with the Quick Start, the executors and commands will be available for use in your
config. The executors are named for the dependencies they include (ruby, ruby\_fcrepo\_solr, etc.), and the
commands are named and documented to avoid surprises.

Circle has general information about [executors](https://circleci.com/docs/2.0/executor-intro/#section=configuration),
and [commands](https://circleci.com/docs/2.0/using-orbs/#commands) that may be useful as well.

## Best practices

The executors allow you to set parameters for the dependencies they use. For instance, you could have in
your parameters

```
solr_version:
    type: string
    default: '7-slim'
```

or in your build matrix:

```
ruby_type: 'ruby'
```

Different dependencies have different parameters, but all of them allow you to specify a version. You should do
this! The orb is permissive in the versions it allows, and may surprise you by upgrading when you least expect
it.

Be prepared! Control your destiny! Specify versions!

## Releasing new versions

1. Install the CircleCI Client -
   [https://circleci.com/docs/2.0/local-cli/#installation](https://circleci.com/docs/2.0/local-cli/#installation)
2. `circleci setup` (You'll need an API key)
3. `circleci config pack src > src/orb.yml`
4. `circleci orb validate src/orb.yml`
5. `circleci orb publish src/orb.yml samvera/circleci-orb@dev:alpha`
6. If Ready for permanent version bump: `circleci orb publish promote
   samvera/circleci-orb@dev:alpha [major/minor/patch]`
