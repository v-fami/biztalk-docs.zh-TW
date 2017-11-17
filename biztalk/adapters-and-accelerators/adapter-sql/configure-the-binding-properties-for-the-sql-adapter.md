---
title: "設定 SQL 配接器的繫結屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2edbd90-039a-48b4-a6fc-d825b4957207
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42576a59aae28c78250f5eba19558072e0e526d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-the-sql-adapter"></a><span data-ttu-id="d920b-102">設定 SQL 配接器的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d920b-102">Configure the binding properties for the SQL adapter</span></span>
<span data-ttu-id="d920b-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。</span><span class="sxs-lookup"><span data-stu-id="d920b-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="d920b-104">本節提供設定的繫結內容的相關資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]來回[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d920b-104">This section provides information about setting the binding properties from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="d920b-105">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要產生結構描述的特定作業的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d920b-105">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the binding properties to generate schema for specific operations.</span></span> <span data-ttu-id="d920b-106">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須指定的繫結屬性一部分的傳送或接收埠的傳送或接收訊息，從 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d920b-106">From [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must specify the binding properties as part of the send or receive port for sending or receiving messages from SQL Server.</span></span>  
  
 <span data-ttu-id="d920b-107">如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d920b-107">For information about the binding properties, including a list of binding properties for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
## <a name="enter-the-binding-properties-in-visual-studio"></a><span data-ttu-id="d920b-108">在 Visual Studio 中輸入的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d920b-108">Enter the binding properties in Visual Studio</span></span>  
 <span data-ttu-id="d920b-109">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以指定繫結屬性使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d920b-109">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can specify the binding properties using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="using-consume-adapter-service-add-in"></a><span data-ttu-id="d920b-110">使用會耗用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="d920b-110">Using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="d920b-111">以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d920b-111">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="d920b-112">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d920b-112">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d920b-113">使用</span><span class="sxs-lookup"><span data-stu-id="d920b-113">Use this</span></span>|<span data-ttu-id="d920b-114">動作</span><span class="sxs-lookup"><span data-stu-id="d920b-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d920b-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="d920b-115">**Categories**</span></span>|<span data-ttu-id="d920b-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d920b-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="d920b-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="d920b-117">**Templates**</span></span>|<span data-ttu-id="d920b-118">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d920b-118">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="d920b-119">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d920b-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="d920b-120">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="d920b-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="d920b-121">在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤，然後再指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d920b-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and then specify the different binding properties.</span></span>  
  
6.  <span data-ttu-id="d920b-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d920b-122">Click **OK**.</span></span>  
  
### <a name="using-add-adapter-metadata-wizard"></a><span data-ttu-id="d920b-123">使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="d920b-123">Using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="d920b-124">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d920b-124">Right-click the BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="d920b-125">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d920b-125">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d920b-126">使用</span><span class="sxs-lookup"><span data-stu-id="d920b-126">Use this</span></span>|<span data-ttu-id="d920b-127">動作</span><span class="sxs-lookup"><span data-stu-id="d920b-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d920b-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="d920b-128">**Categories**</span></span>|<span data-ttu-id="d920b-129">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="d920b-129">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="d920b-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="d920b-130">**Templates**</span></span>|<span data-ttu-id="d920b-131">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="d920b-131">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="d920b-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="d920b-132">Click **Add**.</span></span> <span data-ttu-id="d920b-133">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d920b-133">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="d920b-134">在 新增配接器精靈 中，選取  **WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="d920b-134">In the Add Adapter Wizard, select **WCF-SQL**.</span></span> <span data-ttu-id="d920b-135">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d920b-135">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d920b-136">如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="d920b-136">If you already have a WCF-SQL port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="d920b-137">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d920b-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d920b-138">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="d920b-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="d920b-139">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="d920b-139">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="d920b-140">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d920b-140">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d920b-141">如果您選取現有的 WCF SQL 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d920b-141">If you selected an existing WCF-SQL send port, you need not specify the binding properties.</span></span> <span data-ttu-id="d920b-142">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="d920b-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="d920b-143">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="d920b-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="d920b-144">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d920b-144">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="d920b-145">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="d920b-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
8.  <span data-ttu-id="d920b-146">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d920b-146">Click **OK**.</span></span>  
  
## <a name="enter-binding-properties-from-the-biztalk-server-administration-console"></a><span data-ttu-id="d920b-147">從 BizTalk Server 管理主控台中輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d920b-147">Enter binding properties from the BizTalk Server Administration console</span></span>  
 <span data-ttu-id="d920b-148">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的繫結屬性為 Wcf-custom 或 WCF SQL 連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="d920b-148">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the binding properties as part of the WCF-Custom or WCF-SQL port configuration.</span></span>  
  
### <a name="enter-binding-properties-for-wcf-custom-port"></a><span data-ttu-id="d920b-149">輸入 WCF 自訂連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d920b-149">Enter binding properties for WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="d920b-150">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d920b-150">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="d920b-151">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d920b-151">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="d920b-152">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d920b-152">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="d920b-153">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d920b-153">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d920b-154">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d920b-154">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="d920b-155">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d920b-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
5.  <span data-ttu-id="d920b-156">從**繫結的型別**清單中，選取**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="d920b-156">From the **Binding Type** list, select **sqlBinding**.</span></span>  
  
6.  <span data-ttu-id="d920b-157">在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d920b-157">In the **Configuration** box, specify the values for the different binding properties, and then click **OK**.</span></span>  
  
### <a name="enter-binding-properties-for-the-wcf-sql-port"></a><span data-ttu-id="d920b-158">輸入 WCF SQL 連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d920b-158">Enter binding properties for the WCF-SQL port</span></span>  
  
1.  <span data-ttu-id="d920b-159">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d920b-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="d920b-160">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d920b-160">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="d920b-161">如需指示，請參閱[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="d920b-161">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="d920b-162">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d920b-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="d920b-163">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d920b-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="d920b-164">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d920b-164">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d920b-165">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d920b-165">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="d920b-166">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d920b-166">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d920b-167">根據您要設定傳送埠或接收埠會繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d920b-167">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="d920b-168">例如，通知相關的繫結屬性沒有可用時設定的傳送埠，因為通知為輸入的作業，需要接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="d920b-168">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
6.  <span data-ttu-id="d920b-169">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d920b-169">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d920b-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d920b-170">See Also</span></span>  
[<span data-ttu-id="d920b-171">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="d920b-171">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)