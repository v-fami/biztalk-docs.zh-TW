---
title: "BAM 事件發佈的效能考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- publishing, BAM
- BAM, publishing
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 5a99e61a-a3d9-47fd-a933-2297f79817a5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebab873c94c0ae17abf9938883662ca8777cef36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performance-considerations-for-bam-event-publishing"></a><span data-ttu-id="7c26c-102">BAM 事件發佈的效能考量</span><span class="sxs-lookup"><span data-stu-id="7c26c-102">Performance Considerations for BAM Event Publishing</span></span>
<span data-ttu-id="7c26c-103">BAM 支援兩種發佈商務事件的型式：</span><span class="sxs-lookup"><span data-stu-id="7c26c-103">BAM supports two forms of business event publishing:</span></span>  
  
-   <span data-ttu-id="7c26c-104">同步的</span><span class="sxs-lookup"><span data-stu-id="7c26c-104">Synchronous</span></span>  
  
-   <span data-ttu-id="7c26c-105">非同步的</span><span class="sxs-lookup"><span data-stu-id="7c26c-105">Asynchronous</span></span>  
  
 <span data-ttu-id="7c26c-106">下圖說明這兩種模型。</span><span class="sxs-lookup"><span data-stu-id="7c26c-106">The following diagram illustrates the two models.</span></span>  
  
 ![](../core/media/bam-topologies.gif "bam_topologies")  
<span data-ttu-id="7c26c-107">BAM 拓樸</span><span class="sxs-lookup"><span data-stu-id="7c26c-107">BAM Topologies</span></span>  
  
 <span data-ttu-id="7c26c-108">同步方式簡化了程式碼的管理與使用，非同步方式則可獲致更好的執行效能。</span><span class="sxs-lookup"><span data-stu-id="7c26c-108">The synchronous approach is much simpler for management and using from code, while the asynchronous approach allows for better performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c26c-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c26c-109">In This Section</span></span>  
  
-   [<span data-ttu-id="7c26c-110">同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="7c26c-110">Synchronous Business Event Tracking</span></span>](../core/synchronous-business-event-tracking.md)  
  
-   [<span data-ttu-id="7c26c-111">非同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="7c26c-111">Asynchronous Business Event Tracking</span></span>](../core/asynchronous-business-event-tracking.md)