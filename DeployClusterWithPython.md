# How to deploy a Spark cluster with ESP using python 3

Author: Alexander Lee

### Contents
[**Purpose**][Purpose]<br>
[**Steps**][Steps]<br>
[**Prerequisite**][Prerequisite]<br>
[**Applying Python Script**](#Applying-the-Python-script-to-your-Runbook)<br>
[**Running your Runbook**](Running-the-Runbook)<br>
[**Set Time to live for cluster**](Setting TTL for cluster)





### Purpose
> The purpose of this HowTo is to show CSS Support engineers how to deploy a cluster using python SDK.  In this HowTo we will be using Python 3 to create a spark cluster.  We will also be using the latest modules to deploy the cluster.

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

Once you have completed the Prerequisite you can now apply the Python script to your Runbook.

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

In this final section, you will Run your Runbook to deploy your cluster.

![Start and Status](https://cssexamplesallee.blob.core.windows.net/markdownimages/StartandStatus.png)

## Setting TTL for cluster


[Purpose]: #Purpose

[Steps]: #Steps

[Prerequisite]: #Prerequisite

[Applying the Python script to your Runbook.]: #Applying-the-Python-script-to-your-Runbook

[Running your Runbook]: #Running the Runbook

[Set Time to live for cluster]: #Setting TTL for cluster

