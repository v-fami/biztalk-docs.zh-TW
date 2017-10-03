---
title: "同步的商務事件追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 302c7918-bc62-46f1-a949-fbf94a7073e3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84223714e2e04cec6c079862693a09786cb19a7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="synchronous-business-event-tracking"></a><span data-ttu-id="eef01-102">同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="eef01-102">Synchronous Business Event Tracking</span></span>
<span data-ttu-id="eef01-103">將事件資料傳送至 BAM 的最簡單方式是使用 DirectEventStream 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eef01-103">The simplest way to send event data to BAM is to use an instance of the class DirectEventStream.</span></span> <span data-ttu-id="eef01-104">在目前應用程式交易環境 (如果有的話) 中，此類別會將事件資料直接儲存到「BAM 主要匯入資料庫」。</span><span class="sxs-lookup"><span data-stu-id="eef01-104">This class saves the event data directly into the BAM Primary Import Database in the context of the current transaction of the application (if present).</span></span>  
  
 <span data-ttu-id="eef01-105">如果執行此作業期間發生任何錯誤，方法呼叫將在呼叫的應用程式中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eef01-105">If any error happens during this operation, the method call will throw an exception back in the calling application.</span></span> <span data-ttu-id="eef01-106">例如，如果 UpdateActivity 傳遞的項目名稱與 BAM 活動定義不符，或者您尚未部署 BAM 定義，就會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="eef01-106">This will happen for example if the name of an item passed in UpdateActivity mismatches the BAM Activity Definition, or you did not deploy the BAM Definition yet.</span></span> <span data-ttu-id="eef01-107">這讓呼叫的應用程式可以在儲存 BAM 資料時攔截並復原任何錯誤，使稍後的管理簡單許多。</span><span class="sxs-lookup"><span data-stu-id="eef01-107">This allows the calling application to catch and recover from any errors when saving the BAM data, which results in much easier management later.</span></span>  
  
 <span data-ttu-id="eef01-108">同步地儲存資料可能會影響效能，因為呼叫的應用程式必須等候 BAM 執行所有預存程序與觸發程序。</span><span class="sxs-lookup"><span data-stu-id="eef01-108">Saving the data synchronously might have a performance impact, because the calling application has to wait until BAM executes all stored procedures and triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef01-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eef01-109">See Also</span></span>  
 [<span data-ttu-id="eef01-110">非同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="eef01-110">Asynchronous Business Event Tracking</span></span>](../core/asynchronous-business-event-tracking.md)