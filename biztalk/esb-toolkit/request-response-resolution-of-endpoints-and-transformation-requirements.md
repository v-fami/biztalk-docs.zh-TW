---
title: 要求-回應的解析度，端點並轉換需求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1bfdae-2651-402c-b164-16db663aaa95
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72f442f1d9df457a3c1384f1d717e29c17b433f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294566"
---
# <a name="request-response-resolution-of-endpoints-and-transformation-requirements"></a><span data-ttu-id="0e943-102">要求-回應的端點和轉換需求的解決方式</span><span class="sxs-lookup"><span data-stu-id="0e943-102">Request-Response Resolution of Endpoints and Transformation Requirements</span></span>
<span data-ttu-id="0e943-103">在此使用情況下，用戶端應用程式會提交要求訊息至上手，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="0e943-103">In this use case, a client application submits a request message to an on-ramp and receives a response.</span></span> <span data-ttu-id="0e943-104">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]做為用戶端和目標服務端點之間的暫留處理器，並使用 ESB 解析器和配接器架構，執行動態訊息轉換和路由符合上手組態，如圖所示1。</span><span class="sxs-lookup"><span data-stu-id="0e943-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] acts as mediator between the client and the target service endpoint and uses the ESB Resolver and Adapter Framework to perform the dynamic message transformation and routing in accordance with the on-ramp configuration, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="0e943-105">![要求 &#45;回應的端點解析](../esb-toolkit/media/ch3-requestresponse.gif "Ch3 要求回應")</span><span class="sxs-lookup"><span data-stu-id="0e943-105">![Request&#45;Response Resolution of Endpoints](../esb-toolkit/media/ch3-requestresponse.gif "Ch3-RequestResponse")</span></span>  
  
 <span data-ttu-id="0e943-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="0e943-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="0e943-107">**要求-回應的端點和轉換需求的解決方式**</span><span class="sxs-lookup"><span data-stu-id="0e943-107">**Request-response resolution of endpoints and transformation requirements**</span></span>  
  
 <span data-ttu-id="0e943-108">動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="0e943-108">The Dynamic Resolution sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="0e943-109">它會顯示如何套用動態轉換和解析雙向的情況下使用 XML 路徑語言 (XPath)、 通用描述、 探索與整合 (UDDI)，靜態的或在 BizTalk Server 商務規則引擎中的原則。</span><span class="sxs-lookup"><span data-stu-id="0e943-109">It shows how to apply dynamic transformation and resolution for two-way scenarios using XML Path Language (XPath), Universal Description, Discovery, and Integration (UDDI), STATIC, or policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="0e943-110">如需詳細資訊，請參閱本文中的雙向傳訊案例[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0e943-110">For more information, see the two-way messaging scenario described in [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span></span>