# Heroku operation application

## Feature

- Daily pg:backups and save dump file on s3
  - Post slack

## Set these variables

| NAME                            | DESCRIPTION             |
| ------------------------------- |:-----------------------:|
| HEROKU_API_KEY                  | heroku api key          |
| PGBACKUPS_APP                   | heroku app name         |
| PGBACKUPS_AWS_ACCESS_KEY_ID     | AWS AccessKey           |
| PGBACKUPS_AWS_SECRET_ACCESS_KEY | AWS SecretAccessKey     |
| PGBACKUPS_BUCKET                | s3 bucket name          |
| PGBACKUPS_REGION                | s3 region               |
| SLACK_URL                       | slack webhook url       |
