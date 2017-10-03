---
title: "如何檢視協調流程的執行個體資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, viewing
- managing [orchestrations], viewing
ms.assetid: 860ac2b2-c556-4e1f-8b7f-18ab8be52db4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84129d48fba15dadfc97722ead85b1535a8fa597
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-instance-information-for-an-orchestration"></a>如何檢視協調流程的執行個體資訊
本主題描述如何使用 BizTalk Server 管理主控台來檢視協調流程的執行個體資訊。 服務執行個體是 BizTalk Server 正在處理或已經序列化至 MessageBox 做進一步處理或追蹤的協調流程執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-view-instance-information-for-an-orchestration"></a>檢視協調流程的執行個體資訊  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您要檢視執行個體資訊的協調流程的應用程式。  
  
3.  按一下**協調流程**，選取您要檢視執行個體資訊的協調流程按一下**檢視**，，然後選取 **執行個體資訊**。  
  
     頁面下端區域中的查詢結果面板會顯示協調流程的所有執行個體。  
  
     若要精簡查詢和檢視不同的執行個體資訊的協調流程，請按一下底下的方塊**值**的 搜尋 欄位中，選取 執行個體類型，若要檢視，然後按一下**執行查詢**。 如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md)   
 [如何搜尋已擱置的服務執行個體](../core/how-to-search-for-suspended-service-instances.md)   
 [如何搜尋訊息](../core/how-to-search-for-messages.md)   
 [如何搜尋訂閱](../core/how-to-search-for-subscriptions.md)