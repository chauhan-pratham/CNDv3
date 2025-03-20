### Summary of Steps for Implementing Encryption on SQL Server Database Using Transparent Database Encryption (TDE)

1. **Launch VMs**: Start the Smoothwall Firewall VM and log in with the password `toor`. Then, launch the Web Server VM and log in as `Administrator` (password: `admin@123`). Close the server manager dashboard if it appears.

2. **Open SQL Server Management Studio**: Click the Windows Start icon and select Microsoft SQL Server Management Studio 19 (MSSMS 19). In the Connect to Server window, select:
   - **Server type**: Database Engine
   - **Server name**: Webserver
   - **Authentication**: SQL Server Authentication
   - Log in with username `sa` and password `qwerty@123`, then click `Connect`.

3. **Create Master Key**: In the SQL query editor, type the following command to create a master key:
   ```sql
   USE MASTER;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD='Passw00rdCND';
   GO
   ```
   Click `Execute`. You should see a message indicating that the command completed successfully.

4. **Create Certificate**: Type the following command to create a certificate for encrypting database encryption keys:
   ```sql
   CREATE CERTIFICATE CND
   WITH 
   SUBJECT='CERTIFIED NETWORK DEFENCE';
   GO
   ```
   Click `Execute` and confirm successful execution.

5. **Create New Database**: In Object Explorer, right-click on `Databases` and select `New Database`. Name the database `CNDAccess` and click `OK`.

6. **Create Table**: In the SQL query editor, type the following command to create a table:
   ```sql
   USE [CNDAccess];
   CREATE TABLE empdata (Empid nvarchar(50) NOT NULL,
   Empname nvarchar(50) NULL, CONSTRAINT [PK_empdata] PRIMARY KEY CLUSTERED(Empid));
   GO
   ```
   Click `Execute` to create the table.

7. **Insert Records**: Insert records into the `empdata` table with the following commands:
   ```sql
   INSERT INTO empdata (Empid, Empname) VALUES(1,'john');
   INSERT INTO empdata (Empid, Empname) VALUES(2,'Martin');
   INSERT INTO empdata (Empid, Empname) VALUES(3,'Alice');
   INSERT INTO empdata (Empid, Empname) VALUES(4,'Bob');
   INSERT INTO empdata (Empid, Empname) VALUES(5,'Cherry');
   ```
   Click `Execute` to insert the values.

8. **Create Database Encryption Key**: Type the following command to create a database encryption key:
   ```sql
   CREATE DATABASE ENCRYPTION KEY WITH ALGORITHM = AES_256 ENCRYPTION BY SERVER CERTIFICATE CND;
   GO
   ```
   Click `Execute`. You may receive a warning message.

9. **Enable Encryption**: Resolve the warning by enabling encryption with the following command:
   ```sql
   ALTER DATABASE CNDAccess SET ENCRYPTION ON;
   GO
   ```
   Click `Execute`.

10. **Verify Encryption**:
    - To check the created certificate, type:
      ```sql
      USE MASTER;
      SELECT * FROM sys.certificates;
      ```
      Click `Execute` to confirm the certificate is created.
    
    - To verify the encryption state of the database, type:
      ```sql
      SELECT encryption_state, percent_complete, encryptor_type, * FROM sys.dm_database_encryption_keys;
      ```
      Click `Execute` and check that `encryption_state` shows `3`, indicating the database is encrypted.

By following these steps, network defenders can successfully implement Transparent Data Encryption (TDE) in SQL Server to enhance data security and maintain confidentiality.