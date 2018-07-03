---
title: 執行多個 Web 服務範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765d9785bde94f363ea56178f3cc0f500381d4e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997519"
---
# <a name="running-the-multiple-web-services-sample"></a><span data-ttu-id="0309a-102">執行多個 Web 服務範例</span><span class="sxs-lookup"><span data-stu-id="0309a-102">Running the Multiple Web Services Sample</span></span>
<span data-ttu-id="0309a-103">多個 Web 服務範例會使用路線入口範例提供的 Windows Forms 測試用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="0309a-103">The Multiple Web Services sample uses the Windows Forms test client application provided with the Itinerary On-Ramp sample.</span></span>  
  
 <span data-ttu-id="0309a-104">**若要執行多個 Web 服務範例**</span><span class="sxs-lookup"><span data-stu-id="0309a-104">**To run the Multiple Web Services sample**</span></span>  
  
1. <span data-ttu-id="0309a-105">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="0309a-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2. <span data-ttu-id="0309a-106">在 Windows 檔案總管中，開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 名為 Esb.Itinerary.Test.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0309a-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3. <span data-ttu-id="0309a-107">清除**使用 WCF 服務**核取方塊，以便可以利用用戶端路線。</span><span class="sxs-lookup"><span data-stu-id="0309a-107">Clear the **Use WCF Service** check box, so that a client-side itinerary can be utilized.</span></span>  
  
4. <span data-ttu-id="0309a-108">按一下 **負載路線**按鈕，然後再選取其中一個 \Source\Samples\MultipleWebServices\Itineraries 資料夾中的範例路線。</span><span class="sxs-lookup"><span data-stu-id="0309a-108">Click the **Load Itinerary** button, and then select one of the sample itineraries located in the \Source\Samples\MultipleWebServices\Itineraries folder.</span></span>  
  
5. <span data-ttu-id="0309a-109">選取 **兩個方式服務**核取方塊，讓應用程式會執行雙向路線服務作業。</span><span class="sxs-lookup"><span data-stu-id="0309a-109">Select the **Two Way Service** check box so the application will perform a two-way itinerary services operation.</span></span>  
  
6. <span data-ttu-id="0309a-110">按一下  **LoadMessage**按鈕，然後再選取 從 \Source\Samples\Itinerary\Test\Data 資料夾的 NAOrderDoc.xml 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="0309a-110">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7. <span data-ttu-id="0309a-111">按一下 [ **SubmitRequest** ] 按鈕，將要求傳送至路線入口匝服務。</span><span class="sxs-lookup"><span data-stu-id="0309a-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="0309a-112">等候回應訊息才會出現在**結果** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="0309a-112">Wait for a response message to appear in the **Result** box.</span></span>  
  
   <span data-ttu-id="0309a-113">多個 Web 服務範例如何使用 ESB 路線服務的相關資訊，請參閱[多個 Web 服務範例運作方式](../esb-toolkit/how-the-multiple-web-services-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="0309a-113">For information about how the Multiple Web Services sample uses the ESB Itinerary service, see [How the Multiple Web Services Sample Works](../esb-toolkit/how-the-multiple-web-services-sample-works.md).</span></span>