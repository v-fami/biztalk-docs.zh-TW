---
title: BAM 事件發佈的效能考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, BAM
- publishing, BAM
- BAM, publishing
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 5a99e61a-a3d9-47fd-a933-2297f79817a5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c031f9a3325eda9cbcf865eaf72d1d9e100616c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997535"
---
# <a name="performance-considerations-for-bam-event-publishing"></a><span data-ttu-id="119ef-102">BAM 事件發佈的效能考量</span><span class="sxs-lookup"><span data-stu-id="119ef-102">Performance Considerations for BAM Event Publishing</span></span>
<span data-ttu-id="119ef-103">BAM 支援兩種發佈商務事件的型式：</span><span class="sxs-lookup"><span data-stu-id="119ef-103">BAM supports two forms of business event publishing:</span></span>  
  
- <span data-ttu-id="119ef-104">同步的</span><span class="sxs-lookup"><span data-stu-id="119ef-104">Synchronous</span></span>  
  
- <span data-ttu-id="119ef-105">非同步的</span><span class="sxs-lookup"><span data-stu-id="119ef-105">Asynchronous</span></span>  
  
  <span data-ttu-id="119ef-106">下圖說明這兩種模型。</span><span class="sxs-lookup"><span data-stu-id="119ef-106">The following diagram illustrates the two models.</span></span>  
  
  <span data-ttu-id="119ef-107">![](../core/media/bam-topologies.gif "bam_topologies")</span><span class="sxs-lookup"><span data-stu-id="119ef-107">![](../core/media/bam-topologies.gif "bam_topologies")</span></span>  
  <span data-ttu-id="119ef-108">BAM 拓樸</span><span class="sxs-lookup"><span data-stu-id="119ef-108">BAM Topologies</span></span>  
  
  <span data-ttu-id="119ef-109">同步方式簡化了程式碼的管理與使用，非同步方式則可獲致更好的執行效能。</span><span class="sxs-lookup"><span data-stu-id="119ef-109">The synchronous approach is much simpler for management and using from code, while the asynchronous approach allows for better performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="119ef-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="119ef-110">In This Section</span></span>  
  
-   [<span data-ttu-id="119ef-111">同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="119ef-111">Synchronous Business Event Tracking</span></span>](../core/synchronous-business-event-tracking.md)  
  
-   [<span data-ttu-id="119ef-112">非同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="119ef-112">Asynchronous Business Event Tracking</span></span>](../core/asynchronous-business-event-tracking.md)