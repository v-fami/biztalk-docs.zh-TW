---
title: 如何刪除分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], deleting
- managing [SSO applications], deleting
- deleting, applications [SSO]
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cc742b41735f31b0da43560c19df4beb4f126d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-an-affiliate-application"></a>如何刪除分支機構應用程式
您可以使用 MMC 嵌入式管理單元或命令列，從 SSO 資料庫刪除指定的分支機構應用程式。  
  
> [!IMPORTANT]
>  當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元刪除分支機構應用程式  
  
1.  在 **啟動**  功能表上，按一下  **程式**, ，按一下  **Microsoft 企業單一登入**, ，然後按一下  **SSO 管理**。  
  
2.  在 範圍 窗格的 MMC 嵌入式管理單元，依序展開 **企業單一登入** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下 **刪除**。  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a>使用命令列刪除分支機構應用程式  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssomanage-deleteapp *\<應用程式名稱\>* * *，其中*\<應用程式名稱\>*是您想要從 SSO 資料庫中移除的分支機構應用程式的名稱。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)