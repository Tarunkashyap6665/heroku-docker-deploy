# Heroku Docker Deploy GitHub Action

This GitHub Action enables you to deploy containerized applications on Heroku. It automates the process of building your app's Docker image, pushing it to Heroku's container registry, and releasing it for seamless deployment and scaling.

## Author

Created by [Tarun Kashypap](https://github.com/tarunkashypap).

## Inputs

The following inputs are available for configuring the action:

| Name              | Description                                                        | Required | Default         |
|-------------------|--------------------------------------------------------------------|----------|-----------------|
| `HEROKU_APP_NAME` | The name of your Heroku app where the Docker container will be deployed. | `true`   | `myapp-demo`    |
| `HEROKU_API_KEY`  | The API key used to authenticate with Heroku.                      | `true`   | `N/A`             |
| `DOCKERFILE_NAME` | The path to the Dockerfile used for building the container.         | `false`  | `./Dockerfile`  |

## Outputs

The action provides the following outputs:

| Name             | Description                                |
|------------------|--------------------------------------------|
| `HEROKU_APP_URL` | The URL of the deployed Heroku app.         |

## Usage

Below is an example of how to use this GitHub Action in a workflow:

```yaml
name: Deploy to Heroku

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Deploy Docker app to Heroku
      uses: Tarunkashyap6665/heroku-docker-deploy
      with:
        HEROKU_APP_NAME: 'your-heroku-app-name'
        HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        DOCKERFILE_NAME: './Dockerfile'
