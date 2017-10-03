---
title: "解決資料遺失的進行中協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, MessageBox database
- data recovery
- data loss, recovery
- data loss, orchestrations
- data recovery, MessageBox database
- data recovery, orchestrations
- data loss, data recovery
- orchestrations, data recovery
- orchestrations, data loss
ms.assetid: dc6f1fd2-1976-40f2-ab57-41c7db40705e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eca757b80e31ee5db829d2d2079bf657d01079b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-data-loss-of-in-progress-orchestrations"></a><span data-ttu-id="2d919-102">解析進行中協調流程的資料遺失</span><span class="sxs-lookup"><span data-stu-id="2d919-102">Resolving Data Loss of In-Progress Orchestrations</span></span>
<span data-ttu-id="2d919-103">MessageBox 資料庫包含目前進行中協調流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="2d919-103">MessageBox databases contain the state of orchestrations that are currently in progress.</span></span> <span data-ttu-id="2d919-104">雖然沒有方法可以精確判斷 MessageBox 資料庫中遺失的資料為何，您還是可以採取一些步驟來收集遺失資料的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="2d919-104">Although there is no way to tell exactly what data has been lost from the MessageBox databases, there are some steps you can take to gather information about the lost data:</span></span>  
  
-   <span data-ttu-id="2d919-105">判斷在目前協調流程中已傳送及接收的訊息為何，以及在復原點之後已使用的外部系統為何。</span><span class="sxs-lookup"><span data-stu-id="2d919-105">Determine what messages have been sent and received in the current orchestrations, and what external systems have been used after the point of recovery.</span></span> <span data-ttu-id="2d919-106">例如，如果您的系統會維護訊息及事件的外部記錄，您就可以檢查該記錄。</span><span class="sxs-lookup"><span data-stu-id="2d919-106">For example, if your system maintains an external log of messages and events, you can examine that log.</span></span> <span data-ttu-id="2d919-107">您可能也需要手動檢視外部系統來查看發生了哪些活動。</span><span class="sxs-lookup"><span data-stu-id="2d919-107">You may also need to manually review the external systems to see what activities have occurred.</span></span>  
  
-   <span data-ttu-id="2d919-108">判定資料遺失的原因之後，您就可以開始修正還原的系統，並決定哪些程序可以繼續、哪些程序必須終止和重新啟動 (方法為重新提交遺失的啟動訊息)，以及哪些程序已成功完成，可以被終止。</span><span class="sxs-lookup"><span data-stu-id="2d919-108">After you determine the cause of the data loss, you can begin to correct the restored system, deciding which processes can continue, which processes must be terminated and restarted (by resubmitting the lost activation messages), and which processes have completed successfully and can be terminated.</span></span> <span data-ttu-id="2d919-109">這個程序主要取決於系統的架構，必須視為系統修復計畫的一部分來加以考量。</span><span class="sxs-lookup"><span data-stu-id="2d919-109">This process depends largely on the architecture of your system and must be considered as part of your system recovery planning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d919-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d919-110">See Also</span></span>  
 [<span data-ttu-id="2d919-111">解決資料遺失</span><span class="sxs-lookup"><span data-stu-id="2d919-111">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)