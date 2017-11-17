---
title: "執行 SQL 配接器範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13566d08-7a59-4065-b0d7-19ae2765555e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf04c06a1ef96974912ce3affe278d5a98936325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-sql-adapter-sample"></a><span data-ttu-id="da867-102">執行 SQL 配接器範例</span><span class="sxs-lookup"><span data-stu-id="da867-102">Running the SQL Adapter Sample</span></span>
<span data-ttu-id="da867-103">SQL 配接器範例會使用路線上手範例隨附的 Windows Form 測試用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="da867-103">The SQL Adapter sample uses a Windows Forms test client application provided with the Itinerary On-Ramp sample.</span></span>  
  
 <span data-ttu-id="da867-104">**若要執行 SQL 配接器範例**</span><span class="sxs-lookup"><span data-stu-id="da867-104">**To run the SQL Adapter sample**</span></span>  
  
1.  <span data-ttu-id="da867-105">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="da867-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="da867-106">在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。安裝所在的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 [名為 Esb.Itinerary.Test.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="da867-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="da867-107">清除**使用 WCF 服務**核取方塊，以便可以使用用戶端路線。</span><span class="sxs-lookup"><span data-stu-id="da867-107">Clear the **Use WCF Service** check box so that a client-side itinerary can be used.</span></span>  
  
4.  <span data-ttu-id="da867-108">選取**兩個方式服務**選項</span><span class="sxs-lookup"><span data-stu-id="da867-108">Select the **Two Way Service** option</span></span>  
  
5.  <span data-ttu-id="da867-109">按一下**負載路線**按鈕，然後再選取其中一個位於資料夾 \Source\Samples\SqlAdapter \Itineraries 範例行程。</span><span class="sxs-lookup"><span data-stu-id="da867-109">Click the **Load Itinerary** button, and then select one of the sample itineraries located in the folder \Source\Samples\SqlAdapter \Itineraries.</span></span>  
  
6.  <span data-ttu-id="da867-110">按一下**LoadMessage**按鈕，然後再選取 在資料夾 \Source\Samples\SqlAdapter \Test OrderDoc.xml 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="da867-110">Click the **LoadMessage** button, and then select the OrderDoc.xml sample message in the folder \Source\Samples\SqlAdapter \Test.</span></span>  
  
7.  <span data-ttu-id="da867-111">按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。</span><span class="sxs-lookup"><span data-stu-id="da867-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span>  
  
8.  <span data-ttu-id="da867-112">請確定 GlobalBankESB database 之 Product 資料表中插入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="da867-112">Make sure one row is inserted in the Product table of the GlobalBankESB database.</span></span>  
  
 <span data-ttu-id="da867-113">SQL 配接器範例的運作方式的相關資訊，請參閱[SQL 配接器範例的運作方式](../esb-toolkit/how-the-sql-adapter-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="da867-113">For information about how the SQL Adapter sample works, see [How the SQL Adapter Sample Works](../esb-toolkit/how-the-sql-adapter-sample-works.md).</span></span>