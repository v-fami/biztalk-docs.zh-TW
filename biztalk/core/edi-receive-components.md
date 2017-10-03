---
title: "EDI 接收元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d3b82e8-1168-4c2c-bf1a-886b43ff8108
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc53f4c592b767c8061fb1ed8134636322b35b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-receive-components"></a>EDI 接收元件
本主題所介紹的管線和管線元件，會處理不屬於 EDI/AS2 訊息的 EDI 訊息。 收到的 EDI/AS2 或非 EDI/AS2 訊息的處理程序的相關資訊，請參閱[AS2 接收元件](../core/as2-receive-components.md)。 請注意，除了執行 AS2 處理之外，AS2 接收元件也會執行 EDI 處理。  
  
## <a name="edi-receive-pipeline"></a>EDI 接收管線  
 EDI 接收處理是在 EDI 接收管線中執行。 這個管線會安裝在 Microsoft.BizTalk.Edi.EdiPipelines.dll 中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。 這個管線會處理透過任何傳輸接的 EDI 訊息， 它不會處理透過 HTTP 接收的 AS2 編碼 EDI 訊息。 AS2 編碼 EDI 訊息的處理是由 AS2 管線執行的。 AS2 接收管線會使用 EDI 管線所使用的相同元件來處理 EDI 訊息。  
  
> [!NOTE]
>  若您建立使用 EDIReceive 管線並具有 HTTP 傳輸類型的接收位置，可能會發生安全性問題。 EDIReceive 管線不會產生 HTTP "200 OK" 通知。 若並未傳回 EDI 通知，則不會順利終止連線，而是會維持開啟。 如果超過逾時期間，則連線會逾時。  
  
 EDIReceive 管線包含下列管線元件：  
  
-   EDI 解譯器  
  
-   BatchMarker  
  
## <a name="edi-receive-pipeline-components"></a>EDI 接收管線元件  
 EDIReceive 接收管線會使用下列管線元件。 這些元件安裝在中的 microsoft.biztalk.edi.pipelinecomponents.dll 內[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]管線元件\\。  
  
### <a name="edi-disassembler"></a>EDI 解譯器  
 EDI 解譯器會執行 EDIReceive 管線中針對收到之 EDI 編碼交換的大多數處理作業。 EDI 解譯器如何處理 EDI 訊息的詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。  
  
### <a name="batchmarker"></a>BatchMarker  
 BatchMarker 管線元件會準備交換批次處理升級，將批次識別碼，ToBeBatched 和 ToBeRouted 內容屬性所需的處理批次的交換。 BatchMarker 元件設定這些屬性的方式，取決於多少交易夥伴協議訂閱批次項目。  
  
-   如果只有一個協議訂閱批次項目，BatchMarker 元件將 ToBeBatched 內容屬性設為 True，如此批次處理協調流程才能收取批次項目。  
  
-   如果一個以上的協議訂閱批次項目，BatchMarker 元件 ToBeRouted 內容屬性設定為 True，如此路由協調流程才能收取批次項目。 它也設定 Batchid 內容屬性，以空格分隔批次識別碼的清單。 路由協調流程將會讓批次項目的一個複本的每個批次識別碼，然後將 ToBeBatched 屬性設定為 True 的批次項目，每個複本上，讓批次處理協調流程會收取所有複本。  
  
 BatchMarker 元件會包含在 EDIReceive 管線的最後一個階段 （交易夥伴協議解析）。 所有將處理 EDI 訊息的管線都應該包含 BatchMarker 管線元件。  
  
> [!NOTE]
>  BatchMarker 元件可以包含在不包含 EDI 解譯器，才能執行交易夥伴協議解析，而不剖析 EDI 訊息的接收管線。  
  
 您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 BatchMarker 元件來批次處理非 EDI 訊息。 如需詳細資訊，請參閱 「 非 EDI 訊息在 BatchMarker 元件處理 > 一節[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)