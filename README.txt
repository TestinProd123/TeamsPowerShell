NOTE: This script was created for a particular purpose that suited my environment and was not created by Microsoft. 
Usage of this script is at your own risk and any errors, issues or problems encountered through the use of this script are the reposnsibility of the person running it. 
I take no responsibility for any issues you envounter by using the script.
You are welcome to edit, modify and distribute this script as you see fit.

####Using the script

##Prerequisites:
*Note: this Tool leverages the Add-TeamChannelUser and Remove-TeamChannelUser cmdlets which requires the MicrosoftTeams v1.1.3 Module. 
For guest inviting the Azure AD Module is also required. Without these Modules this script may not function properly.

The script contains a number of commented out functions:
* Specific allowed domains for guest inviting
* Assign users to a group automatically as they are guested in to your AAD.

You should modify the script as needed.

## Selecting an option
1.) Copy the contents of the "Teams Bulk Admin Script" to notepad and save it as "Teams Bulk Admin Script.PS1" as file type "all files".
2.) Right click "Teams Bulk Admin Script.PS1" and click "Run with Powershell"
3.) Accept the terms and conditions set out by the script by pressing "Y"
4.) Choose a program, either option 1 or 2.
	Option 1:  B2B Guesting and User Assignment Tool: This tool is used to onboard guest users to your organisation and allocate them to specific Teams and Private Channels based on a CSV file.
	Option 2:  Bulk Team/Channel Removal Tool: This tool is used to remove B2B guest users from specific Teams and Private Channels based on a CSV file.

## Option 1:  B2B Guesting and User Assignment Tool
1.) Sign in to the Microsoft Teams module with a user with sufficient permissions
2.) Sign in to the Azure AD module with a user with sufficient permissions.
3.) Define your home UPN pattern - this will be used to bypass users from your home UPN when guest inviting.
4.) Define the path of the CSV file you will use for on boarding.
5.) The script will complete and save any errors to a reporting error log
6.) On completion of the script the text file will open from your temporary directory automatically

## Option 2:  Bulk Team/Channel Removal Tool
1.) Sign in to the Microsoft Teams module with a user with sufficient permissions
2.) Sign in to the Azure AD module with a user with sufficient permissions.
3.) Define the path of the CSV file you will use for off boarding.
4.) The script will complete and save any errors to a reporting error log
5.) On completion of the script the text file will open from your temporary directory automatically

##### Option 1:  B2B Guesting and User Assignment Tool: On boarding guest users to AAD and then assigning them to Teams and Private Channels in your environment:

##Purpose:
I have created a script to bulk invite guest users from other organisations in to Azure Active Directory, assign these guested users to teams, set the users permissions and define their access to private channels through automation. 
To batch these actions this script will require a list of the users that you wish to have added to the Teams environment and to which Teams and Channels these users should be assigned.
To make things easier a csv template has been provided which can be edited by using Microsoft Excel(InviteTemplate.CSV). 
 

##The columns include the following:
*UserUPN: this is the UPN or sign-in address of the person you would like to have guest invited to your AAD and Teams environment.
*UserName: The display name you would like to give to the user.
*TeamName: This is the name of the Team that the user will be invited to.*
*ChanelName1: The name of a Private channel that the user requires access to.
*ChanelName2: The name of a Private channel that the user requires access to.
*ChanelName3: The name of a Private channel that the user requires access to.*
Note: If a user is in multiple Teams you should add multiple lines for them in this file to indicate the different Teams that the user should have access to.
If the user needs to be added to more than 3 channels a second line should also be added for the user. 

##How to fill in the fields

*UserName
This would be the display name for the user. Typically this is their first and last name.

*TeamNames:
For each of the users you request to add, you will need to select a Team Name
Please be aware that these must be spelled correctly otherwise the user will not be added to them correctly.

*ChannelName1, ChannelName2, ChannelName3:
Each Team has its own channels, standard channels allow access to all members of a Team whereas Private Channels require specific assignment of user.
Please be aware that these must be spelled correctly otherwise the user will not be added correctly.


####Bulk Team/Channel Removal Tool: Off boarding users from the Teams and Channels in your environment:

##Purpose:
I have created a script to bulk remove guest users and AAD Native/AD synced users from Teams and Private Channels in your environment. 
To batch these actions this script will require a list of the users that you wish to have removed from specific Teams and Private Channels in your Teams environment and from which Teams and Channels these users should be removed
To make things easier a csv template has been provided which can be edited by using Microsoft Excel.(RemovalTemplate.CSV)
 

##The columns include the following:
*UserUPN: this is the UPN or sign-in address of the person you would like to have removed from the Team/Private Channels in your Teams environment.
*UserName: The display name of the user (not required field)
*TeamName: This is the name of the Team that the user will be removed from. This will reflect the Team they are in*
*ChanelName1: The name of a Private channel that the user requires removal from.
*ChanelName2: The name of a Private channel that the user requires removal from.
*ChanelName3: The name of a Private channel that the user requires removal from.*
Note: If a user is in multiple Teams you should add multiple lines for them in this file to indicate the different Teams or Private channels that the user should be removed from.
If the user needs to be removed from more than 3 Private channels a second line should also be added for the user. 
*RemoveFromTeam: Whether the user should be fully removed from the Team or just a channel. “Y” indicates that removal from the whole Team is necessary otherwise leave this field blank.

##How to fill in the fields

*UserName
This would be the display name for the user. Typically this is their first and last name.

*TeamNames:
For each of the users you request to remove, you will need to select a Team Name
Please be aware that these must be spelled correctly otherwise the user will not be added correctly.

*ChannelName1, ChannelName2, ChannelName3:
Each Team has its own channels, standard channels allow access to all members of a Team whereas Private Channels require specific assignment of user.
Please be aware that these must be spelled correctly otherwise the user will not be added correctly.


