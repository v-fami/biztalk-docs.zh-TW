---
title: "執行 「 訊息豐富 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7015a2fe-3727-48f3-a2ed-c368e0630626
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4ed3b3ebc24a908dfefd70711db0d40638c2d3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-message-enrichment-sample"></a>執行 「 訊息豐富 」 範例
「 訊息豐富 」 範例會使用路線上手範例隨附的 Windows Form 測試用戶端應用程式。  
  
 **若要執行訊息豐富 」 範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。安裝所在的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 [名為 Esb.Itinerary.Test.exe 應用程式。  
  
3.  清除**使用 WCF 服務**核取方塊，以便可以利用用戶端路線。  
  
4.  按一下**負載路線**按鈕，然後再選取其中一個 \Source\Samples\MessageEnrichment\Itineraries 資料夾中的範例預定行程。  
  
5.  按一下**LoadMessage**按鈕，然後再從 \Source\Samples\MessageEnrichment\Test\ 資料夾選取 OrderDoc.xml 範例訊息。  
  
6.  按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。  
  
7.  瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out\\%MessageID%.xml 以查看輸出訊息。  
  
 「 訊息豐富 」 範例的運作方式的詳細資訊，請參閱[訊息擴充範例的運作方式](../esb-toolkit/how-the-message-enrichment-sample-works.md)。