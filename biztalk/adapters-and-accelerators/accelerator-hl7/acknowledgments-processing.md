---
title: 處理通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, processing
ms.assetid: 705bc12d-69ac-4641-a45e-4f1fab507e4a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b726eb4698eaa9887703d7df01dc0f6cadf5eefc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments-processing"></a>處理通知
HL7 規格支援兩種格式的訊息交換：  
  
-   來路不明的更新和其通知 (ACK)  
  
-   查詢和回應  
  
 回應訊息從起始應用程式，回應的應用程式的回應訊息，其中包含資料或錯誤指示。 起始應用程式可能會收到拒絕狀態來自回應者應用程式指出，回應者應用程式未收到郵件正確。 在這兩種情況下，訊息交換的程序牽涉到兩個實體，起始，而且有回應的應用程式。 每一個都是傳送者和接收者的訊息。 起始應用程式會傳送第一次，但收到，而回應系統接收，然後傳送。  
  
## <a name="unsolicited-updates"></a>來路不明的更新  
 特定業務 (LOB) 應用程式發佈訊息，或觸發程序事件發生時起始傳送資訊時，就會發生不請自來的更新。 例如，某個病患的實驗室結果可用時，可能有需要將實驗室結果傳送至數個其他系統。 這些更新是未經要求的更新通知會回應。  
  
## <a name="queries"></a>查詢  
 如果查詢時，需要資訊的應用程式會將查詢傳送至另一個應用程式，並接收應用程式回應查詢。 比方說，藥局應用程式可能會傳送包含訂單項目 (CPOE) 系統病患識別碼的要求訊息並接收回應，其中包含必要的資料，以允許訂單處理。 提出要求的交易會是查詢，而且不同之未經要求的更新中。 在回應中包含兩個應用程式之間流動的資訊。 回應本身不需要使用第四個訊息的通知。 不過，修改這在某些環境中以回應通知。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 如果如此設定，會通知以回應。 如需查詢/回應交換的範例，請參閱[Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [驗證訊息](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)