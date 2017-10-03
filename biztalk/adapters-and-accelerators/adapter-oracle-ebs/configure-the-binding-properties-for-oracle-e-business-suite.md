---
title: "設定 for Oracle E-business Suite 繫結屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfdca8c8-4434-4a9f-8e2a-970988c2f685
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddb414ae80e7cff6717d232d1734ec8b98cd2006
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-oracle-e-business-suite"></a><span data-ttu-id="a1529-102">設定 for Oracle E-business Suite 繫結屬性</span><span class="sxs-lookup"><span data-stu-id="a1529-102">Configure the binding properties for Oracle E-Business Suite</span></span>
<span data-ttu-id="a1529-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。</span><span class="sxs-lookup"><span data-stu-id="a1529-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="a1529-104">本節提供設定的繫結內容的相關資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]來回[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a1529-104">This section provides information about setting the binding properties from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a1529-105">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生結構描述的特定作業時，您必須指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a1529-105">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the binding properties while generating schema for specific operations.</span></span> <span data-ttu-id="a1529-106">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須指定的繫結屬性一部分的傳送或接收埠的傳送或接收訊息，從 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="a1529-106">From [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must specify the binding properties as part of the send or receive port for sending or receiving messages from Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="a1529-107">如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a1529-107">For information about the binding properties, including a list of binding properties for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
## <a name="specifying-binding-properties-from-visual-studio"></a><span data-ttu-id="a1529-108">指定 Visual Studio 中的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="a1529-108">Specifying Binding Properties from Visual Studio</span></span>  
 <span data-ttu-id="a1529-109">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定繫結屬性使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a1529-109">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the binding properties using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="a1529-110">若要指定使用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="a1529-110">To specify binding properties using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="a1529-111">以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="a1529-111">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="a1529-112">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a1529-112">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a1529-113">使用</span><span class="sxs-lookup"><span data-stu-id="a1529-113">Use this</span></span>|<span data-ttu-id="a1529-114">動作</span><span class="sxs-lookup"><span data-stu-id="a1529-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a1529-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="a1529-115">**Categories**</span></span>|<span data-ttu-id="a1529-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="a1529-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="a1529-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="a1529-117">**Templates**</span></span>|<span data-ttu-id="a1529-118">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="a1529-118">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="a1529-119">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="a1529-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="a1529-120">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**oracleEBSBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="a1529-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list, select **oracleEBSBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="a1529-121">在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤，然後再指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a1529-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and then specify the different binding properties.</span></span>  
  
6.  <span data-ttu-id="a1529-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1529-122">Click **OK**.</span></span>  
  
#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="a1529-123">若要指定繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="a1529-123">To specify binding properties using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="a1529-124">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="a1529-124">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="a1529-125">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a1529-125">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a1529-126">使用</span><span class="sxs-lookup"><span data-stu-id="a1529-126">Use this</span></span>|<span data-ttu-id="a1529-127">動作</span><span class="sxs-lookup"><span data-stu-id="a1529-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a1529-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="a1529-128">**Categories**</span></span>|<span data-ttu-id="a1529-129">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="a1529-129">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="a1529-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="a1529-130">**Templates**</span></span>|<span data-ttu-id="a1529-131">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="a1529-131">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="a1529-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="a1529-132">Click **Add**.</span></span> <span data-ttu-id="a1529-133">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a1529-133">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="a1529-134">在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracleebs**。</span><span class="sxs-lookup"><span data-stu-id="a1529-134">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleEBS**.</span></span> <span data-ttu-id="a1529-135">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1529-135">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a1529-136">如果您已經設定 biztalk Wcf-oracleebs 連接埠，請從連接埠清單中選取連接埠。</span><span class="sxs-lookup"><span data-stu-id="a1529-136">If you already have a WCF-OracleEBS port configured in BizTalk, select the port from the Port list.</span></span>  
  
5.  <span data-ttu-id="a1529-137">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a1529-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a1529-138">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="a1529-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleEBSBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="a1529-139">按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需的。</span><span class="sxs-lookup"><span data-stu-id="a1529-139">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="a1529-140">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a1529-140">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1529-141">如果您選取的現有 Wcf-oracleebs 傳送埠時，您需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a1529-141">If you selected an existing WCF-OracleEBS send port, you need not specify the binding properties.</span></span> <span data-ttu-id="a1529-142">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="a1529-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="a1529-143">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="a1529-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="a1529-144">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1529-144">In such a case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="a1529-145">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="a1529-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
8.  <span data-ttu-id="a1529-146">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1529-146">Click **OK**.</span></span>  
  
## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a><span data-ttu-id="a1529-147">指定繫結屬性從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="a1529-147">Specifying Binding Properties from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="a1529-148">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定的繫結屬性，Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1529-148">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the binding properties as part of the WCF-Custom or WCF-OracleEBS port configuration.</span></span>  
  
#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="a1529-149">若要指定 WCF 自訂連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="a1529-149">To specify binding properties for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="a1529-150">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a1529-150">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="a1529-151">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="a1529-151">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="a1529-152">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a1529-152">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="a1529-153">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a1529-153">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1529-154">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="a1529-154">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="a1529-155">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a1529-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
5.  <span data-ttu-id="a1529-156">從**繫結的型別**清單中，選取**oracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="a1529-156">From the **Binding Type** list, select **oracleEBSBinding**.</span></span>  
  
6.  <span data-ttu-id="a1529-157">在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a1529-157">In the **Configuration** box, specify the values for the different binding properties, and then click **OK**.</span></span>  
  
#### <a name="to-specify-binding-properties-for-the-wcf-oracleebs-port"></a><span data-ttu-id="a1529-158">若要指定 Wcf-oracleebs 連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="a1529-158">To specify binding properties for the WCF-OracleEBS port</span></span>  
  
1.  <span data-ttu-id="a1529-159">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a1529-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="a1529-160">新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a1529-160">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a1529-161">如需指示，請參閱[Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="a1529-161">For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="a1529-162">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="a1529-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="a1529-163">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a1529-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="a1529-164">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 Wcf-oracleebs 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a1529-164">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleEBS adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1529-165">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="a1529-165">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="a1529-166">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a1529-166">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1529-167">根據您要設定傳送埠或接收埠會繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a1529-167">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="a1529-168">例如，通知相關的繫結屬性沒有可用時設定的傳送埠，因為通知為輸入的作業，需要接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="a1529-168">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1529-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1529-169">See Also</span></span>  
 [<span data-ttu-id="a1529-170">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="a1529-170">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)