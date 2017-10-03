---
title: "SWIFT 傳送配接器架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e52a5a21-0aa1-4cd9-a2a4-f9df425913a0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d772203c980495c5aa62266beb060693c1a8ad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-architecture"></a>SWIFT 傳送配接器架構
一般情況下，BizTalk Server 傳送配接器裝載於 BizTalk 服務處理序，Btsntsvc.exe 中。 這表示 BizTalk Server 管理配接器的存留期間。  
  
 有兩種方式將訊息傳送到的 SWIFT 網路： 同步的 (ExchangeRequest) 和非同步 （此版本並未實作）。 在 BizTalk Server 傳送配接器應支援下列通訊模式與 「 BizTalk 傳訊引擎互動：  
  
-   請求回應 — 訊息組，稱為基本項目與 SWIFT 網路種進行交換。 任何傳送至 SWIFT 的訊息必須是商務、 通知或錯誤的回應。 回應訊息提交至 messagebox。 這種作業模式用於即時通訊。  
  
-   其中一種方式傳送，配接器以其中一種方式進行設定時的儲存和轉送模式操作。 這些訊息會傳送到預先設定的佇列，而不是收件者。 寄件者可以擷取與佇列發送或提取模式中開啟工作階段的回應。  
  
> [!NOTE]
>  建立配接器的方式會影響它的運作的方式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SWIFT 傳送配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)  
  
-   [SWIFT 傳送配接器的動態傳送](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-dynamic-send.md)  
  
-   [SWIFT 傳送配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)  
  
-   [SWIFT 傳送配接器同步模式](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)  
  
-   [SWIFT 傳送配接器的終止](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)