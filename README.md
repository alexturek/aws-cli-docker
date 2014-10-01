# A way to use the AWS CLI through docker.

If you're on e.g. CoreOS and you don't want to have to install Python or other libraries, use Docker to access S3.

## Getting set up

See [http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html](Amazon's help docs) on how to get your access key and credentials

After you have those, run this command to save your AWS creds locally (to the folder `/my/current/directory/.awscreds`)

    docker run --rm -t -i -v $(pwd)/.awscreds:/root/.aws alexturek/aws-cli-docker configure

Enter your key ID and secret (and any other information) at the prompts. These are now saved at ./creds/

## Use the AWS CLI

From the same directory:

    docker run --rm -t -i -v $(pwd)/.awscreds:/root/.aws alexturek/aws-cli-docker my aws commands

If you want to be able to run this from any directory on your machine, replace $(pwd) in both commands with /some/absolute/path


## Examples

See objects in an S3 bucket:

    docker run --rm -t -i -v $(pwd)/.awscreds:/root/.aws alexturek/aws-cli-docker s3 ls s3://my-s3-bucket

For more use see [http://docs.aws.amazon.com/cli/latest/reference/](AWS's documentation)
