---
title: "如何列出使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO maps], listing maps
- maps [SSO], listing maps
ms.assetid: f9b73785-3a59-45c8-9e88-d2d16b5a46aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6041b40c2b6a3fa468462478754079d41881bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-user-mappings"></a>如何列出使用者對應
使用此命令，以列出指定使用者的全部現有對應。  
  
 您必須是 SSO 系統管理員、應用程式系統管理員、SSO 分支機構系統管理員或使用者，才能執行此工作。  
  
 已啟用的使用者對應則會以 (E) \<*網域*>\\*\<使用者名稱 >*，而停用使用者對應會顯示為 (D) \<*網域*>\\*\<使用者名稱 >*。  
  
### <a name="to-list-user-mappings-using-the-administration-utility"></a>使用管理公用程式列出使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  執行下列其中之一：  
  
    -   型別**ssomanage – listmappings *\<網域 >\\< 使用者名稱\>*** 列出特定的使用者擁有在所屬分支機構應用程式中的所有對應到何處*\<網域 >*是 Microsoft Windows 網域使用者帳戶和*\<使用者名稱 >*是您要列出的 Windows 使用者名稱使用者對應。 如果使用者是「分支機構系統管理員」或「SSO 系統管理員」，這個命令便會列出該使用者於所有分支機構應用程式中的所有對應。  
  
         或  
  
    -   型別**ssomanage – listmappings *\<應用程式名稱 >*** 列出給定應用程式的使用者對應。  
  
         或  
  
    -   如果您是應用程式管理員，請輸入**ssomanage – listmappings *\<網域 >\\< 使用者名稱\>* *\<應用程式名稱 >*** 列出的所有對應特定的使用者擁有您身為系統管理員的分支機構應用程式中。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-list-user-mappings-using-the-client-utility"></a>使用用戶端公用程式列出使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – listmappings**列出您所擁有的所有對應。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立使用者對應](../core/how-to-create-user-mappings.md)   
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)