---
title: 如何列出分支機構應用程式的屬性 |Microsoft 文件
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
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3ac0c77dbaad27012f104486797c4e47d1e46be
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>如何列出分支機構應用程式的屬性
此命令顯示分支機構應用程式的下列相關資訊。 如需分支機構應用程式屬性的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。  
  
 SSO 系統從 xml 檔案取得您用來更新分支機構應用程式的這項資訊。 如需詳細資訊，請參閱[如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>使用管理公用程式顯示分支機構應用程式的屬性  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssomanage-displayapp *\<應用程式名稱\>* * *，其中*\<應用程式名稱\>*的分支機構應用程式想要顯示的屬性名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>使用用戶端公用程式顯示分支機構應用程式的屬性  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是\<*安裝磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssoclient – displayapp *\<應用程式名稱\>* * *，其中*\<應用程式名稱\>*的分支機構應用程式想要顯示的屬性名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)