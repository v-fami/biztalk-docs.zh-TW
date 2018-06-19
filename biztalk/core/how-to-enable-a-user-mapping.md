---
title: 如何啟用使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enabling, user maps [SSO]
- maps [SSO], enabling
- managing [SSO maps], enabling
ms.assetid: 0f6448c9-944e-45f6-9436-87a4f3743498
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfd87d300314616fe05a033360d84f5d2eb8b8cd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970828"
---
# <a name="how-to-enable-a-user-mapping"></a>如何啟用使用者對應
您必須先啟用使用者對應，才可以使用「單一登入」系統中的對應。  
  
 當您啟用使用者對應時，將會顯示為 (E) **\<網域\>\\< 使用者名稱\>** 時列出使用者對應。  
  
 請注意，若已使用 -setcredentials 命令來設定認證，對應便已啟用。  
  
### <a name="to-enable-a-user-mapping-using-the-administration-utility"></a>使用管理公用程式啟用使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage-enablemapping\<網域\>\\< 使用者名稱\>\<應用程式名稱\>**，其中 **\<網域\>** 是 Windows 網域使用者帳戶，  **\<username\>** 是 Windows 使用者名稱，您要啟用認證和**\<應用程式名稱\>** 是您想要移除的使用者對應，然後按 ENTER 分支機構應用程式的名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-enable-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式啟用使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – enablemapping\<應用程式名稱\>**，其中**\<應用程式名稱\>** 是您想要的分支機構應用程式的名稱若要移除的使用者對應。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [如何建立使用者對應](../core/how-to-create-user-mappings.md)   
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)