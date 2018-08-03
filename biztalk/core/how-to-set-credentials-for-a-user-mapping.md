---
title: 如何設定認證使用者對應的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], credentials
- managing [SSO maps], configuring credentials
ms.assetid: 75b29114-56b6-4db0-8666-61cf6c675401
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4853499dbfd85cd5114212e37f4d22770d64a22
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972140"
---
# <a name="how-to-set-credentials-for-a-user-mapping"></a>如何設定使用者對應的認證
請使用此命令，為使用者設定認證以存取特定應用程式。  
  
 當您輸入此命令時，不會顯示密碼。  
  
 若使用者對應已經存在，此命令會為現有的對應設定認證。 若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。  
  
### <a name="to-set-credentials-for-a-user-mapping"></a>設定使用者對應的認證  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – setcredentials\<網域\>\\< 使用者名稱\> \<applicationname\>**，其中 **\<網域\>** 是 Windows 網域使用者帳戶， **\<username\>** 是 Windows 使用者名稱和**\<應用程式名稱\>** 是特定的應用程式，您想要設定的認證。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  當 SSO 系統提示您輸入使用者認證時，請輸入此應用程式的使用者密碼。  
  
5.  若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。  
  
### <a name="to-set-credentials-for-a-user-mapping-from-the-client-utility"></a>從用戶端公用程式設定使用者對應的認證  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient-setcredentials\<應用程式名稱\>**，其中**\<應用程式名稱\>** 的分支機構應用程式名稱您要移除的使用者對應。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [如何建立使用者對應](../core/how-to-create-user-mappings.md)   
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)