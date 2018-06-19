---
title: 使用新的 PIP 擴充 BTARN |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTARN, extending functionality
- PIPs, extending BTARN
- BTARN, PIPs
ms.assetid: 3db5cd5c-031f-4451-9be5-4b5d6163c3b1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b1fca61cd40b932e53b2908603a225d3980fa1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007167"
---
# <a name="extending-btarn-with-a-new-pip"></a><span data-ttu-id="4441b-102">使用新的 PIP 擴充 BTARN</span><span class="sxs-lookup"><span data-stu-id="4441b-102">Extending BTARN with a New PIP</span></span>
<span data-ttu-id="4441b-103">本主題說明如何擴充[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]與新的交易夥伴介面程序 (PIP) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4441b-103">This topic describes how to extend [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] with a new Partner Interface Process (PIP) schema.</span></span> <span data-ttu-id="4441b-104">當該 PIP 未與任何由 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式安裝的結構描述關聯時，這可以讓您根據 RosettaNet PIP 新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="4441b-104">This lets you add a schema based on a RosettaNet PIP when that PIP is not associated with any of the schemas installed by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program.</span></span>  
  
 <span data-ttu-id="4441b-105">當您使用新的 PIP 擴充 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 時，便會在這個新結構描述本身的組件中部署這個結構描述。</span><span class="sxs-lookup"><span data-stu-id="4441b-105">When you extend [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] with a new PIP, you deploy the new schema in its own assembly.</span></span> <span data-ttu-id="4441b-106">此外，您也可以修改 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIP 組件內所部署的現有結構描述。</span><span class="sxs-lookup"><span data-stu-id="4441b-106">You can also modify an existing schema that is deployed within the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIPs assembly.</span></span> <span data-ttu-id="4441b-107">如需詳細資訊，請參閱[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。</span><span class="sxs-lookup"><span data-stu-id="4441b-107">For more information, see [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).</span></span>  
  
### <a name="to-extend-btarn-with-a-new-pip"></a><span data-ttu-id="4441b-108">使用新的 PIP 擴充 BTARN</span><span class="sxs-lookup"><span data-stu-id="4441b-108">To extend BTARN with a new PIP</span></span>  
  
1.  <span data-ttu-id="4441b-109">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4441b-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="4441b-110">在命令提示字元中，移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Utilities\Schema Generator。</span><span class="sxs-lookup"><span data-stu-id="4441b-110">At the command prompt, move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Utilities\Schema Generator.</span></span>  
  
3.  <span data-ttu-id="4441b-111">在命令提示字元中，輸入**CScript InstallDTD.vbs**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4441b-111">At the command prompt, type **CScript InstallDTD.vbs**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4441b-112">您只必須在安裝 BizTalk Server 後，一次執行步驟 1 到 3。</span><span class="sxs-lookup"><span data-stu-id="4441b-112">You will only have to perform steps 1 through 3 once after you install BizTalk Server.</span></span>  
  
4.  <span data-ttu-id="4441b-113">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4441b-113">Start Visual Studio.</span></span>  
  
5.  <span data-ttu-id="4441b-114">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="4441b-114">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
6.  <span data-ttu-id="4441b-115">在 新增專案 對話方塊中，選取  **BizTalk 專案**在左的窗格中，然後按一下**空白 BizTalk Server 專案**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="4441b-115">In the New Project dialog box, select **BizTalk Projects** in the left pane, and then click **Empty BizTalk Server Project** in the right pane.</span></span>  
  
7.  <span data-ttu-id="4441b-116">按一下**瀏覽**點指派到您要儲存專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="4441b-116">Click **Browse** and point to the directory where you want to save your project.</span></span>  
  
8.  <span data-ttu-id="4441b-117">在**名稱**方塊中，輸入專案名稱，例如**MyCustomPIP**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4441b-117">In the **Name** box, type a project name, such as **MyCustomPIP**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="4441b-118">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4441b-118">Start Visual Studio command prompt.</span></span>  
  
10. <span data-ttu-id="4441b-119">在命令提示字元中，移至步驟 7 中，型別中輸入位置**sn-k\<專案 name.snk\>**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4441b-119">At the command prompt, move to the location entered in step 7, type **sn -k \<project name.snk\>**, and then press **Enter**.</span></span>  
  
11. <span data-ttu-id="4441b-120">在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4441b-120">In Solutions Explorer, right-click the project name, and then click **Properties**.</span></span>  
  
12. <span data-ttu-id="4441b-121">在**屬性頁**對話方塊中，按一下 **組件**下**通用屬性**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="4441b-121">In the **Property Pages** dialog box, click **Assembly** under **Common Properties** in the left pane.</span></span>  
  
13. <span data-ttu-id="4441b-122">在右窗格中，向下捲動至**強式名稱**，按一下 **組件金鑰檔案**，然後按一下右窗格中的省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="4441b-122">In the right pane, scroll down to **Strong Name**, click **Assembly Key File**, and then click the ellipsis button (...) in the right pane.</span></span> <span data-ttu-id="4441b-123">移至在步驟 7 中輸入的位置，然後選取在步驟 10 中建立的 .snk 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4441b-123">Move to the location entered in step 7, and select the name of the .snk file created in step 10.</span></span>  
  
14. <span data-ttu-id="4441b-124">在 屬性頁 對話方塊中，依序展開**組態屬性**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="4441b-124">In the Property Pages dialog box, expand **Configuration Properties**, and then click **Deployment**.</span></span> <span data-ttu-id="4441b-125">在右窗格中，按一下 **重新部署**，選取`True`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4441b-125">In the right pane, click **Redeploy**, select `True`, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="4441b-126">在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="4441b-126">In Solution Explorer, right-click the project name, point to **Add**, and then click **Existing Item**.</span></span>  
  
16. <span data-ttu-id="4441b-127">在**加入現有項目**對話方塊中，移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Schemas，選取**xml.xsd**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="4441b-127">In the **Add Existing Item** dialog box, move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Schemas, select **xml.xsd**, then click **Add**.</span></span>  
  
17. <span data-ttu-id="4441b-128">從 RosettaNet.org 下載您要用來擴充 RNPIP 的 PIP。如需詳細資訊，請參閱[納入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。</span><span class="sxs-lookup"><span data-stu-id="4441b-128">Download the PIP that you are going to extend RNPIPs with RosettaNet.org. For more information, see [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).</span></span>  
  
18. <span data-ttu-id="4441b-129">在 方案總管 中，展開 專案名稱，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="4441b-129">In Solution Explorer, expand the project name, right-click **Reference**, and then click **Add Reference**.</span></span>  
  
19. <span data-ttu-id="4441b-130">在**加入參考**對話方塊中，按一下 **瀏覽**，並移至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk 2013 Accelerator for RosettaNet\Bin，然後選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**。</span><span class="sxs-lookup"><span data-stu-id="4441b-130">In the **Add Reference** dialog box, click **Browse**, and move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\Bin, and then select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**.</span></span> <span data-ttu-id="4441b-131">按一下**開啟**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4441b-131">Click **Open**, and then click **OK**.</span></span>  
  
20. <span data-ttu-id="4441b-132">在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="4441b-132">In Solution Explorer, right-click the project name, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
21. <span data-ttu-id="4441b-133">在**新增產生的項目**對話方塊中，於**類別**] 窗格中，按一下 [**產生結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4441b-133">In the **Add Generated Items** dialog box, in the **Categories** pane, click **Generate Schemas**.</span></span> <span data-ttu-id="4441b-134">在**範本** 窗格中，按一下 **產生結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="4441b-134">In the **Templates** pane, click **Generate Schemas**, and then click **Add**.</span></span>  
  
22. <span data-ttu-id="4441b-135">在 [產生結構描述] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4441b-135">In the Generate Schemas dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="4441b-136">使用</span><span class="sxs-lookup"><span data-stu-id="4441b-136">Use this</span></span>|<span data-ttu-id="4441b-137">動作</span><span class="sxs-lookup"><span data-stu-id="4441b-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4441b-138">**文件類型**</span><span class="sxs-lookup"><span data-stu-id="4441b-138">**Document type**</span></span>|<span data-ttu-id="4441b-139">選取**DTD 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4441b-139">Select **DTD Schema**.</span></span>|  
    |<span data-ttu-id="4441b-140">**輸入的檔**</span><span class="sxs-lookup"><span data-stu-id="4441b-140">**Input File**</span></span>|<span data-ttu-id="4441b-141">按一下**瀏覽**、 移至含有從 RosettaNet.org 的 DTD 檔案的資料夾、 選取的 DTD 檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="4441b-141">Click **Browse**, move to the folder that contains the DTD file from RosettaNet.org, select the DTD file that you want, and then click **Open**.</span></span>|  
  
23. <span data-ttu-id="4441b-142">在 [產生結構描述] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4441b-142">In the Generate Schemas dialog box, click **OK**.</span></span>  
  
24. <span data-ttu-id="4441b-143">在 [方案總管] 中，按兩下剛匯入的 .xsd 檔。</span><span class="sxs-lookup"><span data-stu-id="4441b-143">In Solution Explorer, double-click the .xsd file that you just imported.</span></span>  
  
25. <span data-ttu-id="4441b-144">在 [BizTalk 編輯器] 中，選取\<*結構描述*\>節點。</span><span class="sxs-lookup"><span data-stu-id="4441b-144">In BizTalk Editor, select the \<*Schema*\> node.</span></span>  
  
26. <span data-ttu-id="4441b-145">在 [屬性] 視窗中向下捲動至**文件類型**。</span><span class="sxs-lookup"><span data-stu-id="4441b-145">In the Properties window, scroll down to **Document Type**.</span></span> <span data-ttu-id="4441b-146">在**文件類型** 方塊中， **PIP**\<*三位數代碼*\>，例如**PIP3A2**。</span><span class="sxs-lookup"><span data-stu-id="4441b-146">In the **Document Type** box, **PIP**\<*three-digit code*\>, for example, **PIP3A2**.</span></span> <span data-ttu-id="4441b-147">在**文件版本**方塊中，輸入**v**\<*xx.xx* \>或**R** \< *xx.xx*\>，例如**R01.02**。</span><span class="sxs-lookup"><span data-stu-id="4441b-147">In the **Document Version** box, type **v**\<*xx.xx*\> or **R**\<*xx.xx*\>, for example, **R01.02**.</span></span> <span data-ttu-id="4441b-148">請依照 RosettaNet PIP 規格記載的方式輸入這個版本。</span><span class="sxs-lookup"><span data-stu-id="4441b-148">This version should be as documented in the RosettaNet PIP specification.</span></span>  
  
27. <span data-ttu-id="4441b-149">在 [屬性] 視窗中向下捲動至**根參考**。</span><span class="sxs-lookup"><span data-stu-id="4441b-149">In the Properties window, scroll down to **Root Reference**.</span></span> <span data-ttu-id="4441b-150">按一下**根參考**，然後從下拉式清單中，選取根節點的結構描述，例如，選取**Pip3C5BillingStatementNotification**。</span><span class="sxs-lookup"><span data-stu-id="4441b-150">Click **Root Reference**, and from the drop-down list, select the root node of the schema, for example, select **Pip3C5BillingStatementNotification**.</span></span>  
  
28. <span data-ttu-id="4441b-151">在 [屬性] 視窗中，向上捲動至**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="4441b-151">In the Properties window, scroll up to **Target Namespace**.</span></span> <span data-ttu-id="4441b-152">如**目標命名空間**，型別**http://schemas.microsoft.com/biztalk/btarn/2004/\<DTD 檔案名稱\>.dtd**，其中的 DTD 檔案名稱是，比方說， **3C5_MS_R01_00_BillingStatementNotification.dtd**。</span><span class="sxs-lookup"><span data-stu-id="4441b-152">For **Target Namespace**, type **http://schemas.microsoft.com/biztalk/btarn/2004/\<DTD file name\>.dtd**, where the DTD file name is, for example, **3C5_MS_R01_00_BillingStatementNotification.dtd**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4441b-153">BTARN 的目標命名空間必須採用這個命名慣例。</span><span class="sxs-lookup"><span data-stu-id="4441b-153">This naming convention for the target namespace is required for BTARN.</span></span> <span data-ttu-id="4441b-154">如果您使用其他命名空間慣例，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將無法處理 PIP 文件來進行結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="4441b-154">If you use another namespace convention, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not process PIP documents for schema validation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4441b-155">目標命名空間屬性中的 DTD 檔案名稱包括了 PIP 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4441b-155">The DTD file name in the target namespace property includes the version number of the PIP.</span></span> <span data-ttu-id="4441b-156">這讓您可以使用同一組 PIP 代碼的多重版本。</span><span class="sxs-lookup"><span data-stu-id="4441b-156">This lets you use multiple versions of the same PIP code.</span></span>  
  
29. <span data-ttu-id="4441b-157">在 [屬性] 視窗中，向上捲動至**匯入**。</span><span class="sxs-lookup"><span data-stu-id="4441b-157">In the Properties window, scroll up to **Imports**.</span></span> <span data-ttu-id="4441b-158">按一下旁邊的省略符號按鈕 （...）**匯入**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="4441b-158">Click the ellipsis button (...) next to **Imports**, and then click **Add**.</span></span>  
  
30. <span data-ttu-id="4441b-159">在**BizTalk 型別選擇器**對話方塊方塊中，展開  \<*專案名稱*\>，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，依序展開**結構描述**，選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.BaseDataTypes**，按一下  **確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="4441b-159">In the **BizTalk Type Picker** dialog box, expand \<*Project Name*\>, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, expand **Schemas**, select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.BaseDataTypes**, click **OK**, and then click **OK** again.</span></span>  
  
31. <span data-ttu-id="4441b-160">以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="4441b-160">Right-click the project name, and then click **Deploy**.</span></span>  
  
32. <span data-ttu-id="4441b-161">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="4441b-161">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
33. <span data-ttu-id="4441b-162">在 BizTalk 管理主控台中，依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，然後展開**主機**。</span><span class="sxs-lookup"><span data-stu-id="4441b-162">In BizTalk Administration Console, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, and then expand **Hosts**.</span></span> <span data-ttu-id="4441b-163">在下**主機**，按一下  **BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="4441b-163">Under **Host**, click **BizTalkServerApplication**.</span></span>  
  
34. <span data-ttu-id="4441b-164">在右窗格中，主機名稱上按一下滑鼠右鍵，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="4441b-164">In the right pane, right-click the name of the host, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4441b-165">使用剛匯入的 PIP 擴充 RNPIP 之後，您必須在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，建立正確的 PIP 組態以及使用該 PIP 的協議。</span><span class="sxs-lookup"><span data-stu-id="4441b-165">After extending RNPIPs with a newly imported PIP, you must create the correct PIP configuration, and an agreement using that PIP, in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4441b-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="4441b-166">See Also</span></span>  
 <span data-ttu-id="4441b-167">[加入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md) </span><span class="sxs-lookup"><span data-stu-id="4441b-167">[Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md) </span></span>  
 <span data-ttu-id="4441b-168">[使用 Pip](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md) </span><span class="sxs-lookup"><span data-stu-id="4441b-168">[Working with PIPs](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md) </span></span>  
 [<span data-ttu-id="4441b-169">修改 RNPIP 中的現有 PIP</span><span class="sxs-lookup"><span data-stu-id="4441b-169">Modifying an Existing PIP in RNPIPs</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)