---
title: 如何停用使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c745dd-4d39-46e5-88bf-b803ae2e0a1b
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 93694ed8a3238be51b255bcad79122169461d885
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250970"
---
# <a name="how-to-disable-a-user-mapping"></a>如何停用使用者對應
當您要關閉與特定對應關聯的所有作業時，可以停用使用者對應。 您必須先停用使用者對應，才能進行移除。  
  
 當您停用使用者對應時，將會顯示為 (D) *\<網域 >\\< 使用者名稱\>* 時列出使用者對應。  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a>使用管理公用程式停用使用者對應  
  
1.  按一下**啟動**，按一下 **執行**，型別`cmd`，然後按下**ENTER**。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –disablemapping <domain>\<username><application name>`，其中*\<網域 >* 是 Windows 網域使用者帳戶， *\<使用者名稱 >* 是您想要停用的 Windows 使用者名稱認證，和*\<應用程式名稱 >* 是您要移除使用者對應的分支機構應用程式的名稱。  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式停用使用者對應  
  
1.  按一下**啟動**，按一下 **執行**，型別`cmd`，然後按下**ENTER**。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssoclient –disablemapping <application name>`，其中*\<應用程式名稱 >* 是您要移除使用者對應的分支機構應用程式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../esso/sso-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)