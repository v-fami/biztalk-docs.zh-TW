---
title: 了解 FileAct 和互動的配接器架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f97a7fe-20df-4509-bb6e-53743c3a57df
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c04d0ba8b1c2bbd99a71e3d76c8d7ad60c251147
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223406"
---
# <a name="understanding-fileact-and-interact-adapter-architecture"></a>了解 FileAct 和互動的配接器架構
SWIFT 配接器是以 BizTalk 配接器架構為基礎。 使用 BizTalk Server 中的配接器的分類，快速的配接器，FileAct 和 InterAct，代表下列各項：  
  
-   自訂配接器。 這是為了與使用專屬的標準呼叫 FileAct 和 Interact 的 SWIFT 網路互動的自訂配接器。  
  
-   傳輸配接器。 此配接器可讓商務軟體應用程式來傳送和接收訊息的 SWIFT 網路。  
  
-   非交易。 配接器不會進行互動的 SWIFT 網路使用的任何交易物件。  
  
-   外掛式。 接收配接器執行個別的處理序中，並定期傳送配接器處理序中執行。  
  
 BizTalk 配接器架構的相關資訊，請參閱 < 什麼是配接器架構？ > 在 BizTalk Server 說明中的主題。  
  
 下圖顯示 FileAct 和 InterAct 架構的高階檢視。  
  
 ![](../../adapters-and-accelerators/fileact-interact/media/035ebb05-ce11-447c-b56b-ba8b41e07e50.gif "035ebb05-ce11-447c-b56b-ba8b41e07e50")  
  
> [!NOTE]
>  Microsoft[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]支援 strict 模式 SWIFTNet 連結 (SNL) API。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SWIFTNet 用戶端和伺服器](../../adapters-and-accelerators/fileact-interact/swiftnet-client-and-server.md)  
  
-   [SWIFT 傳送配接器架構](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)  
  
-   [SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)  
  
-   [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)  
  
-   [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)