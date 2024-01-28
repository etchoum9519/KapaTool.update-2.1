# KapaTool.update-2.1 
Capacity planification with SAP/R3 and Excel, for production departments

<br> 

The KapaTool originates from the need to plan capacities efficiently in production departments. It was important to efficiently manage and process SAP lists in order to make predictions about possible deficits or external orders. The programming of an interactive output calendar was foundedas solution to link employee lists with SAP capacities in a relatively short period of time. The project began in October 2022. The first versions were produced in March 2023 and August 2023, and the current 2.0 version is now fully usable.
<br> <br> 

# I - Usability

Three main steps are relevant by using the KapaTool software:

    1. Filling out the Excel input file
    
    2. Saving the Input file on a Server
    
    3. Analysis of inventories in the output calendar.

The following is a detailled explanation.
<br> <br> 

## A- How to fill the Excel Input file

<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/d99740ab-91b7-4cbf-a164-377be2bd26a6">
</p>

The responsible person receive the "in.xlsm" Input file (Excel Workbook with macros). If the password is entered successfully, the folder opens automatically with the following planning parameters to be filled in:

    • Projects, Orders or PSP-Elements in any order, comma-separated (with freely selectable colors [See Figure 3 right]) 

    • number of working days in the week (5 - 6) 
    
    • number of employees to plan (1 - 50) 
    
    • maximal number of working hours daily (6 - 10) 
    
    • maximal time capacity weekly (1 - 500) 
    
    • number of weeks to plan ( 1 - 30) 
    
    • status of the projects (whether open, already started or already finished), 
    
    • and whether the program should avoid empty Boxes. 

<p align="center">
  <img width="800" height="200" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/2cab8fbf-aab1-4621-a6f0-01b4a86d3719">
</p>

<img align="right" width="380" height="200" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/ab94e7a9-1c1a-40ec-9058-f2a6d8a237b0">
Projects can be assigned to employees. The program follows the specified parameters exactly. Because both departments switchgear manufacture and kiln construction are preferred,some employees could sometimes become no project attributed. This situation can be averted by checking the box „AUTOMATIC FILL“, so that all remaining work projects are automatically distributed.
<br> <br> 
The following informations may prove to be helpful for the correct allocation of capacities.

<br> <br> 

## B - How to save the Input file onto a server

The Kapa-Software offers three execution buttons:

    • SAVE: Automatic storage on the onejoon server (link: ’/opt/kapa/data/in/in.xlt’)

    • REFRESH LIST: Automatic updating of SAP capacity lists (from source: ’/opt/kapa/data/sap/export.xlsx’)

    • ACCEPT: Automatic processing of the Python script with reference to the completed input parameter.

As a rule, the user should specify here in the following order

    1. which object type is concerned for the respective employee. Possible selections are „PROJECT“, „PSP“or „ORDER“. The software offers an automatic selective option to predefine objects based on the updated source table on the right.

    2. up to three different calendar weeks ...

    3. in which the employee can be reported as being in „BUSINESS-TRIP“, „HOLIDAY“, „SICK“, or in „TRAINING“,

    4. as well as the days on which these prescriptions are to take place.

<br>

Note: The KapaTool takes year ends and only current and up-coming calendar weeks and days into account to ensure accuracy in the data generated from the output calendar

<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/b68490e9-86f8-4ae3-8ea9-7febced2c381"
</p>
<br> <br> 

## C - Security procedures, Sustainability

The input file contains three analogous attached workbooks with names resp. „Projects&transaction quantities“, „DATA“(updated SAP lists), and „Time series“. These are used to immediately view the working flow and capacities according to the status specified in the input file, their development over time. They can only be edited by removing the respective sheet protection using the respective sheet password, and automatically updated by pressing the „REFRESH LIST“- button.

<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/d1c7aa84-38c4-4e7e-b58e-6ef611a13f7d"
</p>
<p align="center">
  <img width="800" height="200" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/22a2e6d6-7090-470f-944f-35c430a73ac8"
</p>
<br> 
<img align="left" width="600" height="200" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/a186b26b-f76a-4117-9a69-ce8252e9df24">
<br>   
The software does not necessarily need all open areas in the Team Management section to be closed to work efficiently. In some cases, however, it may be necessary to keep the names of the departments safe from external view. In this case, first collapsing all open areas would be required for this function to be successful.
<br> <br>


# II - Output Calendar, Analysis of Inventories 

After all parameters have been successfully entered in the input file, an output file is placed in the
output directory after two minutes if the „ACCEPT“-button is pressed.

The created calendar mainly consists of three parts:

    • An introduction with all important input parameters as well as an explanation of some derivations of these parameters as well (e.g data, time, total working hours per project, effective and remaining working hours).


<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/dd9df18f-02f3-47c0-8bcb-ea9e604ae7b8"
</p>
    
    • The calendar itself with specifications of the input


<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/66e1a8e8-016a-4297-bbcd-acffdc50fbc2"
</p>
    
    • An area for the analysis of inventories with summations from related calendar weeks, and graphs for an improved view of the project development, as well as an upper limit for the maximum weekly specified workloads in each case

    • For better overview, the grafics can be updated according to maximum weekly capacity utilization, for example
    
<img align="left" width="500" height="600" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/c76458b1-ed7d-4207-b70c-0b5b528e8e57" hspace="10" >
Ist-Soll Analyse
<br clear="left"/>
<img width="500" height="600" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/e1b50558-e7d9-4320-a8dd-49e016729558" hspace="900" >


    • The maximum utilization time is flexible and some target workstations are not assigned according to the designations 63*, 64* or 65* [See Figure 16 and 17].

<p align="center">
  <img width="800" height="200" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/169018ca-ba0e-4ead-953f-7f117ef7a813"
</p> 

    • A related workbook with the selected data set for rapid search is also available

<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/05527d8c-34a7-4d3d-a5cf-700fa142faf2"
</p> 
    • Complete workbook for a quick overview and comparison

<p align="center">
  <img width="800" height="300" src="https://github.com/etchoum/capacity-planification-tool/assets/93908331/c087e86c-15dc-4aad-aecb-3936870f71e6"
</p> 
<br> <br>

# Conclusion - The Software Supply-Chain

The complete process can be described in nine main steps, whereas the last one counts for the repetition of the complete algorithm. In summary, the following main steps are observed:

![Bildschirmfoto 2024-01-27 um 17 43 51](https://github.com/etchoum/capacity-planification-tool/assets/93908331/44868ce0-e217-4021-bd69-70c066164212)

# Contacts
e.tchoumkeungatat@stud.uni-goettingen
etchoum9519@gmail.com



