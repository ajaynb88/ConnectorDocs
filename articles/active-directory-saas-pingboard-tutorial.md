---

title: 'Tutorial: Configuring Pingboard for automatic user provisioning with Azure Active Directory | Microsoft Docs'
description: Learn how to configure Azure Active Directory to automatically provision and de-provision user accounts to Pingboard.
services: active-directory
documentationcenter: ''
author: asmalser-msft
writer: asmalser-msft
manager: sakula

ms.assetid: 0b38ee73-168b-42cb-bd8b-9c5e5126d648
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/19/2017
ms.author: asmalser-msft
ms.reviewer: asmalser

---

# Tutorial: Configuring Pingboard for Automatic User Provisioning

The objective of this tutorial is to show you the steps you need to perform in Pingboard and Azure AD to automatically provision and de-provision user accounts from Azure AD to Pingboard.

## Prerequisites

The scenario outlined in this tutorial assumes that you already have the following items:

*   An Azure Active Active directory tenant
*   A Pingboard tenant [Pro Account](https://pingboard.com/pricing) 
*   A user account in Pingboard with Admin permissions 

> [!NOTE] 
> The Azure AD provisioning integration relies on the Pingboard API(`https://your_domain.pingboard.com/scim/v2`) which is available to your account.

## Assigning users to Pingboard

Azure Active Directory uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users that have been "assigned" to an application in Azure AD will be synchronized. 

Before configuring and enabling the provisioning service, you will need to decide what users in Azure AD represent the users who need access to your Pingboard app. Once decided, you can assign these users to your Pingboard app by following the instructions here:

[Assign a user to an enterprise app](active-directory-coreapps-assign-user-azure-portal.md)

### Important tips for assigning users to Pingboard

*	It is recommended that a single Azure AD user be assigned to Pingboard to test the provisioning configuration. Additional users may be assigned later.

## Configuring user provisioning to Pingboard 

This section guides you through connecting your Azure AD to Pingboard user account provisioning API, and configuring the provisioning service to create, update and disable assigned user accounts in Pingboard based on user assignment in Azure AD.

> [!TIP]
> You may also choose to enabled SAML-based Single Sign-On for Pingboard, following the instructions provided in [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features compliment each other.

### To configure automatic user account provisioning to Pingboard in Azure AD:

1)	In the [Azure portal](https://portal.azure.com), browse to the **Azure Active Directory > Enterprise Apps > All applications**  section.

2) If you have already configured Pingboard for single sign-on, search for your instance of Pingboard using the search field. Otherwise, select **Add** and search for **Pingboard** in the application gallery. Select **Pingboard** from the search results, and add it to your list of applications.

3)	Select your instance of Pingboard, then select the **Provisioning** tab.

4)	Set the **Provisioning Mode** to **Automatic**.

    ![Pingboard Provisioning](media/active-directory-saas-pingboard-provisioning-tutorial/pingboardazureprovisioning.png)
    
5) Under the Admin Credentials section, perform the following steps:
   
    * In the **Tenant URL** textbox, enter `https://your_domain.pingboard.com/scim/v2`
    * Login to [Pingboard](https://pingboard.com/) using admin account.
    * Click on Add-Ons > Integrations > Azure Active Directory.
    * Click on Configure tab and select **Enable user provisioning from Azure**.
    * Copy the **OAuth Bearer Token** field and enter into **Secret Token** textbox.

6) In the Azure portal, click **Test Connection** to ensure Azure AD can connect to your Pingboard app. If the connection fails, ensure your Pingboard account has Admin permissions and try the **"Test Connection"** step again.

7) Enter the email address of a person or group who should receive provisioning error notifications in the **Notification Email** field, and check the checkbox below.

8) Click **Save**. 

9) Under the Mappings section, select **Synchronize Azure Active Directory Users to Pingboard**.

10) In the **Attribute Mappings** section, review the user attributes that will be synchronized from Azure AD to Pingboard. Note that the attributes selected as **Matching** properties will be used to match the user accounts in Pingboard for update operations. Select the **Save** button to commit any changes. See [Customizing User Provisioning Attribute Mappings](active-directory-saas-customizing-attribute-mappings.md) for more details

11) To enable the Azure AD provisioning service for Pingboard, change the **Provisioning Status** to **On** in the **Settings** section

12) Click **Save**. 

This starts the initial synchronization of any users assigned to Pingboard in the Users section. The initial takes longer to perform than subsequent syncs, which occur approximately every 20 minutes as long as the service is running. You can use the **Synchronization Details** section to monitor progress and follow links to provisioning activity reports, which describe all actions performed by the provisioning service on your Pingboard app.

For more information on how to read the Azure AD provisioning logs, see [Reporting on automatic user account provisioning](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-provisioning-reporting).

## Additional Resources

* [Managing user account provisioning for Enterprise Apps](active-directory/active-directory-enterprise-apps-manage-provisioning.md)
* [What is application access and single sign-on with Azure Active Directory?](active-directory/active-directory-appssoaccess-whatis.md)
* [Configure Single Sign-on](active-directory/active-directory-saas-pingboard-tutorial.md)
