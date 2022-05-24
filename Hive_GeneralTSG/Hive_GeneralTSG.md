# General Hive Content

Author: Alexander Lee

## Purpose
> The purpose of this TSG is to have a central location of the most common Hive issues and HowTos.  This Content page will also provide helpful tips and tricks for Hive.

## Content
[**Purpose**][Purpose]<br>
[**Hive logs**](#hive-logs)<br>
[**Hive Kusto query**](#general-hive-kusto-query)<br>
[**How to start your troubleshooting**](#how-to-start-your-troubleshooting)<br>
[**Most common Hive issues**](#most-common-hive-issues)

## Log location

### Hive Logs
[**Back to Content**](#content)
>/var/log/hive

> These log files contains information for why a query may have failed.  There are generally three different logs to help troubleshoot Hive issues.
1. hiveserver2.log (Location /var/log/hive)
2. hivemetastore.log (Location /var/log/hive)
3. Hive application logs (These are generated when running heavy queries like create table statements)
4. Tez logs


**What are Hive server 2 logs:**</br>
Hive server 2 logs contain workflow of Hive servie.  These logs will help to see what may have happened when trying to run a job.  It will also have connection issues when trying to start or why hive service is stopping.

**What are Hive Metastore Logs**</br>
Hive Metastore logs contain workflow of the hive metastore.  These logs show issues if customer's queries require to hit the metastore.

For example:</br>
>If customer is interacting with external tables.

**Hive application Logs**</br>
Hive application logs are created when a customer is running heavy queries.  These logs will show why the job may have failed.

Example of heavy job:</br>
>When customer create a table this will create an application log in yarn.

To collect yarn aggregated logs you can run: 
>```yarn logs -applicationId application_1652101811388_0002 >> application_1652101811388_0002.log```

To get container logs for an application

```
```

**Tez**</br>
Tez logs will help with also reviewing why a hive job fails.  The location for Tez logs would be in Ambari.

![Get to Tez View](https://cssexamplesallee.blob.core.windows.net/markdownimages/Hive_GeneralTSG/TezViewLogs.png)

**Summary**
For hive jobs our clusters now uses Tez.  There are times when reviewing Tez logs will be helpful.  

## General Hive Kusto query
[**Back to Content**](#content)<br>

The below kusto queries should be used to get started on troubleshooting Hive related issues.
>NOTE!</br>
>Always check the cluster health for any issue first using CAmbariAlerts.  This will give you an idea of what is happening to the cluster.
```
cluster("HDInsight").database("HDInsight").CAmbariAlert
| where ClusterDnsName contains "clusterName"
| where PreciseTimeStamp between(dateTime(insert_time)..dateTime(insert_time))
| order by PreciseTimeStamp desc 
```

To get some hive server 2 logs you can use this kusto query.  

>NOTE!</br>
>It is recommended to collect the logs directly from the cluster for more details on issues with hive.

```
cluster("HDInsight").database("HDInsight").CFilteredHdpSvcLog
| where ClusterDnsName contains "cluster_name"
| where PreciseTimeStamp between (datetime(Insert_time)..datetime(Insert_time))
| where ComponentName contains "hiveserver2"
| order by PreciseTimeStamp desc 
```

To get some Hive metastore logs you can use this kusto query:
```
cluster("HDInsight").database("HDInsight").CFilteredHdpSvcLog
| where ClusterDnsName contains "cluster_name"
| where PreciseTimeStamp between (datetime(Insert_time)..datetime(Insert_time))
| where ComponentName contains "metastore"
| order by PreciseTimeStamp desc 
```

To get some information Hive application you can use try this kusto query:

```
let QueryId = "applicationId";
let clusterName = "clusterName";
cluster("HDInsight").database("HDInsight").CFilteredHdpSvcLog
| where ClusterDnsName  contains clusterName
| where Message contains QueryId
| where PreciseTimeStamp between (datetime(Insert_time)..datetime(Insert_time))
| order by PreciseTimeStamp desc
```

## How to start your troubleshooting
[**Back to Content**](#content)
1. To start troubleshooting for Hive issues, I recommend to first use *CAmbariAlerts* to get the current health of the cluster.  Once you get an understanding of the health of the cluster, open ASC to check if there are any useful insights.  I recommend to look at the insights but make sure you cross check with the issue the customer is say that is happening.

2. Next is to make sure you check ASC for the cluster property so you have an understanding of how the cluster is built.

3. Finally, in your FQR make sure that you introduce yourself, let the customer know what team you are from and paraphrase your understanding of the issue.

4. In all FQR, I recommend to always provide steps for customer's to do.  **This could be collecting needed logs, queries or providing a possible solution.**  **ALWAYS** make sure you provide steps.  This shows to the customer that you are engaged and have an understanding of the issue.

>IMPORTANT!</br>
>Always make sure that you meet IR as this is a key component for the team.


## Most common Hive issues
[**Back to Content**](#content)<br>

>Below are some common Hive issues to help get started.

Needs an updated TSG [Hive Metastore DTU, CPU, and Memory]()

[General Hive Metastore information](https://msdata.visualstudio.com/HDInsight/_wiki/wikis/HDInsight-Transition-Wiki/27731/Metastores)

[Hive Server Connection Refuse](https://msdata.visualstudio.com/HDInsight/_wiki/wikis/HDInsight.wiki/8889/Hive_Server_Connection_Refused)

[Unable to access Hive View](https://msdata.visualstudio.com/HDInsight/_wiki/wikis/HDInsight.wiki/1720/Hive_View_inaccessible_with_Connection_timed_error)

If HDFS goes down this can potentially affect Hive.  Please see below TSG:</br>
[AAD-DS failover cause Kerberos login failure for Hadoop services](https://supportability.visualstudio.com/AzureHDinsight/_wiki/wikis/AzureHDinsight/568374/AAD-DS-failover-cause-Kerberos-login-failure-for-Hadoop-services)





[Purpose]: #Purpose
[Hive Logs]: #Hive_Logs
[General Hive Kusto query]: #General-Hive-Kusto-query
[How to start your troubleshooting]: #How_to_start_your_troubleshooting
[Most common Hive issues]: #Most_common_Hive_issues