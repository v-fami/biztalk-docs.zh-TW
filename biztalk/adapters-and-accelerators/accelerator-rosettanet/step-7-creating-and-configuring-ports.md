---
title: "步驟 7： 建立及設定連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
- private process tutorial, configuring ports
ms.assetid: c00344c6-506a-4560-a948-e5fed2b9fd58
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c93f7c07f92c7517dbc84403747da869e0d4ceb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-creating-and-configuring-ports"></a><span data-ttu-id="431e0-102">步驟 7： 建立及設定連接埠</span><span class="sxs-lookup"><span data-stu-id="431e0-102">Step 7: Creating and Configuring Ports</span></span>
<span data-ttu-id="431e0-103">在這個步驟中，您會建立和設定與商務程序進行通訊所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="431e0-103">In this step, you create and configure the ports you use to communicate with business processes.</span></span> <span data-ttu-id="431e0-104">每一個連接埠都有類型、方向和繫結等屬性，</span><span class="sxs-lookup"><span data-stu-id="431e0-104">Each port has a type, direction, and binding property.</span></span> <span data-ttu-id="431e0-105">分別指定通訊的方向和模式、訊息的傳送或接收位置、以及通訊的進行方式。</span><span class="sxs-lookup"><span data-stu-id="431e0-105">These properties establish the direction and pattern of communication, the location of where the message is sent or received, and how the communication occurs.</span></span>  
  
### <a name="to-create-a-logical-send-port"></a><span data-ttu-id="431e0-106">建立邏輯傳送埠</span><span class="sxs-lookup"><span data-stu-id="431e0-106">To create a logical send port</span></span>  
  
1.  <span data-ttu-id="431e0-107">在 Visual Studio 中，從 [工具箱] 拖曳**連接埠**圖形至協調流程設計介面並將它放在**連接埠介面**開啟**連接埠組態精靈**。</span><span class="sxs-lookup"><span data-stu-id="431e0-107">In Visual Studio, from the Toolbox, drag the **Port** shape to the orchestration design surface and drop it on the **Port Surface** to open the **Port Configuration Wizard**.</span></span>  
  
2.  <span data-ttu-id="431e0-108">在**連接埠組態精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="431e0-108">On the **Port Configuration Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="431e0-109">在**連接埠內容**頁面上，於**名稱**方塊中，輸入**ContosoSQLReqResponsePort**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="431e0-109">On the **Port Properties** page, in the **Name** box, type **ContosoSQLReqResponsePort**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="431e0-110">在**選取連接埠類型**頁面上，於**連接埠類型名稱**方塊中，輸入**ContosoSQLReqResponsePortName**。</span><span class="sxs-lookup"><span data-stu-id="431e0-110">On the **Select a Port Type** page, in the **Port Type Name** box, type **ContosoSQLReqResponsePortName**.</span></span>  
  
5.  <span data-ttu-id="431e0-111">如**通訊模式**，選取**要求-回應**。</span><span class="sxs-lookup"><span data-stu-id="431e0-111">For **Communication Pattern**, select **Request-Response**.</span></span>  
  
6.  <span data-ttu-id="431e0-112">如**存取限制**，選取**內部-限制於此專案**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="431e0-112">For **Access Restrictions**, select **Internal - limited to this project**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="431e0-113">在**連接埠繫結**頁面上，選取**我要傳送要求並接收回應**，保留**連接埠繫結**選項設定為**稍後指定**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="431e0-113">On the **Port Binding** page, select **I'll be sending a request and receiving a response**, leave the **Port Binding** option set to **Specify Later**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="431e0-114">按一下**完成**建立連接埠。</span><span class="sxs-lookup"><span data-stu-id="431e0-114">Click **Finish** to create the port.</span></span>  
  
### <a name="to-change-the-variable-type-for-the-orchestration-ports"></a><span data-ttu-id="431e0-115">變更協調流程連接埠的變數類型</span><span class="sxs-lookup"><span data-stu-id="431e0-115">To change the variable type for the orchestration ports</span></span>  
  
1.  <span data-ttu-id="431e0-116">在協調流程 檢視中，展開**類型**，依序展開**連接埠類型**，依序展開**ContosoSQLReqResponsePortName**，依序展開**Operation_1**，然後選取**要求**。</span><span class="sxs-lookup"><span data-stu-id="431e0-116">In Orchestration View, expand **Types**, expand **Port Types**, expand **ContosoSQLReqResponsePortName**, expand **Operation_1**, and then select **Request**.</span></span>  
  
2.  <span data-ttu-id="431e0-117">在 屬性 視窗中，選取**訊息類型**屬性中，展開**結構描述**，然後按一下  **\<從參考組件選取 >**。</span><span class="sxs-lookup"><span data-stu-id="431e0-117">In the Properties window, select the **Message Type** property, expand **Schemas** and then click **\<Select from referenced assembly>**.</span></span>  
  
3.  <span data-ttu-id="431e0-118">在 選取成品類型 對話方塊中，按一下  **ContosoPriceAndAvailability**。</span><span class="sxs-lookup"><span data-stu-id="431e0-118">In the Select Artifact Type dialog box, click **ContosoPriceAndAvailability**.</span></span>  
  
4.  <span data-ttu-id="431e0-119">在右窗格中，選取**rootPriceRequest**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="431e0-119">In the right pane, select **rootPriceRequest**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="431e0-120">在協調流程檢視下**Operation_1**，選取**回應**如**ContosoSQLReqResponsePortName**連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="431e0-120">In Orchestration View, under **Operation_1**, select **Response** for the **ContosoSQLReqResponsePortName** port type.</span></span>  
  
6.  <span data-ttu-id="431e0-121">在 屬性 視窗中，選取**訊息類型**屬性中，展開**結構描述**，然後按一下  \<**從參考組件選取 >**。</span><span class="sxs-lookup"><span data-stu-id="431e0-121">In the Properties window, select the **Message Type** property, expand **Schemas** and then click \<**Select from referenced assembly>**.</span></span>  
  
7.  <span data-ttu-id="431e0-122">在**選取成品類型**對話方塊中，按一下  **ContosoPriceAndAvailability**。</span><span class="sxs-lookup"><span data-stu-id="431e0-122">In the **Select Artifact Type** dialog box, click **ContosoPriceAndAvailability**.</span></span>  
  
8.  <span data-ttu-id="431e0-123">在右窗格中，選取**rootPriceResponse**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="431e0-123">In the right pane, select **rootPriceResponse**, and then click **OK**.</span></span>  
  
### <a name="to-connect-the-ports-to-the-receive-shapes"></a><span data-ttu-id="431e0-124">連接連接埠和接收圖形</span><span class="sxs-lookup"><span data-stu-id="431e0-124">To connect the ports to the Receive shapes</span></span>  
  
1.  <span data-ttu-id="431e0-125">協調流程設計介面上，選取**[send_1]**圖形。</span><span class="sxs-lookup"><span data-stu-id="431e0-125">On the orchestration design surface, select the **Send_1** shape.</span></span>  
  
2.  <span data-ttu-id="431e0-126">在 [屬性] 視窗中，選取**訊息**屬性，然後再選取**Contoso3A2RequestMessage**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="431e0-126">In the Properties window, select the **Message** property, and then select **Contoso3A2RequestMessage** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="431e0-127">連接**ContosoSQLReqResponsePort**旁的 選取的綠色控點**要求**標籤，並將它拖曳上的綠色控點**send_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="431e0-127">Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Request** label and dragging it to the green handle on the **Send_1** shape.</span></span>  
  
4.  <span data-ttu-id="431e0-128">協調流程設計介面上，選取**Receive_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="431e0-128">On the orchestration design surface, select the **Receive_1** shape.</span></span>  
  
5.  <span data-ttu-id="431e0-129">在 [屬性] 視窗中，選取**訊息**屬性，然後再選取**Contoso3A2ResponseMessage**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="431e0-129">In the Properties window, select the **Message** property, and then select **Contoso3A2ResponseMessage** from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="431e0-130">連接**ContosoSQLReqResponsePort**旁的 選取的綠色控點**回應**標籤，並將它拖曳上的綠色控點**Receive_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="431e0-130">Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Response** label and dragging it to the green handle on the **Receive_1** shape.</span></span>  
  
7.  <span data-ttu-id="431e0-131">在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="431e0-131">In the **File** Menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431e0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="431e0-132">See Also</span></span>  
 [<span data-ttu-id="431e0-133">步驟 8： 建置與部署 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="431e0-133">Step 8: Building and Deploying the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)