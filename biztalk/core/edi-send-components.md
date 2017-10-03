---
title: "EDI 傳送元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce270db-a573-48b3-be15-0178a5b7785b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5520a0c1dd0a6ef7e42818314a9f87733aebcb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-send-components"></a>EDI 傳送元件
本主題所介紹的管線和管線元件，會處理不屬於 EDI/AS2 訊息的 EDI 訊息。 如需傳送 EDI/AS2 或非 EDI/AS2 訊息的資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。 請注意，除了執行 AS2 處理之外，AS2 傳送元件也會執行 EDI 處理。  
  
## <a name="edi-send-pipeline"></a>EDI 傳送管線  
 EDI 傳送處理會在下列 EDISend 管線中執行。 這個管線會安裝在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 的 `Microsoft.BizTalk.Edi.EdiPipelines.dll` 中。  
  
 **EDISend 管線**  
  
 這個管線會產生和傳送 EDI 訊息。 它不會處理透過 HTTP 接收的 AS2 編碼 EDI 訊息。 AS2 編碼 EDI 訊息的處理是由 AS2 管線執行的。 AS2 傳送管線會使用 EDI 管線所使用的相同元件來處理 EDI 訊息。  
  
> [!NOTE]
>  不支援從協調流程執行 EDISend 管線。  
  
> [!NOTE]
>  AS2EDISend 管線會產生 EDI 訊息，並透過 AS2 傳輸來傳送。 如需詳細資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。  
  
 此管線是由 EDI 組合器管線元件組成：  
  
## <a name="edi-send-pipeline-component"></a>EDI 傳送管線元件  
 EDISend 管線會使用 EDI 組合器管線元件。 此元件安裝在`Microsoft.BizTalk.Edi.PipelineComponents.dll`中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]管線元件\\。  
  
 EDI 組合器會執行 EDISend 管線中大多數針對 EDI 編碼交換的處理作業。 EDI 組合器如何處理 EDI 訊息的詳細資訊，請參閱[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。