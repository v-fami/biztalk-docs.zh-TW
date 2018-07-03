---
title: 使用傳送埠作為路線服務訂閱者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 898b461c-4d0d-4703-a8ca-7f52f3f15f70
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8cf33ab303127ba369a619637abf455c80ee539
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018725"
---
# <a name="using-a-send-port-as-an-itinerary-service-subscriber"></a><span data-ttu-id="8f31c-102">使用傳送埠作為路線服務訂閱者</span><span class="sxs-lookup"><span data-stu-id="8f31c-102">Using a Send Port as an Itinerary Service Subscriber</span></span>
<span data-ttu-id="8f31c-103">如何使用傳送埠作為路線服務訂閱者的範例，圖 1 顯示的動態單向傳送連接埠挑選符合下列條件的訊息篩選條件：</span><span class="sxs-lookup"><span data-stu-id="8f31c-103">As an example of how to use a send port as an itinerary service subscriber, Figure 1 shows the filter conditions for a dynamic one-way sent port that picks up messages that meet the following conditions:</span></span>  
  
- <span data-ttu-id="8f31c-104">**IsRequestResponse = False**</span><span class="sxs-lookup"><span data-stu-id="8f31c-104">**IsRequestResponse = False**</span></span>  
  
- <span data-ttu-id="8f31c-105">**ServiceName = DynamicTest**</span><span class="sxs-lookup"><span data-stu-id="8f31c-105">**ServiceName = DynamicTest**</span></span>  
  
- <span data-ttu-id="8f31c-106">**ServiceState = 暫止**</span><span class="sxs-lookup"><span data-stu-id="8f31c-106">**ServiceState = Pending**</span></span>  
  
- <span data-ttu-id="8f31c-107">**ServiceType = 傳訊**</span><span class="sxs-lookup"><span data-stu-id="8f31c-107">**ServiceType = Messaging**</span></span>  
  
  <span data-ttu-id="8f31c-108">![傳送埠](../esb-toolkit/media/ch4-sendport.gif "第 4 章第傳送埠")</span><span class="sxs-lookup"><span data-stu-id="8f31c-108">![Send Port](../esb-toolkit/media/ch4-sendport.gif "Ch4-SendPort")</span></span>  
  
  <span data-ttu-id="8f31c-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="8f31c-109">**Figure 1**</span></span>  
  
  <span data-ttu-id="8f31c-110">**傳送埠篩選條件的範例**</span><span class="sxs-lookup"><span data-stu-id="8f31c-110">**Example of send port filters**</span></span>  
  
  <span data-ttu-id="8f31c-111">您可以使用傳送埠篩選條件運算式來指定它將會從透過路線入口匝 Messagebox 資料庫挑選的訊息的屬性和值組。</span><span class="sxs-lookup"><span data-stu-id="8f31c-111">Use send port filter expressions to specify the property and value sets of messages it will pick up from the Message Box database through the itinerary on-ramp.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f31c-112">請務必使用特定且盡可能; 具有焦點的篩選條件否則，就挑出非預期的訊息，在高容量環境中可能會造成問題的風險。</span><span class="sxs-lookup"><span data-stu-id="8f31c-112">It is important to use filter conditions that are as specific and focused as possible; otherwise, there is a risk of picking up unintended messages, which could cause problems in a high-volume environment.</span></span> <span data-ttu-id="8f31c-113">系統 Properties.xsd 的結構描述定義的篩選內容的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="8f31c-113">The schema System-Properties.xsd defines the filter properties of subscriptions.</span></span>