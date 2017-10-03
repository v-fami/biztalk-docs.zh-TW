---
title: "SWIFT 接收配接器架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16f32689-0b70-4389-8596-991fd776f185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aca9b5ef1fd1130feeebad3ec6fdf072d3bf88d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-architecture"></a>SWIFT 接收配接器架構
在 BizTalk Server 中，接收配接器會裝載於自己的記憶體空間，這表示不同的處理序是用來執行主機內。 此主機未繁衍 SWIFTNet 連結 (SNL) 組態中定義的子系統。  
  
 伺服器可執行檔會設定為 SNL 組態 (paramfile) 中的子系統，並產生藉由執行 SWIFTNet 啟動命令。 SNL 伺服器應用程式便會終止執行 SWIFTNet 停止命令。 SNL 管理伺服器可執行檔的存留期間。  
  
> [!NOTE]
>  服務局案例需要服務在其自己的安全性內容下執行的多個 SWIFT 成員介面卡。 藉由設定個別支援此接收位置，每個成員和繁衍 （spawn） 的伺服器可執行檔的多個執行個體，每一部專門用於其中一個接收位置。  
  
 在 BizTalk Server 中，接收配接器支援下列通訊模式與 「 BizTalk 傳訊引擎互動：  
  
-   其中一種方式 — 接收配接器 （伺服器） 正在延遲模式下運作時，就需要此模式。 在延遲模式中，配接器會傳送內送訊息的預設通知。 通知的預設值可以設定在配接器屬性。 可以透過傳送配接器的 LOB 應用程式稍後傳送商務層級回應。  
  
    > [!NOTE]
    >  發生延遲模式中，所有的值必須被填滿在配接器組態中，因為配接器做為建構回應。  
  
-   要求回應 — 在此模式中，配接器提交至 BizTalk 來自 SWIFT 要求並等候回應。 如果從 LOB 應用程式沒有回應，配接器將會逾時。 逾時值是在配接器組態中設定的。 預設值為 60 秒。  
  
     接收配接器可以只在一個執行緒上，以接收來自 SNL 回呼。 這表示，接收配接器可以進一步從接收訊息 SNL 只有在送出第一個訊息之後。 因此，預設批次大小是設定為 1。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)  
  
-   [SWIFT 接收配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)  
  
-   [SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)  
  
-   [SWIFT 接收配接器同步與延遲模式](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)  
  
-   [SWIFT 接收配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)