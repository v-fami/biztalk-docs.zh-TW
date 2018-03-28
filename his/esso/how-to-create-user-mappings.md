---
title: 如何建立使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb91879c-73f4-4e9e-9e5b-534f48cd5584
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 89fd7ab2ca83d23a37944447997becd2d3f008c2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-user-mappings"></a>如何建立使用者對應
使用**createmappings**建立一或多個使用者對應，XML 檔案中所指定的命令。 以下是 XML 檔案的範例。  
  
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
  
 如果使用者帳戶已變更，您必須使用此命令為新的使用者帳戶建立對應。 您也必須移除舊的使用者對應。 如需移除對應的詳細資訊，請參閱[如何刪除使用者對應](../esso/how-to-delete-user-mappings.md)。  
  
 建立使用者對應之後，您必須啟用它，才能使用此對應單一登入 (SSO) 系統中。 如需詳細資訊，請參閱[如何啟用使用者對應](../esso/how-to-enable-a-user-mapping.md)。  
  
> [!IMPORTANT]
>  只有網域群組支援使用者對應。  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a>使用管理公用程式建立使用者對應  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –createmappings <mappings file name>`，其中*\<對應檔案名稱 >*是包含您想要建立的使用者對應的檔案名稱。  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a>使用用戶端公用程式建立使用者對應  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssoclient –setcredentials <application name >`，其中*\<應用程式名稱 >*是使用者想要建立對應的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../esso/sso-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)