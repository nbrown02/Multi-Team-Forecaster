# Multi Team Forecaster for Jira and Azure DevOps
### What is it?
This report enables you to forecast multi-team delivery of a particular initiative/project. For each team it runs a monte carlo simulation based on the number of remaining items and the confidence level chosen. It will also show how reliable the forecast input data is (via a Process Behaviour Chart) and allow you to factor in dependencies. It will then show the combined confidence/delivery date based on the inputs you have chosen.

### Why would you use it? 
- Use it to improve your confidence around delivery dates for individual teams, as well as  overall initiatives/projects 
- Better understand how ‘breliable' your inputs are from a forecasting perspective
- Experiment with different 'what if' scenarios around scope and confidence 
- Understand the impact of dependencies on overall delivery

### Prerequisites/assumptions
* For Jira users:
  - Each team has their own respective project (i.e. not shared) in the same Jira instance
  - Throughput is used at the story level (i.e. may contain stories, bugs, tasks if configured at this backlog level)
* For ADO users:
  - Each team has their own board (i.e. not shared) in the same ADO organisation
  - Throughput is stories/PBIs/bugs and any custom work item types (regardless of backlog level)
* Any teams being used have Throughput (completed items)
* The report covers up to 9 teams, only complete it for as many teams as you need
* A minimum of two teams are needed for the report to work
  
* Download the appropriate template file:
  - [Azure DevOps / Azure DevOps Server / TFS version](https://github.com/nbrown02/Multi-Team-Forecaster/raw/refs/heads/main/Multi-Team%20Forecaster%20(ADO).pbit)
  - [Jira version](https://github.com/nbrown02/Multi-Team-Forecaster/raw/refs/heads/main/Multi-Team%20Forecaster%20(Jira).pbit) 
* Create/save an access token 
  - [Personal Access Token (PAT) if using Azure DevOps (make sure you have 'Read' Analytics access)](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows)
  - [Jira API token if using Jira](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)
* Then you're good to get started!

### Connectivity (Azure DevOps Version)
* Open the .pbit file in Power BI Desktop
* Select http/https (only choose http if your Azure DevOps Server is HTTP)
* Add the Analytics / Azure DevOps Server URL - for Azure DevOps services enter 'analytics.dev.azure.com' / for Azure DevOps Server enter your server details
* Add your organization
* For each respective team, enter the project name and team name, this may mean repeating the project name (note: Don't confuse the team name with the project name, a common mistake. If the URL you use is "http://dev.azure.com/Microsoft-UK/AzureDevOpsTeam/Database", then Microsoft-UK is the Organization Name, AzureDevOpsTeam is the Project name, Database is the team name)
* The report covers up to 9 teams, only complete it for as many teams as you nee
* It should then look something like this:

IMAGE

* Hit 'Load' 
* You will be prompted for a login, choose Basic and enter:
  - Your PAT you created in the Prerequisites in the password field
  - Leave the username as blank or enter 'Dummy'
  
![alt text](https://docs.microsoft.com/en-us/azure/devops/report/powerbi/media/authentication-7.png?view=azure-devops)

* Once signed in hit 'Load' and wait for your report to load!


### Connectivity (Jira Version)
* Open the .pbit file in Power BI Desktop
* Add your Jira URL 
* For each respective team, enter the project key (note: Don't confuse the project name with the project key, a common mistake! Your project key will be in the URL when viewing an item)
* The report covers up to 9 teams, only complete it for as many teams as you need
* It should then look something like this:

IMAGE

* Hit 'Load' 
* You will be prompted for a login, choose Basic and enter:
  - Your email associated with your Jira account for your username
  - Your API token you created in the Prerequisities

![alt text](https://raw.githubusercontent.com/nbrown02/FlowViz-Jira/main/Screenshots/Login2.png)

* Then hit 'Connect' and wait for the data and charts to load!

## Using the report
Once the report has loaded, hide any teams you don't need (unless you need all 9) using the bookmarks:

![GIf1](https://github.com/user-attachments/assets/4af20bc8-3cc7-4176-9444-e71f733b6d2e)

Then you can experiment with the different scenarios around scope (remaining items) and confidence, seeing the impact in your overall date/confidence:

![Gif2](https://github.com/user-attachments/assets/81324937-199a-4f78-b529-88d59bb47dfc)

You can also check any teams where the input data (Throughput) is above the Upper Natural Process Limit (UNPL) which is the orange line. If above the line, this may mean you need to be careful with using it as inputs to the forecast:

<img width="163" height="272" alt="image" src="https://github.com/user-attachments/assets/9d0883cd-fc3a-41fa-811d-65be727f0542" />

You can also factor in one or many dependencies, for example if team X was dependent on team X, we would identify this in the slicer, with our forecast updating:

![GIF3](https://github.com/user-attachments/assets/9116eb13-049a-4089-acd5-767aacb2af38)

Note: there is an assumption here work starts as soon as the team you are depending on finishes...which may not always be the case in your organisation!

For anything else, check out the [FAQs](https://github.com/nbrown02/Multi-Team-Forecaster/blob/main/FAQs.md)
