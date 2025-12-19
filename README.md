# Multi Team Forecaster for Jira and Azure DevOps
### What is it?
This report enables you to forecast multi-team delivery of a particular initiative/project. For each team it runs a monte carlo simulation based on the number of remaining items, Epic/Feature WIP and the confidence level chosen, as well as factoring in dependencies. For each team it will also show how reliable the forecast input data is (via a Process Behaviour Chart). The report can also (optionally) provide you with the actual count of remaining items for an Epic/Feature, so you can use this when deciding how many remaining items there are for a team.

With all teams in the report, it will show the combined confidence/delivery date based on the inputs you have chosen.

There is a demo version using anonymised data available [here](https://app.powerbi.com/view?r=eyJrIjoiNGM0MjE1ZTEtY2RjNi00MDc3LWIxODgtZDJlMDIxMDQ0Y2JjIiwidCI6IjVjYzc5MjVjLWY4MjQtNDJlZC1iYTY0LTRmYzUxMDlhYzE5YyJ9) if you would like to give it a try :)

### Why would you use it? 
- Use it to improve your confidence around delivery dates for individual teams, as well as for overall initiatives/projects 
- Better understand how ‘beliable' your inputs are from a forecasting perspective
- Experiment with different 'what if' scenarios around scope, WIP and confidence levels
- Understand the impact of dependencies on overall delivery

### Prerequisites/assumptions
* [Make sure you have the latest version of Power BI Desktop](https://aka.ms/pbiSingleInstaller)
* For Jira users:
  - Each team has their own respective project (i.e. not shared) in the same Jira instance
  - Throughput is used at the story level (i.e. may contain stories, bugs, tasks if configured at this backlog level)
  - Optionally, ensure you have the Epic/Feature IDs of items you want to know the remaining count for
* For ADO users:
  - Each team has their own board (i.e. not shared) in the same ADO organisation
  - Throughput is stories/PBIs/bugs and any custom work item types (regardless of backlog level)
  - Optionally, ensure you have the Epic/Feature IDs of items you want to know the remaining count for
* All teams being used have Throughput (completed items) - the report covers up to 9 teams, only complete it for as many teams as you need
* A minimum of two teams are needed for the report to work
  
* Download the appropriate template file:
  - [Azure DevOps / Azure DevOps Server / TFS version](https://github.com/nbrown02/Multi-Team-Forecaster/raw/refs/heads/main/Multi-Team%20Forecaster%20(ADO).pbit)
  - [Jira version](https://github.com/nbrown02/Multi-Team-Forecaster/raw/refs/heads/main/Multi-Team%20Forecaster%20(Jira).pbit) 
* Create/save an access token 
  - [Personal Access Token (PAT) if using Azure DevOps (make sure you have 'Read' Analytics access)](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows)
  - [Jira API token if using Jira](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)
* If you are a Mac user (or a user unable to install Power BI desktop) you can use the web-based template app [for Jira here](https://marketplace.microsoft.com/en-us/product/power-bi/thrivvepartners1747925071876.mtdf_jira?tab=Overview) or [for ADO here](https://marketplace.microsoft.com/en-us/product/power-bi/thrivvepartners1747925071876.mtdf_ado?tab=Overview)
* Then you're good to get started!

### Connectivity (Jira Version)
* Open the .pbit file in Power BI Desktop
* Add your Jira URL 
* For each respective team, enter the project key (note: Don't confuse the project name with the project key, a common mistake! Your project key will be in the URL when viewing an item)
* If you would like to know the remaining count for a particular Epic/Feature, add in the ID for this
* The report covers up to 9 teams, for any teams/Epic IDs you do not want/need, you must enter NULL
* It should then look something like this:
  
![JiraLogin](https://github.com/user-attachments/assets/a239650a-5b2c-4c36-a365-503677f9ed1f)

* Hit 'Load' 
* You will be prompted for a login, choose Basic and enter:
  - Your email associated with your Jira account for your username
  - Your API token you created in the Prerequisities

![alt text](https://raw.githubusercontent.com/nbrown02/FlowViz-Jira/main/Screenshots/Login2.png)

* Then hit 'Connect' and wait for the data and charts to load!

### Connectivity (Azure DevOps version)
* Open the .pbit file in Power BI Desktop
* Select http/https (only choose http if your Azure DevOps Server is HTTP)
* Add the Analytics / Azure DevOps Server URL - for Azure DevOps services enter 'analytics.dev.azure.com' / for Azure DevOps Server enter your server details
* Add your organization
* For each respective team, enter the project name and team name, please note this may mean repeating the project name, however don't confuse the team name with the project name, a common mistake. If the URL you use is "http://dev.azure.com/Microsoft-UK/AzureDevOpsTeam/Database", then *Microsoft-UK* is the Organization Name, *AzureDevOpsTeam* is the Project name, *Database* is the team name)
* As all fields are mandatory, if you do not need any project/team name values then enter BLANK
* If you would like to know the remaining count for a particular Epic/Feature, add in the ID for this
* As all fields are mandatory, if you do not need any Epic/Feature values then enter 0
* It should then look something like this:

![ADOLogin](https://github.com/user-attachments/assets/b4a8a16f-bb3e-4049-9aa9-cab8a89c647d)

* Hit 'Load' 
* You will be prompted for a login, choose Basic and enter:
  - Your PAT you created in the Prerequisites in the password field
  - Leave the username as blank or enter 'Dummy'
  
![alt text](https://docs.microsoft.com/en-us/azure/devops/report/powerbi/media/authentication-7.png?view=azure-devops)

* Once signed in hit 'Load' and wait for your report to load!

## Using the report
Once the report has loaded, hide any teams you don't need (unless you need all 9!) using the bookmarks. Then you can experiment with the different scenarios such as:

Scope (Remaining items)

![ScopeChange](https://github.com/user-attachments/assets/440f2959-1637-4855-a121-1ec050b6c8fa)

WIP limits

![WIPChange](https://github.com/user-attachments/assets/29b6fc45-4411-490c-83e6-603081e3b3d6)

Confidence levels

![PercentileChange](https://github.com/user-attachments/assets/5158c948-0238-4d3a-9298-1ed94546d49f)

As well as identifying dependencies between teams and the subsequent impact, for example if Team C became dependent on Team A:

![DependencyChange](https://github.com/user-attachments/assets/48a3580d-f866-418d-a25b-b65d3431efd9)

Note: there is an assumption here that work starts as soon as the team you are depending on finishes...which may not always be the case in your organisation!

You can also validate teams' Throughput data is above the Upper Natural Process Limit (UNPL) which is the orange line. If above the line, this may mean you need to be careful with using it as inputs to the forecast:

<img width="163" height="272" alt="image" src="https://github.com/user-attachments/assets/9d0883cd-fc3a-41fa-811d-65be727f0542" />


For anything else, check out the [FAQs](https://github.com/nbrown02/Multi-Team-Forecaster/blob/main/FAQs.md)
