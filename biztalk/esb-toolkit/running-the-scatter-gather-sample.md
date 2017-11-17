---
title: "執行分散-集中範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53676974-ea1f-4c95-9dbb-98fff92286fa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dcafa519aac074ccb339373a591b590846c9341
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-scatter-gather-sample"></a><span data-ttu-id="c854a-102">執行分散-集中範例</span><span class="sxs-lookup"><span data-stu-id="c854a-102">Running the Scatter-Gather Sample</span></span>
<span data-ttu-id="c854a-103">分散-集中範例會使用 Windows Form 測試用戶端應用程式隨附路線上手範例，示範此模式如何套用路線服務的功能。</span><span class="sxs-lookup"><span data-stu-id="c854a-103">The Scatter-Gather sample uses a the Windows Forms test client application provided with the Itinerary On-Ramp sample to demonstrate how this pattern applies the features of the Itinerary service.</span></span>  
  
 <span data-ttu-id="c854a-104">**若要執行分散-集中範例**</span><span class="sxs-lookup"><span data-stu-id="c854a-104">**To run the Scatter-Gather sample**</span></span>  
  
1.  <span data-ttu-id="c854a-105">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="c854a-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="c854a-106">在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。安裝所在的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 [名為 Esb.Itinerary.Test.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c854a-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="c854a-107">按一下**LoadItinerary**按鈕，然後再選取 範例路線名為 ScatterGatherItinerary.xml \Source\Samples\ScatterGather\Itineraries 資料夾中的。</span><span class="sxs-lookup"><span data-stu-id="c854a-107">Click the **LoadItinerary** button, and then select the sample itinerary named ScatterGatherItinerary.xml from the \Source\Samples\ScatterGather\Itineraries folder.</span></span>  
  
4.  <span data-ttu-id="c854a-108">清除**為要求回應**核取方塊，讓應用程式將會執行單向路線服務的作業。</span><span class="sxs-lookup"><span data-stu-id="c854a-108">Clear the **Is Request Response** check box so the application will perform a one-way itinerary services operation.</span></span>  
  
5.  <span data-ttu-id="c854a-109">（選擇性）設定**使用 WCF 服務**核取方塊，如果您想要使用 OnRamp.Itinerary.Response.WCF 應用程式接收位置而不使用預設 OnRamp.Itinerary.Response.SOAP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="c854a-109">(Optional) Set the **Use WCF Service** check box if you want the application to use the OnRamp.Itinerary.Response.WCF receive location instead of the default OnRamp.Itinerary.Response.SOAP receive location.</span></span>  
  
6.  <span data-ttu-id="c854a-110">按一下**LoadMessage**按鈕，然後再從 \Source\Samples\Itinerary\Test\Data 資料夾選取 NAOrderDoc.xml 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="c854a-110">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7.  <span data-ttu-id="c854a-111">按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。</span><span class="sxs-lookup"><span data-stu-id="c854a-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="c854a-112">開啟資料夾 \Source\Samples\DynamicResolution\Test\FileDrop\Out 以查看回應訊息。</span><span class="sxs-lookup"><span data-stu-id="c854a-112">Open the folder \Source\Samples\DynamicResolution\Test\FileDrop\Out to see the response message.</span></span>  
  
 <span data-ttu-id="c854a-113">如需如何散佈蒐集的範例使用 ESB 行程服務資訊，請參閱[分散-集中範例的運作方式](../esb-toolkit/how-the-scatter-gather-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="c854a-113">For information about how the Scatter Gather sample uses the ESB Itinerary service, see [How the Scatter-Gather Sample Works](../esb-toolkit/how-the-scatter-gather-sample-works.md).</span></span>