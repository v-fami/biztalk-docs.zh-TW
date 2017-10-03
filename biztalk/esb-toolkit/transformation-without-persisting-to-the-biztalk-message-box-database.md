---
title: "轉換而沒有保存到 BizTalk Messagebox 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f5b4caf-88e9-41dd-a644-e229e411a4a7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 407725509121948619e4eb05b583f6c8c1362f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transformation-without-persisting-to-the-biztalk-message-box-database"></a>轉換而沒有保存到 BizTalk Messagebox 資料庫
在此使用案例中，呼叫 Web 服務會執行即時訊息時，若要套用，適當的對應執行階段解析為基礎的轉換，並傳回已轉換的結果。 圖 1 所示處理程序的圖解的檢視。  
  
 ![轉換而沒有保存](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3 TransformationWithout")  
  
 **圖 1**  
  
 **將訊息轉換而沒有保存到 Microsoft BizTalk Server Messagebox 資料庫**  
  
 「 轉換服務 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 使用此模型中，您可以呼叫在 ESB 轉換服務這可讓您轉換和對應的測試和測試您所開發元件和 BizTalk Server 商務規則引擎中的原則。  
  
 如需詳細資訊，請參閱[安裝及執行 「 轉換服務 」 範例](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)。  
  
> [!NOTE]
>  請勿混淆與 BizTalk Server 轉換代理程式所執行的轉換動態作業在此稱為 Transformation Service。 轉換服務是高效能的 Web 服務，而不需要透過 Messagebox 資料庫會大幅降低藉由直接將 BizTalk Server 呼叫的延遲。