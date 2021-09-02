# **Demo 12: Azure Sentinel**

## What is Azure Sentinel?

Microsoft Azure Sentinel is a scalable, cloud-native, security information event management (SIEM) and security orchestration automated response (SOAR) solution. Azure Sentinel delivers intelligent security analytics and threat intelligence across the enterprise, providing a single solution for alert detection, threat visibility, proactive hunting, and threat response.

Azure Sentinel is your birds-eye view across the enterprise alleviating the stress of increasingly sophisticated attacks, increasing volumes of alerts, and long resolution time frames.

- **Collect data at cloud scale** across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds. 

- **Detect previously undetected threats**, and minimize false positives using Microsoft's analytics and unparalleled threat intelligence. 

- **Investigate threats with artificial intelligence**, and hunt for suspicious activities at scale, tapping into years of cyber security work at Microsoft. 

- **Respond to incidents rapidly** with built-in orchestration and automation of common tasks.

![ws name.](media/sentinel1.png)

To on-board Azure Sentinel, you first need to enable Azure Sentinel, and then connect your data sources. Azure Sentinel comes with a number of connectors for Microsoft solutions, available out of the box and providing real-time integration, including Microsoft 365 Defender (formerly Microsoft Threat Protection) solutions, Microsoft 365 sources (including Office 365), Azure AD, Microsoft Defender for Identity (formerly Azure ATP), Microsoft Cloud App Security, Azure Defender alerts from Azure Security Center, and more.

## Global prerequisites

- Active Azure Subscription, if you don't have one, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

- Log Analytics workspace. Learn how to [create a Log Analytics workspace](https://docs.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace). For more information about Log Analytics workspaces, see [Designing your Azure Monitor Logs deployment](https://docs.microsoft.com/en-us/azure/azure-monitor/logs/design-logs-deployment).

- To enable Azure Sentinel, you need contributor permissions to the subscription in which the Azure Sentinel workspace resides.

- To use Azure Sentinel, you need either contributor or reader permissions on the resource group that the workspace belongs to.

- Additional permissions may be needed to connect specific data sources.

- Azure Sentinel is a paid service. For pricing information see [About Azure Sentinel](https://go.microsoft.com/fwlink/?linkid=2104058).

## **Task 1: Demo and Walkthrough of Azure Sentinel**

1. Sign in to the Azure portal and search for and select Azure Sentinel.

![ws name.](media/sentinel2.png)

2. Click on **log-analytics-avd-prod-EUS1-001**

![ws name.](media/sentinel3.png)

3. Click on **Data Connectors** and highlight the Connected Data connectors

![ws name.](media/sentinel4.png)

4. Click on **Azure Active Directory** and then click on **Open connector page**

![ws name.](media/sentinel5.png)

5. On this page you can highlight the **Sign-In** Logs checkbox which indicates that the AAD Sign Logs are now being sent over to Azure Sentinel.

![ws name.](media/sentinel6.png)

6. Click on **Next steps**; On this page you can highlight the **Relevant analytics templates** and showcase the in-built Rules that you can create for various types of events.

![ws name.](media/sentinel7.png)

7. Click on **Analytics**; On this page you can highlight the **Active Rules** and showcase the in-built Rules.

![ws name.](media/sentinel8.png)

8. Click on **Incidents**; On this page you can highlight the **Open, New and Active Incidents**. These are Test incidents generated as a result of a simulated malicious command line.

![ws name.](media/sentinel9.png)

9. Select any of the Incidents; Click on **Actions**, and then click on **Investigate**.

![ws name.](media/sentinel10.png)

10. On this page you can highlight the level of details that is shown, like how the process was run, what other child processes were created, who exceuted the process, etc.

![ws name.](media/sentinel11.png)

## **Task 2: Attack Simulation**

1. Using AVD Client on your JumpVM, Login to any of the Session Desktops with any of the User Accounts.

2. Open CMD as non-Admin, and execute the below Commandline.

```
powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-WDATP-test\\invoice.exe');Start-Process 'C:\\test-WDATP-test\\invoice.exe'
```

This should take couple of minutes to report to Defender and then eventually being captured by Azure Sentinel. In sometime you should be able to see a new Incident getting created for the above malicious command execution.

![ws name.](media/sentinel12.png)

![ws name.](media/sentinel13.png)