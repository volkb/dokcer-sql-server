# DockerMSSQLServer

1. Create a .env file on the root of the project at the same level as the docker-compose.yml and define the following:
    ```
    SA_PASSWORD=<YOUR-DB-PASSWORD>
    ACCEPT_EULA=Y
    USERNAME=<YOUR-USERNAME>
    PASSWORD=<YOUR-PASSWORD>
    ```
2. Create your script for restoring the database. Use the following command to assist you in getting the names of the .mdf and .ldf in your backup.
    ```RESTORE FILELISTONLY FROM DISK='<PATH-To-YOUR-BACKUP-FILE>' WITH FILE=1```

3. create a folder in the /Docker directory called 'databases'	

4. Open a terminal (for windows use Powershell), and cd into the directory of the docker-compose file

5. Run `docker-compose up` and wait for the terminal to read "Finished setup script"

6. open Sql Server mgmt studio and login, your options should read as follows:
	```
	Server type: Database Engine
	Server name: localhost,1433
	Authentication: SQL Server Authentication
	Login: sa
	Password: [whatever password you set for SA_PASSWORD in the .env file mentioned above]
	```
7. Begin working. Any `.mdf` or other database files placed in the /Docker/databases directory will appear in the /tmp directory

8. When you are finished working, simply open a terminal (for windows use Powershell) and run `docker-compose down` this will turn off the server, freeing system resources and re-openeing port 1433  
