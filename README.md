# What's In This Starter Kit?
- Latest Django
- Python 3
- Heroku deployment-ready
- Redis and Django-RQ for asynchronous tasks
- Sentry for exception tracking
- Sendgrid for email sending
- Automated testing configured
- Login/logout/reset password/forgot password API endpoints
- Django Suit theme for the Django Admin

# Dev Setup
0. Clone this repo: `git clone git@github.com:simplefractal/fractal-django-genie.git`;
1. Rename the cloned directory to your project name, create a new repo on GitHub with the same name, change the local git origin to point to the new repo and the push.
2. Inside this new repo, erase this README so it will lose this current text;
3. Create a virtualenv for Python 3.5: `mkvirtualenv {{ VIRTUAL_ENV_NAME }} -p /usr/bin/python3.5`;
4. Copy default postactivate: `cp contrib/proj_postactivate $VIRTUAL_ENV/bin/postactivate`;
5. Edit `$VIRTUAL_ENV/bin/postactivate` for you custom env config (e.g. update DATABASE_URL) and re-run the `workon` command;
6. Install the packages: `pip install -r dev-requirements.txt`;
7. Create postgres db: `createdb {{ DATABASE_NAME }}`;
8. Install redis ([click here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis) if you're using Ubuntu)
9. Migrations: `python project/manage.py migrate`
10. Create admin user: `python project/manage.py createsuperuser`
11. Runserver: `python project/manage.py runserver`

# Asynchronous Tasks
Run django-rq for email sending: `python project/manage.py rqworker`

# How to run the tests
`make test`

# Alternative env setup
You can also create a `.env` file inside of `config` similar to `.env-example`

# Git Workflow
0. Create feature branch off of `dev` with the `feature` prefix such as `feature/sso-login`
1. Develop and commit in this branch
2. Make sure tests are passing with `pytest` command from the `project` directory
3. When finished, open a pull request
4. When reviewed and updated, merge into `dev` with the following commands or just use the Github merge button and remember deleting the remote branch:

```bash
$ git checkout dev
$ git merge --no-ff feature/sso-login
$ git push origin dev
$ git push origin :feature/sso-login  # deletes remote branch
```
