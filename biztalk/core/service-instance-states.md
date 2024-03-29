---
title: 服務執行個體狀態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service instances, states
- messages, processing
- states, service instances
ms.assetid: 38189538-72b3-49df-810b-e134362e35ef
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e6eca4af163e3b493eb2d2916f3866366c389cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022440"
---
# <a name="service-instance-states"></a>服務執行個體狀態
在處理訊息時，會發生下列動作：  
  
- 在 接收位置，接收配接器，或傳輸元件 — 從外部應用程式接收訊息，並將它提交至 BizTalk Server 中，進行處理。  
  
  > [!NOTE]
  >  系統可接收多種格式的訊息：XML、一般檔案或公司之間的電子資料交換 (EDI)。  
  
- 接收管線解密、解碼和解譯訊息。  
  
- 傳訊引擎傳送的訊息和及其捷徑屬性，例如訊息類型，以及來源 — 到 MessageBox 資料庫。  
  
- 在找到符合的訂閱時，會依據一組結構描述與對應來處理訊息，有時候則依據存在主控件伺服器上的商務規則或原則來處理訊息。  
  
- 處理完成後，產生的訊息會保存 (寫入) 至 MessageBox 資料庫。 捷徑屬性已經修改，指出要將訊息傳送至何處，例如，使用哪個傳送埠。  
  
- 依照在傳送埠定義的篩選條件運算式來評估訊息的捷徑屬性，而 MessageBox 資料庫將訊息傳遞至適當的傳送埠。  
  
- 傳送管線和/或傳送埠的訂閱必須符合要傳送的訊息。 訊息已加密且已傳輸。  
  
  此週期中的每個程序都會產生自己的事件集。  
  
  當服務執行個體 (接收埠、協調流程、傳送埠) 在 BizTalk Server 中逐步處理訊息時，這些服務執行個體的狀態為數種可能狀態中的一種。 本節討論有哪些狀態，並顯示在其生命週期中不同時期的狀態範例。  
  
## <a name="service-instance-states"></a>服務執行個體狀態  
 下表顯示服務執行個體的各種可能狀態，以及每個狀態的說明。  
  
|State|說明|  
|-----------|-----------------|  
|**在中斷點**|作用中的協調流程會叫用此中斷點，通常由 BizTalk Server 解決方案開發人員設定。 此狀態只對協調流程有效。|  
|**準備好要執行**|已經啟動但尚未開始執行的服務執行個體，通常是因為暫時無法使用資源，例如，伺服器處理負載過重。|  
|**作用中**|執行服務執行個體。|  
|**凍結**|保存在 MessageBox 資料庫中的執行個體狀態，沒有任何 Windows 服務正在執行該執行個體。|  
|**完成並有捨棄的訊息**|服務執行個體已完成，不過該執行個體沒有消耗一些訊息。|  
|**已擱置 （可繼續）**|執行個體已擱置，您可繼續此執行個體。 **重要事項：** 繼續傳訊執行個體將會執行下列動作： <ul><li>繼續訊息的執行個體。</li><li>將訊息傳送至傳送埠。</li><li>傳送埠會將訊息傳遞到目的地;即使傳送埠不是已啟動 」 狀態。</li></ul> <br /><br /> 請注意，當您擱置排程的執行個體然後繼續時，執行個體便會進入已凍結狀態。|  
|**已擱置 （不可繼續）**|執行個體已擱置，但您不能繼續此執行個體。 您可以儲存執行個體參考的訊息，然後終止執行個體。<br /><br /> 請注意，當您擱置排程的執行個體然後繼續時，執行個體便會進入已凍結狀態。|  
|**擱置的擱置 / 擱置的終止**|一種狀態，並非獨立的狀態。 您可以將它與其他狀態結合。<br /><br /> 擱置或終止的控制訊息已傳送至服務執行個體，但執行個體尚未拾取。 每次只允許一個擱置作業。 當含有擱置作業的執行個體凍結時，您可以終止此執行個體。|  
  
### <a name="tracked-service-instance-states"></a>追蹤的服務執行個體狀態  
 下表顯示服務執行個體追蹤狀態，並附上每個狀態的解釋。  
  
|State|說明|  
|-----------|-----------------|  
|**已啟動**|目前位於 MessageBox 中，任何處於已擱置狀態 (可繼續) 或在中斷點狀態的服務執行個體，會在 BizTalk 追蹤資料庫中顯示為「已啟動」。|  
|**已完成**|服務執行個體處理已成功完成。|  
|**終止**|服務執行個體已終止。|  
  
## <a name="message-states"></a>訊息狀態  
 下表顯示訊息的狀態，並附上每個狀態的解釋。  
  
|State|說明|  
|-----------|-----------------|  
|**取用**|正在由服務執行個體處理的訊息。|  
|**在 處理程序**|訊息已傳送至引擎，並正在處理中。 訊息在記憶體中。|  
|**已排入佇列**|「已排入佇列」狀態包含「已排入佇列」(等待處理)、「已排入佇列」(排程在稍後傳遞) 和「已排入佇列」(等待重試) 等執行個體狀態。|  
|**已排入佇列 （等待處理）**|當排序的傳遞傳送埠正在重試先前的訊息時，訊息是處於排序的傳遞實例中。|  
|**已排入佇列 （排程在稍後傳遞）**|訊息正在等待由擁有服務窗口集的傳送埠來傳送。|  
|**已排入佇列 （等待重試）**|訊息因為無法使用目的 URI，而與嘗試重新傳送訊息的傳送埠關聯。|  
|**已暫停**|「已擱置」狀態包含「已擱置」(可繼續) 和「已擱置」(不可繼續) 執行個體狀態。|  
|**已擱置 （可繼續）**|與訊息關聯的服務執行個體已擱置，而且可以繼續。<br /><br /> 繼續訊息的執行個體將會執行下列作業：<br /><br /> -繼續進行傳訊執行個體。<br />-傳送訊息至傳送埠。<br />-傳送埠會將訊息傳遞到目的地;即使傳送埠不是已啟動 」 狀態。|  
|**已擱置 （不可繼續）**|與訊息關聯的服務執行個體已擱置，而且不可繼續。|  
  
## <a name="instance-states-before-and-after-an-operation"></a>作業之前與之後的執行個體狀態  
 下表顯示作業之前與之後的狀態。  
  
> [!NOTE]
>  開始和結束狀態以粗體顯示在左資料行及上方資料列。 作業顯示在表格內文中。  
  
|開始狀態|套用作業之後的新狀態|||||||  
|--------------------|------------------------------------------|------|------|------|------|------|------|  
||**在中斷點**|**作用中**|**凍結**|**已暫停**|**終止**|**擱置的終止**|**擱置的擱置**|  
|**在中斷點**|從偵錯工具附加|從偵錯工具繼續|停止 Windows 服務|||Terminate|暫止|  
|**在 中斷點 （已凍結）**|從偵錯工具附加|從偵錯工具繼續|停止 Windows 服務|暫止|Terminate|||  
|**準備好要執行**||||暫止|Terminate|||  
|**已排程**||執行階段因為服務視窗已啟動而拾取執行個體||||||  
|**作用中**|||停止 Windows 服務|||Terminate|暫止|  
|**凍結**||執行階段拾取執行個體|停止 Windows 服務|暫止|Terminate|||  
|**已擱置 （可繼續）**|從偵錯工具在中斷點繼續|繼續|||Terminate|||  
|**已擱置 （不可繼續）**|||||Terminate|||  
|**具有未使用訊息**|||||Terminate|||  
|**擱置的擱置**|可嘗試附加，但最後應會失敗||停止 Windows 服務|已處理要求|只有在執行個體凍結時，終止才會作用|||  
|**擱置的終止**|可嘗試附加，但最後應會失敗||停止 Windows 服務，執行個體凍結||已處理要求，或執行個體凍結|||  
  
## <a name="instance-states-during-an-operation"></a>作業期間的執行個體狀態  
 下表顯示系統對執行個體執行作業時狀態的變更。  
  
|開始狀態|作業||||||  
|--------------------|---------------|------|------|------|------|------|  
||**終止**|**暫止**|**繼續**|**在中斷點繼續**|**Continue**|**附加**|  
|**在中斷點**|已終止|已暫停|||作用中|在中斷點|  
|**在 中斷點 （已凍結）**|已終止|已暫停|||作用中|在中斷點|  
|**準備好要執行**|已終止|已暫停|||||  
|**已排程**|已終止|已暫停|||||  
|**作用中**|已終止|已暫停|||||  
|**凍結**|已終止|已暫停|||||  
|**已擱置 （可繼續）**|已終止||作用中|在中斷點|||  
|**已擱置 （不可繼續）**|已終止||||||  
|**具有未使用訊息**|已終止||||||  
|**擱置的擱置**|已終止；只有在執行個體凍結時才會作用|||||競爭條件|  
|**擱置的終止**|已終止；只有在執行個體凍結時才會作用|||||競爭條件|  
  
> [!NOTE]
>  當系統傳遞多個控制訊息至執行個體時，就會發生競爭條件，且無法保證執行個體處理這些訊息的順序。  
  
## <a name="see-also"></a>另請參閱  
 [使用群組中樞頁面](../core/using-the-group-hub-page.md)