---
title: 如何刪除使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: a9d0a31c3dbc9d5980f59d9f30d20ec15f603a38
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30251082"
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
  
 如果使用者不是應用程式使用者帳戶的成員，或不存在於 Active Directory，您應該使用此命令從認證資料庫中移除使用者對應。  
  
 若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。 如需有關如何建立對應的詳細資訊，請參閱[如何建立使用者對應](../esso/how-to-create-user-mappings.md)。  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>使用管理公用程式刪除使用者對應  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –deletemappings <mappings file name>`，其中\<*對應檔案名稱*> 是包含您想要刪除的使用者對應的檔案名稱。  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>使用管理公用程式刪除特定使用者對應  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –deletemapping <domain>\<username> <application name>`，其中*\<網域 >* 是 Windows 網域使用者帳戶， *\<使用者名稱 >* 是 Windows 使用者名稱和\< *應用程式名稱*> 是您要移除使用者對應的特定應用程式。  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式刪除使用者對應  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssoclient –deletemapping <application name>`，其中*\<應用程式名稱 >* 是您要移除使用者對應的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../esso/sso-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)