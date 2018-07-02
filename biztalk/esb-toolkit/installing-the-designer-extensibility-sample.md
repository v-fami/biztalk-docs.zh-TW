---
title: 安裝設計工具擴充性範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eba13a4a-1b87-4268-af91-29af3a5bc5ef
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7068f86f3e6be2cd71741a6afe5f2438ac3800b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985711"
---
# <a name="installing-the-designer-extensibility-sample"></a><span data-ttu-id="14032-102">安裝設計工具擴充性範例</span><span class="sxs-lookup"><span data-stu-id="14032-102">Installing the Designer Extensibility Sample</span></span>
<span data-ttu-id="14032-103">本章節描述的程序安裝設計工具擴充性範例。</span><span class="sxs-lookup"><span data-stu-id="14032-103">This section describes the process for installing the Designer Extensibility sample.</span></span> <span data-ttu-id="14032-104">您必須安裝中的範例[安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)並[安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)安裝和使用此範例之前。</span><span class="sxs-lookup"><span data-stu-id="14032-104">You must install the samples in [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) before you install and use this sample.</span></span>  

 <span data-ttu-id="14032-105">**若要安裝的設計工具擴充性範例**</span><span class="sxs-lookup"><span data-stu-id="14032-105">**To install the Designer Extensibility sample**</span></span>  

1. <span data-ttu-id="14032-106">在 Windows 檔案總管中，開啟 資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 Microsoft Visual Studio 方案檔名為Extenders.Itinerary.OrchestrationSample.sln。</span><span class="sxs-lookup"><span data-stu-id="14032-106">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Microsoft Visual Studio solution file named Extenders.Itinerary.OrchestrationSample.sln.</span></span>  

2. <span data-ttu-id="14032-107">在 Visual Studio 中，按一下**建置方案**上**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="14032-107">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  

3. <span data-ttu-id="14032-108">關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="14032-108">Close Visual Studio.</span></span>  

4. <span data-ttu-id="14032-109">在 Windows 檔案總管中，開啟 資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 Visual Studio 方案檔名為Extenders.Resolvers.ResolverSample.sln。</span><span class="sxs-lookup"><span data-stu-id="14032-109">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Visual Studio solution file named Extenders.Resolvers.ResolverSample.sln.</span></span>  

5. <span data-ttu-id="14032-110">在 Visual Studio 中，按一下**建置方案**上**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="14032-110">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  

6. <span data-ttu-id="14032-111">關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="14032-111">Close Visual Studio.</span></span>  

7. <span data-ttu-id="14032-112">在 Windows 檔案總管中，開啟路線設計工具安裝路徑下的 \Lib 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14032-112">In Windows Explorer, open the \Lib folder under the Itinerary Designer install path.</span></span>  

8. <span data-ttu-id="14032-113">從先前步驟中建置的 Visual Studio 方案的 \bin\Debug 資料夾，將檔案複製 Extenders.Resolvers.ResolverSample.dll 和 Extenders.Itinerary.OrchestrationSample.dll \Lib 目錄。</span><span class="sxs-lookup"><span data-stu-id="14032-113">From the \bin\Debug folders of the Visual Studio solutions built in the preceding steps, copy the files Extenders.Resolvers.ResolverSample.dll and Extenders.Itinerary.OrchestrationSample.dll to the \Lib directory.</span></span>
