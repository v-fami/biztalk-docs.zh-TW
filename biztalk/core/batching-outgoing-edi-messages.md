---
title: "批次處理外寄 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a2bd68-4974-4927-938a-8eaf8f007566
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f95ed755dcc709084d52c6fb8b207e9bbd9e866d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batching-outgoing-edi-messages"></a>批次處理外寄 EDI 訊息
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會批次處理 EDI 交易集，前提是已經針對與接收它之商業夥伴相關聯的協議來啟用批次處理。 協議的 EDI 屬性可讓您執行下列作業：  
  
-   定義多個外寄批次  
  
-   定義交換  
  
-   定義交換內的群組  
  
-   設定批次釋放準則  
  
-   設定批次啟動準則。  
  
 Microsoft [!INCLUDE[prague](../includes/prague-md.md)] EDI 和 AS2 可處理下列 EDI 交換：  
  
-   EDI 交換可包含交易集和 (或) 通知。  
  
-   EDI 接收管線可將交換分割成 XML 交易集以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進一步處理，也可以保留交換，再以其所接收的格式傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   EDI 路由協調流程可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將單一交易集批次處理成多個外寄交換。  
  
-   EDI 批次處理協調流程會將 XML 交易集組合成 EDI 交換，並根據協議的 EDI 屬性驗證和傳遞交換。  
  
 EDI 批次 (稱為交換) 包含訊息群組，而訊息群組包含個別訊息。 外寄批次可包含多個群組，但每種文件類型只能有一個群組。 一個群組可以包含多個交易集，但每個交易集的文件類型都必須相同。 訊息信封是用來包裝個別交易集、個別群組和整個交換。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定外寄批次](../core/configuring-an-outgoing-batch.md)  
  
-   [組合批次的 EDI 交換](../core/assembling-a-batched-edi-interchange.md)  
  
-   [傳送保留批次交換](../core/sending-a-preserved-batch-interchange.md)