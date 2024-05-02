# Troubleshooting Notes

## 1- AWS CDK LambdaLayer build error on Apple Slicon Chip:

### AWS Lambda error message:

{ "errorMessage": "Unable to import module 'src.handler': Unable to import required dependencies:
numpy: Error importing numpy: you should not try to import numpy from
its source directory; please exit the numpy source tree, and relaunch
your python interpreter from there.", 
"errorType": "Runtime.ImportModuleError", "requestId": "61bd8c32-68b4-43c7-a820-52bd58853310", "stackTrace": [] }

### Solution:
AWS cdk uses docker to build the lambda layer. If you don't declare cpu architecture, docker takes system cpu architecture as default. that causes the issue. you should pass default architecure:

<code>DOCKER_DEFAULT_PLATFORM=linux/amd64 cdk deploy ...</code>

