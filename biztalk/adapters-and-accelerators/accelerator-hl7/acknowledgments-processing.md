---
title: 通知處理 |Microsoft Docs
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
ms.openlocfilehash: cb8bf0620c3e336317382cbeb299cf2d6d17faa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969463"
---
# <a name="acknowledgments-processing"></a>通知處理
HL7 規格會支援兩種格式的訊息交換：  
  
- 來路不明的更新和其通知 (ACK)  
  
- 查詢和回應  
  
  在回應訊息從起始應用程式，回應的應用程式會回應包含資料或錯誤指示的訊息。 起始應用程式可能會收到拒絕狀態回應應用程式，指出，回應者應用程式未收到訊息正確。 在這兩種情況下，訊息交換的程序牽涉到兩個實體，起始和回應的應用程式。 每一個是傳送者和接收者的訊息。 起始應用程式會傳送第一次，然後接收，而接收回應的系統，並接著會傳送。  
  
## <a name="unsolicited-updates"></a>來路不明的更新  
 特定業務 (LOB) 應用程式發佈訊息，或觸發程序事件發生時，會起始傳輸的資訊時，就會發生不請自來的更新。 比方說，病患的實驗室結果可用時，有可能需要將實驗室結果傳送至數個其他系統。 這些更新是未經要求的更新通知回應。  
  
## <a name="queries"></a>查詢  
 在查詢時，需要資訊的應用程式會將查詢傳送至另一個應用程式，並接收應用程式回應查詢。 比方說，一個配藥應用程式可能會傳送包含訂單項目 (CPOE) 系統病患的 ID 編號的要求訊息並接收回應，其中包含必要的資料，以允許訂單處理。 此要求的交易的查詢，而且不同於來路不明的更新。 在回應中包含兩個應用程式之間流動的資訊。 回應本身不需要使用第四個訊息的通知。 不過，修改這在某些環境中以回應的通知。 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 如果如此設定，以通知回應。 如需查詢/回應交換的範例，請參閱 <<c0> [ 詢問式教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [驗證訊息](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)