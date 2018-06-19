---
title: 接收配接器批次支援的介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6ee780-189c-41e3-9ab0-6b869e791c0a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2de4d27ec65620adbb5428491c5ab1a53300fd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22258006"
---
# <a name="interfaces-for-a-batch-supported-receive-adapter"></a>批次支援接收配接器介面
接收介面永遠會批次提交訊息。 批次指的是內含許多資料庫作業的一個單位，您可以用來執行許多動作，而不只是提交。 例如，接收配接器可以在相同的批次作業中提交一組訊息、暫停一組不同的訊息，並刪除另一組訊息。 我們非常鼓勵您使用批次作業，因為將這些分開的作業群組至相同的批次中可以降低所需的資料庫往返並最佳化效能。  
  
 內含式與外掛式接收配接器需要實作下列介面，將一批批的訊息提交至伺服器中：  
  
-   **IBTTransport**  
  
-   **IBTTransportControl** （只有內含式配接器）  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchCallBack**  
  
 下列步驟說明接收配接器為了將訊息提交至伺服器中，所執行的動作順序。  
  
1.  接收配接器從傳輸 proxy 取得批次，藉由呼叫**Ibttransportproxy**方法**IBTTransportProxy**介面。 呼叫中**Ibttransportproxy**配接器傳遞指標，其**IBTBatchCallback**介面實作。  
  
2.  配接器將一個訊息一次加入批次呼叫**SubmitMessage**方法**IBTTransportBatch**介面。 如果這是雙向作業，例如請求-回應傳訊， **SubmitResponseMessage**呼叫此相同介面的方法來提交回應訊息。  
  
3.  當所有訊息都已加入至批次時，配接器會呼叫**完成**方法**IBTTransportBatch**提交給傳輸 proxy 批次的介面。 因為接收配接器是非同步的本質，配接器可以立即取得新批次開始提交其他訊息之後，它會呼叫**完成**。  
  
4.  處理批次之後，傳訊引擎會叫用配接器的**BatchComplete**使用傳輸 proxy 來進行實際呼叫的回呼方法。 陣列**BTBatchOperationStatus**物件包含了提交的狀態傳遞至配接器。 每個物件都對應到一個作業類型，且包含作業的整體狀態以及每個要求執行作業的訊息狀態。 下列順序說明為了分析處理中的批次狀態，配接器需要執行的動作：  
  
    1.  當做參數傳遞的整體批次狀態 HRESULT 值的核取**BatchComplete**方法。 如果呈現失敗狀態，代表批次中至少有一個作業沒有成功。 因此，以一個實體單位來提交整個批次的作業失敗。 這時候配接器應該要試著探索作業失敗的訊息，並將那些一開始就成功的訊息整合為一個批次重新提交。  
  
         如果整體批次狀態成功，代表所有傳遞至傳輸 Proxy 的訊息都已保存至磁碟中。 然而，這不代表管線已成功處理所有的訊息， 而是代表管線中失敗的訊息可能已被擱置。 針對在管線中失敗的訊息，傳回的整體批次狀態還是成功的，因為資料已經寫入磁碟。  
  
    2.  在 `operationStatus` 參數中檢查每個作業類型的狀態。 如果狀態為**S_OK**，提交此作業成功，且您不需要進一步任何檢查的狀態。 如果狀態設為**BTS_S_EPM_MESSAGE_SUSPENDED**某些訊息已被擱置。 **BTS_S_EPM_SECURITY_CHECK_FAILED**表示某些訊息無法在驗證需要驗證的接收埠。 如果**E_FAIL**傳回，或者任何帶有小於零，此作業失敗的訊息送出的值 HRESULT。  
  
    3.  針對作業類型檢查每個訊息的狀態。 針對提交作業類型，每個訊息的狀態設定為**S_OK**如果提交成功。 **BTS_S_EPM_MESSAGE_SUSPENDED**如果暫止訊息傳回。 **BTS_S_EPM_SECURITY_CHECK_FAILED**會傳回訊息失敗時需要驗證的接收埠上的驗證。 **E_BTS_NO_SUBSCRIPTION**恢復時沒有任何訂閱者的已發佈的訊息。 如果**E_FAIL**傳回，或者任何帶有值小於零，此訊息提交失敗，HRESULT。  
  
    4.  根據您的配接器，您可能要擱置訊息傳回**E_FAIL**或任何失敗的 HRESULT。  
  
5.  **BatchComplete**方法需要傳回**S_OK**或**E_FAIL**以表示執行結果。 如果**BatchComplete**方法會傳回**E_FAIL**或任何負數 HRESULT，傳輸 proxy 來記錄錯誤。  
  
 下圖顯示在建立支援批次處理的接收配接器時所牽涉的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter1.gif "ebiz_sdk_devadapter1")  
接收配接器提交訊息批次的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [介面的內含式接收配接器](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [接收配接器同步要求-回應的介面](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)