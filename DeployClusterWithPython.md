# How to deploy a Spark cluster with ESP using python 3

Author: Alexander Lee

### Contents
[**Purpose**][Purpose]<br>
[**Steps**][Steps]<br>
[**Prerequisite**][Prerequisite]<br>
[**Applying Python Script**](#applying-the-python-script-to-your-runbook)<br>
[**Running your Runbook**](#running-the-runbook)<br>
[**Setting Time to live for cluster**](#setting-time-to-live-for-cluster)





### Purpose
> The purpose of this HowTo is to show CSS Support engineers how to deploy a cluster using python SDK.  In this HowTo we will be using Python 3 to create a spark cluster.  We will also be using the latest modules to deploy the cluster.
> This will help with cost saving for our ESP Subscription.

### Steps
Step 1: (Prerequisite) Install all packages to your Runbook.<br>
Step 2: Copy provided python script.<br>
Step 3: Replace information in the python script.<br>
Step 4: Run the Runbook.


### Prerequisite:
> Python packages needs to be added to the runbook before running the python script.  In order to add packages you can follow this document.  Below are also images of how to do this.

Adding Python packages to runbook:<br>
https://docs.microsoft.com/en-us/azure/automation/python-3-packages#import-a-package

Adding Python packages to the Runbook:<br>

***Python packages in Runbook Image***
![Python packages to Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/runbookPythonPackages.png)

After following the steps in the picture above you will get to this:

***Add Python Package Popup Image***

![Add Python Package side popup](https://cssexamplesallee.blob.core.windows.net/markdownimages/sidepopupPythonPackages.png)

Once you are at this point, you will need to download wheel files from python package distribution.  Follow this link: https://pypi.org/search/

Once you are at pypi.org, you'll be able to search for the packages you need for the runbook.

***PyPi Search Image***
![PyPi Search page](https://cssexamplesallee.blob.core.windows.net/markdownimages/pypiSearchPage.png)

In the search bar you will need to look for these packages.  **See number 3 in *Needed Package Images* and download all packages in the box.**
<br>

***Needed Package Images***

![Needed Packages](https://cssexamplesallee.blob.core.windows.net/markdownimages/neededPackages.png)


Once you have added in all four packages to your Runbook, you are now ready to add the python script to your Runbook.

## Applying the Python script to your Runbook.

>Once you have completed the Prerequisite you can now apply the Python script to your Runbook.
Let's create a new Runbook to use it for a Python script.  To create a new Runbook click on Runbooks on the left hand side.

![Runbook Creation](https://cssexamplesallee.blob.core.windows.net/markdownimages/RunbookCreation.png)

To apply the Python script to your Runbook you need to click on **Edit**.

![Runbook Edit Button](https://cssexamplesallee.blob.core.windows.net/markdownimages/RunbookEdit.png)

After clicking on **Edit** a new section will come up.

![Runbook Edit Button](https://cssexamplesallee.blob.core.windows.net/markdownimages/RunbookEditPage.png)

You will need to download this example script and replace your information into **' '** and **< username >**

The script is located here: https://cssexamplesallee.blob.core.windows.net/examplepythonscripts/pythonscripts/pythonClusterCreationExample.py

Once you have downloaded the python script and made the appropriate adjustments, you can Publish.

![Runbook Edit Button](https://cssexamplesallee.blob.core.windows.net/markdownimages/RunbookPublish.png)

## Running the Runbook

>In this final section, you will Run your Runbook to deploy your cluster.

![Start and Status](https://cssexamplesallee.blob.core.windows.net/markdownimages/StartandStatus.png)

## Setting Time To Live for cluster

>Once you have tested your cluster creation using the Python Script and it is successful, you need to create a new Runbook.
This new Runbook will delete the cluster with the provided time.

To start let's create a new Runbook for the deletion.  Make sure to choose **Powershell** under **Runbook Type**.

![Create delete Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/CreateDeleteRunbook.png)

Please name the Runbook so you understand what it is for.  Also, it is recommended to provide a Description of what this Runbook does.

Once this Runbook is created click into the newly created Runbook.

![Click delete Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/clickDeleteRunbook.png)

This will take you into the Runbook.  Here you will see **Edit** at the top.

![Click ddit delete Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/EditDeleteRunbook.png)

This will bring up a blank page where you can add in Powershell commands.

![Edit Powershell Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/editPowershell.png)

In the highlighted section where powershell commands go, you will need to add this into there and publish the Runbook.

```powershell
Param
(
[Parameter (Mandatory= $true)]
[String] $clusterName
)

### Authenticate to Azure
$Conn = Get-AutomationConnection -Name 'AzureRunAsConnection'
Add-AzureRMAccount -ServicePrincipal -Tenant $Conn.TenantID -ApplicationId $Conn.ApplicationID -CertificateThumbprint $Conn.CertificateThumbprint

Remove-AzureRmHDInsightCluster -ClusterName $clusterName
```
It should be located here.  Once it has been placed inside the Edit box you can publish the Runbook.

![Edit Powershell Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/AddPowershellToRunbook.png)

Once your Delete Runbook is publish we need to add a **Schedule** to control time to live for the cluster using the Delete Runbook.

![Go to Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/addSchedule.png)

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/clickSchedule.png)

Once you click on **Add a schedule**, it will show two options.

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/changeSchedule.png)

Let's first pick the first option **Link a schedule to your runbook** then click on **Add a schedule**.

A side section will come up.  Here you will need to decide on when the Runbook will run.

Example:

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/configSchedule.png)

Once you have decided on the Schedule click on Create at the bottom of the section.

After this it will bring you back to the Schedule Runbook.  Here we will now click on **Configure parameters and run settings**.

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/parametersSchedule.png)

Put in your cluster name that will be created using the Python Runbook and click on **OK** at the bottom.

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/clusterParameters.png)

After this is completed, you will be brought back to the **Schedule Runbook**.  Click on Ok at the bottom.

You will be returned to the Delete Runbook and now you will see an added Schedule.

![Add Schedule Runbook](https://cssexamplesallee.blob.core.windows.net/markdownimages/finishSchedule.png)

>This will now delete your cluster everyday.  You will need to do this to create the cluster as well everyday.
Once all this is completed you have successfully created an Automated Runbook to create an ESP Spark cluster.  This can be simulated for your standard Subscription as well.
> There are a few changes as you will not need AADDS.  If you have any questions you can contact allee@microsoft.com

##Thanks for reading this HowTo

[Purpose]: #Purpose

[Steps]: #Steps

[Prerequisite]: #Prerequisite

[Applying the Python script to your Runbook.]: #Applying-the-Python-script-to-your-Runbook


