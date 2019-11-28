# AWS SAM CLI Docker

It's in the name.

# How do I use it?

First, cd into the directory with your lambda. It should look something like
 
```bash
$ cd lambdas/my-lambda ; ls

main.go         template.yml

$ GOOS=linux go build main.go && zip ./main.zip ./main

$ docker run -v /var/run/docker.sock:/var/run/docker.sock -v $(PWD):/app aws-sam-cli-docker:0.34.0 local start-api --host=0.0.0.0
```

# Is it production ready?

Heavens no. Not yet, anyway. But it works and I can iterate more on it.
