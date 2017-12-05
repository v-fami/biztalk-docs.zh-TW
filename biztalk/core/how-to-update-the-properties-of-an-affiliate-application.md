---
title: "如何更新分支機構應用程式的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], updating properties
- applications [SSO], properties
ms.assetid: b06eefdd-a5ca-4a32-93d7-72246e31a2e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ef4a2fb99d423f7c7ccb08cec58c3c49928e1ed
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-the-properties-of-an-affiliate-application"></a>如何更新分支機構應用程式的內容
您可以使用 MMC 嵌入式管理單元或此命令來更新一或多個應用程式屬性，如 XML 檔案所指定。 您必須是分支機構系統管理員，才能執行此工作。 下列是一個範例 XML 檔案，其中列出您可以更新的欄位。  
  
```  
<SSO>  
<application name="SSOApplication">  
<description>An SSO Application</description>  
<contact>someone@companyname.com</contact>  
<appUserAccount>DomainName\AppUserGroup</appUserAccount>  
<appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
<flags allowTickets="no" validateTickets="yes"  timeoutTickets="yes" enableApp="no" />  
</application>  
</SSO>  
  
```  
  
 建立分支機構應用程式後，無法修改以下屬性：  
  
-   分支機構應用程式的名稱  
  
-   與分支機構應用程式關聯的欄位  
  
-   分支機構應用程式類型 (主控件群組、個別或組態存放區)  
  
-   與分支機構系統管理員群組相同的管理帳戶。 (指定這個旗標會永遠使用分支機構系統管理員群組做為此分支機構應用程式的系統管理員帳戶)  
  
> [!IMPORTANT]
>  您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。 不過，您只可以在單一電腦的情況下使用這個旗標。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員、SSO 分支機構系統管理員或應用程式系統管理員，才能執行這項工作。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員才能修改票證旗標 (validateTickets 和 timeoutTickets)。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能修改應用程式管理帳戶。  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元更新分支機構應用程式的屬性  
  
1.  上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下**更新**。  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-command-line"></a>使用命令列更新分支機構應用程式的屬性  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – updateapps\<應用程式檔案名稱\>**，其中應用程式檔案名稱是 XML 檔案。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)