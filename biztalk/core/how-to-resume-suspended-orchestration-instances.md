---
title: 如何繼續擱置的協調流程執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f3243173f454d560515d1c3cbb9bef749fc17d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991167"
---
# <a name="how-to-resume-suspended-orchestration-instances"></a>如何繼續擱置的協調流程執行個體
如果您有列示為「已擱置，可繼續」的擱置協調流程執行個體，則可以嘗試從 [查詢結果] 或 [預覽] 窗格中繼續該協調流程執行個體。 只有同時解決導致協調流程執行個體擱置的基本問題之後，您才能夠順利繼續協調流程執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。  
  
### <a name="to-resume-suspended-orchestration-instances"></a>繼續擱置的協調流程執行個體  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。  
  
3. 在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。  
  
4. 在 **查詢運算式**群組中**值**欄中，選取**已擱置服務執行個體**從下拉式清單方塊。  
  
5. 執行下列其中之一：  
  
   - 若要可繼續的單一執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **服務名稱</em>* 篩選器，然後在**值** 欄中，指定服務名稱。  
  
   - 若要可繼續大量執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **群組結果依據</em>* ，然後在**值** 欄中，指定服務名稱。  
  
6. 按一下 **執行查詢**。  
  
7. 在查詢結果清單中，以滑鼠右鍵按一下您想要繼續，然後按一下 協調流程執行個體**繼續執行個體**或是**繼續的執行個體**。 這可讓您選取要繼續的執行個體。  
  
    [服務執行個體狀態](../core/service-instance-states.md)上將詳細說明有關擱置狀態。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)
