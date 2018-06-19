---
title: 步驟 2： 建立 Orchestration1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a88cafbb-3b6f-4d27-8516-79a2391b4e31
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1989fe18d9c9c81741ac83bd2f96627ea818eb91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276486"
---
# <a name="step-2-create-the-orchestration"></a><span data-ttu-id="a53a7-102">步驟 2： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="a53a7-102">Step 2: Create the Orchestration</span></span>
<span data-ttu-id="a53a7-103">協調流程設定使用名為 BeginDocTest 的專案，包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="a53a7-103">The orchestration setup is as follows using a project called BeginDocTest:</span></span>  
  
-   <span data-ttu-id="a53a7-104">連接埠</span><span class="sxs-lookup"><span data-stu-id="a53a7-104">Ports</span></span>  
  
-   <span data-ttu-id="a53a7-105">訊息</span><span class="sxs-lookup"><span data-stu-id="a53a7-105">Messages</span></span>  
  
-   <span data-ttu-id="a53a7-106">傳送與接收</span><span class="sxs-lookup"><span data-stu-id="a53a7-106">Send and Receive</span></span>  
  
-   <span data-ttu-id="a53a7-107">建構訊息</span><span class="sxs-lookup"><span data-stu-id="a53a7-107">Construct Message</span></span>  
  
-   <span data-ttu-id="a53a7-108">轉換</span><span class="sxs-lookup"><span data-stu-id="a53a7-108">Transforms</span></span>  
  
 <span data-ttu-id="a53a7-109">協調流程並不會進行任何例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="a53a7-109">The orchestration does not do any exception handling.</span></span> <span data-ttu-id="a53a7-110">J.D.</span><span class="sxs-lookup"><span data-stu-id="a53a7-110">J.D.</span></span> <span data-ttu-id="a53a7-111">Edwards OneWorld 執行的 BeginDoc 和隱含交易內的後續作業會在連線逾時發生時進行回復。因而，BizTalk 協調流程不需要對 J.D. Edwards OneWorld 造成的變更進行任何回復</span><span class="sxs-lookup"><span data-stu-id="a53a7-111">Edwards OneWorld performs the BeginDoc and subsequent operations within an implicit transaction that it will rollback if the connection times out. The BizTalk orchestration thus does not need to do anything to rollback changes J.D.</span></span> <span data-ttu-id="a53a7-112">。</span><span class="sxs-lookup"><span data-stu-id="a53a7-112">Edwards OneWorld makes.</span></span> <span data-ttu-id="a53a7-113">然而，逾時會在 BizTalk 協調流程中導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a53a7-113">However, a time out will cause an exception in the BizTalk orchestration.</span></span> <span data-ttu-id="a53a7-114">BizTalk 會將例外狀況記錄在事件日誌中。</span><span class="sxs-lookup"><span data-stu-id="a53a7-114">BizTalk will record the exception in the event log.</span></span> <span data-ttu-id="a53a7-115">如果您想要加入例外狀況處理協調流程，請參閱 < 如何新增 Catch 例外狀況區塊 」 和 「 如何新增補償區塊 」 在 Microsoft BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="a53a7-115">If you want to add exception handling to the orchestration, see "How to Add a Catch Exception Block" and "How to Add a Compensation Block" in the Microsoft BizTalk Server Help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a53a7-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="a53a7-116">In This Section</span></span>  
  
-   [<span data-ttu-id="a53a7-117">工作 1： 建立連接埠</span><span class="sxs-lookup"><span data-stu-id="a53a7-117">Task 1: Create the Ports</span></span>](../core/task-1-create-the-ports2.md)  
  
-   [<span data-ttu-id="a53a7-118">工作 2： 建立訊息</span><span class="sxs-lookup"><span data-stu-id="a53a7-118">Task 2: Create the Messages</span></span>](../core/task-2-create-the-messages1.md)  
  
-   [<span data-ttu-id="a53a7-119">工作 3： 設定傳送埠和接收圖形</span><span class="sxs-lookup"><span data-stu-id="a53a7-119">Task 3: Configure the Send and Receive Shapes</span></span>](../core/task-3-configure-the-send-and-receive-shapes1.md)  
  
-   [<span data-ttu-id="a53a7-120">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="a53a7-120">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape2.md)  
  
-   [<span data-ttu-id="a53a7-121">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="a53a7-121">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)