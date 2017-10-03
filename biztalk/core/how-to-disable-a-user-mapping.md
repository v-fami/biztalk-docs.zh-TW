---
title: "如何停用使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, maps
- managing [SSO maps], disabling
- maps [SSO], disabling
ms.assetid: 9b6eaff2-674b-49f7-8d5c-3e040a7dc7f8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 417a28dd117a51d0bb1d45238f0efc96417c391a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-a-user-mapping"></a>如何停用使用者對應
當您要關閉與特定對應關聯的所有作業時，可以停用使用者對應。 您必須先停用使用者對應，才能進行移除。  
  
 當您停用使用者對應時，將會顯示為 (D) *\<網域 >\\< 使用者名稱\>*時列出使用者對應。  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a>使用管理公用程式停用使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 **ssomanage-disablemapping *\<網域 >*\\*\<使用者名稱 >\<應用程式名稱 >***，其中*\<網域 >*是 Windows 網域使用者帳戶和*\<使用者名稱 >*是您想要停用的 Windows 使用者名稱認證，和*\<應用程式名稱 >*是您想要移除的使用者對應的分支機構應用程式的名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式停用使用者對應  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoclient – disablemapping *\<應用程式名稱 >***，其中*\<應用程式名稱 >*分支機構的名稱您想要移除的使用者對應的應用程式。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)