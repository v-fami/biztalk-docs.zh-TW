---
title: InterAct 配接器訊息進行商務交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b443b8a-4e56-47f1-8d91-5c807fd54ccc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea8e7d4f4ed8397c88a3cf21280352b446d629c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020150"
---
# <a name="interact-adapter-messages-for-business-exchange"></a>商務交換的 interAct 配接器訊息
InterAct 配接器端對端循環中有四個訊息。 這些訊息是 SWIFTNet 基本型別。 第一個和最後一個訊息會包含用戶端的基本項目、 SwInt:ExchangeRequest 和 SwInt:ExchangeResponse。 中間的兩個訊息包含的伺服器端基本類型、 SwInt:HandleRequest 和 SwInt:HandleResponse。  
  
 在此層級的簡化方式，有六個步驟中的端對端訊息週期：  
  
1. 用戶端應用程式會準備要求訊息。  
  
2. 用戶端應用程式會將要求訊息給 SWIFTNet。  
  
3. SWIFTNet 處理要求訊息，並將它傳送至伺服器應用程式。  
  
4. 伺服器應用程式從 SWIFTNet 接收要求訊息。  
  
5. 伺服器應用程式會準備回應訊息。  
  
6. 伺服器應用程式會將回應訊息給 SWIFTNet。  
  
7. SWIFTNet 處理回應訊息，並將它傳送至用戶端應用程式。  
  
8. 用戶端應用程式從 SWIFTNet 接收回應訊息。  
  
   下圖顯示 InterAct 訊息交換。  
  
   ![InterAct 訊息交換](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")  
  
## <a name="see-also"></a>另請參閱  
 [InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct 配接器儲存和轉寄](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [InterAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct 配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)