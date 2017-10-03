---
title: "如何繼續擱置的協調流程執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, resuming [HAT]
- HAT, resuming orchestrations
- HAT, resuming pipelines
- orchestrations, resuming
- resuming, pipelines
- resuming, orchestrations
- HAT, debug mode
ms.assetid: da133183-68d9-48d1-9601-8f6d4d5b8898
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6696547ce3e918dc8d84b7cfcb4f24e31c8b70a0
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-resume-suspended-orchestration-instances"></a>如何繼續擱置的協調流程執行個體
如果您有列示為「已擱置，可繼續」的擱置協調流程執行個體，則可以嘗試從 [查詢結果] 或 [預覽] 窗格中繼續該協調流程執行個體。 只有同時解決導致協調流程執行個體擱置的基本問題之後，您才能夠順利繼續協調流程執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-resume-suspended-orchestration-instances"></a>繼續擱置的協調流程執行個體  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  
  
3.  在 詳細資料 窗格中，按一下**新查詢** 索引標籤。  
  
4.  在**查詢運算式**群組中**值**欄中，選取**已擱置服務執行個體**從下拉式清單方塊。  
  
5.  執行下列其中之一：  
  
    -   若要繼續單一執行個體，在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**服務名稱**篩選和接著在**值**資料行中，指定服務名稱。  
  
    -   若要繼續大量執行個體，在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**群組結果依據**，然後在**值**資料行中，指定服務名稱。  
  
6.  按一下**執行查詢**。  
  
7.  在查詢結果清單中，以滑鼠右鍵按一下您要繼續，然後按一下 協調流程執行個體**繼續的執行個體**或**繼續的執行個體**。 這可讓您選取的執行個體將繼續。  
  
     [服務執行個體狀態](../core/service-instance-states.md)提供的詳細資訊在暫停狀態。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、 連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)
