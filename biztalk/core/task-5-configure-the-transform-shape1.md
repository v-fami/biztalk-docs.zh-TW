---
title: "工作 5： 設定轉換 Shape1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a73fd2-0f34-4681-8aed-7d54d69c86d3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e76313ca87ad3138da83480b46a38a802d89ff15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="task-5-configure-the-transform-shape"></a><span data-ttu-id="39d60-102">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="39d60-102">Task 5: Configure the Transform Shape</span></span>
<span data-ttu-id="39d60-103">請使用下列程序設定「轉換」圖形。</span><span class="sxs-lookup"><span data-stu-id="39d60-103">Use the following procedure to configure the Transform shape.</span></span>  
  
### <a name="to-configure-the-transform-shape"></a><span data-ttu-id="39d60-104">設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="39d60-104">To configure the Transform shape</span></span>  
  
1.  <span data-ttu-id="39d60-105">將「建構訊息」圖形拖曳至 ReceiveBeginDocResponse 後面。</span><span class="sxs-lookup"><span data-stu-id="39d60-105">Drag a Construct Message shape after ReceiveBeginDocResponse.</span></span>  
  
    -   <span data-ttu-id="39d60-106">**建構的訊息：** EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="39d60-106">**Messages Constructed:** EditLineMsg</span></span>  
  
    -   <span data-ttu-id="39d60-107">**名稱：** ConstructEditLineMessageWithData</span><span class="sxs-lookup"><span data-stu-id="39d60-107">**Name:** ConstructEditLineMessageWithData</span></span>  
  
     <span data-ttu-id="39d60-108">以滑鼠右鍵按一下中央，選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="39d60-108">Right-click in the middle, select **Insert Shape**, and then select **Transform**.</span></span>  
  
     ![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")  
  
     <span data-ttu-id="39d60-109">使用 [轉換]，對應來自您要傳送至已傳送資料的資料。</span><span class="sxs-lookup"><span data-stu-id="39d60-109">Using Transform, map data from the data you are sending to the data that is sent.</span></span>  
  
     <span data-ttu-id="39d60-110">針對您的工作環境，您可能會傳送文件 (而非 BeginDoc)，其中包含可讓您建構所有可能訊息、BeginDoc、EditLine 和 EndDoc 的所有值。</span><span class="sxs-lookup"><span data-stu-id="39d60-110">For your work environment you would send a document (instead of BeginDoc) with all values possible allowing you to construct all possible messages, BeginDoc, EditLine, and EndDoc.</span></span> <span data-ttu-id="39d60-111">不過，此範例只有硬式編碼資料。</span><span class="sxs-lookup"><span data-stu-id="39d60-111">For this example, however, there is only hard coded data.</span></span>  
  
2.  <span data-ttu-id="39d60-112">按兩下**[transform_1]**開啟。</span><span class="sxs-lookup"><span data-stu-id="39d60-112">Double-click **Transform_1** to open.</span></span>  
  
    1.  <span data-ttu-id="39d60-113">選取來源，在 加入資料列中按一下**變數名稱**選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="39d60-113">Select Source and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
         ![](../core/media/jde-transform-source.gif "JDE_transform_source")  
  
    2.  <span data-ttu-id="39d60-114">選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EditLineMsg**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="39d60-114">Select **Destination** and click in the Add row under **Variable Name**, select **EditLineMsg**, and click **OK**.</span></span>  
  
         ![](../core/media/jde-transform-destination.gif "JDE_transform_destination")  
  
3.  <span data-ttu-id="39d60-115">在 [方案總管] 中，按兩下**[transform_1.btm]**開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="39d60-115">In the Solution Explorer, double-click **Transform_1.btm** to open the mapping tool.</span></span> <span data-ttu-id="39d60-116">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="39d60-116">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="39d60-117">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="39d60-117">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="39d60-118">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="39d60-118">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="39d60-119">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="39d60-119">mnProcessID</span></span>  
  
    -   <span data-ttu-id="39d60-120">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="39d60-120">mnTransactionID</span></span>  
  
     ![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")  
  
     <span data-ttu-id="39d60-121">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="39d60-121">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="39d60-122">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="39d60-122">Click the item in the Destination Schema and set the following Value.</span></span>  
  
     ![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")  
  
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
  
4.  <span data-ttu-id="39d60-123">將「建構訊息」拖曳至 ReceiveEditLine 後面。</span><span class="sxs-lookup"><span data-stu-id="39d60-123">Drag a Construct Message after ReceiveEditLine.</span></span>  
  
    -   <span data-ttu-id="39d60-124">**建構的訊息：** EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="39d60-124">**Messages Constructed:** EndDocMsg</span></span>  
  
    -   <span data-ttu-id="39d60-125">**名稱：** ConstructEndDocMessageWithData</span><span class="sxs-lookup"><span data-stu-id="39d60-125">**Name:** ConstructEndDocMessageWithData</span></span>  
  
     <span data-ttu-id="39d60-126">以滑鼠右鍵按一下中央並選取**插入圖形**，然後選取**轉換**。</span><span class="sxs-lookup"><span data-stu-id="39d60-126">Right-click in the middle and select **Insert Shape**, and then select **Transform**.</span></span>  
  
5.  <span data-ttu-id="39d60-127">按兩下**[transform_2]**開啟。</span><span class="sxs-lookup"><span data-stu-id="39d60-127">Double-click **Transform_2** to open.</span></span>  
  
    1.  <span data-ttu-id="39d60-128">選取**來源**按一下底下的 加入資料列中的 **變數名稱**選取**begindocresponsemsg**。</span><span class="sxs-lookup"><span data-stu-id="39d60-128">Select **Source** and click in the Add row under **Variable Name** and select **BeginDocResponseMsg**.</span></span>  
  
    2.  <span data-ttu-id="39d60-129">選取**目的地**按一下底下的 加入資料列中的 **變數名稱**，選取**EndDocMsg**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="39d60-129">Select **Destination** and click in the Add row under **Variable Name**, select **EndDocMsg**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="39d60-130">在 [方案總管] 中，按兩下**[transform_2.btm]**開啟對應工具。</span><span class="sxs-lookup"><span data-stu-id="39d60-130">In the Solution Explorer, double-click **Transform_2.btm** to open the mapping tool.</span></span> <span data-ttu-id="39d60-131">連結下列四個項目：</span><span class="sxs-lookup"><span data-stu-id="39d60-131">Link the following four items:</span></span>  
  
    -   <span data-ttu-id="39d60-132">mnCMJobNo</span><span class="sxs-lookup"><span data-stu-id="39d60-132">mnCMJobNo</span></span>  
  
    -   <span data-ttu-id="39d60-133">szCMComputerID</span><span class="sxs-lookup"><span data-stu-id="39d60-133">szCMComputerID</span></span>  
  
    -   <span data-ttu-id="39d60-134">mnProcessID</span><span class="sxs-lookup"><span data-stu-id="39d60-134">mnProcessID</span></span>  
  
    -   <span data-ttu-id="39d60-135">mnTransactionID</span><span class="sxs-lookup"><span data-stu-id="39d60-135">mnTransactionID</span></span>  
  
     <span data-ttu-id="39d60-136">為了方便使用起見，此範例包含硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="39d60-136">For ease of use, this example has hardcoded values.</span></span> <span data-ttu-id="39d60-137">按一下 [目的結構描述] 中的項目，並設定下列值。</span><span class="sxs-lookup"><span data-stu-id="39d60-137">Click the item in the Destination Schema and set the following Value.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
        [JDE://CSALES/B4200310]">  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
       <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
    </ns0:F4211FSEndDoc>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39d60-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39d60-138">See Also</span></span>  
 <span data-ttu-id="39d60-139">[工作 1： 建立連接埠](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="39d60-139">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="39d60-140">[工作 2： 建立訊息](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="39d60-140">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="39d60-141">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="39d60-141">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 [<span data-ttu-id="39d60-142">工作 4： 設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="39d60-142">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape2.md)