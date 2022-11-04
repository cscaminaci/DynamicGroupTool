# DynamicGroupTool

This tool was originally written to help bring O365 distribution groups into managed on-premises security groups that could be programmatically kept up to date
and synced back forward to O365.

This tool does a few things:

1. On startup will look for the closest domain controller and pull OUs from it.
2. Hitting "Connect Exchange Online" will have the tool look for your Azure PFX - you need to fill this data in before running the script. If you prefer to use
manual authentication you can change the script to just "Connect-ExchangeOnline" and it'll show a prompt instead of looking for a PFX.
3. You can then see a list of distro groups that exist in 365. Selecting one and hitting "Create Group" will compare the 365 group to on-prem AD users and mirror the
group with membership to an AD security group and assign all the necessary values to allow the group to sync forward. It DOES NOT remove the existing 365 group. 
You will need to do that yourself to allow the new group to sync from on-prem. (This process assumes you have a hybrid setup or you have extended your AD schema with
the msEXCH attributes)
4. You can also load a CSV of users in that it will parse and create the group with.
![image](https://user-images.githubusercontent.com/68078971/199983488-81c9eeb7-7a68-419f-8a50-f2a1a345dc3d.png)
