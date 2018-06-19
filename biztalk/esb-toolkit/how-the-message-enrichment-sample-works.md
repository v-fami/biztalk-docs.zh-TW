---
title: 「 訊息豐富 」 範例的運作方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1188c1c9-b133-4438-b41c-ea6cffcf40fd
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ef516b992acbcee2936edb6341cbf1434ba4c79
ms.sourcegitcommit: 7497f6f23d7aadfa8535d0530493f8b4a2a50a0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2017
ms.locfileid: "22303670"
---
# <a name="how-the-message-enrichment-sample-works"></a><span data-ttu-id="ec5ff-102">「 訊息豐富 」 範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="ec5ff-102">How the Message Enrichment Sample Works</span></span>
 <span data-ttu-id="ec5ff-103">「 訊息豐富 」 範例示範可以封裝為泛型的可重複使用服務的整合模式。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-103">The Message Enrichment sample demonstrates that it is possible to encapsulate an integration pattern as a generic reusable service.</span></span> <span data-ttu-id="ec5ff-104">在此情況下此範例會實作內容 Enricher 模式。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-104">In this case the sample implements the Content Enricher pattern.</span></span> <span data-ttu-id="ec5ff-105">內容 Enricher 模式通常牽涉到使用轉換以準備傳輸到查閱的詳細資訊，才能外部服務的訊息和回應中併入新的訊息，其中也包含從資料則另一個轉換原始訊息。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-105">The Content Enricher pattern generally involves using a transform to prepare a message for transmission to an external service in order to lookup information, and then another transform to incorporate the response into a new message which also contains data from the original message.</span></span> <span data-ttu-id="ec5ff-106">若要實作此模式以一般方式，「 訊息豐富 」 範例提供的協調流程為基礎路線服務可以使用最多兩個解析程式設定使用從外部來源的資訊訊息豐富 」。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-106">In order to implement the pattern in a generic fashion, the Message Enrichment sample provides an orchestration-based itinerary service that can use up to two resolvers to configure enrichment of a message using information from an external source.</span></span>
  
 <span data-ttu-id="ec5ff-107">第一個的解析程式必須傳回路由資訊;它也可以傳回轉換旁邊的資訊。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-107">The first resolver must return routing information; it can also return transform information alongside it.</span></span> <span data-ttu-id="ec5ff-108">如果指定，轉換適用於內送訊息之前傳送到解析程式所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-108">If specified, the transform is applied to the incoming message before being routed to the location specified by the resolver.</span></span> <span data-ttu-id="ec5ff-109">在提供的範例路線，Wcf-custom 配接器提供者用來執行名為 GetOrderDetails GlobalBankESB 資料庫中的 SQL 預存程序，並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-109">In the provided sample itinerary, the WCF-Custom adapter provider is used to execute a SQL stored procedure within the GlobalBankESB database named GetOrderDetails and return the result.</span></span>  
  
 <span data-ttu-id="ec5ff-110">（選擇性） 可以包含第二個解決器。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-110">Optionally, a second resolver can be included.</span></span> <span data-ttu-id="ec5ff-111">如果提供，第二個的解析程式必須包含轉換資訊。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-111">If provided, the second resolver must include transformation information.</span></span> <span data-ttu-id="ec5ff-112">將會提供這項轉換，原始訊息並傳回任何資料來源已聯繫，做為輸入的結果。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-112">This transform will be given the original message and the result, returned by whichever data source was contacted, as input.</span></span> <span data-ttu-id="ec5ff-113">在範例路線，對應被參考提取資訊超出原始訊息與預存程序的結果，並將它包含在產生的 InventoryOrder 訊息內使用表格迴圈運算質。</span><span class="sxs-lookup"><span data-stu-id="ec5ff-113">In the sample itinerary, a map is referenced that uses a table looping functoid to pull information out of the original message and the result of the stored procedure and include it inside the resulting InventoryOrder message.</span></span>
