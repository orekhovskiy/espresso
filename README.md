# Android CI Testing Example with Selectel Mobile Farm
This project provides an example setup for running automated Android tests using Selectel Mobile Farm, integrated with CI/CD pipelines such as GitHub Actions or GitLab CI. This setup allows you to run tests on real Android devices in the cloud using `Espresso` framework.

# CI/CD Configuration Files
CI/CD Configuration Files include steps to set up the Android SDK, obtain authentication tokens, and connect to a remote device in Selectel Mobile Farm.  

This repository includes the following CI configuration files:
## GitHub Actions
[ci.yml](./.github/workflows/ci.yml): This file is designed to run Android tests using GitHub Actions.
## GitLab CI (Optional)
[.gitlab-ci.yml](./.gitlab-ci.yml): If you are using GitLab CI instead of GitHub Actions, you can use this file.

# Key Considerations
## Environment variables
Ensure you have properly set up all of the tokens used inside CI/CD file. These include your service user's `USER_NAME` and `PASSWORD`, `PROJECT_NAME`, `ACCOUNT_NAME`, `DEVICE_SERIAL`.
## Selectel Authorization Tokens:
- Mobile Farm supports only Selectel Keystone authorization tokens.
- Provided tokens are valid for one day. Be careful when exposing tokens inside pipeline.
- You can always refer to the [docs](https://docs.selectel.ru/api/authorization/) about Selectel authorization if you having any troubles obtaining the X-Auth-Token.
## Device Screen State:
Ensure that the device screen is not locked before running the tests. Ensure that no other activities or pop-ups are blocking the device screen during testing, as this might interfere with the tests.
## Espresso Testing:
- Espresso tests do not support the execution of tests in the middle of a user's journey.
- Ensure your tests follow a clear sequence without interruption.
## Device Assignment:
When assigning devices, make sure you are using the correct device serial number (provided as an environment variable `DEVICE_SERIAL`) which is present inside the project you specify by an environment variable `PROJECT_NAME`.
## Pipeline customization
You can modify CI/CD configuration file by your needs. For example: 
- Use multiple devices.
- Store ADB keys inside the repository so you won't have to generate them every time during pipeline execution.
- Add devices to a farm during pipeline execution.
- For more information checkout our [Swagger documentation]((https://docs.selectel.ru/api/mobile-farm/).
