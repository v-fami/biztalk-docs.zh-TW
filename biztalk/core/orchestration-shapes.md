---
title: 協調流程圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer]
- Loop shape [Orchestration Designer]
- Throw Exception shape [Orchestration Designer]
- Expression shape [Orchestration Designer]
- Decide shape [Orchestration Designer]
- Receive shape [Orchestration Designer]
- Compensate shape [Orchestration Designer]
- orchestrations, shapes
- Suspend shape [Orchestration Designer]
- Send shape [Orchestration Designer]
- Group shape [Orchestration Designer]
- Listen shape [Orchestration Designer]
- shapes, about shapes
- Construct Message shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer]
- Call Rules shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer]
- Transform shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Role Link shape [Orchestration Designer]
- Call Orchestration shape [Orchestration Designer]
- Port shape [Orchestration Designer]
- shapes
- Scope shape [Orchestration Designer]
- Terminate shape [Orchestration Designer]
- Orchestration Designer, shapes
- Insufficient Configuration Smart Tag [Orchestration Designer]
ms.assetid: a1d03baa-a267-499d-94fc-700b3e959458
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181656208b757c595feb9d19ee786fe91f1b78f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264294"
---
# <a name="orchestration-shapes"></a>協調流程圖形
協調流程設計師是用來建立協調流程的視覺化工具， 它提供了幾個圖形，讓您以基礎動作的視覺化表示方式將這些圖形放在設計介面上，這些圖形也可讓您有效率地設計及實作協調流程。  
  
 **組態不完整的動作**  
  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!NOTE]
>  當協調流程設計師偵測到關聯的圖形未完整設定時，會顯示協調流程設計師中不足，無法設定動作。 如果協調流程中的圖形未完整設定，則關聯的協調流程將不會編譯。  
  
 下表列出可用的圖形，連同每一個圖形功能的簡短描述。  
  
|形狀圖|圖形名稱|目的|  
|-----------|----------------|-------------|  
|![](../core/media/ebiz-orch-callorchestrat.gif "ebiz_orch_callorchestrat")|**呼叫協調流程**|可讓您的協調流程同步呼叫另一個協調流程。|  
|![](../core/media/ebiz-orch-call-rules.gif "ebiz_orch_call_rules")|**呼叫規則**|可讓您設定要在協調流程中執行的商務規則原則。|  
|![](../core/media/ebiz-orch-compensate.gif "ebiz_orch_compensate")|**補償**|可讓您呼叫程式碼，使其在發生錯誤時復原或補償已經由協調流程執行的作業。|  
|![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")|**建構訊息**|可讓您建構訊息。|  
|![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")|**決定**|可讓您在協調流程中進行條件式分支。|  
|![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")|**延遲**|可讓您根據逾時間隔在協調流程中建置延遲。|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|**運算式**|可讓您為變數指派值或發出 .NET 呼叫。|  
|![](../core/media/ebiz-orch-group.gif "ebiz_orch_group")|**群組**|可讓您將作業群組成單一可摺疊及可展開的單位，以提供視覺上的方便性。|  
|![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")|**接聽**|可讓您的協調流程根據收到的訊息或逾時期間過期進行條件式分支。|  
|![](../core/media/ebiz-orch-loop.gif "ebiz_orch_loop")|**迴圈**|可讓您的協調流程在遇到某個條件之前不斷循環。|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|**訊息指派**|可讓您指派訊息值。|  
|![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")|**平行動作**|可讓您的協調流程執行兩個或多個彼此獨立的作業。|  
|![](../core/media/ebiz-orch-port.gif "ebiz_orch_port")|**[通訊埠]**|定義訊息的傳輸地點及方式。|  
|![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")|**接收**|可讓您接收協調流程中的訊息。|  
|![](../core/media/ebiz-orch-rolelink.gif "ebiz_orch_rolelink")|**角色連結**|可讓您建立要與相同邏輯夥伴通訊的連接埠集合 (可能是透過不同的傳輸或端點)。|  
|![](../core/media/ebiz-orch-scope.gif "ebiz_orch_scope")|**範圍。**|提供交易和例外處理的架構。|  
|![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")|**傳送**|可讓您從協調流程傳送訊息。|  
|![](../core/media/ebiz-orch-strtorchestrat.gif "ebiz_orch_strtorchestrat")|**啟動協調流程**|可讓您的協調流程非同步呼叫另一個協調流程。|  
|![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")|**暫止**|當發生某個錯誤狀況時，擱置協調流程的作業來啟用介入。|  
|![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")|**終止**|當發生某個錯誤狀況時，可讓您立即結束協調流程的作業。|  
|![](../core/media/ebiz-orch-throwexcept.gif "ebiz_orch_throwexcept")|**擲回例外狀況**|可讓您在發生錯誤時明確地擲出例外狀況。|  
|![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")|**轉換**|可讓您將現有訊息中的欄位對應到新訊息中的欄位。|