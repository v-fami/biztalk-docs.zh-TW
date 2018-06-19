---
title: 教學課程 2： 使用回應配接器從.NET |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e489c79-51b4-4067-9584-67c67f86aedd
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5291fc9e465476ea804cd8c46b1b53ea6c02d842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223646"
---
# <a name="tutorial-2-consume-the-echo-adapter-from-net"></a><span data-ttu-id="d7292-102">教學課程 2： 使用回應配接器從.NET</span><span class="sxs-lookup"><span data-stu-id="d7292-102">Tutorial 2: Consume the Echo Adapter from .NET</span></span>
<span data-ttu-id="d7292-103">本節提供使用從.NET 回應配接器所公開的輸入和輸出作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="d7292-103">This section gives the steps for consuming the inbound and outbound operations exposed by the Echo adapter from .NET.</span></span> <span data-ttu-id="d7292-104">回應配接器在開發[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d7292-104">The Echo adapter was developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7292-105">將回應配接器和測試程式碼隨附於 BizTalk 安裝檔案在`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。</span><span class="sxs-lookup"><span data-stu-id="d7292-105">The Echo Adapter and test code is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="d7292-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="d7292-106">In This Section</span></span>  
  
-   [<span data-ttu-id="d7292-107">步驟 1： 測試輸出回應配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="d7292-107">Step 1: Test Outbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md)  
  
-   [<span data-ttu-id="d7292-108">步驟 2： 測試輸入的回應配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="d7292-108">Step 2: Test Inbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7292-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7292-109">See Also</span></span>  
 <span data-ttu-id="d7292-110">[教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7292-110">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="d7292-111">WCF LOB 配接器 SDK 教學課程</span><span class="sxs-lookup"><span data-stu-id="d7292-111">WCF LOB Adapter SDK Tutorials</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)