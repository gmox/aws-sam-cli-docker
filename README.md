# AWS SAM CLI Docker

This brings the AWS SAM CLI to Docker, allowing developers to run their lambdas in more automated scenarios such as CI/CD or integration tests.

# How do I use it?

This all assumes some basic familiarity with AWS serverless technologies. For more in-depth treatments of that, consult many of the wonderful articles out there that go over Lambdas and API Gateways in depth.

First, cd into the directory with your lambda. It should look something like this
 
```bash
$ cd lambdas/my-lambda ; ls

main.go         template.yml
```

Then you'll build your lambda.

```bash
$ GOOS=linux go build main.go && zip ./main.zip ./main
```

And finally, run the AWS SAM CLI docker image. In this example, it starts up a local API
via SAM.

```bash
$ docker run -v $(PWD):/$(PWD) -w $(PWD) aws-sam-cli-docker:0.34.0 local start-api --host=0.0.0.0
```

`$(PWD):$(PWD)` tells Docker to add our current working directory (the directory with the lambda in it) to the container at `/$(PWD)`.
This path can be changed by the user. This is what allows SAM to utilize the lambda. `-w ($PWD)` sets the current working directory to the directory that was added to the container
