# AWS SAM CLI Docker

This brings the AWS SAM CLI to Docker, allowing developers to run their lambdas in more automated scenarios such as CI/CD or integration tests.

# How do I use it?

This all assumes some basic familiarity with AWS serverless technologies. For more in-depth treatments of that, consult many of the wonderful articles out there that go over Lambdas and API Gateways in depth.

First, cd into the directory with your lambda. It should look something like this
 
```bash
$ cd lambdas/my-lambda ; ls

main.go         template.yml
```

Then you'll compile your lambda.

```bash
$ GOOS=linux go build main.go && zip ./main.zip ./main
```

And last, run the AWS SAM CLI docker image.

```bash
$ docker run -v /var/run/docker.sock:/var/run/docker.sock -v $(PWD):/app aws-sam-cli-docker:0.34.0 local start-api --host=0.0.0.0
```

# Is it production ready?

Heavens no. Not yet, anyway. But it works. And I can iterate more on it.
