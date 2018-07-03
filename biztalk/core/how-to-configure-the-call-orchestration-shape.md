---
title: 如何設定呼叫協調流程圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Orchestration shape [Orchestration Designer], parameters
- Call Orchestration shape [Orchestration Designer], configuring
- Call Orchestration shape [Orchestration Designer], about Call Orchestration shapes
- configuring [Orchestration Designer], Call Orchestration shapes
- Call Orchestration shape [Orchestration Designer]
- nonserializable objects
- orchestrations, nonserializable objects
- Call Orchestration shape [Orchestration Designer], referencing orchestrations
- orchestrations, parameters
ms.assetid: 718ce2a0-ac08-4662-8b4e-1be279dbc749
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aab9f1ab84836d436ea1570b7d63f8a3cc0c0064
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981031"
---
# <a name="how-to-configure-the-call-orchestration-shape"></a>如何設定呼叫協調流程圖形
**呼叫的協調流程**圖形可以用來同步呼叫另一個專案中參考的協調流程。 如此可在 BizTalk 專案之間重複使用共同的協調流程工作流程模式。 當您叫用另一個巢狀協調流程，以同步方式**呼叫的協調流程**圖形封閉式協調流程會等待巢狀協調流程完成後再繼續。  
  
 您可以指定將傳遞給巢狀協調流程的參數。 參數可以是訊息、變數、連接埠參考、角色連結或相互關聯集。 傳入的連接埠參考、 角色連結和相互關聯集運作方式都與自我定址信封相同： 他們提供可用來將資訊傳送回封閉式協調流程的巢狀協調流程資訊。  
  
> [!CAUTION]
>  如果您將不可序列化的物件 (如 XmlDocument 或 XmlNode) 當做參數傳遞給協調流程，它將會失敗。  
  
 如需如何使用的範例**呼叫的協調流程**圖形，請參閱[CallOrchestration （BizTalk Server 範例）](../core/callorchestration-biztalk-server-sample.md)。  
  
### <a name="to-configure-a-call-orchestration-shape"></a>若要設定呼叫協調流程圖形  
  
1. 使用**協調流程選取**下拉式清單方塊中，選取清單中的協調流程。  
  
2. 使用**協調流程參數**方格控制項，指定要傳遞至協調流程的引數 — 中所指定**協調流程選取**下拉式清單方塊中，呼叫。 您可以輸入變數名稱或按一下儲存格下拉式清單中的變數，在 [變數] 資料行的儲存格中指定這些引數，每個儲存格一個變數。  
  
3. 若要設定**呼叫的協調流程**圖形根據服務和您在對話方塊中指定的引數，請按一下**確定**。 若要關閉**呼叫的協調流程組態**對話方塊，而不進行任何變更地**呼叫協調流程**圖形，請按一下**取消**。  
  
   > [!CAUTION]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援遞迴協調流程。 若協調流程 A 呼叫或啟動協調流程 B，則協調流程 B 就不能直接呼叫或啟動協調流程 A，而且它也不能呼叫或啟動直接或間接呼叫協調流程 A 的任何協調流程。  
  
## <a name="referenced-orchestrations"></a>被參考的協調流程  
 為了要能夠呼叫被參考的協調流程，請確保已經設定被呼叫端協調流程的下列屬性：  
  
- 設定**型別修飾詞**屬性設**公用**呼叫之協調流程。 若要設定**型別修飾詞**協調流程屬性**公用**，開啟協調流程，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下綠色啟動圖形頂端的 協調流程，以顯示**協調流程屬性**對話方塊，並設定**型別修飾詞**屬性設**公用**。  
  
- 設定**Activate**協調流程中初始接收圖形的屬性**False**。  
  
## <a name="orchestration-selection-drop-down-list-box"></a>協調流程選取下拉式清單方塊  
 按一下下拉式清單方塊中的向下箭號，檢視可用的服務並從中選取一個服務。 此清單包含可以從目前協調流程中呼叫的所有服務，包含被參考的組件。  
  
## <a name="orchestration-parameters-grid-control"></a>協調流程參數方格控制項  
 指定要傳遞至參數化的協調流程所使用的引數**協調流程參數**方格控制項。 此方格有四個資料行： 在範圍中，參數名稱、 參數型別，以及參數方向的變數。 您只能在第一個資料行進行變更，其他是唯讀的資料行。  
  
 當您選取有效的協調流程時，其參數會填入方格控制項的參數名稱、類型及方向欄。 然後，在每一個資料列中選取要當做引數傳遞的變數。 您可以從 [範圍內的變數] 資料行中每個儲存格的下拉式清單選取這些變數。 此清單會顯示相鄰的 [參數類型] 儲存格中所指定之類型的所有可用變數。 若該類型只有一個可用物件，則 [範圍內的變數] 儲存格會自動填入該物件。 您也可以在 [範圍內的變數] 儲存格中進行輸入，以選取下拉式清單中可用的變數。  
  
> [!NOTE]
>  因為**呼叫的協調流程**圖形呼叫協調流程，協調流程選取 [參數] 您在此對話方塊中實際上是指協調流程變數。  
  
 如果您正在呼叫的協調流程沒有已定義的參數，則此對話方塊中的方格控制項無法使用。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定啟動協調流程圖形](../core/how-to-configure-the-start-orchestration-shape.md)