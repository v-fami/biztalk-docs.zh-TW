---
title: 了解追蹤的資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- instances, viewing
- service instances, viewing
- viewing, suspended instances
- messages, viewing
- viewing, service details
- viewing, orchestration details
- viewing, message details
- orchestrations, viewing
- suspended instances
- instances, suspended
ms.assetid: dcc3fbd5-cd2c-4780-a577-0ccd521cf5eb
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed30934ca154c8b6921682112b12d016c57f92be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286582"
---
# <a name="understanding-tracked-data"></a><span data-ttu-id="86b04-102">瞭解追蹤資料</span><span class="sxs-lookup"><span data-stu-id="86b04-102">Understanding Tracked Data</span></span>
<span data-ttu-id="86b04-103">當您執行的追蹤查詢時，追蹤的資訊會出現在 [查詢結果] 視窗底部的 [結果] 清單中。</span><span class="sxs-lookup"><span data-stu-id="86b04-103">When you run a tracking query, the tracked information appears in the results list at the bottom of the Query Results window.</span></span>  
  
## <a name="viewing-message-details"></a><span data-ttu-id="86b04-104">檢視訊息詳細資訊</span><span class="sxs-lookup"><span data-stu-id="86b04-104">Viewing message details</span></span>  
 <span data-ttu-id="86b04-105">您可以追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="86b04-105">You can track message properties.</span></span> <span data-ttu-id="86b04-106">您也可以追蹤的訊息內文儲存至檔案，並檢視使用非 Microsoft 工具。</span><span class="sxs-lookup"><span data-stu-id="86b04-106">You can also save tracked message bodies to a file and view them using non-Microsoft tools.</span></span>  
  
-   <span data-ttu-id="86b04-107">您可使用滑鼠右鍵按一下服務執行個體所參考的任何訊息，然後選取 [訊息詳細資料]。</span><span class="sxs-lookup"><span data-stu-id="86b04-107">You can right-click any message referenced by a service instance and select Message details.</span></span>  
  
-   <span data-ttu-id="86b04-108">如果已處理訊息，但追蹤，因為您所開啟的追蹤，您可以將它儲存到您的硬碟，並檢查它。</span><span class="sxs-lookup"><span data-stu-id="86b04-108">If the message is already processed but it was tracked—because you had tracking turned on—you can save it to your hard disk and examine it.</span></span>  
  
-   <span data-ttu-id="86b04-109">您可以連接至協調流程執行個體，並使用「協調流程偵錯工具」。</span><span class="sxs-lookup"><span data-stu-id="86b04-109">You can attach to the orchestration instance and use the Orchestration Debugger.</span></span>  
  
## <a name="viewing-service-events"></a><span data-ttu-id="86b04-110">檢視服務事件</span><span class="sxs-lookup"><span data-stu-id="86b04-110">Viewing service events</span></span>  
 <span data-ttu-id="86b04-111">當已擱置的服務會出現在事件記錄檔時，您可以藉由調查服務**訊息流程**，**協調流程偵錯工具**，**顯示追蹤的訊息事件**，**顯示即時服務執行個體**，從選項**內容**功能表。</span><span class="sxs-lookup"><span data-stu-id="86b04-111">When a suspended service appears in the event log, you can investigate a service by using the **Message Flow**, **Orchestration Debugger**, **Show Tracked Message Events**, **Show Live Service Instances**, options from the **Context** menu.</span></span>  
  
## <a name="viewing-orchestration-events"></a><span data-ttu-id="86b04-112">檢視協調流程事件</span><span class="sxs-lookup"><span data-stu-id="86b04-112">Viewing orchestration events</span></span>  
 <span data-ttu-id="86b04-113">使用協調流程偵錯工具來檢視訊息執行個體透過協調流程取得的路徑。</span><span class="sxs-lookup"><span data-stu-id="86b04-113">Use the Orchestration Debugger to view the path a message instance has taken through an orchestration.</span></span> <span data-ttu-id="86b04-114">當您進行時，協調流程的影像會顯示訊息的進度，讓您在協調流程中放置中斷點以進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="86b04-114">As you step through, a rendered image of the orchestration shows the progress of the message, and allows you to place breakpoints in the orchestration for debugging purposes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86b04-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="86b04-115">In This Section</span></span>  
  
-   [<span data-ttu-id="86b04-116">什麼是訊息追蹤？</span><span class="sxs-lookup"><span data-stu-id="86b04-116">What is Message Tracking?</span></span>](../core/what-is-message-tracking.md)  
  
-   [<span data-ttu-id="86b04-117">何謂事件追蹤？</span><span class="sxs-lookup"><span data-stu-id="86b04-117">What is Event Tracking?</span></span>](../core/what-is-event-tracking.md)