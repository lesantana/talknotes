Welcome to the Fabric Workshop wiki page. This page contains all of the links you will need for today's content, plus any changes/workarounds that may be needed. We hope you enjoy the day!
 
## Links
 
* This page: [https://aka.ms/fabric-toronto](https://aka.ms/fabric-toronto)
* Eval Form for End of Day: [Fabric Event Eval](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbR5UnTHndg5dHvqF4p45wkjZUOUI3TUdTODlRTVM0NEtVOE02R0ROTk5HNy4u&origin=QRCode&qrcodeorigin=presentation)
 
Portals:
* Azure Portal: [https://portal.azure.com](https://portal.azure.com)
* Fabric Portal: [https://app.fabric.microsoft.com](https://app.fabric.microsoft.com)
 
Content Origin (for reference, outside of lab):
* Original GitHub repo with Labs: [https://aka.ms/fabricrealtimelab](https://aka.ms/fabricrealtimelab)
* Resources Zip File (notebooks): [https://aka.ms/fabricrealtimelab-resources](https://aka.ms/fabricrealtimelab-resources)
 
Lab Access and Information:
* Registering for labs: [https://cloudweeks.learnondemand.net](https://cloudweeks.learnondemand.net/)
* Key: 75ACD06FC7824114
 
Partner Resources:
* [Microsoft Fabric Partner Community](https://aka.ms/JoinFabricPartnerCommunity)
* [Learn Fabric](https://aka.ms/learn-fabric)
* [Fabric Bootcamp](https://aka.ms/azuredepthworkshops)
* [Fabric Partner Resources](https://aka.ms/FabricPartnerResources)
* [Industry Dream Demos](https://aka.ms/dreams)
* [Analytics Campaign in a Box](https://aka.ms/AnalyticsCIAB)
* [Deliver a x-IAD - In a Day Workshop](https://aka.ms/XIADPartnerOpportunity)
* [Azure Innovate](https://aka.ms/AzurePLofferings)
* [Fabric Featured Partner](https://aka.ms/FabricFeaturedPartners)
* [How to become a Microsoft Featured Partner](https://aka.ms/HowToBecomeFFP)
 
Highlights from [Build](https://build.microsoft.com):
* [Microsoft Fabric: What's new and what's next](https://build.microsoft.com/en-US/sessions/e2dadf62-d982-4467-9c5c-fd232d663783?source=sessions)
* [Reimagine Real-Time Intelligence with Microsoft Fabric](https://build.microsoft.com/en-US/sessions/2b5c3675-36e7-4d70-bf4e-3d98c913a018?source=sessions)
* [The mechanics of Real-Time Intelligence in Microsoft Fabric](https://build.microsoft.com/en-US/sessions/514d3926-7f9a-412b-a095-93d6e5df0bca?source=sessions)
* [Integrating Azure AI and Microsoft Fabric for Next-Gen AI Solutions](https://build.microsoft.com/en-US/sessions/91971ab3-93e4-429d-b2d7-5b60b2729b72?source=sessions)
 
## Agenda
 
Note: in today's workshop, we are skipping **Lab 03: Building a DW using Pipelines**.
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/b2dc58b3-5666-4817-9b00-b949480bedf5)
 
***
 
## Lab Notes
 
There are several changes in the labs that are covered in these notes below.
 
## LAB 01: Ingesting Data using RTA
 
After launching the lab, retrieve your username and password from the Resources tab and keep them handy (such as in a local notepad window). The Azure promo code is used to activate an Azure trial environment. You may use the VM provided in the lab and/or log in using your own browser:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/3021ecc2-208b-4ce6-8a5e-7bd6f7a8c2e5)
 
### Exercise 1: Environment Setup
 
The data generator app we've built uses a container and Event Hub that is deployed in Azure. If you'd like to deploy this yourself, you can do so either using your own Azure subscription (~$1.70/day), or redeem an Azure Pass free trial using the promo code on the Resources tab. However, to help streamline the day, we've deployed the generator for the group, so you will not need Azure access if you'd like to use the group Event Hub. Connection details are included here -- each attendee is assigned a Consumer Group.
 
If you are using the group Event Hub, you only need to do these Tasks in the module:
 
* **Task 1: Sign in to Power BI account and sign up for the free Microsoft Fabric trial**
* **Task 2: Start the Microsoft Fabric trial**
* Skip Task 3: Redeem Azure Pass
* Skip Task 4: Log Analytics Contributor role assignment
* Skip Task 5: Create Storage Account
* **Task 6: Create Fabric Workspace**
  * When naming your workspace, you will likely need to make the name globally unique. Instead of "RealTimeWorkspace", add your initials, firstname, or change the name as you see fit. All items from the workshop today will go into this workspace.
* Skip Task 7: Deploy the app via Azure Container Instance
* **Task 8: Get data with Eventstream**
 
If you'd like to deploy the stock generator app yourself, follow these steps:
 
* **Task 1: Sign in to Power BI account and sign up for the free Microsoft Fabric trial**
* **Task 2: Start the Microsoft Fabric trial**
* **Task 3: Redeem Azure Pass**
* Skip Task 4: Log Analytics Contributor role assignment
* Skip Task 5: Create Storage Account
* **Task 6: Create Fabric Workspace**
  * When naming your workspace, you will likely need to make the name globally unique. Instead of "RealTimeWorkspace", add your initials, firstname, or change the name as you see fit. All items from the workshop today will go into this workspace.
* **Task 7: Deploy the app via Azure Container Instance**
* **Task 8: Get data with Eventstream**
 
In **Task 6**, give the Workspace a unique name, such as "Workshop-initials" or similar:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/467d5e14-36aa-4862-ab45-5ab3d5e214c6)
 
In **Task 8**, be sure to do the following:
* Use the following Event Hub connection details:
 
| Setting | Value|
| -------- | ------- |
| Event Hub namespace| **ehns-toronto-fabricworkshop** |
| Event Hub| **stockeventhub** |
| SAS Name| **stockeventhub_sas** |
| SAS Key| **9TR249DduSgW0hgHucZEwNFVCQ+GOhK1H+AEhHxJpUE=** |
| Consumer Group | Individually assigned, see handout |
 
* Delete the default Connection Name and provide a unique name in the textbox, such as *EventHub-Connection-{initials}* or similar:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/4e093598-c03b-4b1b-b07e-a3916c7542a1)
 
### Exercise 2: KQL Database Configuration and Ingestion
 
#### Task 1: Create KQL Database
 
As part of the new Real-Time Intelligence features, all KQL databases are part of an EventHouse. Some screenshots may not have been updated.
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/6860198d-ef85-4f41-a933-cfe45e611977)
 
***
 
## LAB 02: Using KQL and building reports
 
No additional notes at this time.
 
***
 
## Lab 03: Building a DW using Pipelines
 
Please skip this lab for today's workshop. (Of course, you are free to work on this if time permits or outside of the lab!)
 
***
 
## Lab 04: Building a Data Lakehouse
 
When working with the notebook **Lakehouse 2: Build Aggregation Tables**, many steps focus on using Data Activator to help shape and aggregate the data. Data Wrangler is a visual tool that outputs Python code into a new notebook cell. If you'd like to save time, each of the 3 Data Wrangler steps has been completed and is commented out, and should look like the below image:
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/60655d53-d012-478e-9229-4e5abdf348ff)
 
If you'd prefer to avoid going through the Data Wrangler steps or run into any challenges, you can use the code in the commented cell. Highlight all of the code in the cell (**CTRL-A**) and then uncomment all of the code (**CTRL-/**). This can be done for any or all of the Data Wrangler steps.
 
***
 
## Lab 05: Getting Started with Building a ML Model in Fabric
 
There are 3 notebooks used in this lab:
 
| Notebook | Purpose |
| -------- | ------- |
| DS 1 - Build Model | Builds an ML model using Prophet, examines data, and stores model in MLflow |
| DS 2 - Predict Stock Prices | Consume MLflow from a notebook |
| DS 3 - Forecast All | Build predictions for all stock symbols and store in a Delta table |
 
DS 1 and DS 2 are largely examples/theory of how to work with data, evaluate the results, and store the model in MLflow. DS 3 is the main notebook that generates predictions for all stocks and stores the results in the **stocks_prediction** table.
 
To save time: if you're primarily interested in data analysis and setting up experiments and comparing runs in MLflow, focus on DS 1 and DS 2. If you're more interested in getting the predictions and building a semantic model and report, consider jumping right to DS 3 (which is **Exercise 3: Solution in practice** in the lab).
 
![image](https://github.com/bhitney/TalkNotes/assets/2793422/f40d2b5a-43b0-4f9f-91fc-49f223360d85)
