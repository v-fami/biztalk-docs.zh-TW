---
title: "InterAct 配接器用戶端應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdab4624-0fc2-42a3-9867-8f77e144b40c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac8f459799f59b63976c29f4a87dfe22b56e7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-client-application"></a>InterAct 配接器用戶端應用程式
互動配接器用戶端應用程式要求訊息是從用戶端應用程式用戶端 SWIFTNet 連結 (SNL) 傳遞的 XML 文件。 為用戶端上執行基本的 SWIFTNet 要求/回應的第一個部分，會發生此類型的訊息。  
  
 本主題描述 SwInt:ExchangeRequest 訊息。 它用於 「 同步 」 SWIFTNet 用戶端呼叫。 在此情況下，「 同步 」 表示函式呼叫中封鎖用戶端應用程式，強制等候從伺服器端應用程式收到的回應。 （或者，或者，就會發生錯誤狀況和該錯誤會回報給用戶端。）  
  
 密碼編譯的區塊 (SwSec:Crypto)，如果有的話，包含訊息簽署及/或驗證處理的結果。 此外，在特定的處理階段，它們可能會包含直接 SNL 所要執行的密碼編譯處理的指示。  
  
## <a name="interact-adapter-payload-format"></a>互動配接器裝載格式  
 要求承載包含獨特的商務訊息。 裝載的結構必須符合格式正確的 XML （這只是表示裝載不會中斷 XML 剖析，但是在這種情況，它沒有使用 XML 文件結構） 的需求。 如果套用 SWIFTNet 訊息驗證，則還有承載必須遵守其他結構化的需求。 除了，裝載結構和內容取決於商務應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [互動配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)