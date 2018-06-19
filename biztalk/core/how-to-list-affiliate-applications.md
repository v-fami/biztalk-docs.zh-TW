---
title: 如何列出分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], listing applications
- applications [SSO], listing applications
ms.assetid: b51ff597-824e-4488-a47f-3a9b3d4437c6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6c4d4e4118bfe5f5cab7a9c44e770dd12656c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974148"
---
# <a name="how-to-list-affiliate-applications"></a>如何列出分支機構應用程式
使用這個命令可列出所有分支機構應用程式。 若使用者是「應用程式系統管理員」帳戶的成員，這個命令將只顯示使用者為系統管理員的應用程式。  
  
### <a name="to-list-affiliate-applications-using-the-administration-utility"></a>使用管理公用程式列出分支機構應用程式  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage-listapps [all]** 其中**所有**這也會顯示應用程式使用的組態存放區功能是選擇性參數。 如果應用程式系統管理員身分執行此命令的使用者，它只會列出其自己是系統管理員的應用程式。 若執行這個命令的使用者是「分支機構系統管理員」或「SSO 系統管理員」，將會列出所有分支機構應用程式。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-list-affiliate-applications-using-the-client-utility"></a>使用用戶端公用程式列出分支機構應用程式  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – listapps**列出分支機構應用程式。 這只會列出執行此工作的使用者為其成員的分支機構應用程式，也就是說，他們必須屬於該分支機構應用程式的應用程式使用者群組帳戶。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何建立分支機構應用程式](../core/how-to-create-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)