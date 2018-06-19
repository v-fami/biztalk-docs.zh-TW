---
title: 轉換而沒有保存到 BizTalk Messagebox 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5b4caf-88e9-41dd-a644-e229e411a4a7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 407725509121948619e4eb05b583f6c8c1362f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294982"
---
# <a name="transformation-without-persisting-to-the-biztalk-message-box-database"></a><span data-ttu-id="ef12b-102">轉換而沒有保存到 BizTalk Messagebox 資料庫</span><span class="sxs-lookup"><span data-stu-id="ef12b-102">Transformation Without Persisting to the BizTalk Message Box Database</span></span>
<span data-ttu-id="ef12b-103">在此使用案例中，呼叫 Web 服務會執行即時訊息時，若要套用，適當的對應執行階段解析為基礎的轉換，並傳回已轉換的結果。</span><span class="sxs-lookup"><span data-stu-id="ef12b-103">In this use case, a call to a Web service performs real-time transformation of a message, based on run-time resolution of the appropriate map to apply, and returns the transformed result.</span></span> <span data-ttu-id="ef12b-104">圖 1 所示處理程序的圖解的檢視。</span><span class="sxs-lookup"><span data-stu-id="ef12b-104">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="ef12b-105">![轉換而沒有保存](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3 TransformationWithout")</span><span class="sxs-lookup"><span data-stu-id="ef12b-105">![Transformation Without Persisting](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3-TransformationWithout")</span></span>  
  
 <span data-ttu-id="ef12b-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="ef12b-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="ef12b-107">**將訊息轉換而沒有保存到 Microsoft BizTalk Server Messagebox 資料庫**</span><span class="sxs-lookup"><span data-stu-id="ef12b-107">**Transforming a message without persisting to the Microsoft BizTalk Server Message Box database**</span></span>  
  
 <span data-ttu-id="ef12b-108">「 轉換服務 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="ef12b-108">The Transformation Service sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="ef12b-109">使用此模型中，您可以呼叫在 ESB 轉換服務這可讓您轉換和對應的測試和測試您所開發元件和 BizTalk Server 商務規則引擎中的原則。</span><span class="sxs-lookup"><span data-stu-id="ef12b-109">By using it, you can call the ESB Transformation Service; this enables you to test transformations and mappings as you are developing components and policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="ef12b-110">如需詳細資訊，請參閱[安裝及執行 「 轉換服務 」 範例](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ef12b-110">For more information, see [Installing and Running the Transformation Service Sample](../esb-toolkit/installing-and-running-the-transformation-service-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef12b-111">請勿混淆與 BizTalk Server 轉換代理程式所執行的轉換動態作業在此稱為 Transformation Service。</span><span class="sxs-lookup"><span data-stu-id="ef12b-111">Do not confuse the Transformation Service referred to here with the dynamic transformation operations performed by the BizTalk Server Transformation Agent.</span></span> <span data-ttu-id="ef12b-112">轉換服務是高效能的 Web 服務，而不需要透過 Messagebox 資料庫會大幅降低藉由直接將 BizTalk Server 呼叫的延遲。</span><span class="sxs-lookup"><span data-stu-id="ef12b-112">The Transformation Service is a high-performance Web service that significantly reduces latency by calling directly into BizTalk Server without going through the Message Box database.</span></span>