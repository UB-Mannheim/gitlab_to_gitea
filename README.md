# Gitlab to Gitea migration script.

This script uses the Gitlab and Gitea API's to migrate all data from
Gitlab to Gitea.

This script support migrating the following data:
 - Repositories & Wiki (fork status is lost)
 - Milestones
 - Labels
 - Issues (no comments)
 - Users (no profile pictures)
 - Groups
 - Public SSH keys

This fork was used to migrate from Gitlab Version 14.8 to Gitea Version 1.16.7.

Modifications:
 - Use Gitlab api-key instead of login/password authentication
 - Only import active users from gitlab instance
 - Import organisations and projects by PATH instead of NAME to preserve URLs

## Usage
Change items in the config section of the script.

Install all dependencies via `python -m pip install -r requirements.txt` and
use python3 to execute the script.

### How to use with venv
To keep your local system clean, it might be helpful to store all Python dependencies in one folder.
Python provides a virtual environment package which can be used to accomplish this task.

```bash
python3 -m venv migration-env
source migration-env/bin/activate
python3 -m pip install -r requirements.txt
```

Then start the migration script `python3 migrate.py`.

## Notes
Users have to reset their password so E-Mail has to be configured on the gitea instance.
