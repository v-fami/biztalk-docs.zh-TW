---
title: 如何刪除使用者對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 034f587d8c7d87f5fa6aa7e5e33ca4ef147d9f9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014383"
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
  
 若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。 如需建立對應的詳細資訊，請參閱[如何建立使用者對應](../core/how-to-create-user-mappings.md)。  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>使用管理公用程式刪除使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別<strong>ssomanage-deletemappings *\<對應檔名\></strong><em>，其中\<</em>對應檔案名稱*\>是包含您想要刪除之使用者對應的檔案名稱。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>使用管理公用程式刪除特定使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 **ssomanage-deletemapping *\<網域\>*\\*\<username\> *   *\<應用程式名稱\>**<em>，其中*\<網域\></em>是 Windows 網域使用者帳戶 *\<使用者名稱\>* 是 Windows 使用者名稱，以及\<* 應用程式名稱*\>是您要移除使用者對應的特定應用程式。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式刪除使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssoclient-deletemapping *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要移除的分支機構應用程式的名稱使用者對應。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)