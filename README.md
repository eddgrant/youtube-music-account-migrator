# YouTube Music Account Migrator

A utility to migrate YouTube Music libraries between different Google accounts. The utility is a thin wrapper around [ytmusicapi][ytmusicapi-github] which does all the heavy lifting.

# Does it support migration from GSuite / Google Workspace accounts?

Yes, in fact that was why I wrote it as I needed to do just this.

# What gets migrated?

The utility can currently migrate the following items:

1. Liked songs
2. Individual library songs
3. Library Albums
4. Library playlists

# What doesn't get migrated?

1. Music that has been manually uploaded (suggestions on how to do this are welcome!)

# How do I migrate my account?

1. [Install Poetry](https://python-poetry.org/docs/#installing-with-the-official-installer) if you don't already have it. 
2. Clone this repository locally
3. Open the repository in a shell
4. Run `poetry install`
5. Run `poetry run oauth-old-account`, this will take you through the authentication process. Ensure you authenticate with your "old" account (i.e. the account you want to migrate your library from). See the [Authentication](#Authentication) section below for more detail.
6. Run `poetry run oauth-new-account`, this will take you through the authentication process. Ensure you authenticate with your "new" account (i.e. the account you want to migrate your library to). 
7. Run `poetry run dry_run_migration`, This will run the migration in "dry run" mode. This mode doesn't make any changes, instead it outputs the changes that would be made during an actual migration.
8. Check that you are happy with the changes output by the dry run migration.
9. Run `poetry run migrate`, this will run the actual migration from your old YouTube Music account over to your new YouTube Music account.
10. Log in to YouTube Music using your new account. If the migration has completed successfully you should see all the migrated items in your account.

# Authentication

In order to perform the migration it is necessary to capture authentication details for both the old and new Google accounts. `ytmusicapi` does this by taking the user through Google's login flow in a browser. Further details can be found on the [oauth page of the ytmusicapi documentation][ytmusicapi-docs-oauth-page].

[ytmusicapi-github]: https://github.com/sigma67/ytmusicapi
[ytmusicapi-docs-oauth-page]: https://ytmusicapi.readthedocs.io/en/latest/setup/oauth.html