---
title: 如何刪除分支機構應用程式 |Microsoft Docs
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
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97315d21e3793ec6a282deb5f8cdd69d79ab7491
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003319"
---
# <a name="how-to-delete-an-affiliate-application"></a>如何刪除分支機構應用程式
您可以使用 MMC 嵌入式管理單元或命令列，從 SSO 資料庫刪除指定的分支機構應用程式。  
  
> [!IMPORTANT]
>  當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元刪除分支機構應用程式  
  
1.  上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。  
  
2.  在 [範圍] 窗格的 [MMC] 嵌入式管理單元，依序展開**企業單一登入**節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下**刪除**。  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a>使用命令列刪除分支機構應用程式  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 類型 * * ssomanage-deleteapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要移除的分支機構應用程式的名稱SSO 資料庫。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)