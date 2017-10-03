---
title: "處理內送的批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f47903-933a-4bde-b320-f7689c3d8366
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca3781d9b7c1ed2190a8334f272c04d304669ace
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-incoming-batches"></a>處理內送批次
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收批次處理的 EDI 交換時，可以將交換分割為其交易集、以個別的方式處理每個交易集，或保留交換，以群組的方式處理所有的交易集。  
  
 決定批次中處理**本機主機設定**中的單向協議索引標籤頁面**協議屬性**適用於 X12 和 EDIFACT 協議 對話方塊。 保留交換時，您可以選擇發生錯誤時要擱置交換或交易集。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [分割批次的 EDI 交換](../core/splitting-a-batched-edi-interchange.md)  
  
-   [分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)  
  
-   [保留收到的批次 EDI 交換](../core/preserving-a-received-batched-edi-interchange.md)