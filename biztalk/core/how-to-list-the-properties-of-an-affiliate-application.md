---
title: 如何列出分支機構應用程式屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], listing properties
- managing [SSO applications], listing properties
ms.assetid: a120acd7-2f0b-4c72-8a8a-f8e500a773c8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5920263006a9188da83f82dcf65dad8fb8faada
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002719"
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>如何列出分支機構應用程式屬性
此命令顯示分支機構應用程式的下列相關資訊。 如需分支機構應用程式屬性的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。  
  
 SSO 系統從 xml 檔案取得您用來更新分支機構應用程式的這項資訊。 如需詳細資訊，請參閱 <<c0> [ 如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>使用管理公用程式顯示分支機構應用程式的屬性  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssomanage-displayapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要顯示的分支機構應用程式名稱屬性。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>使用用戶端公用程式顯示分支機構應用程式的屬性  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*安裝磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssoclient-displayapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要顯示的分支機構應用程式名稱屬性。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)