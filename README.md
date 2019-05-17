# AWS CLI Docker Based on Alpine Linux

## Usage
```console
docker run -it -v /path/to/.aws:/root/.aws dwdraju/aws-cli-docker aws s3api list-buckets --query "Buckets[].Name"
```

### CI/CD on Gitlab
```yaml
code-build-artifact:
  stage: publish
  image: dwdraju/aws-cli-docker
  script:
    - echo $AWS_CREDENTIALS | base64 -d > ~/.aws/credentials
    - aws codebuild start-build --project $CODEBUILD_PROJECT --region $AWS_REGION
  only:
    - branches
```
