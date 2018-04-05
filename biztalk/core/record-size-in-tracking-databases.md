---
title: 追蹤資料庫中記錄大小 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: be7a891b-2674-49a3-a8e0-6aa11a918bf2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1f4d09d1af92ce4777f5036885d81ea7bf3e648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="record-size-in-tracking-databases"></a><span data-ttu-id="cde84-102">追蹤資料庫中的記錄大小</span><span class="sxs-lookup"><span data-stu-id="cde84-102">Record Size in Tracking Databases</span></span>
<span data-ttu-id="cde84-103">為了協助您規劃 BizTalk 的硬體需求，下表會顯示追蹤資料庫中不同事件記錄的預期記錄大小。</span><span class="sxs-lookup"><span data-stu-id="cde84-103">To help you plan your hardware requirements for BizTalk, the following table shows the expected record size for various event records in the Tracking database.</span></span>  
  
|<span data-ttu-id="cde84-104">動作類型</span><span class="sxs-lookup"><span data-stu-id="cde84-104">Action Type</span></span>|<span data-ttu-id="cde84-105">大小</span><span class="sxs-lookup"><span data-stu-id="cde84-105">Size</span></span>|<span data-ttu-id="cde84-106">注意</span><span class="sxs-lookup"><span data-stu-id="cde84-106">Notes</span></span>|  
|-----------------|----------|-----------|  
|<span data-ttu-id="cde84-107">部署服務</span><span class="sxs-lookup"><span data-stu-id="cde84-107">Deploying a Service</span></span>|<span data-ttu-id="cde84-108">1864 + 符號資訊大小</span><span class="sxs-lookup"><span data-stu-id="cde84-108">1864 + Symbolic Information Size</span></span>|<span data-ttu-id="cde84-109">符號資訊會根據協調流程的大小而定。</span><span class="sxs-lookup"><span data-stu-id="cde84-109">Symbolic Information depends on the size of the orchestration.</span></span> <span data-ttu-id="cde84-110">例如，接收一個訊息並將訊息以兩個圖形傳送出的協調流程大約需要 4000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-110">For example, an orchestration that receives one message and sends one message out with 2 shapes in it takes approximately 4000 bytes.</span></span>|  
|<span data-ttu-id="cde84-111">已啟動及已成功完成的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="cde84-111">Started and Successfully Completed Service Instance</span></span>|<span data-ttu-id="cde84-112">通常需要 252 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-112">Normally 252 bytes.</span></span><br /><br /> <span data-ttu-id="cde84-113">特別狀況下可達到 735 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-113">Extreme cases, can reach 735 bytes.</span></span>||  
|<span data-ttu-id="cde84-114">已啟動及遇到失敗/例外狀況的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="cde84-114">Started and Failed/Exception Met Service Instance</span></span>|<span data-ttu-id="cde84-115">通常需要 252 個位元組 + 錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cde84-115">Normally 252 bytes + error information.</span></span><br /><br /> <span data-ttu-id="cde84-116">特別狀況下可達到 735 個位元組 + 錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cde84-116">Extreme cases can reach 735 bytes + error information.</span></span>|<span data-ttu-id="cde84-117">錯誤資訊是由 BizTalk 或使用者元件傳回的文字資料。</span><span class="sxs-lookup"><span data-stu-id="cde84-117">Error information is the text data returned by a BizTalk or user component.</span></span> <span data-ttu-id="cde84-118">範圍從 100 個位元組到 2 KB。</span><span class="sxs-lookup"><span data-stu-id="cde84-118">Ranges from 100 bytes to 2 KB.</span></span>|  
|<span data-ttu-id="cde84-119">協調流程中的圖形開始/結束</span><span class="sxs-lookup"><span data-stu-id="cde84-119">Start/End of a Shape In an Orchestration</span></span>|<span data-ttu-id="cde84-120">每個 120 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-120">120 bytes each.</span></span>||  
|<span data-ttu-id="cde84-121">訊息進/出事件</span><span class="sxs-lookup"><span data-stu-id="cde84-121">Message In/Out Events</span></span>|<span data-ttu-id="cde84-122">最小需要 162 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-122">Minimum 162 bytes.</span></span><br /><br /> <span data-ttu-id="cde84-123">第一次看見訊息時為 202 個位元組 + 訊息屬性 (若進行追蹤)</span><span class="sxs-lookup"><span data-stu-id="cde84-123">First time message is seen it is 202 bytes + Message Property (if tracked)</span></span><br /><br /> <span data-ttu-id="cde84-124">特別狀況下可達到 2930 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-124">Extreme cases can reach 2930 bytes.</span></span>|<span data-ttu-id="cde84-125">若沒有訊息屬性追蹤，您可安全地假設平均為 182 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-125">You can safely assume that the average is 182 bytes if there is no message property tracking.</span></span>|  
|<span data-ttu-id="cde84-126">訊息屬性大小</span><span class="sxs-lookup"><span data-stu-id="cde84-126">Message Property Size</span></span>|<span data-ttu-id="cde84-127">40 至 288 個位元組 (若 DTA 可識別此追蹤屬性)。</span><span class="sxs-lookup"><span data-stu-id="cde84-127">40 to 288 bytes if DTA recognizes this tracking property.</span></span><br /><br /> <span data-ttu-id="cde84-128">第一次追蹤屬性時最大為 268 個位元組。</span><span class="sxs-lookup"><span data-stu-id="cde84-128">Add up to 268 bytes for tracking the property the first time.</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="cde84-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cde84-129">See Also</span></span>  
 <span data-ttu-id="cde84-130">[什麼是訊息追蹤？](../core/what-is-message-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="cde84-130">[What is Message Tracking?](../core/what-is-message-tracking.md) </span></span>  
 [<span data-ttu-id="cde84-131">管理與追蹤架構</span><span class="sxs-lookup"><span data-stu-id="cde84-131">Management and Tracking Architecture</span></span>](../core/management-and-tracking-architecture.md)