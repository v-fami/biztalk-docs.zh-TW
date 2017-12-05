---
title: "部署和測試應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2c86d5f-1849-4b7d-8061-23f156245f5b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d93284823c2ce5d0c00a1601a5b9ae0aac4643c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="deploy-and-test-the-application"></a><span data-ttu-id="bac34-102">部署和測試應用程式</span><span class="sxs-lookup"><span data-stu-id="bac34-102">Deploy and test the application</span></span>
> [!NOTE]
>  <span data-ttu-id="bac34-103">本教學課程僅適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="bac34-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 <span data-ttu-id="bac34-104">本主題中，我們建置、 部署、 設定及測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="bac34-104">In this topic, we build, deploy, configure, and test the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="build-and-deploy-the-application"></a><span data-ttu-id="bac34-105">建置和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="bac34-105">Build and deploy the application</span></span>  
  
1.  <span data-ttu-id="bac34-106">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bac34-106">In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bac34-107">在 屬性頁面上，按一下 簽署 索引標籤，選取 簽署組件 核取方塊，，從下拉式清單選擇建立新的強式名稱金鑰檔案的選項。</span><span class="sxs-lookup"><span data-stu-id="bac34-107">On the Property page, click the Signing tab, select the Sign the assembly check box, and from the drop-down choose the option to create a new strong name key file.</span></span> <span data-ttu-id="bac34-108">遵循提示來建立檔案。</span><span class="sxs-lookup"><span data-stu-id="bac34-108">Follow the prompts to create the file.</span></span>  
  
3.  <span data-ttu-id="bac34-109">將變更儲存至專案。</span><span class="sxs-lookup"><span data-stu-id="bac34-109">Save changes to the project.</span></span> <span data-ttu-id="bac34-110">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="bac34-110">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="bac34-111">專案建置成功之後，在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="bac34-111">After project builds successfully, in the Solution Explorer, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
## <a name="configure-the-application"></a><span data-ttu-id="bac34-112">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="bac34-112">Configure the application</span></span>  
 <span data-ttu-id="bac34-113">在 設定應用程式，[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]建立傳送和接收埠，然後將它們繫結至協調流程和邏輯傳送/接收埠建立協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="bac34-113">To configure the application, in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], create the send and receive ports and then bind them to the orchestration and the logical send/receive ports created as part of the orchestration.</span></span>  
  
1.  <span data-ttu-id="bac34-114">建立接收埠所接收 JSON 訂單會透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="bac34-114">Create a receive port through which a JSON purchase order is received by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
    1.  <span data-ttu-id="bac34-115">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**.</span><span class="sxs-lookup"><span data-stu-id="bac34-115">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
    2.  <span data-ttu-id="bac34-116">提供接收埠名稱，然後再從左邊的移動瀏覽，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="bac34-116">Provide a name for the receive port, and then from the left pan, click **Receive Locations**.</span></span> <span data-ttu-id="bac34-117">在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="bac34-117">In the **Receive Locations** tab, click **New**.</span></span>  
  
    3.  <span data-ttu-id="bac34-118">指定接收位置的名稱，請選取連接埠類型為**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-118">Specify a name for the receive location, select the port type as **FILE**, and then click **Configure**.</span></span>  
  
    4.  <span data-ttu-id="bac34-119">提供的資料夾位置，從接收位置選取內送的 JSON 訂單的地方。</span><span class="sxs-lookup"><span data-stu-id="bac34-119">Provide the folder location from where the receive location will pick the incoming JSON purchase order.</span></span> <span data-ttu-id="bac34-120">指定`*.json`作為檔案遮罩，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-120">Specify `*.json` as the file mask and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="bac34-121">從**接收管線**下拉式清單中，選取**JSONToXml**。</span><span class="sxs-lookup"><span data-stu-id="bac34-121">From the **Receive Pipeline** drop-down, select **JSONToXml**.</span></span> <span data-ttu-id="bac34-122">建立此自訂接收管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="bac34-122">You created this custom receive pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="bac34-123">以滑鼠右鍵按一下省略符號**（...）**按鈕旁至管線，然後在之下**階段 1 – Deocde 元件**，提供下列值：</span><span class="sxs-lookup"><span data-stu-id="bac34-123">Right-click the ellipsis **(…)** button next to the pipeline, and then under **Stage 1 – Deocde Component**, provide the following values:</span></span>  
  
        -   <span data-ttu-id="bac34-124">根節點-`ROOT`</span><span class="sxs-lookup"><span data-stu-id="bac34-124">RootNode - `ROOT`</span></span>  
  
        -   <span data-ttu-id="bac34-125">RootNodeNamespace –`http://BTSJSON`。</span><span class="sxs-lookup"><span data-stu-id="bac34-125">RootNodeNamespace –`http://BTSJSON`.</span></span>  
  
         <span data-ttu-id="bac34-126">這些值代表目標命名空間和 XML 採購單結構描述所產生 JSON 採購訂單使用 JSON 結構描述精靈中的根節點名稱。</span><span class="sxs-lookup"><span data-stu-id="bac34-126">These values represent the target namespace and the root node name of the XML purchase order schema that was generated from the JSON purchase order using the JSON schema wizard.</span></span>  
  
    6.  <span data-ttu-id="bac34-127">按一下**確定**直到結束所有開啟的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bac34-127">Click **OK** until you exit all open dialog boxes.</span></span>  
  
2.  <span data-ttu-id="bac34-128">建立傳送埠傳送出 JSON 發票訊息。</span><span class="sxs-lookup"><span data-stu-id="bac34-128">Create a send port for sending out JSON invoice messages.</span></span>  
  
    1.  <span data-ttu-id="bac34-129">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態的單向傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="bac34-129">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
    2.  <span data-ttu-id="bac34-130">指定傳送埠的名稱，請選取連接埠類型為**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-130">Specify a name for the send port, select the port type as **FILE**, and then click **Configure**.</span></span>  
  
    3.  <span data-ttu-id="bac34-131">提供傳送埠要將複製的連出 JSON 發票的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="bac34-131">Provide the folder location where the send port copies the outgoing JSON invoice.</span></span> <span data-ttu-id="bac34-132">指定`%MessageID%.json`做為檔案名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-132">Specify `%MessageID%.json` as the file name and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="bac34-133">從**傳送管線**下拉式清單中，選取**XmlToJSON**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-133">From the **Send Pipeline** drop-down, select **XmlToJSON**, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="bac34-134">按一下**確定**直到結束所有開啟的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bac34-134">Click **OK** until you exit all open dialog boxes.</span></span>  
  
3.  <span data-ttu-id="bac34-135">最後，繫結的邏輯連接埠，您建立的實際協調流程連接埠，您現在可以設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="bac34-135">Finally, bind the logical ports you created as part of the orchestration to the physical ports you created now to configure the application.</span></span>  
  
    1.  <span data-ttu-id="bac34-136">以滑鼠右鍵按一下**BizTalk Application 1**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-136">Right-click **BizTalk Application 1**, and then click **Configure**.</span></span>  
  
    2.  <span data-ttu-id="bac34-137">從左窗格中，按一下  **ProcessPO**。</span><span class="sxs-lookup"><span data-stu-id="bac34-137">From the left pane, click **ProcessPO**.</span></span> <span data-ttu-id="bac34-138">從右窗格中，關聯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]裝載，將邏輯連接埠對應到實體連接埠，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="bac34-138">From the right pane, associate a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host, map the logical ports to the physical ports, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="bac34-139">以滑鼠右鍵按一下**BizTalk Application 1**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="bac34-139">Right-click **BizTalk Application 1**, and then click **Start**.</span></span>  
  
## <a name="test-the-application"></a><span data-ttu-id="bac34-140">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="bac34-140">Test the application</span></span>  
  
1.  <span data-ttu-id="bac34-141">瀏覽至您下載時，此範例中，且從**TestMessage**資料夾，複製**JsonPurchaseOrder.json**，並將它貼入您與接收位置相關聯的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bac34-141">Navigate to the sample you downloaded, and from the **TestMessage** folder, copy **JsonPurchaseOrder.json**, and paste it in the folder you associated with the receive location.</span></span> <span data-ttu-id="bac34-142">等候檔案消失時。</span><span class="sxs-lookup"><span data-stu-id="bac34-142">Wait till the file disappears.</span></span>  
  
2.  <span data-ttu-id="bac34-143">瀏覽至您與您所建立的傳送埠相關聯的資料夾。</span><span class="sxs-lookup"><span data-stu-id="bac34-143">Navigate to the folder that you associated with the send port you created.</span></span> <span data-ttu-id="bac34-144">請注意，   ***\<GUID\>*.json**檔案位於資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bac34-144">Notice that a ***\<GUID\>*.json** file is available in the folder.</span></span> <span data-ttu-id="bac34-145">開啟檔案，並確認它是發票訊息。</span><span class="sxs-lookup"><span data-stu-id="bac34-145">Open the file and verify that it’s the invoice message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac34-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="bac34-146">See Also</span></span>  
 [<span data-ttu-id="bac34-147">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="bac34-147">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)