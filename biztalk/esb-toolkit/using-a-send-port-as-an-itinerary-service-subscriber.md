---
title: "為路線服務的訂閱者使用傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 898b461c-4d0d-4703-a8ca-7f52f3f15f70
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5213b22c1bdfaa505dbf4b62a03095bcec5a1746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-send-port-as-an-itinerary-service-subscriber"></a><span data-ttu-id="cc4e4-102">為路線服務的訂閱者使用傳送埠</span><span class="sxs-lookup"><span data-stu-id="cc4e4-102">Using a Send Port as an Itinerary Service Subscriber</span></span>
<span data-ttu-id="cc4e4-103">如需如何為路線服務的訂閱者使用的傳送埠的範例，圖 1 所示動態單向傳送埠拾取訊息符合下列條件的篩選條件：</span><span class="sxs-lookup"><span data-stu-id="cc4e4-103">As an example of how to use a send port as an itinerary service subscriber, Figure 1 shows the filter conditions for a dynamic one-way sent port that picks up messages that meet the following conditions:</span></span>  
  
-   <span data-ttu-id="cc4e4-104">**IsRequestResponse = False**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-104">**IsRequestResponse = False**</span></span>  
  
-   <span data-ttu-id="cc4e4-105">**ServiceName = DynamicTest**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-105">**ServiceName = DynamicTest**</span></span>  
  
-   <span data-ttu-id="cc4e4-106">**ServiceState = 暫止**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-106">**ServiceState = Pending**</span></span>  
  
-   <span data-ttu-id="cc4e4-107">**ServiceType = 傳訊**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-107">**ServiceType = Messaging**</span></span>  
  
 <span data-ttu-id="cc4e4-108">![傳送埠](../esb-toolkit/media/ch4-sendport.gif "第 4 章第傳送埠")</span><span class="sxs-lookup"><span data-stu-id="cc4e4-108">![Send Port](../esb-toolkit/media/ch4-sendport.gif "Ch4-SendPort")</span></span>  
  
 <span data-ttu-id="cc4e4-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="cc4e4-110">**傳送埠篩選條件的範例**</span><span class="sxs-lookup"><span data-stu-id="cc4e4-110">**Example of send port filters**</span></span>  
  
 <span data-ttu-id="cc4e4-111">您可以使用傳送埠篩選條件運算式來指定它將會從路線上手透過 Messagebox 資料庫拾取的訊息的屬性和值集合。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-111">Use send port filter expressions to specify the property and value sets of messages it will pick up from the Message Box database through the itinerary on-ramp.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc4e4-112">請務必使用特定且盡可能; 已取得焦點的篩選條件否則，會有的挑出非預期的訊息，在高容量環境中可能會造成問題的風險。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-112">It is important to use filter conditions that are as specific and focused as possible; otherwise, there is a risk of picking up unintended messages, which could cause problems in a high-volume environment.</span></span> <span data-ttu-id="cc4e4-113">系統 Properties.xsd 的結構描述定義的篩選條件屬性的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-113">The schema System-Properties.xsd defines the filter properties of subscriptions.</span></span>