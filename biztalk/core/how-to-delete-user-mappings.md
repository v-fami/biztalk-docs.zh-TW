---
title: "如何刪除使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03f7c1fa75b6fe7bb4c78e18c97fccd1404f89c9
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-delete-user-mappings"></a>如何刪除使用者對應
使用下列命令可刪除在 XML 檔案中指定的一或多個使用者對應。 以下是 XML 檔案的範例。  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
```  
  
 若使用者並非應用程式使用者帳戶的成員或不存在 Active Directory 中，則應使用此命令從 SSO 資料庫移除使用者對應。  
  
 若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。 如需有關如何建立對應的詳細資訊，請參閱[如何建立使用者對應](../core/how-to-create-user-mappings.md)。  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>使用管理公用程式刪除使用者對應  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 **ssomanage – deletemappings *\<對應檔案名稱\>* * *，其中\<*對應檔案名稱*\>是包含的檔案名稱您想要刪除的使用者對應。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>使用管理公用程式刪除特定使用者對應  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 **ssomanage-deletemapping *\<網域\>*\\*\<username\> *  *\<應用程式名稱\>* * *，其中*\<網域\>*是 Windows 網域使用者帳戶，  *\<的使用者名稱\>*是 Windows 使用者名稱和\<*應用程式名稱*\>是您要移除使用者對應的特定應用程式。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式刪除使用者對應  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssoclient – deletemapping *\<應用程式名稱\>* * *，其中*\<應用程式名稱\>*是您想要移除的使用者對應的分支機構應用程式的名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)