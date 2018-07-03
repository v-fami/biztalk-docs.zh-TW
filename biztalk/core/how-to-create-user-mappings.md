---
title: 如何建立使用者對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], creating
- managing [SSO maps], creating user maps
ms.assetid: c2e9f0db-920b-4d89-8e1e-5dc92805fd23
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f9b505288ea10e48eb0cf8607a870b5509425
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009887"
---
# <a name="how-to-create-user-mappings"></a>如何建立使用者對應
使用此命令可建立一或多個使用者對應，如 XML 檔案所指定。 以下是 XML 檔案的範例。  
  
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
  
 如果使用者帳戶已變更，您必須使用此命令為新的使用者帳戶建立對應。 您也必須移除舊的使用者對應。 如需有關移除對應的詳細資訊，請參閱 <<c0> [ 如何刪除使用者對應](../core/how-to-delete-user-mappings.md)。  
  
 建立使用者對應之後，您必須先啟用，才能在 SSO 系統中使用這個對應。 如需詳細資訊，請參閱 <<c0> [ 如何啟用使用者對應](../core/how-to-enable-a-user-mapping.md)。  
  
> [!IMPORTANT]
>  只有網域群組支援使用者對應。  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a>使用管理公用程式建立使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssomanage – createmappings *\<對應檔名\>**<em>，其中 *\<對應檔名\></em>是包含您想要的使用者對應的檔案名稱若要建立。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a>使用用戶端公用程式建立使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssoclient-setcredentials *\<應用程式名稱\> ** <em>，其中 *\<應用程式名稱\></em>是使用者想要的分支機構應用程式的名稱建立的對應。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)