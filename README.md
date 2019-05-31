# Anonymize Isah Databases

Anonymize data in Isah databases

The scripts in this repo can be used to anonymize data in Isah Databases. 
The script will make it safer to distributed a copy of an Isah Database by replacing the data that may impose a security or GDPR risk with dummy data.

Use the correct script (created for the Isah Database version you are using) to make sure it will operate as intended and without error's. We suggest to load a backup of the live/production environment to a new database named 'Anonimized_[ORIGINALNAME]' and excecute the script on that database. The script is secured to only work on database with the word 'anonimized' in the name to prevent unintended execution. 

This sql script may be used at your own risk. 
Tambien will not accept any responsibility for the functionality of this script.
Tambien hereby grants anyone the right to use and modify this script to it's own liking.
It is appreciated when improvements to the script are sent to anonymize@tambien.nl.

WARNING
Take note that the script modifies data in the database which can cause the database to stop functioning.
Test the script in a safe environment before using it in your production environment.

This script will take some time to complete, be patient!

------------------
Details

The script will perform these actions:
- Check if the target database contains the word TEST. If not the script will not run. This is to ensure no live data is removed
- Create table ST_T_Anonymized (if not existing) and insert a record for logging of the execution and
- Create some helpers tables (IBAN and VAT numbers to replace existing ones with technical valid ones)
- Anonimize T_BankAccount
- Empty T_BankAccountLog
- Anonimize T_CallRegistration
- Anonimize T_Customer
- Empty T_CustomerLog
- Anonimize T_CustomerAddress
- Empty T_CustomerAddressLog
- Anonimize T_CustomerRelation
- Anonimize T_Department
- Anonimize T_DossierDetail
- Anonimize T_DossierMain
- Anonimize T_Employee
- Empty all T_Hist?? tables
- Anonimize T_InvoiceDetail
- Anonimize T_InvoiceMain
- Anonimize T_MemoDetail
- Anonimize T_Part
- Anonimize T_ProductionHeader
- Anonimize T_ServObject
- Anonimize T_Vendor
- Empty T_VendorLog
- Anonimize T_VendorAddress
- Empty T_VendorAddressLog
- Anonimize T_VendorRelation
- Update ST_T_Anonymized with end time
