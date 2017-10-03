---
title: "如何使用用戶端公用程式之分支機構應用程式設定認證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], configuring credentials
- SSOClient [SSO], configuring credentials
- applications [SSO], credentials
ms.assetid: 454b6257-3538-40be-840c-00172a2c1dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31ba167bc35d01907166bb6610720e03be654c4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a>如何使用用戶端公用程式之分支機構應用程式設定認證
使用此命令設定使用者的認證，讓使用者能夠存取特定應用程式。 此命令也會自動啟用對應。  
  
 當您輸入此命令時，不會顯示密碼。  
  
 若使用者對應已經存在，此命令會為現有對應設定認證。 若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。  
  
### <a name="to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a>使用用戶端公用程式設定分支機構應用程式的認證  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – setcredentials\<應用程式名稱 >**，其中**\<應用程式名稱 >**是特定的應用程式，您想要設定的認證。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  提示輸入使用者認證時，請輸入此應用程式的使用者密碼。  
  
5.  若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)