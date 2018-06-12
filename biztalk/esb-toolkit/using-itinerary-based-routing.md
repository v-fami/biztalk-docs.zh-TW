---
title: 使用行程為基礎的路由 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0e0dad0f49e07c0941614dd0130d0e77c459ab
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34848982"
---
# <a name="using-itinerary-based-routing"></a><span data-ttu-id="5d9e9-102">使用行程為基礎的路由</span><span class="sxs-lookup"><span data-stu-id="5d9e9-102">Using Itinerary-Based Routing</span></span>
<span data-ttu-id="5d9e9-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供行程為基礎之訊息路由，方法是實作傳閱名單模式，以啟用案例時的處理順序的特定訊息的步驟不知道在設計階段，且每個訊息會有所不同。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides itinerary-based message routing by implementing the Routing Slip pattern to enable scenarios when the sequence of processing steps for a particular message is not known at design time and may vary for each message.</span></span> <span data-ttu-id="5d9e9-104">此模式的實作用於路由 slip 代表集合，這些步驟，以 XML 格式，並判斷必須在執行階段期間發生的步驟。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-104">The implementation of this pattern uses a routing slip to represent a collection of these steps in XML format and determines which steps need to occur during at run time.</span></span> <span data-ttu-id="5d9e9-105">路由名單，通常稱為 「 ESB 行程 」，狀態為已排序的集合的宣告式定義必須在處理的訊息執行的步驟的指示[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件和 BizTalk Server 執行階段。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-105">A state of the routing slip, frequently referred to as an "ESB itinerary," is an ordered set of declarative instructions that define the steps that must be executed for a message as it is being processed by [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] components and the BizTalk Server runtime.</span></span> <span data-ttu-id="5d9e9-106">ESB 行程中指定特定的處理指示聯[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件，也稱為 「 ESB 路線服務 」。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-106">A particular processing instruction specified in ESB itinerary is associated with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] component, which is also referred to as the "ESB itinerary service."</span></span> <span data-ttu-id="5d9e9-107">ESB 路線服務的目的是要執行的處理指示，並更新路由 slip 表示暫止的指示下一個狀態。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-107">The purpose of the ESB itinerary service is to execute the processing instructions and to update the state of the routing slip to indicate the next pending instruction.</span></span>  
  
 <span data-ttu-id="5d9e9-108">本章節描述的行程為基礎的處理功能[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d9e9-108">This section describes the itinerary-based processing features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="5d9e9-109">它包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="5d9e9-109">It contains the following topics:</span></span>  
  
-   [<span data-ttu-id="5d9e9-110">ESB 路線管理</span><span class="sxs-lookup"><span data-stu-id="5d9e9-110">ESB Itinerary Management</span></span>](../esb-toolkit/esb-itinerary-management.md)  
  
-   [<span data-ttu-id="5d9e9-111">入口和出口</span><span class="sxs-lookup"><span data-stu-id="5d9e9-111">On-Ramps and Off-Ramps</span></span>](../esb-toolkit/on-ramps-and-off-ramps.md)  
  
-   [<span data-ttu-id="5d9e9-112">選擇傳訊與協調流程路線服務</span><span class="sxs-lookup"><span data-stu-id="5d9e9-112">Choosing Between Messaging and Orchestration Itinerary Services</span></span>](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  
  
-   [<span data-ttu-id="5d9e9-113">使用管線元件選取現有路線</span><span class="sxs-lookup"><span data-stu-id="5d9e9-113">Using a Pipeline Component to Select an Existing Itinerary</span></span>](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  
  
-   [<span data-ttu-id="5d9e9-114">使用管線元件讀取路線</span><span class="sxs-lookup"><span data-stu-id="5d9e9-114">Using a Pipeline Component to Read an Itinerary</span></span>](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  
  
-   [<span data-ttu-id="5d9e9-115">使用管線元件快取請求-回應的路線</span><span class="sxs-lookup"><span data-stu-id="5d9e9-115">Using a Pipeline Component to Cache an Itinerary for Solicit-Response</span></span>](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  
  
-   [<span data-ttu-id="5d9e9-116">建立路線訂閱者</span><span class="sxs-lookup"><span data-stu-id="5d9e9-116">Creating Itinerary Subscribers</span></span>](../esb-toolkit/creating-itinerary-subscribers.md)  
  
-   [<span data-ttu-id="5d9e9-117">執行路線服務</span><span class="sxs-lookup"><span data-stu-id="5d9e9-117">Executing an Itinerary Service</span></span>](../esb-toolkit/executing-an-itinerary-service.md)  
  
-   <span data-ttu-id="5d9e9-118">超連結"http://msdn.microsoft.com/library/ee236752(BTS.10).aspx"[行程為基礎的路由成品](../esb-toolkit/itinerary-based-routing-artifacts.md)</span><span class="sxs-lookup"><span data-stu-id="5d9e9-118">HYPERLINK "http://msdn.microsoft.com/library/ee236752(BTS.10).aspx" [Itinerary-Based Routing Artifacts](../esb-toolkit/itinerary-based-routing-artifacts.md)</span></span>