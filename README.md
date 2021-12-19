# docker-to-ecr
This repo is used for pushing docker image to aws ecr using aws codebuild with github
When building is started the codebuild read buildspec.yml file and create a docker image of the code, which is then published to ecr.
Don't forget to add trigger/webhook on push in codebuild


I had to change this line from buildspec.yml as it is no longer supported in cli v2

`$(aws ecr get-login --region $AWS_DEFAULT_REGION --no-include-email)`

instead use the updated version below

`aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin 966771679518.dkr.ecr.us-east-1.amazonaws.com/docker2ecr
`

Do not add $() in new command.

