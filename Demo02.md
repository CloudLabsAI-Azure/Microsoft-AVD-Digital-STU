# **Demo 2: Accessing Azure Portal from DSVM**


## **Task 1: Access the Azure Portal from DSVM**

>**More Information:**
>In this task, We will first access the Azure Management Portal from the DSVM. Using the Azure Active Directory Conditional access policy, the access to the Azure portal is only allowed from the DSVM.
>Later we will try to access the same Azure Portal from the AVD Session Host and find that it is being blocked.

1. Connect to the Desktop of the DSVM if not already connected.

2. Launch Edge browser and navigate to Azure Portal using following URL. You can either use the Shortcut on the desktop or the Edge icon on the taskbar:     
```
https://portal.azure.com
```
![ws name.](media/img83.png)				

3. Sign in into the portal using the below credentials.
- Username:
```
odl_user_837245@azurehol1182.onmicrosoft.com
```
![ws name.](media/img84.png)	

- Password: **<inject key="Demo Admin Password" />**

![ws name.](media/img85.png)

4. Select **Skip for now (14 days until this is required)**.

![ws name.](media/img86.png)

5. You will now be logged into the Azure Management Portal.

>**More Information:**
>This validates that we can access the Azure Portal from the DSVM.
>We will return to the Azure Management Portal later for reviewing the Azure Deployments.
> Next, we will try to access the same Azure Portal from the AVD Session Host.

## **Task 2: Access the Azure Portal from AVD Session Host**