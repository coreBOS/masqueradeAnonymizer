# Initial Analysis of tables

The actual project deviated a little from this layout, but it is mostly correct

What is **pending** is to create a special provider for the Email Details table. Email Details needs a provider to return a JSON array of emails for to, cc and bcc email column

## tables to be emptied directly

- cb_messagequeue
- cb_settings > must keep only the rows: cbmqtm_classfile, cbmqtm_classname, coreBOSMessageModuleWithS
- vtiger_cbcredentials
- vtiger_emailtemplates
- vtiger_mail_accounts
- vtiger_notificationdrivers (new columns)
- vtiger_portalinfo
- vtiger_smsnotifier_server, vtiger_smsnotifier_status
- vtiger_systems
- vtiger_webforms
- vtiger_ws_userauthtoken

## tables to be anonymized

- vtiger_account, vtiger_accountbillads, vtiger_accountshipads
- vtiger_activity
- vtiger_assets
- vtiger_asteriskincomingcalls, vtiger_asteriskincomingevents
- vtiger_campaign
- vtiger_cbcompany
- vtiger_cbsurvey*
- vtiger_cbtandc
- vtiger_cobropago
- vtiger_contactaddress, vtiger_contactdetails, vtiger_contactsubdetails
- vtiger_crmentity.description
- vtiger_emaildetails
- vtiger_faq
- vtiger_groups
- vtiger_inventorydetails
- vtiger_invoice, vtiger_invoicebillads, vtiger_invoiceshipads
- vtiger_leadaddress, vtiger_leaddetails, vtiger_leadsubdetails.website
- vtiger_mailmanager_mailrecord
- vtiger_mailscanner
- vtiger_modcomments
- vtiger_modtracker_detail
- vtiger_msgtemplate (subject, template, templateonlytext)
- vtiger_notes
- vtiger_potential
- vtiger_products, vtiger_service
- vtiger_project
- vtiger_projecttask
- vtiger_projectmilestone.projectmilestonename
- vtiger_purchaseorder, vtiger_pobillads, vtiger_poshipads
- vtiger_quotes, vtiger_quotesbillads, vtiger_quotesshipads
- vtiger_salesorder, vtiger_sobillads, vtiger_soshipads
- vtiger_servicecontracts
- vtiger_troubletickets, vtiger_ticketcomments
- vtiger_users
- vtiger_vendor

## tables with special treatment

### vtiger_globalvariable

The list of defined/oficial global variables can be found [in this file](
https://github.com/tsolucio/corebos/blob/master/build/changeSets/DefineGlobalVariables.php#L17).

- Any global variable that is not in this list must be deleted
- These global variables must be deleted if they exist
  - Debug_Send_AdminLoginIPAuth_Error
  - Debug_Send_UserLoginIPAuth_Error
  - Debug_Email_Send_To_Inbucket
  - Application_AdminLoginIPs
  - Application_UserLoginIPs
  - Application_DetailView_PageHeader_Message
  - Application_Announcement
  - Application_Customer_Portal_URL
  - Application_Customer_Portal_BeingUsed
  - Application_Help_URL
  - Application_UI_Name
  - Application_UI_NameHTML
  - Application_UI_CompanyName
  - Application_UI_URL
  - Application_UI_CoverImage
  - Application_FirstTimeLogin_Template
  - Application_Unique_Identifier
  - Application_CSRF_Valid_IP
  - Calendar_Notification_Sound
  - CronTasks_cronWatcher_mailto
  - Webservice_CORS_Enabled_Domains
  - User_2FAAuthentication
  - User_2FAAuthentication_SendMethod
  - User_MandatoryAuthenticationSQL
  - PBX_Get_Line_Prefix
  - PBX_Unknown_CallerID
  - PBX_callerNumberField
  - PBX_callerNumberSeparator
  - Workflow_Send_Email_ToCCBCC
  - Workflow_GeoDistance_Country_Default
  - Workflow_GeoDistance_ServerIP
  - Workflow_GeoDistance_Email
  - Workflow_GeoDistance_Nominatim_Server
  - HelpDesk_Support_EMail
  - HelpDesk_Support_Name
  - HelpDesk_Support_Reply_EMail
  - HelpDesk_Notify_Owner_EMail
  - Zero_Bounce_API_KEY
  - ip_elastic_server
  - ip_elastic_indexprefix
  - esusername
  - espassword

### vtiger_cbmap

The list of defined/oficial business maps can be found [in this file](
https://github.com/tsolucio/corebos/blob/master/build/changeSets/cbMapAddMapTypes.php#L27).

- Any business map that is not in this list must be deleted
- These types of business maps must be deleted if they exist
  - DecisionTable
  - Webservice Mapping
  - InformationMap

### com_vtiger_workflows*

For the moment we are not going to modify these tables. Let's do a first phase of the project and see how it goes. Then we will decide if these tables need to be changed.

### custom field tables

- All custom fields must be anonymzed as we do not know what they could contain, but we decide to leave this as a specific task for each install to do on their own as there is no easy way to get the meta-information without programming.
