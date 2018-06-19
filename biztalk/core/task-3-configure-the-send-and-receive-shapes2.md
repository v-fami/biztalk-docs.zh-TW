---
title: 工作 3： 設定傳送埠和接收 Shapes2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ebe7141-f2bd-4e6a-9204-d61bd64286af
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6923a90b43d1bdc3004a03ac588dd2410d81a3cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279022"
---
# <a name="task-3-configure-the-send-and-receive-shapes"></a><span data-ttu-id="b0a6e-102">工作 3： 設定傳送埠和接收圖形</span><span class="sxs-lookup"><span data-stu-id="b0a6e-102">Task 3: Configure the Send and Receive Shapes</span></span>
<span data-ttu-id="b0a6e-103">請使用下列程序設定傳送和接收圖形。</span><span class="sxs-lookup"><span data-stu-id="b0a6e-103">Use the following procedure to configure the Send and Receive shapes.</span></span>  
  
### <a name="to-configure-the-send-and-receive-shapes"></a><span data-ttu-id="b0a6e-104">若要設定傳送和接收圖形</span><span class="sxs-lookup"><span data-stu-id="b0a6e-104">To configure the Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="b0a6e-105">依照下列順序，將傳送和接收圖形從工具箱中拖到協調流程的中央位置。</span><span class="sxs-lookup"><span data-stu-id="b0a6e-105">Drag Send and Receive shapes from the tool box into the center of the orchestration in the following order.</span></span>  
  
2.  <span data-ttu-id="b0a6e-106">設定下列參數：</span><span class="sxs-lookup"><span data-stu-id="b0a6e-106">Set the following parameters:</span></span>  
  
    |<span data-ttu-id="b0a6e-107">形狀圖</span><span class="sxs-lookup"><span data-stu-id="b0a6e-107">Shape</span></span>|<span data-ttu-id="b0a6e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-108">Name</span></span>|<span data-ttu-id="b0a6e-109">設定</span><span class="sxs-lookup"><span data-stu-id="b0a6e-109">Setting</span></span>|  
    |-----------|----------|-------------|  
    |<span data-ttu-id="b0a6e-110">Receive1</span><span class="sxs-lookup"><span data-stu-id="b0a6e-110">Receive1</span></span>|<span data-ttu-id="b0a6e-111">Activate</span><span class="sxs-lookup"><span data-stu-id="b0a6e-111">Activate</span></span>|<span data-ttu-id="b0a6e-112">True</span><span class="sxs-lookup"><span data-stu-id="b0a6e-112">True</span></span>|  
    ||<span data-ttu-id="b0a6e-113">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-113">Message</span></span>|<span data-ttu-id="b0a6e-114">BeginDocMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-114">BeginDocMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-115">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-115">Name</span></span>|<span data-ttu-id="b0a6e-116">ReceiveBeginDoc</span><span class="sxs-lookup"><span data-stu-id="b0a6e-116">ReceiveBeginDoc</span></span>|  
    ||<span data-ttu-id="b0a6e-117">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-117">Operation</span></span>|<span data-ttu-id="b0a6e-118">BeginDoc.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="b0a6e-118">BeginDoc.Operation_1.Request</span></span>|  
    |<span data-ttu-id="b0a6e-119">Send1</span><span class="sxs-lookup"><span data-stu-id="b0a6e-119">Send1</span></span>|<span data-ttu-id="b0a6e-120">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-120">Message</span></span>|<span data-ttu-id="b0a6e-121">BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-121">BeginDocSessionMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-122">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-122">Name</span></span>|<span data-ttu-id="b0a6e-123">SendBeginDoc</span><span class="sxs-lookup"><span data-stu-id="b0a6e-123">SendBeginDoc</span></span>|  
    ||<span data-ttu-id="b0a6e-124">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-124">Operation</span></span>|<span data-ttu-id="b0a6e-125">JDEPort.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="b0a6e-125">JDEPort.Operation_1.Request</span></span>|  
    |<span data-ttu-id="b0a6e-126">Receive2</span><span class="sxs-lookup"><span data-stu-id="b0a6e-126">Receive2</span></span>|<span data-ttu-id="b0a6e-127">Activate</span><span class="sxs-lookup"><span data-stu-id="b0a6e-127">Activate</span></span>|<span data-ttu-id="b0a6e-128">False</span><span class="sxs-lookup"><span data-stu-id="b0a6e-128">False</span></span>|  
    ||<span data-ttu-id="b0a6e-129">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-129">Message</span></span>|<span data-ttu-id="b0a6e-130">BeginDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-130">BeginDocResponseMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-131">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-131">Name</span></span>|<span data-ttu-id="b0a6e-132">ReceiveBeginDocResponse</span><span class="sxs-lookup"><span data-stu-id="b0a6e-132">ReceiveBeginDocResponse</span></span>|  
    ||<span data-ttu-id="b0a6e-133">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-133">Operation</span></span>|<span data-ttu-id="b0a6e-134">JDEPort.Operation_1.Response</span><span class="sxs-lookup"><span data-stu-id="b0a6e-134">JDEPort.Operation_1.Response</span></span>|  
    |<span data-ttu-id="b0a6e-135">Send2</span><span class="sxs-lookup"><span data-stu-id="b0a6e-135">Send2</span></span>|<span data-ttu-id="b0a6e-136">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-136">Message</span></span>|<span data-ttu-id="b0a6e-137">EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-137">EditLineSessionMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-138">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-138">Name</span></span>|<span data-ttu-id="b0a6e-139">SendEditLine</span><span class="sxs-lookup"><span data-stu-id="b0a6e-139">SendEditLine</span></span>|  
    ||<span data-ttu-id="b0a6e-140">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-140">Operation</span></span>|<span data-ttu-id="b0a6e-141">JDEPort.Operation_2.Request</span><span class="sxs-lookup"><span data-stu-id="b0a6e-141">JDEPort.Operation_2.Request</span></span>|  
    |<span data-ttu-id="b0a6e-142">Receive3</span><span class="sxs-lookup"><span data-stu-id="b0a6e-142">Receive3</span></span>|<span data-ttu-id="b0a6e-143">Activate</span><span class="sxs-lookup"><span data-stu-id="b0a6e-143">Activate</span></span>|<span data-ttu-id="b0a6e-144">False</span><span class="sxs-lookup"><span data-stu-id="b0a6e-144">False</span></span>|  
    ||<span data-ttu-id="b0a6e-145">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-145">Message</span></span>|<span data-ttu-id="b0a6e-146">EditLineResponseMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-146">EditLineResponseMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-147">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-147">Name</span></span>|<span data-ttu-id="b0a6e-148">ReceiveEditLine</span><span class="sxs-lookup"><span data-stu-id="b0a6e-148">ReceiveEditLine</span></span>|  
    ||<span data-ttu-id="b0a6e-149">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-149">Operation</span></span>|<span data-ttu-id="b0a6e-150">JDEPort.Operation_2.Response</span><span class="sxs-lookup"><span data-stu-id="b0a6e-150">JDEPort.Operation_2.Response</span></span>|  
    |<span data-ttu-id="b0a6e-151">Send3</span><span class="sxs-lookup"><span data-stu-id="b0a6e-151">Send3</span></span>|<span data-ttu-id="b0a6e-152">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-152">Message</span></span>|<span data-ttu-id="b0a6e-153">EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-153">EndDocSessionMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-154">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-154">Name</span></span>|<span data-ttu-id="b0a6e-155">SendEndDoc</span><span class="sxs-lookup"><span data-stu-id="b0a6e-155">SendEndDoc</span></span>|  
    ||<span data-ttu-id="b0a6e-156">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-156">Operation</span></span>|<span data-ttu-id="b0a6e-157">JDEPort.Operation_3.Request</span><span class="sxs-lookup"><span data-stu-id="b0a6e-157">JDEPort.Operation_3.Request</span></span>|  
    |<span data-ttu-id="b0a6e-158">Receive4</span><span class="sxs-lookup"><span data-stu-id="b0a6e-158">Receive4</span></span>|<span data-ttu-id="b0a6e-159">Activate</span><span class="sxs-lookup"><span data-stu-id="b0a6e-159">Activate</span></span>|<span data-ttu-id="b0a6e-160">False</span><span class="sxs-lookup"><span data-stu-id="b0a6e-160">False</span></span>|  
    ||<span data-ttu-id="b0a6e-161">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-161">Message</span></span>|<span data-ttu-id="b0a6e-162">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-162">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-163">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-163">Name</span></span>|<span data-ttu-id="b0a6e-164">ReceiveEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="b0a6e-164">ReceiveEndDocResponse</span></span>|  
    ||<span data-ttu-id="b0a6e-165">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-165">Operation</span></span>|<span data-ttu-id="b0a6e-166">JDEPort.Operation_3.Response</span><span class="sxs-lookup"><span data-stu-id="b0a6e-166">JDEPort.Operation_3.Response</span></span>|  
    |<span data-ttu-id="b0a6e-167">Send4</span><span class="sxs-lookup"><span data-stu-id="b0a6e-167">Send4</span></span>|<span data-ttu-id="b0a6e-168">訊息</span><span class="sxs-lookup"><span data-stu-id="b0a6e-168">Message</span></span>|<span data-ttu-id="b0a6e-169">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="b0a6e-169">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="b0a6e-170">名稱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-170">Name</span></span>|<span data-ttu-id="b0a6e-171">SendEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="b0a6e-171">SendEndDocResponse</span></span>|  
    ||<span data-ttu-id="b0a6e-172">作業</span><span class="sxs-lookup"><span data-stu-id="b0a6e-172">Operation</span></span>|<span data-ttu-id="b0a6e-173">EndDocOut.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="b0a6e-173">EndDocOut.Operation_1.Request</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0a6e-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0a6e-174">See Also</span></span>  
 <span data-ttu-id="b0a6e-175">[工作 1： 建立連接埠](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="b0a6e-175">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="b0a6e-176">[工作 2： 建立訊息](../core/task-2-create-the-messages2.md) </span><span class="sxs-lookup"><span data-stu-id="b0a6e-176">[Task 2: Create the Messages](../core/task-2-create-the-messages2.md) </span></span>  
 <span data-ttu-id="b0a6e-177">[工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="b0a6e-177">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md) </span></span>  
 [<span data-ttu-id="b0a6e-178">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="b0a6e-178">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)