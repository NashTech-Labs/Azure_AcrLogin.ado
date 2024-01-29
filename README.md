# Azure_AcrLogin.ado
Use this template to log in or log out, start or stop containers, or run a Docker command. It can be used to shows a container registry sign on using a Docker registry service connection.


## Parameters:

The pipeline requires the following parameters to be defined:


| Name | type | Default | Required/Optional | Comments |
| :-------------: | :-------------: | :-------------: | :-------------: | :------------- |
| serviceConnection | Azure Service Connection for acr registry or azure resource manager in your Azure pipeline | string | | | Required | This helps the module to authenticate with registry or azure cli |
| addPipelineData  | pipeline data: source branch, build ID| boolean | true | true / false | Optional | helps to inspect error of image built |
| addBaseImageData | base image data: image name, digest | boolean | true | true / false | Optional |helps in traceability |
| stepname | String |  | Optional | It enables the step name to be defined | 

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_AcrLogin.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_AcrLogin.yaml
    parameters:
      containerRegistry: ${{parameters.serviceConnection}}
      addPipelineData: ${{parameters.addPipelineData}}
      addBaseImageData: ${{parameters.addBaseImageData}}
        
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
