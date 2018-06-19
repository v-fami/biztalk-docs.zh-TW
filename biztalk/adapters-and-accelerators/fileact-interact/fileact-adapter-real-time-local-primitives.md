---
title: FileAct 配接器的即時本機原型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef4da4f8-3de2-4d35-8f8a-1e12937e52a1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcc0f1d093d56b8cd4580ef068007d02aab6346f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223070"
---
# <a name="fileact-adapter-real-time-local-primitives"></a>FileAct 配接器即時區域基本型別
區域基本型別牽涉到兩個訊息，這會在用戶端 SWIFTNet 連結 (SNL) 和本機 FileAct 子系統之間交換。  
  
 下圖顯示 FileAct 區域基本型別。  
  
 ![FileAct 區域基本型別](../../adapters-and-accelerators/fileact-interact/media/67ca0c3b-3c81-401d-87cb-473c68cae63f.gif "67ca0c3b-3c81-401d-87cb-473c68cae63f")  
  
## <a name="get-status-for-a-single-transfer"></a>取得單一傳輸中的狀態  
 取得狀態基本擷取有關從本機永續性內容的一項傳輸的狀態資訊。  
  
## <a name="subscribe-to-transfer-events"></a>要傳送的事件訂閱  
 使用訂閱的事件基本項目來漸進式傳送狀態資訊可能會收到事件的事件為基礎。 每個檔案傳輸可能會在交涉期間呼叫的事件端點的具名實體連結。 事件的伺服器，會叫用的訂閱事件的基本指示一個這類事件端點至其本身的所有事件報表。  
  
 事件的伺服器可以訂閱特性 （不同層級的詳細資料，以及不同的事件類型）。  
  
 事件的伺服器可能會叫用基本項目多次來訂閱事件的多個端點。 只有一個事件的伺服器可以訂閱任何特定的事件端點在指定的時間。 此外，事件伺服器可以叫用基本項目變更特性多次相同的事件端點。  
  
## <a name="receive-transfer-events"></a>接收轉送事件  
 接收轉送的事件是處理事件的事件狀態資訊有關傳輸進行中的基本類型。 它的回應設定的設定訂閱的事件基本的訂用帳戶中的條款。 此基本類型可以實作傳送或接收方的傳輸。  
  
## <a name="abort-transfer"></a>中止傳輸  
 使用者應用程式可能會中止傳輸正在進行使用中止基本項目。 中止基本項目是可能在傳送端或在進度傳輸的接收端執行的基本類型。 當起始或接受傳輸時，每一端會有建立可做為存取金鑰來保護該傳輸，從其一方的傳輸索引鍵的選項。 如果正在進行傳輸建立傳輸金鑰，它可能不會中止該端從未提供的練習中中止基本型別中的傳輸金鑰值。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)