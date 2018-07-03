---
title: 逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- InfoPath forms, creating
- InfoPath forms, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, integrating Microsoft Office
- Windows SharePoint Services, document libraries
ms.assetid: 2f81a712-bb20-4c32-bbac-fb438deded38
caps.latest.revision: 48
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79297c55152688821ba5b472335eade1d31b0ffe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022388"
---
# <a name="walkthrough-module-2---integrating-office-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="536c2-102">逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="536c2-102">Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="536c2-103">這個逐步解說會將延續[逐步解說： 模組 1-傳送和接收 Windows SharePoint Services 配接器的訊息](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)，並說明如何整合 Microsoft Office 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以內容為基礎您所建立的路由 (CBR) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="536c2-103">This walkthrough is a continuation of [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and shows you how to integrate Microsoft Office with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] content-based routing (CBR) application you created.</span></span> <span data-ttu-id="536c2-104">如需 Windows SharePoint Services 配接器的簡介，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="536c2-104">For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="536c2-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="536c2-105">Prerequisites</span></span>  
 <span data-ttu-id="536c2-106">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="536c2-106">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
- <span data-ttu-id="536c2-107">您必須擁有的完整安裝的單一伺服器部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="536c2-107">You must have a single-server deployment with a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="536c2-108">您必須完成下列逐步解說：[逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="536c2-108">You must complete the following walkthrough: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)</span></span>  
  
  <span data-ttu-id="536c2-109">在多重伺服器部署中使用 Windows SharePoint Services 配接器的相關資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="536c2-109">For information about using the Windows SharePoint Services Adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="create-a-biztalk-project"></a><span data-ttu-id="536c2-110">建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="536c2-110">Create a BizTalk project</span></span>  
 <span data-ttu-id="536c2-111">在此程序中，您要使用 [BizTalk 編輯器] 建立空白的 BizTalk 專案與結構描述。</span><span class="sxs-lookup"><span data-stu-id="536c2-111">In this procedure you create an empty BizTalk project and a schema using the BizTalk Editor.</span></span> <span data-ttu-id="536c2-112">必須執行這個程序，才能建立稍後要使用的 InfoPath 表單結構描述。</span><span class="sxs-lookup"><span data-stu-id="536c2-112">This procedure is required to create the schema for the InfoPath form that is used later.</span></span>  
  
#### <a name="create-a-strong-name-key-file"></a><span data-ttu-id="536c2-113">建立強式名稱金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="536c2-113">Create a strong name key file</span></span>  
  
1.  <span data-ttu-id="536c2-114">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="536c2-114">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="536c2-115">型別`sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="536c2-115">Type `sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`, and then press **Enter**.</span></span> <span data-ttu-id="536c2-116">將會撰寫金鑰組。</span><span class="sxs-lookup"><span data-stu-id="536c2-116">The key pair will be written.</span></span>  
  
3.  <span data-ttu-id="536c2-117">關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="536c2-117">Close the command prompt.</span></span>  
  
#### <a name="create-an-empty-biztalk-project"></a><span data-ttu-id="536c2-118">建立空白 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="536c2-118">Create an empty BizTalk project</span></span>  
  
1.  <span data-ttu-id="536c2-119">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="536c2-119">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="536c2-120">按一下 **檔案**，**新增**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="536c2-120">Click **File**, **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="536c2-121">底下**專案類型**，選取**BizTalk 專案**。</span><span class="sxs-lookup"><span data-stu-id="536c2-121">Under **Project types**, select **BizTalk Projects**.</span></span>  
  
4.  <span data-ttu-id="536c2-122">底下**範本**，選取**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="536c2-122">Under **Templates**, select **Empty BizTalk Server Project**.</span></span>  
  
5.  <span data-ttu-id="536c2-123">型別`OrderProcess`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-123">Type `OrderProcess` in the **Name** field.</span></span>  
  
6.  <span data-ttu-id="536c2-124">輸入您的工作目錄中的檔案路徑**位置**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-124">Type the file path to your working directory in the **Location** field.</span></span> <span data-ttu-id="536c2-125">例如， `C:\WSSAdapterWalkthrough\`。</span><span class="sxs-lookup"><span data-stu-id="536c2-125">For example, `C:\WSSAdapterWalkthrough\`.</span></span>  
  
7.  <span data-ttu-id="536c2-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="536c2-126">Click **OK**.</span></span>  
  
#### <a name="associate-the-key-file-with-the-assembly"></a><span data-ttu-id="536c2-127">將金鑰檔案與組件建立關聯</span><span class="sxs-lookup"><span data-stu-id="536c2-127">Associate the key file with the assembly</span></span>  
  
1.  <span data-ttu-id="536c2-128">在 方案總管 中，以滑鼠右鍵按一下`OrderProcess`專案，然後再按一下**屬性**以啟動 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="536c2-128">In Solution Explorer, right-click the `OrderProcess` project, and then click **Properties** to launch the Project Designer.</span></span>  
  
2.  <span data-ttu-id="536c2-129">按一下 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="536c2-129">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="536c2-130">選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-130">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
4.  <span data-ttu-id="536c2-131">輸入 `C:\WSSAdapterWalkthrough\OrderProcess.snk`。</span><span class="sxs-lookup"><span data-stu-id="536c2-131">Type `C:\WSSAdapterWalkthrough\OrderProcess.snk`.</span></span>  
  
5.  <span data-ttu-id="536c2-132">按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-132">Click **Open**.</span></span>  
  
#### <a name="create-an-xsd-schema-by-using-the-biztalk-editor"></a><span data-ttu-id="536c2-133">使用 [BizTalk 編輯器] 建立 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="536c2-133">Create an XSD schema by using the BizTalk Editor</span></span>  
  
1. <span data-ttu-id="536c2-134">在 [方案總管] 中，以滑鼠右鍵按一下`OrderProcess`專案中，按一下**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="536c2-134">In Solution Explorer, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.</span></span>  
  
2. <span data-ttu-id="536c2-135">底下**分類**，按一下**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="536c2-135">Under **Categories**, click **Schema Files**.</span></span>  
  
3. <span data-ttu-id="536c2-136">底下**範本**，按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="536c2-136">Under **Templates**, click **Schema**.</span></span>  
  
4. <span data-ttu-id="536c2-137">型別`OrderProcessSchema`中**名稱**欄位，，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="536c2-137">Type `OrderProcessSchema` in the **Name** field, and then click **Add**.</span></span>  
  
5. <span data-ttu-id="536c2-138">在 [屬性] 視窗`OrderProcessSchema`，選取`Qualified`for **Element FormDefault**屬性。</span><span class="sxs-lookup"><span data-stu-id="536c2-138">In the Properties Window for `OrderProcessSchema`, select `Qualified` for the **Element FormDefault** property.</span></span>  
  
6. <span data-ttu-id="536c2-139">在 [屬性] 視窗`OrderProcessSchema`，型別`http://OrderProcess.PurchaseOrder`中**目標命名空間**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-139">In the Properties Window for `OrderProcessSchema`, type `http://OrderProcess.PurchaseOrder` in the **Target Namespace** field.</span></span>  
  
7. <span data-ttu-id="536c2-140">在**BizTalk 編輯器**，以滑鼠右鍵按一下`Root`，按一下 **重新命名**，然後輸入`PurchaseOrder`。</span><span class="sxs-lookup"><span data-stu-id="536c2-140">In the **BizTalk Editor**, right-click `Root`, click **Rename**, and then type `PurchaseOrder`.</span></span>  
  
8. <span data-ttu-id="536c2-141">以滑鼠右鍵按一下**PurchaseOrder**節點中，按一下**插入結構描述節點**，然後按一下**子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="536c2-141">Right-click the **PurchaseOrder** node, click **Insert Schema Node**, then click **Child Field Element**.</span></span>  
  
9. <span data-ttu-id="536c2-142">將它命名為 `PurchaseOrderID`。</span><span class="sxs-lookup"><span data-stu-id="536c2-142">Name it `PurchaseOrderID`.</span></span>  
  
10. <span data-ttu-id="536c2-143">建立另一個子欄位項目並命名為`BillTo`。</span><span class="sxs-lookup"><span data-stu-id="536c2-143">Create another child field element and name it `BillTo`.</span></span>  
  
11. <span data-ttu-id="536c2-144">建立另一個子欄位項目並命名為`Amount`。</span><span class="sxs-lookup"><span data-stu-id="536c2-144">Create another child field element and name it `Amount`.</span></span>  
  
12. <span data-ttu-id="536c2-145">在 [屬性] 視窗中，設定**資料型別**屬性`Amount`為 xs: unsignedint。</span><span class="sxs-lookup"><span data-stu-id="536c2-145">In the Properties Window, set the **Data Type** property for `Amount` to xs:unsignedInt.</span></span>  
  
13. <span data-ttu-id="536c2-146">建立另一個子欄位項目並命名為`PurchaseOrderDate`。</span><span class="sxs-lookup"><span data-stu-id="536c2-146">Create another child field element and name it `PurchaseOrderDate`.</span></span>  
  
14. <span data-ttu-id="536c2-147">在 [屬性] 視窗中，設定**資料型別**屬性`PurchaseOrderDate`為 xs: datetime。</span><span class="sxs-lookup"><span data-stu-id="536c2-147">In the Properties Window, set the **Data Type** property for `PurchaseOrderDate` to xs:dateTime.</span></span>  
  
15. <span data-ttu-id="536c2-148">按一下 **檔案**，然後按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="536c2-148">Click **File**, and then click **Save All**.</span></span>  
  
16. <span data-ttu-id="536c2-149">關閉 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="536c2-149">Close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="create-an-infopath-form"></a><span data-ttu-id="536c2-150">建立 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="536c2-150">Create an InfoPath form</span></span>  
 <span data-ttu-id="536c2-151">在此程序中，您要根據在上一個程序所建立的結構描述，建立另一個文件庫與 InfoPath 表單。</span><span class="sxs-lookup"><span data-stu-id="536c2-151">In this procedure you create another document library and an InfoPath form based on the schema you created in the last procedure.</span></span> <span data-ttu-id="536c2-152">此 InfoPath 表單會用來提交文件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="536c2-152">This InfoPath form will be used to submit a document to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="536c2-153">本逐步解說需要 Microsoft Office InfoPath 2007</span><span class="sxs-lookup"><span data-stu-id="536c2-153">This walkthrough requires Microsoft Office InfoPath 2007</span></span>  
  
#### <a name="create-a-new-document-library"></a><span data-ttu-id="536c2-154">建立新文件庫</span><span class="sxs-lookup"><span data-stu-id="536c2-154">Create a new document library</span></span>  
  
1.  <span data-ttu-id="536c2-155">開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="536c2-155">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="536c2-156">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="536c2-156">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="536c2-157">在上方導覽列中，按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="536c2-157">On the top navigation bar, click **Create**.</span></span>  
  
3.  <span data-ttu-id="536c2-158">底下**文件庫**，按一下**文件庫**。</span><span class="sxs-lookup"><span data-stu-id="536c2-158">Under **Document Libraries**, click **Document Library**.</span></span>  
  
4.  <span data-ttu-id="536c2-159">在 [**名稱和描述**區段中，輸入`InfoPathSolutions`中**名稱] 欄位**。</span><span class="sxs-lookup"><span data-stu-id="536c2-159">In the **Name and Description** section, type `InfoPathSolutions` in the **Name field**.</span></span>  
  
5.  <span data-ttu-id="536c2-160">在 [**瀏覽**區段中，選取**是**快速啟動] 列上顯示此表單程式庫。</span><span class="sxs-lookup"><span data-stu-id="536c2-160">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
6.  <span data-ttu-id="536c2-161">在 **文件範本**區段中，選取`None`如**文件範本**。</span><span class="sxs-lookup"><span data-stu-id="536c2-161">In the **Document Template** section, select `None` for the **Document Template**.</span></span>  
  
7.  <span data-ttu-id="536c2-162">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-162">Click **Create**.</span></span> <span data-ttu-id="536c2-163">您將被重新導向至剛建立的空白文件庫。</span><span class="sxs-lookup"><span data-stu-id="536c2-163">You will be redirected to the empty library you just created.</span></span>  
  
8.  <span data-ttu-id="536c2-164">在左側，按一下**修改設定和資料行**。</span><span class="sxs-lookup"><span data-stu-id="536c2-164">On the left side, click **Modify Settings and Columns**.</span></span>  
  
9. <span data-ttu-id="536c2-165">底下**資料行**，按一下**加入新的資料行**。</span><span class="sxs-lookup"><span data-stu-id="536c2-165">Under **Columns**, click **Add a New Column**.</span></span>  
  
10. <span data-ttu-id="536c2-166">底下**名稱和型別**，型別`Namespace`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-166">Under **Name and Type**, type `Namespace` in the **Name** field.</span></span>  
  
11. <span data-ttu-id="536c2-167">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="536c2-167">Click **OK**.</span></span>  
  
12. <span data-ttu-id="536c2-168">關閉 `WSSAdapterWalkthrough` 網站。</span><span class="sxs-lookup"><span data-stu-id="536c2-168">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
#### <a name="create-an-infopath-form-based-on-the-orderprocessschema-schema-file"></a><span data-ttu-id="536c2-169">根據 OrderProcessSchema 結構描述檔案建立 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="536c2-169">Create an InfoPath form based on the OrderProcessSchema schema file</span></span>  
  
1.  <span data-ttu-id="536c2-170">按一下 **開始**，指向**所有程式**，指向**Microsoft Office**，然後按一下**Microsoft Office InfoPath 2007**。</span><span class="sxs-lookup"><span data-stu-id="536c2-170">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office InfoPath 2007**.</span></span>  
  
2.  <span data-ttu-id="536c2-171">在 **填滿表單**對話方塊中，選取**設計的表單。**</span><span class="sxs-lookup"><span data-stu-id="536c2-171">In the **Fill Out a Form** dialog box, select **Design a Form.**</span></span>  
  
3.  <span data-ttu-id="536c2-172">在 **設計表單**工作窗格中，選取**從 XML 文件或結構描述新增**。</span><span class="sxs-lookup"><span data-stu-id="536c2-172">In the **Design a Form** task pane, select **New from XML Document or Schema**.</span></span>  
  
4.  <span data-ttu-id="536c2-173">在 **資料來源精靈**，按一下**瀏覽**並選取您在上一個程序中建立的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="536c2-173">In the **Data Source Wizard**, click **Browse** and select the schema file you created in the last procedure.</span></span> <span data-ttu-id="536c2-174">例如， `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`。</span><span class="sxs-lookup"><span data-stu-id="536c2-174">For example, `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`.</span></span>  
  
5.  <span data-ttu-id="536c2-175">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-175">Click **Next**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="536c2-176">在 **資料來源**工作窗格中，以滑鼠右鍵按一下**PurchaseOrder**節點，然後再按一下**有控制項區段**。</span><span class="sxs-lookup"><span data-stu-id="536c2-176">In the **Data Source** task pane, right-click the **PurchaseOrder** node, and then click **Section with Controls**.</span></span> <span data-ttu-id="536c2-177">將在範本上建立表單。</span><span class="sxs-lookup"><span data-stu-id="536c2-177">This will create the form on the template.</span></span>  
  
7.  <span data-ttu-id="536c2-178">按一下 **檔案**，按一下**儲存**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="536c2-178">Click **File**, click **Save**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="536c2-179">在 [**另存新檔**] 對話方塊中，輸入`PurchaseOrder.xsn`中**檔案名稱**欄位，，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="536c2-179">In the **Save As** dialog box, type `PurchaseOrder.xsn` in the **File name** field, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="536c2-180">按一下 **檔案**，然後按一下**發佈**。</span><span class="sxs-lookup"><span data-stu-id="536c2-180">Click **File**, and then click **Publish**.</span></span>  
  
10. <span data-ttu-id="536c2-181">在 [**發佈精靈**，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-181">In the **Publishing Wizard**, click **Next**.</span></span>  
  
11. <span data-ttu-id="536c2-182">選取 [**至 Web 伺服器**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-182">Select **To a Web Server**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="536c2-183">輸入的路徑和檔案名稱，以便您`InfoPathSolutions`文件庫，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="536c2-183">Type the path and filename to your `InfoPathSolutions` document library, and then click **Next**.</span></span> <span data-ttu-id="536c2-184">例如， `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`。</span><span class="sxs-lookup"><span data-stu-id="536c2-184">For example, `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`.</span></span>  
  
13. <span data-ttu-id="536c2-185">按一下 **完成**，然後按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="536c2-185">Click **Finish**, and then click **Close**.</span></span>  
  
14. <span data-ttu-id="536c2-186">關閉 Microsoft InfoPath。</span><span class="sxs-lookup"><span data-stu-id="536c2-186">Close Microsoft InfoPath.</span></span>  
  
## <a name="modify-the-sharepoint-document-libraries"></a><span data-ttu-id="536c2-187">修改 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="536c2-187">Modify the SharePoint document libraries</span></span>  
 <span data-ttu-id="536c2-188">在此程序中，您將更新 PurchaseOrder.xsn 檔案的命名空間屬性並修改 [目的地] 文件庫。</span><span class="sxs-lookup"><span data-stu-id="536c2-188">In this procedure you will update the namespace property for the PurchaseOrder.xsn file and modify the Destination Document Library.</span></span> <span data-ttu-id="536c2-189">判斷以內容為基礎的路由實例所發佈之文件的訂閱者時，會使用此命名空間做為變數。</span><span class="sxs-lookup"><span data-stu-id="536c2-189">This namespace is used as a variable when determining subscribers of published documents for content based routing scenarios.</span></span>  
  
#### <a name="update-the-namespace-for-purchaseorderxsn"></a><span data-ttu-id="536c2-190">更新 PurchaseOrder.xsn 的命名空間</span><span class="sxs-lookup"><span data-stu-id="536c2-190">Update the namespace for PurchaseOrder.xsn</span></span>  
  
1.  <span data-ttu-id="536c2-191">開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="536c2-191">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="536c2-192">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="536c2-192">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="536c2-193">在左側，底下**文件**，按一下  `InfoPathSolutions`。</span><span class="sxs-lookup"><span data-stu-id="536c2-193">On the left side, under **Documents**, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="536c2-194">將指標移`PurchaseOrder.xsn`，以滑鼠右鍵按一下，然後按一下 **編輯屬性**。</span><span class="sxs-lookup"><span data-stu-id="536c2-194">Move the pointer over `PurchaseOrder.xsn`, right-click it, and then click **Edit Properties**.</span></span>  
  
4.  <span data-ttu-id="536c2-195">型別`http://OrderProcess.PurchaseOrder`中**命名空間**欄位，，然後按一下**儲存並關閉**。</span><span class="sxs-lookup"><span data-stu-id="536c2-195">Type `http://OrderProcess.PurchaseOrder` in the **Namespace** field, and then click **Save and Close**.</span></span>  
  
#### <a name="modify-the-destination-document-library"></a><span data-ttu-id="536c2-196">修改 [目的地] 文件庫</span><span class="sxs-lookup"><span data-stu-id="536c2-196">Modify the Destination document library</span></span>  
  
1.  <span data-ttu-id="536c2-197">在上方導覽列中，按一下**文件，並列出**。</span><span class="sxs-lookup"><span data-stu-id="536c2-197">On the top navigation bar, click **Documents and Lists**.</span></span>  
  
2.  <span data-ttu-id="536c2-198">底下**文件庫**，按一下**目的地**。</span><span class="sxs-lookup"><span data-stu-id="536c2-198">Under **Document Libraries**, click **Destination**.</span></span>  
  
3.  <span data-ttu-id="536c2-199">在左側，按一下**修改設定和資料行**。</span><span class="sxs-lookup"><span data-stu-id="536c2-199">On the left side, click **Modify Settings and Columns**.</span></span>  
  
4.  <span data-ttu-id="536c2-200">底下**資料行**，按一下**加入新資料行**。</span><span class="sxs-lookup"><span data-stu-id="536c2-200">Under **Columns**, click **Add New Column**.</span></span>  
  
5.  <span data-ttu-id="536c2-201">底下**名稱和型別**，型別`Partner Name`中**資料行名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-201">Under **Name and Type**, type `Partner Name` in the **Column name** field.</span></span>  
  
6.  <span data-ttu-id="536c2-202">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="536c2-202">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="536c2-203">關閉 `WSSAdapterWalkthrough` 網站。</span><span class="sxs-lookup"><span data-stu-id="536c2-203">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
## <a name="modify-the-send-port-from-walkthrough-1"></a><span data-ttu-id="536c2-204">修改源自逐步解說 1 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="536c2-204">Modify the send port from walkthrough 1</span></span>  
 <span data-ttu-id="536c2-205">在此程序，您會修改源自逐步解說 1 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="536c2-205">In this procedure you modify the send port from walkthrough 1.</span></span> <span data-ttu-id="536c2-206">此程序，才能確保在此逐步解說中處理的文件會正確路由至傳送埠。</span><span class="sxs-lookup"><span data-stu-id="536c2-206">This procedure is required to ensure that the document processed in this walkthrough is correctly routed to the send port.</span></span>  
  
#### <a name="modify-the-send-port"></a><span data-ttu-id="536c2-207">修改傳送埠</span><span class="sxs-lookup"><span data-stu-id="536c2-207">Modify the send port</span></span>  
  
1. <span data-ttu-id="536c2-208">開啟**BizTalk Server 管理。**</span><span class="sxs-lookup"><span data-stu-id="536c2-208">Open **BizTalk Server Administration.**</span></span>  
  
2. <span data-ttu-id="536c2-209">依序展開**Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**，展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="536c2-209">Expand **Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Send Ports** node.</span></span>  
  
3. <span data-ttu-id="536c2-210">以滑鼠右鍵按一下`SendToDestination`，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="536c2-210">Right-click `SendToDestination`, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="536c2-211">底下**傳輸**，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="536c2-211">Under **Transport**, click **Configure**.</span></span>  
  
5. <span data-ttu-id="536c2-212">在 **檔名**欄位中，輸入`PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`。</span><span class="sxs-lookup"><span data-stu-id="536c2-212">In the **Filename** field, type `PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`.</span></span>  
  
6. <span data-ttu-id="536c2-213">在 **命名空間別名**欄位中，輸入`pons="http://OrderProcess.PurchaseOrder"`。</span><span class="sxs-lookup"><span data-stu-id="536c2-213">In the **Namespace Aliases** field, type `pons="http://OrderProcess.PurchaseOrder"`.</span></span>  
  
7. <span data-ttu-id="536c2-214">在 **範本文件庫**，輸入`InfoPathSolutions`。</span><span class="sxs-lookup"><span data-stu-id="536c2-214">In the **Templates Document Library**, type `InfoPathSolutions`.</span></span>  
  
8. <span data-ttu-id="536c2-215">在 **範本命名空間資料行**，輸入`Namespace`。</span><span class="sxs-lookup"><span data-stu-id="536c2-215">In the **Templates Namespace Column**, type `Namespace`.</span></span>  
  
9. <span data-ttu-id="536c2-216">選取  `Yes` for **Microsoft Office 整合**屬性。</span><span class="sxs-lookup"><span data-stu-id="536c2-216">Select `Yes` for the **Microsoft Office Integration** property.</span></span>  
  
10. <span data-ttu-id="536c2-217">底下**Windows SharePoint Services 的整合**，型別`Partner Name`中**資料行 01**欄位。</span><span class="sxs-lookup"><span data-stu-id="536c2-217">Under **Windows SharePoint Services Integration**, type `Partner Name` in the **Column 01** field.</span></span>  
  
11. <span data-ttu-id="536c2-218">型別`%XPATH=//pons:PurchaseOrder/pons:BillTo%`中**資料行 01 值**欄位中，按一下**確定**，然後按一下**確定** ，結束**傳送埠屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="536c2-218">Type `%XPATH=//pons:PurchaseOrder/pons:BillTo%` in the **Column 01 Value** field, click **OK**, and then click **OK** again to exit the **Send Port Properties** dialog box.</span></span>  
  
#### <a name="restart-the-send-port"></a><span data-ttu-id="536c2-219">重新啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="536c2-219">Restart the send port</span></span>  
  
1.  <span data-ttu-id="536c2-220">在  **BizTalk 管理主控台**，按一下**傳送連接埠**節點。</span><span class="sxs-lookup"><span data-stu-id="536c2-220">In the **BizTalk Administration Console**, click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="536c2-221">以滑鼠右鍵按一下`SendToDestination`，然後按一下**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="536c2-221">Right-click `SendToDestination`, and then click **Unenlist**.</span></span>  
  
3.  <span data-ttu-id="536c2-222">以滑鼠右鍵按一下`SendToDestination`，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="536c2-222">Right-click `SendToDestination`, and then click **Start**.</span></span>  
  
4.  <span data-ttu-id="536c2-223">關閉**BizTalk 管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="536c2-223">Close the **BizTalk Administration Console**.</span></span>  
  
## <a name="send-a-message-through-the-system"></a><span data-ttu-id="536c2-224">透過系統傳送訊息</span><span class="sxs-lookup"><span data-stu-id="536c2-224">Send a message through the system</span></span>  
 <span data-ttu-id="536c2-225">在此程序中，您要建立 InfoPath 表單，並將它上載至 Windows SharePoint Services 網站。</span><span class="sxs-lookup"><span data-stu-id="536c2-225">In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="536c2-226">Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。</span><span class="sxs-lookup"><span data-stu-id="536c2-226">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="536c2-227">此程序示範如何在文件從 Sharepoint 網站上，透過流動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以及 Sharepoint Services 網站使用的 Windows Sharepoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="536c2-227">This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a><span data-ttu-id="536c2-228">建立 InfoPath 表單以透過系統傳送</span><span class="sxs-lookup"><span data-stu-id="536c2-228">Create an InfoPath form to send through the system</span></span>  
  
1.  <span data-ttu-id="536c2-229">開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="536c2-229">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="536c2-230">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="536c2-230">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="536c2-231">在左側，底下**文件**，按一下  `InfoPathSolutions`。</span><span class="sxs-lookup"><span data-stu-id="536c2-231">On the left side, under **Documents**, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="536c2-232">按一下 `PurchaseOrder`檔案，以顯示**檔案下載**對話方塊，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="536c2-232">Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**.</span></span> <span data-ttu-id="536c2-233">InfoPath 將載入此表單。</span><span class="sxs-lookup"><span data-stu-id="536c2-233">InfoPath will load the form.</span></span>  
  
4.  <span data-ttu-id="536c2-234">在 **採購單識別碼**欄位中，輸入`1002`。</span><span class="sxs-lookup"><span data-stu-id="536c2-234">In the **Purchase Order ID** field, type `1002`.</span></span>  
  
5.  <span data-ttu-id="536c2-235">在 **付款人**欄位中，輸入`John Doe`。</span><span class="sxs-lookup"><span data-stu-id="536c2-235">In the **Bill To** field, type `John Doe`.</span></span>  
  
6.  <span data-ttu-id="536c2-236">在 **金額**欄位中，輸入`750`。</span><span class="sxs-lookup"><span data-stu-id="536c2-236">In the **Amount** field, type `750`.</span></span>  
  
7.  <span data-ttu-id="536c2-237">在 **採購單日期**欄位中，輸入`1/2/2005`。</span><span class="sxs-lookup"><span data-stu-id="536c2-237">In the **Purchase Order Date** field, type `1/2/2005`.</span></span>  
  
8.  <span data-ttu-id="536c2-238">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="536c2-238">Click **Save**.</span></span>  
  
9. <span data-ttu-id="536c2-239">在 [**另存新檔**] 對話方塊中，輸入`http://<server_name>/sites/WSSAdapterWalkthrough/Source`中**檔案名稱**欄位，然後再按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="536c2-239">In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then hit Enter.</span></span>  
  
10. <span data-ttu-id="536c2-240">型別`PurchaseOrder2.xml`中**檔案名稱**欄位，，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="536c2-240">Type `PurchaseOrder2.xml` in the **file name** field, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="536c2-241">關閉 Microsoft Office InfoPath。</span><span class="sxs-lookup"><span data-stu-id="536c2-241">Close Microsoft Office InfoPath.</span></span>  
  
12. <span data-ttu-id="536c2-242">在網頁瀏覽器，在上方導覽列中，按一下**文件，並列出**。</span><span class="sxs-lookup"><span data-stu-id="536c2-242">In the Web browser, on the top navigation bar, click **Documents and Lists**.</span></span>  
  
13. <span data-ttu-id="536c2-243">底下**文件庫**，按一下**目的地**。</span><span class="sxs-lookup"><span data-stu-id="536c2-243">Under **Document Libraries**, click **Destination**.</span></span>  
  
14. <span data-ttu-id="536c2-244">在 [目的地] 文件庫中，您現在會看見已列出您的訊息。</span><span class="sxs-lookup"><span data-stu-id="536c2-244">In the Destination document library, you will now see your message listed.</span></span> <span data-ttu-id="536c2-245">您也可以在 [封存] 文件庫中找到封存的複本。</span><span class="sxs-lookup"><span data-stu-id="536c2-245">You will also find a copy archived in the Archive document library.</span></span>  
  
15. <span data-ttu-id="536c2-246">在 [目的地] 文件庫中，按一下 `PurchaseOrder1.xml`。</span><span class="sxs-lookup"><span data-stu-id="536c2-246">In the Destination document library, click `PurchaseOrder1.xml`.</span></span> <span data-ttu-id="536c2-247">請注意，您可以在 [Microsoft Internet Explorer] 中開啟此 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="536c2-247">Note that this XML file is opened in Microsoft Internet Explorer.</span></span>  
  
16. <span data-ttu-id="536c2-248">在 [目的地] 文件庫中，按一下 `PurchaseOrder2.xml`。</span><span class="sxs-lookup"><span data-stu-id="536c2-248">In the Destination document library, click `PurchaseOrder2.xml`.</span></span> <span data-ttu-id="536c2-249">請注意，您在 Microsoft Office InfoPath 中開啟此 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="536c2-249">Note that this XML file is opened in Microsoft Office InfoPath.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="536c2-250">在 [目的地] 文件庫中，[檔案名稱] 資料行應該包含 [PurchaseOrderID] 欄位的值，而 [夥伴名稱] 資料行應該包含 [付款人] 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="536c2-250">In the Destination document library, the file name column should contain the value of the PurchaseOrderID field and the Partner Name column should contain the value of the BillTo field.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="536c2-251">摘要</span><span class="sxs-lookup"><span data-stu-id="536c2-251">Summary</span></span>  
 <span data-ttu-id="536c2-252">在此逐步解說中，您已經瞭解如何藉由使用 Windows SharePoint Services 配接器與以內容為基礎的路由 (CBR)，使 Microsoft InfoPath 更緊密整合。</span><span class="sxs-lookup"><span data-stu-id="536c2-252">In this walkthrough you have seen how to add tighter integration with Microsoft InfoPath using the Windows SharePoint Services Adapter and content-based routing (CBR).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="536c2-253">後續步驟</span><span class="sxs-lookup"><span data-stu-id="536c2-253">Next Steps</span></span>  
 <span data-ttu-id="536c2-254">既然您已完成本逐步解說中，執行[逐步解說： 模組 3-從協調流程存取 SharePoint 屬性](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md)整合，可在此逐步解說中，您已完成的工作上擴充的逐步解說協調流程至專案，並說明如何從其中存取 SharePoint 屬性內。</span><span class="sxs-lookup"><span data-stu-id="536c2-254">Now that you have completed this walkthrough, perform the [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md) walkthrough which expands on the work you have done with this walkthrough, integrates an orchestration into the project, and shows you how to access SharePoint properties from within it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536c2-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="536c2-255">See Also</span></span>  
 <span data-ttu-id="536c2-256">[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="536c2-256">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="536c2-257">Windows SharePoint Services 配接器逐步解說</span><span class="sxs-lookup"><span data-stu-id="536c2-257">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)