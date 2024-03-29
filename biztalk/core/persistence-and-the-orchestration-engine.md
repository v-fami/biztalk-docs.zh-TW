---
title: 持續性和協調流程引擎 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration engine, persistence
- persistence
- orchestration engine, serialization
ms.assetid: 088230ef-13b3-440b-9875-6449f29dd5c6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d61d6665ba0828fb6cf24ef71ffb04fbcb94d5e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022516"
---
# <a name="persistence-and-the-orchestration-engine"></a>持續性及協調流程引擎
狀態持續性及其管理與還原，構成協調流程引擎許多基本功能的基礎。 特別是持續性，對下列功能的運作尤為重要：  
  
- 凍結和解除凍結  
  
- 與電腦無關的執行和解除凍結  
  
- 補償模型  
  
- 在控制情況下的系統關閉  
  
- 復原  
  
  協調流程引擎會在不同點持續儲存執行中協調流程執行個體的整個狀態，這樣就可以在稍後將執行個體完整地還原於記憶體中。 此狀態包含：  
  
- 引擎的內部狀態，包括其目前的進度。  
  
- 任何維護狀態資訊且由協調流程所使用之 .NET 元件的狀態。  
  
- 訊息和變數值。  
  
## <a name="persistence-points"></a>持續點  
 協調流程引擎會在不同點儲存執行中協調流程執行個體的狀態。 若它需要解除凍結協調流程執行個體，請從控制的關閉啟動，或從未預期的關閉復原，它會從最後的持續點執行協調流程執行個體，就像從未發生過任何事一樣。 例如，若收到了某個訊息，但在儲存狀態之前發生了未預期的關閉，則引擎將不會記錄它已收到訊息，並會在重新啟動時再次接收該訊息。 引擎將會在下列狀況中儲存協調流程的狀態：  
  
-   已達交易式範圍的結尾。  
  
    -   引擎會在交易式範圍結束時儲存狀態，這樣就可以明確地定義協調流程應該繼續的點，而且若有需要，還可以正確地執行補償。  
  
    -   若持續性機制是成功的，協調流程將會從範圍結束時繼續執行，否則，會叫用適當的例外狀況處理常式。  
  
    -   如果範圍是交易式且不可部分完成的，引擎便會在認可時，將狀態儲存在該不可部分完成範圍的結尾。  
  
    -   如果範圍是交易式且長期執行的，則引擎會在範圍完成時，產生新交易並保存完整的執行階段狀態。  
  
-   已達到偵錯中斷點。  
  
-   已傳送訊息。 唯一的例外是，當訊息是從不可部分完成的交易範圍內所傳送時。  
  
-   協調流程會啟動另一個協調流程以非同步的方式，如同**啟動協調流程**圖形。  
  
-   已擱置協調流程執行個體。  
  
-   當協調流程引擎被要求關閉時，它會嘗試儲存控制資訊，以及所有執行中協調流程執行個體的目前狀態，如此，當它再次啟動時，便可以繼續執行它們。 如果引擎無法成功儲存目前狀態，它會從關閉前所發生的最後一個持續點繼續執行協調流程執行個體。 這種方式適用於控制情況下的系統關閉以及不正常終止。  
  
-   引擎會決定應該凍結的執行個體。  
  
-   已完成協調流程執行個體。  
  
## <a name="serialization"></a>序列化  
 協調流程直接或間接 (像是透過其他物件) 參考的所有物件執行個體都必須是可序列化的，這樣協調流程狀態才得以保存。 以下有兩個例外:  
  
-   您可以在不可部分完成的交易中宣告不可序列化的物件。 您可以這麼做是因為不可部分完成的範圍並不包含持續點。  
  
-   System.Xml.XmlDocument 不是一個可序列化的類別；它是以特殊案例來處理，且可用於任何地方。  
  
> [!CAUTION]
>  為了讓 .NET 物件得以保存，它必須標示為可序列化。  
  
> [!NOTE]
>  COM 物件不能使用標準 .NET 序列化程序來保存。 若您想要呼叫不可部分完成交易以外的 COM 物件，則必須將 COM 物件包裝在 .NET 物件中，這個 .NET 物件必須是 .NET 可序列化的，並且知道要如何保存和還原 COM 物件的狀態。  
  
## <a name="system-shutdown"></a>系統關閉  
 當協調流程引擎被要求關閉時，它會嘗試儲存控制資訊，以及所有執行中協調流程執行個體的目前狀態，如此，當它再次啟動時，便可以繼續執行它們。 如果引擎無法成功儲存目前狀態，它會從關閉前所發生的最後一個持續點繼續執行協調流程執行個體。 這種方式適用於控制情況下的系統關閉以及不正常終止。  
  
## <a name="recovery"></a>復原  
 引擎會將協調流程執行個體的狀態資訊定期儲存至永久儲存體，並會儲存系統關機時的狀態。  
  
 當協調流程執行個體因故發生異常失敗時，可從最後持續的狀態復原該執行個體，並可像沒有中斷過一樣繼續執行。 即使原來執行該執行個體的伺服器因為某種原因而中斷服務，執行個體也能在另一台機器上繼續執行。 因為有了這種多重伺服器的修復模型，所以也就不再需要叢集。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程凍結和解除凍結](../core/orchestration-dehydration-and-rehydration.md)