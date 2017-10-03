---
title: "步驟 2： 建立 Orchestration2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08d65525-77a9-4be2-a509-40ea60fa7401
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13973edb14fbaed331a33eff429d623a33c3ff71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-orchestration"></a><span data-ttu-id="084f8-102">步驟 2： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="084f8-102">Step 2: Create the Orchestration</span></span>
<span data-ttu-id="084f8-103">協調流程設定使用名為 BeginDocTest 的專案，包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="084f8-103">The orchestration setup is as follows using a project called BeginDocTest:</span></span>  
  
 <span data-ttu-id="084f8-104">• 連接埠</span><span class="sxs-lookup"><span data-stu-id="084f8-104">• Ports</span></span>  
  
 <span data-ttu-id="084f8-105">• 訊息</span><span class="sxs-lookup"><span data-stu-id="084f8-105">• Messages</span></span>  
  
 <span data-ttu-id="084f8-106">• 傳送與接收</span><span class="sxs-lookup"><span data-stu-id="084f8-106">• Send and Receive</span></span>  
  
 <span data-ttu-id="084f8-107">• 建構訊息</span><span class="sxs-lookup"><span data-stu-id="084f8-107">• Construct Message</span></span>  
  
 <span data-ttu-id="084f8-108">• 轉換</span><span class="sxs-lookup"><span data-stu-id="084f8-108">• Transforms</span></span>  
  
 <span data-ttu-id="084f8-109">協調流程並不會進行任何例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="084f8-109">The orchestration does not do any exception handling.</span></span> <span data-ttu-id="084f8-110">J.D.</span><span class="sxs-lookup"><span data-stu-id="084f8-110">J.D.</span></span> <span data-ttu-id="084f8-111">Edwards EnterpriseOne 執行的 BeginDoc 和隱含交易則會復原，如果連接逾時內的後續作業。因而，BizTalk 協調流程不需要對 J.D. Edwards OneWorld 造成的變更進行任何回復</span><span class="sxs-lookup"><span data-stu-id="084f8-111">Edwards EnterpriseOne performs the BeginDoc and subsequent operations within an implicit transaction that it will rollback if the connection times out. The BizTalk orchestration thus does not need to do anything to rollback changes J.D.</span></span> <span data-ttu-id="084f8-112">Edwards EnterpriseOne 可讓。</span><span class="sxs-lookup"><span data-stu-id="084f8-112">Edwards EnterpriseOne makes.</span></span> <span data-ttu-id="084f8-113">然而，逾時會在 BizTalk 協調流程中導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="084f8-113">However, a time out will cause an exception in the BizTalk orchestration.</span></span> <span data-ttu-id="084f8-114">BizTalk 會將例外狀況記錄在事件日誌中。</span><span class="sxs-lookup"><span data-stu-id="084f8-114">BizTalk will record the exception in the event log.</span></span> <span data-ttu-id="084f8-115">如果您要在協調流程中加入例外狀況處理，請參閱 Microsoft BizTalk 2006 主要說明內容中的＜如何新增 Catch 例外狀況區塊＞和＜如何新增補償區塊＞。</span><span class="sxs-lookup"><span data-stu-id="084f8-115">If you want to add exception handling to the orchestration, see "How to Add a Catch Exception Block" and "How to Add a Compensation Block" in the Microsoft BizTalk 2006 main help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="084f8-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="084f8-116">In This Section</span></span>  
  
-   [<span data-ttu-id="084f8-117">工作 1： 建立連接埠</span><span class="sxs-lookup"><span data-stu-id="084f8-117">Task 1: Create the Ports</span></span>](../core/task-1-create-the-ports1.md)  
  
-   [<span data-ttu-id="084f8-118">工作 2： 建立訊息</span><span class="sxs-lookup"><span data-stu-id="084f8-118">Task 2: Create the Messages</span></span>](../core/task-2-create-the-messages2.md)  
  
-   [<span data-ttu-id="084f8-119">工作 3： 設定傳送埠和接收圖形</span><span class="sxs-lookup"><span data-stu-id="084f8-119">Task 3: Configure the Send and Receive Shapes</span></span>](../core/task-3-configure-the-send-and-receive-shapes2.md)  
  
-   [<span data-ttu-id="084f8-120">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="084f8-120">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape1.md)  
  
-   [<span data-ttu-id="084f8-121">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="084f8-121">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)