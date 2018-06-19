---
title: 工作 5： 設定轉換 Shape2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e92874e-9021-4cf6-bab6-d4173308c469
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 596afdecc38f25ef92dbeb368197d9c71adaffc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279630"
---
# <a name="task-5-configure-the-transform-shape"></a><span data-ttu-id="a5210-102">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="a5210-102">Task 5: Configure the Transform Shape</span></span>
<span data-ttu-id="a5210-103">請使用下列程序設定「轉換」圖形。</span><span class="sxs-lookup"><span data-stu-id="a5210-103">Use the following procedure to configure the Transform shape.</span></span>  
  
### <a name="to-configure-the-transform-shape"></a><span data-ttu-id="a5210-104">設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="a5210-104">To configure the Transform shape</span></span>  
  
1.  <span data-ttu-id="a5210-105">將「建構訊息」圖形拖曳至 ReceiveBeginDocResponse 後面。</span><span class="sxs-lookup"><span data-stu-id="a5210-105">Drag a Construct Message shape after ReceiveBeginDocResponse.</span></span>  
  
    -   <span data-ttu-id="a5210-106">**建構的訊息：** EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="a5210-106">**Messages Constructed:** EditLineMsg</span></span>  
  
    -   <span data-ttu-id="a5210-107">**名稱：** ConstructEditLineMessageWithData</span><span class="sxs-lookup"><span data-stu-id="a5210-107">**Name:** ConstructEditLineMessageWithData</span></span>  
  
    1.  <span data-ttu-id="a5210-108">以滑鼠右鍵按一下中央，選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="a5210-108">Right-click in the middle, select **Insert Shape**, and then select **Transform**.</span></span>  
  
         <span data-ttu-id="a5210-109">![插入圖形轉換](../core/media/insert-shape-transform.gif "insert_shape_transform")</span><span class="sxs-lookup"><span data-stu-id="a5210-109">![Insert Shape Transform](../core/media/insert-shape-transform.gif "insert_shape_transform")</span></span>  
  
    2.  <span data-ttu-id="a5210-110">使用 [轉換]，對應來自您要傳送至已傳送資料的資料。</span><span class="sxs-lookup"><span data-stu-id="a5210-110">Using Transform, map data from the data you are sending to the data that is sent.</span></span>  
  
     <span data-ttu-id="a5210-111">針對您的工作環境，您可能會傳送文件 (而非 BeginDoc)，其中包含可讓您建構所有可能訊息、BeginDoc、EditLine 和 EndDoc 的所有值。</span><span class="sxs-lookup"><span data-stu-id="a5210-111">For your work environment you would send a document (instead of BeginDoc) with all values possible allowing you to construct all possible messages, BeginDoc, EditLine, and EndDoc.</span></span> <span data-ttu-id="a5210-112">不過，此範例只有硬式編碼資料。</span><span class="sxs-lookup"><span data-stu-id="a5210-112">For this example, however, there is only hard coded data.</span></span>  
  
2.  <span data-ttu-id="a5210-113">按兩下 [Transform_1] 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="a5210-113">Double-click Transform_1 to open.</span></span>  
  
    1.  <span data-ttu-id="a5210-114">選取來源，在 加入資料列中按一下**變數名稱**選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="a5210-114">Select Source and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
         <span data-ttu-id="a5210-115">![轉換來源](../core/media/transform-source.gif "transform_source")</span><span class="sxs-lookup"><span data-stu-id="a5210-115">![Transform Source](../core/media/transform-source.gif "transform_source")</span></span>  
  
    2.  <span data-ttu-id="a5210-116">選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EditLineMsg**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5210-116">Select **Destination** and click in the Add row under **Variable Name**, select **EditLineMsg**, and click **OK**.</span></span>  
  
         <span data-ttu-id="a5210-117">![轉換目的](../core/media/transform-destination.gif "transform_destination")</span><span class="sxs-lookup"><span data-stu-id="a5210-117">![Transform Destination](../core/media/transform-destination.gif "transform_destination")</span></span>  
  
3.  <span data-ttu-id="a5210-118">在 [方案總管] 中，按兩下 **[transform_1.btm]** 開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="a5210-118">In the Solution Explorer, double-click **Transform_1.btm** to open the mapping tool.</span></span> <span data-ttu-id="a5210-119">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="a5210-119">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="a5210-120">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="a5210-120">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="a5210-121">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="a5210-121">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="a5210-122">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="a5210-122">mnProcessID</span></span>  
  
    -   <span data-ttu-id="a5210-123">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="a5210-123">mnTransactionID</span></span>  
  
     <span data-ttu-id="a5210-124">![範例轉換對應](../core/media/example-transformmapping.gif "example_transformmapping")</span><span class="sxs-lookup"><span data-stu-id="a5210-124">![Example Transform Mapping](../core/media/example-transformmapping.gif "example_transformmapping")</span></span>  
  
     <span data-ttu-id="a5210-125">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="a5210-125">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="a5210-126">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="a5210-126">Click the item in the Destination Schema and set the following Value.</span></span>  
  
     <span data-ttu-id="a5210-127">![硬式編碼對應](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")</span><span class="sxs-lookup"><span data-stu-id="a5210-127">![Hard Coded Mapping](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")</span></span>  
  
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
  
4.  <span data-ttu-id="a5210-128">將「建構訊息」拖曳至 ReceiveEditLine 後面。</span><span class="sxs-lookup"><span data-stu-id="a5210-128">Drag a Construct Message after ReceiveEditLine.</span></span>  
  
    -   <span data-ttu-id="a5210-129">**建構的訊息：** EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="a5210-129">**Messages Constructed:** EndDocMsg</span></span>  
  
    -   <span data-ttu-id="a5210-130">**名稱：** ConstructEndDocMessageWithData</span><span class="sxs-lookup"><span data-stu-id="a5210-130">**Name:** ConstructEndDocMessageWithData</span></span>  
  
         <span data-ttu-id="a5210-131">以滑鼠右鍵按一下中央並選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="a5210-131">Right-click in the middle and select **Insert Shape**, and then select **Transform**.</span></span>  
  
5.  <span data-ttu-id="a5210-132">按兩下 [Transform_2] 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="a5210-132">Double-click Transform_2 to open.</span></span>  
  
    1.  <span data-ttu-id="a5210-133">選取**來源**按一下底下的 加入資料列中的 **變數名稱**選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="a5210-133">Select **Source** and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
    2.  <span data-ttu-id="a5210-134">選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EndDocMsg**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5210-134">Select **Destination** and click in the Add row under **Variable Name**, select **EndDocMsg**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="a5210-135">在 [方案總管] 中，按兩下 **[transform_2.btm]** 開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="a5210-135">In the Solution Explorer, double-click **Transform_2.btm** to open the mapping tool.</span></span> <span data-ttu-id="a5210-136">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="a5210-136">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="a5210-137">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="a5210-137">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="a5210-138">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="a5210-138">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="a5210-139">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="a5210-139">mnProcessID</span></span>  
  
    -   <span data-ttu-id="a5210-140">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="a5210-140">mnTransactionID</span></span>  
  
     <span data-ttu-id="a5210-141">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="a5210-141">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="a5210-142">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="a5210-142">Click the item in the Destination Schema and set the following Value.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
        [JDE://CSALES/B4200310]">  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
       <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
    </ns0:F4211FSEndDoc>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5210-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5210-143">See Also</span></span>  
 <span data-ttu-id="a5210-144">[工作 1： 建立連接埠](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="a5210-144">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="a5210-145">[工作 2： 建立訊息](../core/task-2-create-the-messages2.md) </span><span class="sxs-lookup"><span data-stu-id="a5210-145">[Task 2: Create the Messages](../core/task-2-create-the-messages2.md) </span></span>  
 <span data-ttu-id="a5210-146">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes2.md) </span><span class="sxs-lookup"><span data-stu-id="a5210-146">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md) </span></span>  
 [<span data-ttu-id="a5210-147">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="a5210-147">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape1.md)