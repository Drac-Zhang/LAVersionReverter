## Introduction
This tool can be used for revert the Logic App Standard workflow's previous version which we don't have this this feature on portal yet.

## How to use
1. Open Kudu (Advanced Tools) of Logic App Standard and upload this tool into a folder
![image](https://user-images.githubusercontent.com/72241569/139808016-75b98cb6-c976-4b90-a23b-c032020094c2.png)

2. Use command **LAVersionReverter backup -cs [ConnectionString]** to backup all the existing workflows. The connection string can be found in Storage Account - Access Key
   After run the command, the tool will create a new folder which called "**Backup**", the sub-folders will be named as workflow name. Each definition will be a seperate json file.
![image](https://user-images.githubusercontent.com/72241569/139810655-bf91315a-c49a-4d96-8c0c-a5628c0c9cd6.png)

3. Recently we have to check the definition manually to see which version we would like to revert to. 
   The version is the last part of the file name.
![image](https://user-images.githubusercontent.com/72241569/139812550-29420c41-ab80-4ccd-ad2e-59a471991ab1.png)

4. Use command **LAVersionReverter Revert -cs [ConnectionString] -n [Workflow Name] -v [Version]** to revert to previous version

## Limitation
1. This tool only modify workflow.json, if the API connection metadata get lost in connections.json, the reverted workflow will not work.
2. If the definition not be used in 90 days, the backend service will remove it from storage table, so this tool will not be able to retrieve the definitions older than 90 days.

## Supported Command
1. **Backup**: Backup all the existing definitions into Json files
2. **Clone**: Clone a workflow to a new one, exactly the same as clone in Logic App comsumption
3. **Decode** Decode a difinition into readable content
4. **ListVersions** List all the existing versions of a workflow
5. **Revert** Revert a workflow to previous version as per version ID.
6. **-?/[command] -?** help of the command
