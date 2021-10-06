# Sample HDInsight TSG

### Contents
<hr style="border-bottom: 1px dashed #686868; width: 50%; margin-left: 0; margin-bottom: 15px" />

### [What Is Impacted](#what-is-impacted-1)
### [Symptoms](#symptoms-1)
### [Troubleshooting](#troubleshooting-1)
### [Replication](#replication-1)
### [Cause](#cause-1)
### [Mitigation](#mitigation-1)
### [Resolution](#resolution-1)

<hr style="border-bottom: 1px dashed #686868; width: 50%; margin-left: 0; margin-top: 15px" />
<br>
<br>

# What Is Impacted

|HDInsight Version|Cluster Type|Component Version|
|:---------------:|:----------:|:---------------:|
|3.6|All|All|
|4.0|All|All|

<br>
<br>

# Symptoms

## Symptom 1

<br>

> Information on symptom 1

<br>

## Symptom 2

<br>

> Information on symptom 2

...

<br>
<br>

# Troubleshooting

<br>

## Kusto Queries

<br>

> Any kusto queries to run for finding helpful information or making confirmations

```
let ClusterName = "";
LogEntry
| where ClusterDnsName =~ ClsuterName
| where PreciseTimeStamp >= ago(1d)
| order by PreciseTimeStamp desc nulls last
```

<br>

## Helpful Logs

<br>

> Any logs to collect, including full file paths, and specific information to look for

<br>

### Log 1

<br>

**File Path: &nbsp; &nbsp;/var/log/...**

Any specific information to look for and examples of what will be in the file. For example:

``` 
Exception in thread "main" java.lang.RuntimeException: A test exception
  at com.stackify.stacktrace.StackTraceExample.methodB(StackTraceExample.java:13)
  at com.stackify.stacktrace.StackTraceExample.methodA(StackTraceExample.java:9)
  at com.stackify.stacktrace.StackTraceExample.main(StackTraceExample.java:5)
```

<br>
<br>

# Replication

> Any steps to reproduce the issue which a support engineer can follow using their internal subscription. Provide as much clarity as possible such as infographics and screenshots of each step.

<br>
<br>

# Cause

> Provide a root cause if known

<br>
<br>

# Mitigation

> Mitigation steps if known

<br>
<br>

# Resolution

> The full resolution for the issue if different from mitigation steps and known

<br>
<br>
<br>

<div id='csswikifeedback-start'></div>
<br/>

**How good have you found this content?**

<div>
<span>
<a href='https://csswikifeedback.azurewebsites.net/feedback/smile?wiki=AzureHDinsight&pageId=402593&pageTitle=SampleTsg&product=HDInsight' target='_blank'>
<img alt='Smile' src='https://sqldbwikifeedback.blob.core.windows.net/assets/smile.png'>
</a>
</span>

<span>
<a href='https://csswikifeedback.azurewebsites.net/feedback/frown?wiki=AzureHDinsight&pageId=402593&pageTitle=SampleTsg&product=HDInsight' target='_blank'>
<img alt='Sad' src='https://sqldbwikifeedback.blob.core.windows.net/assets/sad.png'>
</a>
</span>
</div>
<div id='csswikifeedback-end'></div>

