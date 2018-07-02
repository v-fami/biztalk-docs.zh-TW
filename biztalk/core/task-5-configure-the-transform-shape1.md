---
title: 工作 5： 設定轉換圖案 1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a73fd2-0f34-4681-8aed-7d54d69c86d3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e5b690774061e95fb34a070e19890d3a2a4eb0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003063"
---
# <a name="task-5-configure-the-transform-shape"></a><span data-ttu-id="46054-102">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="46054-102">Task 5: Configure the Transform Shape</span></span>
<span data-ttu-id="46054-103">請使用下列程序設定「轉換」圖形。</span><span class="sxs-lookup"><span data-stu-id="46054-103">Use the following procedure to configure the Transform shape.</span></span>  
  
### <a name="to-configure-the-transform-shape"></a><span data-ttu-id="46054-104">設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="46054-104">To configure the Transform shape</span></span>  
  
1. <span data-ttu-id="46054-105">將「建構訊息」圖形拖曳至 ReceiveBeginDocResponse 後面。</span><span class="sxs-lookup"><span data-stu-id="46054-105">Drag a Construct Message shape after ReceiveBeginDocResponse.</span></span>  
  
   - <span data-ttu-id="46054-106">**建構的訊息：** EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="46054-106">**Messages Constructed:** EditLineMsg</span></span>  
  
   - <span data-ttu-id="46054-107">**名稱：** ConstructEditLineMessageWithData</span><span class="sxs-lookup"><span data-stu-id="46054-107">**Name:** ConstructEditLineMessageWithData</span></span>  
  
     <span data-ttu-id="46054-108">以滑鼠右鍵按一下中央，選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="46054-108">Right-click in the middle, select **Insert Shape**, and then select **Transform**.</span></span>  
  
     <span data-ttu-id="46054-109">![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")</span><span class="sxs-lookup"><span data-stu-id="46054-109">![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")</span></span>  
  
     <span data-ttu-id="46054-110">使用 [轉換]，對應來自您要傳送至已傳送資料的資料。</span><span class="sxs-lookup"><span data-stu-id="46054-110">Using Transform, map data from the data you are sending to the data that is sent.</span></span>  
  
     <span data-ttu-id="46054-111">針對您的工作環境，您可能會傳送文件 (而非 BeginDoc)，其中包含可讓您建構所有可能訊息、BeginDoc、EditLine 和 EndDoc 的所有值。</span><span class="sxs-lookup"><span data-stu-id="46054-111">For your work environment you would send a document (instead of BeginDoc) with all values possible allowing you to construct all possible messages, BeginDoc, EditLine, and EndDoc.</span></span> <span data-ttu-id="46054-112">不過，此範例只有硬式編碼資料。</span><span class="sxs-lookup"><span data-stu-id="46054-112">For this example, however, there is only hard coded data.</span></span>  
  
2. <span data-ttu-id="46054-113">按兩下 **[transform_1]** 開啟。</span><span class="sxs-lookup"><span data-stu-id="46054-113">Double-click **Transform_1** to open.</span></span>  
  
   1.  <span data-ttu-id="46054-114">選取來源，在底下的 加入資料列中按一下**變數名稱**，然後選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="46054-114">Select Source and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
        <span data-ttu-id="46054-115">![](../core/media/jde-transform-source.gif "JDE_transform_source")</span><span class="sxs-lookup"><span data-stu-id="46054-115">![](../core/media/jde-transform-source.gif "JDE_transform_source")</span></span>  
  
   2.  <span data-ttu-id="46054-116">選取**目的地**下方的 加入資料列中按一下 **變數名稱**，選取**EditLineMsg**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="46054-116">Select **Destination** and click in the Add row under **Variable Name**, select **EditLineMsg**, and click **OK**.</span></span>  
  
        <span data-ttu-id="46054-117">![](../core/media/jde-transform-destination.gif "JDE_transform_destination")</span><span class="sxs-lookup"><span data-stu-id="46054-117">![](../core/media/jde-transform-destination.gif "JDE_transform_destination")</span></span>  
  
3. <span data-ttu-id="46054-118">在 [方案總管] 中，按兩下 **[transform_1.btm]** 以開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="46054-118">In the Solution Explorer, double-click **Transform_1.btm** to open the mapping tool.</span></span> <span data-ttu-id="46054-119">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="46054-119">Link the following four items:</span></span>  
  
   - <span data-ttu-id="46054-120">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="46054-120">mnCMJobNo</span></span>  
  
   - <span data-ttu-id="46054-121">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="46054-121">szCMComputerID</span></span>  
  
   - <span data-ttu-id="46054-122">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="46054-122">mnProcessID</span></span>  
  
   - <span data-ttu-id="46054-123">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="46054-123">mnTransactionID</span></span>  
  
     <span data-ttu-id="46054-124">![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")</span><span class="sxs-lookup"><span data-stu-id="46054-124">![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")</span></span>  
  
     <span data-ttu-id="46054-125">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="46054-125">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="46054-126">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="46054-126">Click the item in the Destination Schema and set the following Value.</span></span>  
  
     <span data-ttu-id="46054-127">![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")</span><span class="sxs-lookup"><span data-stu-id="46054-127">![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")</span></span>  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:F4211FSEditLine xmlns:ns0="http://schemas.microsoft.com/  
         [JDE://CSALES/B4200310]">  
      <ns0:cCMLineAction>A</ns0:cCMLineAction>  
      <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
      <ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>  
      <ns0:szItemNo>210</ns0:szItemNo>  
      <ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>  
      <ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
      <ns0:szTransactionUOM>EA</ns0:szTransactionUOM>  
      <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
      <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
   </ns0:F4211FSEditLine>  
   ```  
  
4. <span data-ttu-id="46054-128">將「建構訊息」拖曳至 ReceiveEditLine 後面。</span><span class="sxs-lookup"><span data-stu-id="46054-128">Drag a Construct Message after ReceiveEditLine.</span></span>  
  
   - <span data-ttu-id="46054-129">**建構的訊息：** EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="46054-129">**Messages Constructed:** EndDocMsg</span></span>  
  
   - <span data-ttu-id="46054-130">**名稱：** ConstructEndDocMessageWithData</span><span class="sxs-lookup"><span data-stu-id="46054-130">**Name:** ConstructEndDocMessageWithData</span></span>  
  
     <span data-ttu-id="46054-131">以滑鼠右鍵按一下中央並選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="46054-131">Right-click in the middle and select **Insert Shape**, and then select **Transform**.</span></span>  
  
5. <span data-ttu-id="46054-132">按兩下**Transform_2**開啟。</span><span class="sxs-lookup"><span data-stu-id="46054-132">Double-click **Transform_2** to open.</span></span>  
  
   1.  <span data-ttu-id="46054-133">選取 **來源**下方的 加入資料列中按一下 **變數名稱**，然後選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="46054-133">Select **Source** and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
   2.  <span data-ttu-id="46054-134">選取**目的地**下方的 加入資料列中按一下 **變數名稱**，選取**EndDocMsg**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="46054-134">Select **Destination** and click in the Add row under **Variable Name**, select **EndDocMsg**, and click **OK**.</span></span>  
  
6. <span data-ttu-id="46054-135">在 [方案總管] 中，按兩下 **[transform_2.btm]** 以開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="46054-135">In the Solution Explorer, double-click **Transform_2.btm** to open the mapping tool.</span></span> <span data-ttu-id="46054-136">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="46054-136">Link the following four items:</span></span>  
  
   - <span data-ttu-id="46054-137">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="46054-137">mnCMJobNo</span></span>  
  
   - <span data-ttu-id="46054-138">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="46054-138">szCMComputerID</span></span>  
  
   - <span data-ttu-id="46054-139">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="46054-139">mnProcessID</span></span>  
  
   - <span data-ttu-id="46054-140">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="46054-140">mnTransactionID</span></span>  
  
     <span data-ttu-id="46054-141">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="46054-141">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="46054-142">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="46054-142">Click the item in the Destination Schema and set the following Value.</span></span>  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
       [JDE://CSALES/B4200310]">  
      <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
      <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
      <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
   </ns0:F4211FSEndDoc>  
   ```  
  
## <a name="see-also"></a><span data-ttu-id="46054-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46054-143">See Also</span></span>  
 <span data-ttu-id="46054-144">[工作 1： 建立連接埠](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="46054-144">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="46054-145">[工作 2： 建立訊息](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="46054-145">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="46054-146">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="46054-146">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="46054-147">工作 4：設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="46054-147">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape2.md)