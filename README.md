# thomaslomas/s3cmd-cron

This image provides an easy way to tar.gz a folder and upload to S3 scheduled by a cron. This is designed to be a lightweight image built on alpine 3.3.

## Installation

    docker pull thomaslomas/s3cmd-cron

## Example Usage

    docker run -it --rm --env AWS_ACCESS_KEY="ABC123" --env AWS_SECRET_KEY="dfdsfsf/234234fgf/example" --env AWS_BUCKET=s3://my-backup-bucket --env AWS_BUCKET_LOCATION=EU -v /var/important-folder:/backup --env BACKUP_SCHEDULE="0 * * * *" thomaslomas/s3cmd-cron

## Environmental Variables

| Key                 | Required | Default   | Description                                                                        |
|---------------------|----------|-----------|------------------------------------------------------------------------------------|
| AWS_ACCESS_KEY      | Y        |           | This is your AWS Access Key                                                        |
| AWS_SECRET_KEY      | Y        |           | This is your AWS Secret Key                                                        |
| AWS_BUCKET          | Y        |           | This is the full bucket path of where to put the files. E.g. "s3://my-bucket-name" |
| AWS_BUCKET_LOCATION | N        | US        | This is the AWS bucket location                                                    |
| BACKUP_SCHEDULE     | N        | 0 3 * * * | This is how often the cron should execute. This defaults to 3am                    |


## Required Volumes

You must register a data volume at /backup. This is the folder which will be archived and uploaded to S3 as per the schedule.

## Credits

I took some influence from [sekka1/docker-s3cmd](https://github.com/sekka1/docker-s3cmd).
