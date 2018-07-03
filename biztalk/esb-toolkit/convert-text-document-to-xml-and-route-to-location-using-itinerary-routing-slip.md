---
title: 如何： 將文字文件轉換成 XML 和路由至檔案位置，以使用路線傳閱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01597a5f-5ca3-440e-ad97-70332233f319
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e6690af0cd326853fc0f96254aaaf7083ccd15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982567"
---
# <a name="how-to-convert-a-text-document-to-xml-and-route-to-a-file-location-using-an-itinerary-routing-slip"></a><span data-ttu-id="ad804-102">如何： 將文字文件轉換成 XML，並路由至使用路線傳閱的檔案位置</span><span class="sxs-lookup"><span data-stu-id="ad804-102">How to: Convert a Text Document to XML and Route to a File Location Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="ad804-103">目標</span><span class="sxs-lookup"><span data-stu-id="ad804-103">Goal</span></span>  
 <span data-ttu-id="ad804-104">一節示範如何建立管線以將文字文件轉換成 XML，然後選取適當的路線並將訊息路由傳送至檔案位置。</span><span class="sxs-lookup"><span data-stu-id="ad804-104">The section demonstrates how to create a pipeline that will convert a text document to XML and then select the appropriate itinerary and route the message to a FILE location.</span></span>  
  
 <span data-ttu-id="ad804-105">在本使用說明主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ad804-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="ad804-106">您可以使用管線來接收一般檔案文件，並將它轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="ad804-106">Use a pipeline to receive a flat file document and convert it to XML.</span></span>  
  
-   <span data-ttu-id="ad804-107">設定路線選取器管線元件來解析適當的傳閱名單。</span><span class="sxs-lookup"><span data-stu-id="ad804-107">Configure the Itinerary Selector pipeline component to resolve the appropriate routing slip.</span></span>  
  
-   <span data-ttu-id="ad804-108">建立入口匝使用自訂管線。</span><span class="sxs-lookup"><span data-stu-id="ad804-108">Create an on-ramp that uses the custom pipeline.</span></span>  
  
-   <span data-ttu-id="ad804-109">以路線為基礎的一般檔案訊息路由的測試。</span><span class="sxs-lookup"><span data-stu-id="ad804-109">Test itinerary-based routing of a flat file message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ad804-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="ad804-110">Prerequisites</span></span>  
 <span data-ttu-id="ad804-111">本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="ad804-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ad804-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="ad804-112">Before You Begin</span></span>  
 <span data-ttu-id="ad804-113">您執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="ad804-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
- <span data-ttu-id="ad804-114">部署**DataFormatTransformation**路線。</span><span class="sxs-lookup"><span data-stu-id="ad804-114">Deploy the **DataFormatTransformation** itinerary.</span></span>  
  
- <span data-ttu-id="ad804-115">建立測試訊息。</span><span class="sxs-lookup"><span data-stu-id="ad804-115">Create the test message.</span></span>  
  
  <span data-ttu-id="ad804-116">下列程序描述如何進行每一種。</span><span class="sxs-lookup"><span data-stu-id="ad804-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-deploy-the-dataformattransformation-itinerary"></a><span data-ttu-id="ad804-117">若要部署 DataFormatTransformation 路線</span><span class="sxs-lookup"><span data-stu-id="ad804-117">To deploy the DataFormatTransformation itinerary</span></span>  
  
1.  <span data-ttu-id="ad804-118">在 Visual Studio 中，開啟 [C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln]。</span><span class="sxs-lookup"><span data-stu-id="ad804-118">In Visual Studio, open C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln.</span></span>  
  
2.  <span data-ttu-id="ad804-119">在 方案總管中**Itinerary.Library**專案中，按兩下**DataFormatTransformation.itinerary**在路線設計工具中開啟它。</span><span class="sxs-lookup"><span data-stu-id="ad804-119">In Solution Explorer, in the **Itinerary.Library** project, double-click **DataFormatTransformation.itinerary** to open it in the Itinerary Designer.</span></span>  
  
3.  <span data-ttu-id="ad804-120">在 Visual Studio 中，按一下設計介面**DataFormatTransformation.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="ad804-120">In Visual Studio, click the design surface of **DataFormatTransformation.itinerary**.</span></span> <span data-ttu-id="ad804-121">在 [ **DataFormatTransformation.itinerary**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ad804-121">In the **DataFormatTransformation.itinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="ad804-122">在 **路線狀態**下拉式清單中，按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="ad804-122">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    2.  <span data-ttu-id="ad804-123">在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="ad804-123">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="ad804-124">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="ad804-124">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    4.  <span data-ttu-id="ad804-125">在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="ad804-125">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
4.  <span data-ttu-id="ad804-126">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="ad804-126">Save all project artifacts.</span></span>  
  
5.  <span data-ttu-id="ad804-127">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**DataModelTransformation**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="ad804-127">In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.</span></span>  
  
#### <a name="to-create-the-receive-pipeline"></a><span data-ttu-id="ad804-128">若要建立的接收管線</span><span class="sxs-lookup"><span data-stu-id="ad804-128">To create the receive pipeline</span></span>  
  
1.  <span data-ttu-id="ad804-129">在 Visual Studio 中，以滑鼠右鍵按一下**DataFormatTransformation.Schemas**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ad804-129">In Visual Studio, right-click **DataFormatTransformation.Schemas**, and then click **Properties**.</span></span> <span data-ttu-id="ad804-130">按一下 [**應用程式**，然後輸入**GlobalBank.ESB.DataFormatTransformation.Schemas**中**組件名稱**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ad804-130">Click **Application**, and then type **GlobalBank.ESB.DataFormatTransformation.Schemas** in the **Assembly name** box.</span></span>  
  
2.  <span data-ttu-id="ad804-131">以滑鼠右鍵按一下**DataFormatTransformation.Schemas**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ad804-131">Right-click **DataFormatTransformation.Schemas**, and then click **Properties**.</span></span> <span data-ttu-id="ad804-132">按一下  **Signing**，然後確認**簽署組件**核取方塊已選取，而且此組件位置指向 **。\\...\\..\\..\\..\\..\keys\Microsoft.Practices.ESB.snk**。</span><span class="sxs-lookup"><span data-stu-id="ad804-132">Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **.\\..\\..\\..\\..\\..\keys\Microsoft.Practices.ESB.snk**.</span></span>  
  
3.  <span data-ttu-id="ad804-133">以滑鼠右鍵按一下**DataFormatTransformation.Pipelines**，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="ad804-133">Right-click **DataFormatTransformation.Pipelines**, and then click **Remove**.</span></span>  
  
4.  <span data-ttu-id="ad804-134">以滑鼠右鍵按一下**DataFormatTransformation**，指向**新增**，然後按一下**新專案**。</span><span class="sxs-lookup"><span data-stu-id="ad804-134">Right-click **DataFormatTransformation**, point to **Add**, and then click **New Project**.</span></span> <span data-ttu-id="ad804-135">按一下  **Biztalk 專案**，然後按一下**空白 Biztalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="ad804-135">Click **Biztalk Projects**, and then click **Empty Biztalk Server Project**.</span></span> <span data-ttu-id="ad804-136">在 **名稱**方塊中，輸入**DataFormatTransformationReceive.Pipeline**。</span><span class="sxs-lookup"><span data-stu-id="ad804-136">In the **Name** box, type **DataFormatTransformationReceive.Pipeline**.</span></span>  
  
5.  <span data-ttu-id="ad804-137">以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ad804-137">Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**.</span></span> <span data-ttu-id="ad804-138">按一下  **Signing**，然後確認**簽署組件**核取方塊已選取，而且此組件位置指向**C:\projects\Microsoft.Practices.ESB\keys\Microsoft.Practices.ESB.snk**。</span><span class="sxs-lookup"><span data-stu-id="ad804-138">Click **Signing**, and then verify that the **Sign the assembly** check box is selected and that the assembly location points to **C:\projects\Microsoft.Practices.ESB\keys\Microsoft.Practices.ESB.snk**.</span></span>  
  
6.  <span data-ttu-id="ad804-139">以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="ad804-139">Right-click **DataFormatTransformationReceive.Pipeline**, point to **Add**, and then click **New Item**.</span></span>  
  
7.  <span data-ttu-id="ad804-140">在 **加入新項目** 對話方塊中，按一下**接收管線**範本 窗格中。</span><span class="sxs-lookup"><span data-stu-id="ad804-140">In the **Add New Item** dialog box, click **Receive Pipeline** in the Templates pane.</span></span> <span data-ttu-id="ad804-141">在 **名稱**方塊中，輸入**ItinerarySelectReceiveFF**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ad804-141">In the **Name** box, type **ItinerarySelectReceiveFF**, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="ad804-142">以滑鼠右鍵按一下**參考**為 DataFormatTransformationReceive.Pipeline 專案，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="ad804-142">Right-click **References** for the DataFormatTransformationReceive.Pipeline project, and then click **Add Reference**.</span></span> <span data-ttu-id="ad804-143">按一下 **專案**索引標籤，然後再按一下**DataFormatTransformation.Schemas**。</span><span class="sxs-lookup"><span data-stu-id="ad804-143">Click the **Projects** tab, and then click **DataFormatTransformation.Schemas**.</span></span> <span data-ttu-id="ad804-144">按一下 **確定**加入參考。</span><span class="sxs-lookup"><span data-stu-id="ad804-144">Click **OK** to add the reference.</span></span>  
  
9. <span data-ttu-id="ad804-145">從 [工具箱] 拖曳**一般檔案解譯器**管線元件來**解譯**管線階段。</span><span class="sxs-lookup"><span data-stu-id="ad804-145">From the Toolbox, drag a **Flat file disassembler** pipeline component to the **Disassemble** stage of the pipeline.</span></span>  
  
10. <span data-ttu-id="ad804-146">在 屬性 視窗的 一般檔案解譯，請按一下**DataModelTransformation.Schemas.NAOrderDocFF**中**文件結構描述**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ad804-146">In the Properties window for the flat file disassemble, click **DataModelTransformation.Schemas.NAOrderDocFF** in the **Document schema** drop-down list.</span></span>  
  
11. <span data-ttu-id="ad804-147">從 [工具箱] 拖曳**ESB 路線選取器**管線元件來**解析合作對象**管線階段。</span><span class="sxs-lookup"><span data-stu-id="ad804-147">From the Toolbox, drag an **ESB Itinerary Selector** pipeline component to the **Resolve Party** stage of the pipeline.</span></span>  
  
12. <span data-ttu-id="ad804-148">從 [工具箱] 拖曳**ESB 發送器**管線元件來**解析合作對象**管線階段，然後將其下放置**ESB 路線選取器**管線元件。</span><span class="sxs-lookup"><span data-stu-id="ad804-148">From the Toolbox, drag an **ESB Dispatcher** pipeline component to the **Resolve Party** stage of the pipeline, and then place it under the **ESB Itinerary Selector** pipeline component.</span></span>  
  
13. <span data-ttu-id="ad804-149">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="ad804-149">Save all project artifacts.</span></span>  
  
## <a name="to-create-the-test-message"></a><span data-ttu-id="ad804-150">若要建立測試訊息</span><span class="sxs-lookup"><span data-stu-id="ad804-150">To create the test message</span></span>  
  
1.  <span data-ttu-id="ad804-151">DataFormatTransformation.Schemas 專案 NAOrderDocFF.xsd 結構描述檔案時，按一次。</span><span class="sxs-lookup"><span data-stu-id="ad804-151">Click once in the NAOrderDocFF.xsd schema file of the DataFormatTransformation.Schemas project.</span></span> <span data-ttu-id="ad804-152">在 Visual Studio 的 [屬性] 窗格中，變更下列兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="ad804-152">In the Properties pane of Visual Studio, change the following two properties:</span></span>  
  
    -   <span data-ttu-id="ad804-153">**產生執行個體輸出類型**。</span><span class="sxs-lookup"><span data-stu-id="ad804-153">**Generate Instance Output Type**.</span></span> <span data-ttu-id="ad804-154">按一下這個屬性，以將它變更為下拉式清單**原生**。</span><span class="sxs-lookup"><span data-stu-id="ad804-154">Click the drop-down list for this property to change it to **Native**.</span></span>  
  
    -   <span data-ttu-id="ad804-155">**輸出執行個體檔案名稱**。</span><span class="sxs-lookup"><span data-stu-id="ad804-155">**Output Instance Filename**.</span></span> <span data-ttu-id="ad804-156">按一下此屬性的省略符號按鈕 （...） 並接受 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation 的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="ad804-156">Click the ellipsis button (…) for this property and accept the default path of C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation.</span></span> <span data-ttu-id="ad804-157">在 **檔名**方塊中，輸入**NAOrderDocFF**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="ad804-157">In the **File name** box, type **NAOrderDocFF**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="ad804-158">以滑鼠右鍵按一下**NAOrderDocFF.xsd**下方**DataFormatTransformation.Schemas**，然後按一下**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="ad804-158">Right-click **NAOrderDocFF.xsd** under **DataFormatTransformation.Schemas**, and then click **Generate Instance**.</span></span> <span data-ttu-id="ad804-159">此時，您應該有 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation 目錄中產生新的檔案。</span><span class="sxs-lookup"><span data-stu-id="ad804-159">At this point, you should have a new file generated in the C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation directory.</span></span>  
  
3.  <span data-ttu-id="ad804-160">複製 （不會移動） 檔案至 C:\HowTos 從 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation NAOrderDocFF.txt。</span><span class="sxs-lookup"><span data-stu-id="ad804-160">Copy (do not move) the file NAOrderDocFF.txt from C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation to C:\HowTos.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad804-161">這是您將會接收並轉換為 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad804-161">This is the message you will receive and convert to XML.</span></span> <span data-ttu-id="ad804-162">這份文件表示 North American 訂單文件的一般檔案版本。</span><span class="sxs-lookup"><span data-stu-id="ad804-162">This document represents a flat file version of North American Order document.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="ad804-163">步驟</span><span class="sxs-lookup"><span data-stu-id="ad804-163">Steps</span></span>  
  
#### <a name="to-deploy-the-receive-pipeline-and-the-schema"></a><span data-ttu-id="ad804-164">若要部署的接收管線和結構描述</span><span class="sxs-lookup"><span data-stu-id="ad804-164">To deploy the receive pipeline and the schema</span></span>  
  
1.  <span data-ttu-id="ad804-165">以滑鼠右鍵按一下**DataFormatTransformationReceive.Pipeline**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ad804-165">Right-click **DataFormatTransformationReceive.Pipeline**, and then click **Properties**.</span></span> <span data-ttu-id="ad804-166">按一下 [**部署**，然後輸入**Microsoft.Practices.ESB**中**應用程式名稱**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ad804-166">Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.</span></span>  
  
2.  <span data-ttu-id="ad804-167">以滑鼠右鍵按一下**DataFormatTransformation.Schemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ad804-167">Right-click the **DataFormatTransformation.Schemas** project, and then click **Properties**.</span></span> <span data-ttu-id="ad804-168">按一下 [**部署**，然後輸入**Microsoft.Practices.ESB**中**應用程式名稱**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ad804-168">Click **Deployment**, and then type **Microsoft.Practices.ESB** in the **Application Name** box.</span></span>  
  
3.  <span data-ttu-id="ad804-169">關閉 [屬性] 窗格，針對**DataFormatTransformationReceive.Pipeline**並**DataFormatTransformation.Schemas**。</span><span class="sxs-lookup"><span data-stu-id="ad804-169">Close the Properties panes for both **DataFormatTransformationReceive.Pipeline** and **DataFormatTransformation.Schemas**.</span></span>  
  
4.  <span data-ttu-id="ad804-170">在 [方案總管] 中，以滑鼠右鍵按一下**DataFormatTransformation**專案，然後再按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="ad804-170">In Solution Explorer, right-click the **DataFormatTransformation** project, and then click **Deploy Solution**.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="ad804-171">建立和設定 ESB 匝道</span><span class="sxs-lookup"><span data-stu-id="ad804-171">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="ad804-172">按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ad804-172">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ad804-173">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，展開**應用程式**，然後按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="ad804-173">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then click **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="ad804-174">以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="ad804-174">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="ad804-175">在 [**選取接收埠**] 對話方塊中，按一下**OnRamp.Itinerary**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ad804-175">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ad804-176">在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.FlatFile.FILE**。</span><span class="sxs-lookup"><span data-stu-id="ad804-176">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.FlatFile.FILE**.</span></span>  
  
6.  <span data-ttu-id="ad804-177">在 **型別**下拉式清單中，按一下**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="ad804-177">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="ad804-178">在  **FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**。</span><span class="sxs-lookup"><span data-stu-id="ad804-178">In the **FILE Transport Properties** dialog box, in the **Receive Folder** box, type **C:\HowTos\DropFolder**.</span></span>  
  
8.  <span data-ttu-id="ad804-179">中**FILE 傳輸屬性**對話方塊中，於**檔案遮罩**方塊中，輸入 **\*.txt**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ad804-179">In the **FILE Transport Properties** dialog box, in the **File mask** box, type **\*.txt**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="ad804-180">若要設定路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="ad804-180">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="ad804-181">在 **接收位置屬性** 對話方塊中，按一下**ItinerarySelectReceiveFF**中**接收管線**下拉式清單中，然後按一下 省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="ad804-181">In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveFF** in the **Receive pipeline** drop down list, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="ad804-182">使用**設定管線**對話方塊，即可設定下列各項**路線選取器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="ad804-182">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="ad804-183">按一下  **ItineraryFactKey**屬性，然後按**Resolver.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="ad804-183">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="ad804-184">按一下  **ResolverConnectionString**屬性中，輸入**路線：\\\name=DataFormatTransformation;** ，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ad804-184">Click the **ResolverConnectionString** property, type **ITINERARY:\\\name=DataFormatTransformation;** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ad804-185">按一下 [ **[確定]** 以關閉**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ad804-185">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="ad804-186">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.FlatFile.FILE**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="ad804-186">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-itinerary-based-routing-of-a-flat-file-message"></a><span data-ttu-id="ad804-187">若要測試以路線為基礎的一般檔案訊息路由</span><span class="sxs-lookup"><span data-stu-id="ad804-187">To test itinerary-based routing of a flat file message</span></span>  
  
1.  <span data-ttu-id="ad804-188">在 Windows 檔案總管中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="ad804-188">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="ad804-189">複製 （不會移動） 到 C:\HowTos\DropFolder NAOrderDocFF.txt。</span><span class="sxs-lookup"><span data-stu-id="ad804-189">Copy (do not move) NAOrderDocFF.txt to C:\HowTos\DropFolder.</span></span>  
  
3.  <span data-ttu-id="ad804-190">瀏覽至 C:\HowTos\Out。確認目錄中已寫入 DFT%MessageID%.xml 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad804-190">Browse to C:\HowTos\Out. Verify that the DFT%MessageID%.xml message has been written to the directory.</span></span>  
  
4.  <span data-ttu-id="ad804-191">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.FlatFile.FILE**接收位置，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="ad804-191">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.FlatFile.FILE** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="ad804-192">在後**OnRamp.Itinerary.FlatFile.FILE**接收位置已停用，以滑鼠右鍵按一下，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="ad804-192">After the **OnRamp.Itinerary.FlatFile.FILE** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="ad804-193">在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="ad804-193">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="ad804-194">其他資源</span><span class="sxs-lookup"><span data-stu-id="ad804-194">Additional Resources</span></span>  
 <span data-ttu-id="ad804-195">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="ad804-195">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="ad804-196">如何：轉換訊息，並使用路線傳閱名單將產生的訊息路由至檔案位置</span><span class="sxs-lookup"><span data-stu-id="ad804-196">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="ad804-197">如何：使用路線傳閱名單將單一訊息路由至多個收件者</span><span class="sxs-lookup"><span data-stu-id="ad804-197">How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip</span></span>](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
-   [<span data-ttu-id="ad804-198">開發活動</span><span class="sxs-lookup"><span data-stu-id="ad804-198">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="ad804-199">訊息轉換模式</span><span class="sxs-lookup"><span data-stu-id="ad804-199">Message Transformation Patterns</span></span>](../esb-toolkit/message-transformation-patterns.md)