---
title: "如何擱置、 繼續和終止協調流程執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], resuming
- orchestrations, terminating
- managing [orchestrations], suspending
- orchestrations, resuming
- orchestrations, suspending
- managing [orchestrations], terminating
ms.assetid: 7b373dad-57d5-4696-9b29-a6c351d44fa8
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9528ac0e810a3d4e203733ab1cc5b041d3d61d31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-suspend-resume-and-terminate-orchestration-instances"></a>如何擱置、繼續和終止協調流程執行個體
本主題說明如何使用 BizTalk Server 管理主控台來擱置、繼續和終止協調流程的一或多個執行中的服務執行個體。 服務執行個體是 BizTalk Server 正在處理或已經序列化至 MessageBox 做進一步處理或追蹤的協調流程執行個體。  
  
 以下說明這三項作業的作用：  
  
-   **暫止。** 這會暫停服務執行個體。 正在處理中訊息則會執行完畢。 訊息仍然會路由傳送至服務執行個體，但不會經過處理。  
  
-   **繼續執行。** 這會繼續處理已擱置的執行個體。  
  
> [!NOTE]
>  您不能從中斷點狀態繼續執行個體。 繼續這種執行個體可能顯示「擱置」狀態，但執行個體實際上會失敗。  
  
-   **終止。** 這會終止所有訊息處理。 服務執行個體會從 BizTalk Server 資料庫刪除。 此服務執行個體正在處理的訊息也會被刪除，但其他未終止之服務執行個體所參考的任何訊息除外。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-view-start-stop-or-terminate-an-instance-of-an-orchestration"></a>若要檢視、啟動、停止或終止協調流程的執行個體  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  選取要顯示 [群組中樞] 頁面的 BizTalk 群組。  
  
3.  在下**進行中的工作**，按一下 **執行服務執行個體**。  
  
     頁面下端區域中的查詢結果面板會顯示協調流程的所有執行個體。  
  
4.  若要精簡查詢並檢視協調流程的不同執行個體，請按一下底下的方塊**值**如**搜尋**欄位中，選取執行個體類型，若要檢視，然後按一下**執行查詢**. 如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。  
  
5.  以滑鼠右鍵按一下執行個體，然後按一下**暫停**，**繼續**，或**Terminate**。 此功能可讓您選取哪些執行個體將繼續。  
  
    > [!NOTE]
    >  若要在多個執行個體上執行作業，請按住 CTRL 鍵並按一下所要的執行個體。 以滑鼠右鍵按一下執行個體，然後按一下 **暫停**，**繼續**，或**Terminate**。  
  
     [服務執行個體狀態](../core/service-instance-states.md)提供暫止狀態的詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md)   
 [如何搜尋已擱置的服務執行個體](../core/how-to-search-for-suspended-service-instances.md)