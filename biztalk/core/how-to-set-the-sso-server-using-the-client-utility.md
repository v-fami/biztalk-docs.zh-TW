---
title: "如何設定使用用戶端公用程式的 SSO 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d917114d21ceed37eb68ee4bb9503aac97735ffa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a>如何設定 SSO 伺服器使用用戶端公用程式
每次使用 ssoclient 時，您必須先將使用者指向包含其組態資訊的正確「單一登入」伺服器。  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a>使用用戶端公用程式設定使用者的 SSO 伺服器  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – 伺服器*\<單一登入伺服器 >***，其中\<*單一登入伺服器 >*是 「 單一登入名稱伺服器使用者想要連接到。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)