trigger: none

jobs:
- job: RunTest
  workspace:
    clean: all
  pool:
    vmImage: 'ubuntu-latest'
  steps:
  - task: Docker@2
    displayName: Login to ACR
    inputs:
      command: login
      containerRegistry: my-acr
  - script: |
      docker run my-registry.azurecr.io/somerepo/rnd-hello:latest 
