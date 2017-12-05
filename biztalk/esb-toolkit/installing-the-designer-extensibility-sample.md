---
title: "安裝設計工具擴充性範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eba13a4a-1b87-4268-af91-29af3a5bc5ef
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea0cd71c22fdd614d2e49c996939b785ecadf8bd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-designer-extensibility-sample"></a><span data-ttu-id="227a1-102">安裝設計工具擴充性範例</span><span class="sxs-lookup"><span data-stu-id="227a1-102">Installing the Designer Extensibility Sample</span></span>
<span data-ttu-id="227a1-103">本章節描述設計工具擴充性範例的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="227a1-103">This section describes the process for installing the Designer Extensibility sample.</span></span> <span data-ttu-id="227a1-104">您必須安裝中的範例[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)和[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)您安裝及使用這個範例。</span><span class="sxs-lookup"><span data-stu-id="227a1-104">You must install the samples in [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) before you install and use this sample.</span></span>  
  
 <span data-ttu-id="227a1-105">**若要安裝的設計工具擴充性範例**</span><span class="sxs-lookup"><span data-stu-id="227a1-105">**To install the Designer Extensibility sample**</span></span>  
  
1.  <span data-ttu-id="227a1-106">在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 [Microsoft Visual Studio 方案檔名為Extenders.Itinerary.OrchestrationSample.sln。</span><span class="sxs-lookup"><span data-stu-id="227a1-106">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Microsoft Visual Studio solution file named Extenders.Itinerary.OrchestrationSample.sln.</span></span>  
  
2.  <span data-ttu-id="227a1-107">在 Visual Studio 中，按一下 **建置方案**上**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="227a1-107">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="227a1-108">關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="227a1-108">Close Visual Studio.</span></span>  
  
4.  <span data-ttu-id="227a1-109">在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 [Visual Studio 方案檔名為Extenders.Resolvers.ResolverSample.sln。</span><span class="sxs-lookup"><span data-stu-id="227a1-109">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Visual Studio solution file named Extenders.Resolvers.ResolverSample.sln.</span></span>  
  
5.  <span data-ttu-id="227a1-110">在 Visual Studio 中，按一下 **建置方案**上**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="227a1-110">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  
  
6.  <span data-ttu-id="227a1-111">關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="227a1-111">Close Visual Studio.</span></span>  
  
7.  <span data-ttu-id="227a1-112">在 Windows 檔案總管 中，開啟路線設計工具安裝路徑下的 \Lib 資料夾。</span><span class="sxs-lookup"><span data-stu-id="227a1-112">In Windows Explorer, open the \Lib folder under the Itinerary Designer install path.</span></span>  
  
8.  <span data-ttu-id="227a1-113">從先前步驟中建立 Visual Studio 方案的 \bin\Debug 資料夾，將檔案複製 Extenders.Resolvers.ResolverSample.dll 和 Extenders.Itinerary.OrchestrationSample.dll \Lib 目錄。</span><span class="sxs-lookup"><span data-stu-id="227a1-113">From the \bin\Debug folders of the Visual Studio solutions built in the preceding steps, copy the files Extenders.Resolvers.ResolverSample.dll and Extenders.Itinerary.OrchestrationSample.dll to the \Lib directory.</span></span>