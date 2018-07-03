---
title: 若要了解 WCF LOB 配接器 SDK 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99002b01-da8a-483e-ada3-1ffbe9cd7357
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e98ba2cd875df0def595f55786990d64b9234288
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011055"
---
# <a name="tutorials-to-learn-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="3e391-102">若要了解 WCF LOB 配接器 SDK 教學課程</span><span class="sxs-lookup"><span data-stu-id="3e391-102">Tutorials to learn the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="3e391-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]教學課程包含有關如何使用資訊[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]開發功能豐富的企業配接器，以協助您在企業內部的企業應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="3e391-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tutorials contain information about how you can use [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to develop feature-rich line of business adapters to facilitate enterprise application integration within your enterprise.</span></span> <span data-ttu-id="3e391-104">藉由使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，operations 主控台和您所公開的資料可供任何應用程式可以取用 WCF 繫結，包括[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3e391-104">By using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the operations and data you expose can be consumed by any application that can consume a WCF binding, including [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3e391-105">教學課程包含簡單的範例，專為一組預先定義的作業。</span><span class="sxs-lookup"><span data-stu-id="3e391-105">The tutorials contain simple examples built around a set of predefined operations.</span></span> <span data-ttu-id="3e391-106">您不需要能夠完成這些教學課程的商務系統中實際的一行。</span><span class="sxs-lookup"><span data-stu-id="3e391-106">You do not need an actual line of business system available to complete these tutorials.</span></span> <span data-ttu-id="3e391-107">不過，在教學課程中提供詳細資料可以從了解中繼資料寫入輸出的處理常式和更新版本套用至您的配接器開發需求。</span><span class="sxs-lookup"><span data-stu-id="3e391-107">However, details provided in the tutorials can be applied to your adapter development needs, from understanding metadata to writing outbound handlers and beyond.</span></span>  

> [!TIP]
> <span data-ttu-id="3e391-108">已完成的 Echo 配接器的 BizTalk 安裝檔案隨附`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。</span><span class="sxs-lookup"><span data-stu-id="3e391-108">The completed Echo Adapter is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
 <span data-ttu-id="3e391-109">使用下列的教學課程來了解如何使用的重要部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3e391-109">Use the following tutorials to learn how to use key parts of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span></span>  
  
- <span data-ttu-id="3e391-110">[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3e391-110">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="3e391-111">提供建立配接器會公開從一組預先定義的方法做為各種商務系統的字串作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="3e391-111">Provides step-by-step instructions for creating an adapter that exposes string operations from a set of predefined methods that act as the line of business system.</span></span> <span data-ttu-id="3e391-112">配接器會提供許多常見的處理常式中實作[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包括搜尋、 瀏覽、 輸入和輸出作業。</span><span class="sxs-lookup"><span data-stu-id="3e391-112">The adapter provides an implementation for many of the common handlers in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] including search, browse, inbound and outbound operations.</span></span> <span data-ttu-id="3e391-113">在成功完成本教學課程時，您會有功能的介面卡。</span><span class="sxs-lookup"><span data-stu-id="3e391-113">At the successful completion of this tutorial, you will have a functional adapter.</span></span>  
  
- <span data-ttu-id="3e391-114">[教學課程 2： 使用 Echo 配接器，從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。</span><span class="sxs-lookup"><span data-stu-id="3e391-114">[Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).</span></span> <span data-ttu-id="3e391-115">若是使用 Echo 配接器開發中，提供逐步指示[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)從.NET 專案。</span><span class="sxs-lookup"><span data-stu-id="3e391-115">Provides step-by-step instructions for consuming the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) from a .NET project.</span></span> <span data-ttu-id="3e391-116">您會新增至新的專案中，配接器服務參考，並提供程式碼來測試 Echo 配接器的輸入和輸出作業。</span><span class="sxs-lookup"><span data-stu-id="3e391-116">You will add an adapter service reference to a new project, and provide code to test the inbound and outbound operations of the Echo Adapter.</span></span>  
  
- <span data-ttu-id="3e391-117">[教學課程 3： 裝載 Echo 配接器在 IIS 中的](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="3e391-117">[Tutorial 3: Hosting the Echo Adapter in IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md).</span></span> <span data-ttu-id="3e391-118">提供逐步指示，針對中裝載 Echo 配接器開發[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在網際網路資訊服務 (IIS) 處理。</span><span class="sxs-lookup"><span data-stu-id="3e391-118">Provides step-by-step instructions for hosting the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="3e391-119">您也會建立簡單的用戶端應用程式來取用 EchoString 作業的裝載配接器使用 svcutil.exe （ServiceModel 中繼資料公用程式）。</span><span class="sxs-lookup"><span data-stu-id="3e391-119">You will also use svcutil.exe (ServiceModel Metadata Utility) to create a simple client application to consume the EchoString operation of the hosted adapter.</span></span>  
  
  <span data-ttu-id="3e391-120">這些教學課程提供結構化的方法，來了解一些重要功能[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3e391-120">These tutorials provide a structured approach to understanding some of the key features of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="3e391-121">不需要知道已完成[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]或[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3e391-121">They can be completed with no knowledge of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] or [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="3e391-122">不過，您將了解多個如果您了解配接器設計背後的概念，並了解如何在可促進配接器設計[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3e391-122">However, you will learn more if you understand the concepts behind adapter design, and understand how adapter design is facilitated in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="3e391-123">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="3e391-123">For more information, see:</span></span>  
  
- [<span data-ttu-id="3e391-124">一般的開發人員工作，針對 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="3e391-124">Common Developer Tasks for the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/common-developer-tasks-for-the-wcf-lob-adapter-sdk.md)  
  
- [<span data-ttu-id="3e391-125">WCF LOB 配接器 SDK 的重要元件</span><span class="sxs-lookup"><span data-stu-id="3e391-125">Key Components of the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/key-components-of-the-wcf-lob-adapter-sdk.md)  
  
  <span data-ttu-id="3e391-126">這些教學課程之前，您應該檢閱中的需求[您開始教學課程之前](../../core/before-you-begin-the-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="3e391-126">Before you begin these tutorials, you should review the requirements in [Before You Begin the Tutorials](../../core/before-you-begin-the-tutorial.md).</span></span>  
  
 
## <a name="in-this-section"></a><span data-ttu-id="3e391-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e391-127">In This Section</span></span>  
  
-   [<span data-ttu-id="3e391-128">開始教學課程之前</span><span class="sxs-lookup"><span data-stu-id="3e391-128">Before You Begin the Tutorials</span></span>](../../core/before-you-begin-the-tutorial.md)  
  
-   [<span data-ttu-id="3e391-129">教學課程 1：開發 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="3e391-129">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)  
  
-   [<span data-ttu-id="3e391-130">教學課程 2：從 .NET 使用 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="3e391-130">Tutorial 2: Consume the Echo Adapter from .NET</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)  
  
-   [<span data-ttu-id="3e391-131">教學課程 3：在 IIS 中裝載 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="3e391-131">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e391-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e391-132">See Also</span></span>  
 [<span data-ttu-id="3e391-133">開始使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3e391-133">Getting started with BizTalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)