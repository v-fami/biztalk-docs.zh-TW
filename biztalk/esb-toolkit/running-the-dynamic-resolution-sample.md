---
title: 執行動態解析範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c933839f-13e6-4b49-9838-2773e3f99b64
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66a61262bab3c3abeb7a4eb7113f09d8d3f7e8db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983127"
---
# <a name="running-the-dynamic-resolution-sample"></a><span data-ttu-id="6feb8-102">執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="6feb8-102">Running the Dynamic Resolution Sample</span></span>
<span data-ttu-id="6feb8-103">若要執行其中一個使用案例範例，您適當的 Microsoft BizTalk 繫結檔案匯入 GlobalBank.ESB BizTalk 應用程式，然後將適當的訊息放入範例輸入資料夾，或呼叫的範例 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="6feb8-103">To execute one of the use case examples, you import the appropriate Microsoft BizTalk binding file into the GlobalBank.ESB BizTalk application and then either drop a suitable message into the sample input folder or call the sample Web service.</span></span> <span data-ttu-id="6feb8-104">動態解析範例支援兩個主要案例：</span><span class="sxs-lookup"><span data-stu-id="6feb8-104">The Dynamic Resolution sample supports two main scenarios:</span></span>  
  
- <span data-ttu-id="6feb8-105">[動態解析範例的單向傳訊案例](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6feb8-105">[One-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="6feb8-106">此案例中使用與發行集的檔案放置資料夾移到 Microsoft BizTalk 動態解析範例的支援。</span><span class="sxs-lookup"><span data-stu-id="6feb8-106">The Dynamic Resolution sample supports this scenario using a file drop folder as the publication point into Microsoft BizTalk.</span></span>  
  
- <span data-ttu-id="6feb8-107">[動態解析範例的雙向傳訊案例](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6feb8-107">[Two-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="6feb8-108">動態解析範例支援此案例中使用 NorthAmerican Web 服務位於 http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx 與發行集點到 BizTalk。</span><span class="sxs-lookup"><span data-stu-id="6feb8-108">The Dynamic Resolution sample supports this scenario using the NorthAmerican Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx as the publication point into BizTalk.</span></span>  
  
  <span data-ttu-id="6feb8-109">若要了解此範例會使用 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="6feb8-109">To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span></span>