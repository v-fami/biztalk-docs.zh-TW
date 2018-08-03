---
title: 如何停用使用者對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disabling, maps
- managing [SSO maps], disabling
- maps [SSO], disabling
ms.assetid: 9b6eaff2-674b-49f7-8d5c-3e040a7dc7f8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e49f524337fffde9261af4aa2cd64c75e307ccb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972631"
---
# <a name="how-to-disable-a-user-mapping"></a>如何停用使用者對應
當您要關閉與特定對應關聯的所有作業時，可以停用使用者對應。 您必須先停用使用者對應，才能進行移除。  
  
 當您停用使用者對應時，將會顯示為 (D) *\<網域\>\\< 使用者名稱\>* 當您列出使用者對應。  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a>使用管理公用程式停用使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別**ssomanage-disablemapping *\<網域\>*\\*\<username\> \<應用程式名稱\>**  <em>，其中 *\<網域\></em>是 Windows 網域使用者帳戶，以及*\<username\>* 是您要停用認證的 Windows 使用者名稱和*\<應用程式名稱\>* 是您想要移除的使用者對應的分支機構應用程式的名稱。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a>使用用戶端公用程式停用使用者對應  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssoclient-disablemapping *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要移除的分支機構應用程式的名稱使用者對應。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 對應](../core/sso-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)   
 [管理使用者對應](../core/managing-user-mappings.md)