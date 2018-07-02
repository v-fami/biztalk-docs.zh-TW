---
title: 如何設定啟動協調流程圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Start Orchestration shapes
- Start Orchestration shape [Orchestration Designer], parameters
- Start Orchestration shape [Orchestration Designer], configuring
- orchestrations, starting
- Start Orchestration shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], about Star Orchestration shape
ms.assetid: 9d01c41e-9bc5-4c1c-a869-b2f0df13036a
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4877d775b30f7ab407f57ebf2679f8cb65a0ef08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974911"
---
# <a name="how-to-configure-the-start-orchestration-shape"></a>如何設定啟動協調流程圖形
**啟動協調流程**圖案大致**呼叫的協調流程**圖形，但您叫用另一個協調流程，以非同步方式與**啟動協調流程**圖形 — 也就是叫用的協調流程中的控制流程會繼續超出引動過程，而不需等待叫用的協調流程完成其工作。  
  
 您可以指定將傳遞給被叫用之協調流程的參數。 參數可以是訊息、變數、連接埠參考、角色連結或相互關聯集。 **啟動協調流程**圖形只能採用*中*參數，它能*out*或*ref*參數。  
  
> [!CAUTION]
>  如果您將不可序列化的物件 (如 XmlDocument 或 XmlNode) 當做參數傳遞給此協調流程，它將會失敗。  
  
 **啟動協調流程**圖形是在其中您可以做為參數傳遞的連接埠反轉極性的唯一圖形，例如*使用*連接埠 （傳送埠） 可以傳入叫用的協調流程，但叫用的協調流程可以將它視為*實作*連接埠 （接收埠）。 請注意，只有使用直接繫結的連接埠才可以這樣處理。  
  
 **啟動協調流程**圖形也可用來呼叫另一個專案中參考的協調流程。 如此可在 BizTalk 專案之間重複使用共同的協調流程工作流程模式。 要能夠呼叫參考的協調流程，請確定**型別修飾詞**呼叫的協調流程的屬性設定為**公用**。 若要設定**型別修飾詞**協調流程屬性**公用**，開啟協調流程，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下綠色啟動圖形頂端的 協調流程，以顯示**協調流程屬性**對話方塊，並設定**型別修飾詞**屬性設**公用**。 預設值**型別修飾詞**是**私人**。  
  
 如需如何使用的範例**啟動協調流程**圖形，請從下載 SDK 範例 「 實作 Scatter and Gather Pattern" [ http://go.microsoft.com/fwlink/?LinkId=73703 ](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
### <a name="to-configure-a-start-orchestration-shape"></a>設定啟動協調流程圖形  
  
1. 使用**協調流程選取**下拉式清單方塊中，選取清單中的協調流程。  
  
2. 使用**協調流程參數**方格控制項，指定要傳遞至協調流程的引數 — 中所指定**協調流程選取**下拉式清單方塊中，啟動的。 您可以輸入變數名稱或按一下儲存格下拉式清單中的變數，在 [變數] 資料行的儲存格中指定這些引數，每個儲存格一個變數。  
  
3. 若要設定**啟動協調流程**圖形根據服務和您在對話方塊中指定的引數，請按一下**確定**。 若要關閉**啟動協調流程組態**對話方塊，而不進行任何變更地**啟動協調流程**圖形，請按一下**取消**。  
  
   > [!CAUTION]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援遞迴協調流程。 若協調流程 A 呼叫或啟動協調流程 B，則協調流程 B 就不能直接呼叫或啟動協調流程 A，而且它也不能呼叫或啟動直接或間接呼叫協調流程 A 的任何協調流程。  
  
## <a name="orchestration-selection-drop-down-list-box"></a>協調流程選取下拉式清單方塊  
 按一下下拉式清單方塊中的向下箭號，以檢視可用的協調流程並從中選取一個協調流程。 此清單包含可以從目前協調流程中啟動的所有協調流程，包含參考的組件。  
  
## <a name="orchestration-parameters-grid-control"></a>協調流程參數方格控制項  
 指定要傳遞至參數化的協調流程所使用的引數**協調流程參數**方格控制項。 此方格有四個資料行： 在範圍中，參數名稱、 參數型別，以及參數方向的變數。 您只能在第一個資料行進行變更，其他是唯讀的資料行。  
  
 當您選取有效的協調流程時，其參數會填入參數名稱、類型以及方格控制項的方向資料行。 然後，在每一個資料列中選取要當做引數傳遞的變數。 您可以從 [範圍內的變數] 資料行中每個儲存格的下拉式清單選取這些變數。 此清單會顯示相鄰的 [參數類型] 儲存格中所指定之類型的所有可用變數。 若該類型只有一個可用物件，則 [範圍內的變數] 儲存格會自動填入該物件。 您也可以在 [範圍內的變數] 儲存格中進行輸入，以選取下拉式清單中可用的變數。  
  
> [!NOTE]
>  因為**啟動協調流程**圖形啟動協調流程時，協調流程參數 」 您在此對話方塊中選取實際上是指協調流程變數。  
  
 若您正在執行的協調流程沒有定義的參數，則此對話方塊中的方格控制項無法使用。  
  
## <a name="in-this-section"></a>本節內容  
 [如何建立接收訂用帳戶在叫用的協調流程](../core/how-to-create-receive-subscriptions-at-invoked-orchestrations.md) 
  
## <a name="see-also"></a>另請參閱  
 [如何設定呼叫協調流程圖形](../core/how-to-configure-the-call-orchestration-shape.md)