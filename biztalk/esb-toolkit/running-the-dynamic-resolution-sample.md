---
title: "執行動態解析範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933839f-13e6-4b49-9838-2773e3f99b64
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e613934c44db03cf29edbf3fff4ef34d6b946577
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-dynamic-resolution-sample"></a><span data-ttu-id="5e7fc-102">執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="5e7fc-102">Running the Dynamic Resolution Sample</span></span>
<span data-ttu-id="5e7fc-103">若要執行其中一個使用案例範例，您將適當的 Microsoft BizTalk 繫結檔案匯入 GlobalBank.ESB BizTalk 應用程式然後放置範例輸入資料夾的適當的訊息或呼叫範例 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-103">To execute one of the use case examples, you import the appropriate Microsoft BizTalk binding file into the GlobalBank.ESB BizTalk application and then either drop a suitable message into the sample input folder or call the sample Web service.</span></span> <span data-ttu-id="5e7fc-104">動態解析範例支援兩種主要案例：</span><span class="sxs-lookup"><span data-stu-id="5e7fc-104">The Dynamic Resolution sample supports two main scenarios:</span></span>  
  
-   <span data-ttu-id="5e7fc-105">[動態解析範例單向傳訊案例](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-105">[One-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="5e7fc-106">動態解析範例支援此案例中使用與發行集的檔案放置資料夾會指向 Microsoft BizTalk。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-106">The Dynamic Resolution sample supports this scenario using a file drop folder as the publication point into Microsoft BizTalk.</span></span>  
  
-   <span data-ttu-id="5e7fc-107">[動態解析範例的雙向傳訊案例](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-107">[Two-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="5e7fc-108">動態解析範例支援此案例中使用位於與發行集的 http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx NorthAmerican Web 服務點至 BizTalk。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-108">The Dynamic Resolution sample supports this scenario using the NorthAmerican Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx as the publication point into BizTalk.</span></span>  
  
 <span data-ttu-id="5e7fc-109">若要了解此範例會使用 「 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例的運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="5e7fc-109">To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span></span>