---
title: 配接器訊息互動的商務交換 |Microsoft 文件
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
ms.openlocfilehash: d19e10940e6a83c24e9397f0df94d0fc54e4da38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224598"
---
# <a name="interact-adapter-messages-for-business-exchange"></a>配接器訊息互動的商務交換
InterAct 配接器的端對端循環中有四種訊息。 這些訊息是 SWIFTNet 基本型別。 第一個和最後一個訊息是由用戶端基本型別、 SwInt:ExchangeRequest 與 SwInt:ExchangeResponse 組成。 伺服器端基本型別、 SwInt:HandleRequest 與 SwInt:HandleResponse 的各構成中間兩個訊息。  
  
 此層級的簡化，有六個步驟中的端對端訊息週期：  
  
1.  用戶端應用程式會準備要求訊息。  
  
2.  用戶端應用程式會將要求訊息傳遞至 SWIFTNet。  
  
3.  SWIFTNet 處理要求訊息，並將它傳送至伺服器應用程式。  
  
4.  伺服器應用程式從 SWIFTNet 接收要求訊息。  
  
5.  伺服器應用程式會準備回應訊息。  
  
6.  伺服器應用程式會將回應訊息傳遞至 SWIFTNet。  
  
7.  SWIFTNet 處理回應訊息，並將它傳送至用戶端應用程式。  
  
8.  用戶端應用程式從 SWIFTNet 接收回應訊息。  
  
 下圖顯示 InterAct 訊息交換。  
  
 ![InterAct 訊息交換](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)