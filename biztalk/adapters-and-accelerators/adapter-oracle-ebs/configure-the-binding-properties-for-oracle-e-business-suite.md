---
title: 設定 Oracle E-business Suite 繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfdca8c8-4434-4a9f-8e2a-970988c2f685
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1e2d60ede3e41c08b15d3839f6ece41a68aa373
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989175"
---
# <a name="configure-the-binding-properties-for-oracle-e-business-suite"></a><span data-ttu-id="e3505-102">設定 Oracle E-business Suite 繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e3505-102">Configure the binding properties for Oracle E-Business Suite</span></span>
<span data-ttu-id="e3505-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現可讓您控制其行為特性的數個繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e3505-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="e3505-104">本節提供設定的繫結屬性的相關資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]進出[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e3505-104">This section provides information about setting the binding properties from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="e3505-105">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須在產生特定作業的結構描述時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e3505-105">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the binding properties while generating schema for specific operations.</span></span> <span data-ttu-id="e3505-106">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須指定的繫結屬性一部分傳送或接收埠來傳送或接收 Oracle E-business Suite 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="e3505-106">From [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must specify the binding properties as part of the send or receive port for sending or receiving messages from Oracle E-Business Suite.</span></span>  

 <span data-ttu-id="e3505-107">如需繫結屬性的資訊，包括一份的繫結屬性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3505-107">For information about the binding properties, including a list of binding properties for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  

## <a name="specifying-binding-properties-from-visual-studio"></a><span data-ttu-id="e3505-108">指定繫結屬性，從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3505-108">Specifying Binding Properties from Visual Studio</span></span>  
 <span data-ttu-id="e3505-109">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定使用的繫結屬性[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e3505-109">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the binding properties using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="e3505-110">若要指定使用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e3505-110">To specify binding properties using Consume Adapter Service Add-in</span></span>  

1.  <span data-ttu-id="e3505-111">以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="e3505-111">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  

2.  <span data-ttu-id="e3505-112">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e3505-112">In the **Add Generated Items** dialog box, do the following:</span></span>  

    |<span data-ttu-id="e3505-113">使用</span><span class="sxs-lookup"><span data-stu-id="e3505-113">Use this</span></span>|<span data-ttu-id="e3505-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e3505-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e3505-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="e3505-115">**Categories**</span></span>|<span data-ttu-id="e3505-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="e3505-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="e3505-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="e3505-117">**Templates**</span></span>|<span data-ttu-id="e3505-118">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="e3505-118">Click **Consume Adapter Service**.</span></span>|  

3.  <span data-ttu-id="e3505-119">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="e3505-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4.  <span data-ttu-id="e3505-120">在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleEBSBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="e3505-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list, select **oracleEBSBinding**, and then click **Configure**.</span></span>  

5.  <span data-ttu-id="e3505-121">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後再指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e3505-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and then specify the different binding properties.</span></span>  

6.  <span data-ttu-id="e3505-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="e3505-122">Click **OK**.</span></span>  

#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="e3505-123">若要指定繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="e3505-123">To specify binding properties using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="e3505-124">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="e3505-124">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2. <span data-ttu-id="e3505-125">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e3505-125">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="e3505-126">使用</span><span class="sxs-lookup"><span data-stu-id="e3505-126">Use this</span></span>    |           <span data-ttu-id="e3505-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e3505-127">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="e3505-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="e3505-128">**Categories**</span></span> |     <span data-ttu-id="e3505-129">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="e3505-129">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="e3505-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="e3505-130">**Templates**</span></span>  | <span data-ttu-id="e3505-131">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="e3505-131">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="e3505-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="e3505-132">Click **Add**.</span></span> <span data-ttu-id="e3505-133">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e3505-133">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="e3505-134">在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracleebs**。</span><span class="sxs-lookup"><span data-stu-id="e3505-134">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleEBS**.</span></span> <span data-ttu-id="e3505-135">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3505-135">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="e3505-136">如果您已經在 BizTalk 設定 Wcf-oracleebs 連接埠，請從連接埠清單中選取連接埠。</span><span class="sxs-lookup"><span data-stu-id="e3505-136">If you already have a WCF-OracleEBS port configured in BizTalk, select the port from the Port list.</span></span>  

5. <span data-ttu-id="e3505-137">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="e3505-137">Click **Next**.</span></span>  

6. <span data-ttu-id="e3505-138">在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="e3505-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleEBSBinding**, and then click **Configure**.</span></span>  

7. <span data-ttu-id="e3505-139">按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。</span><span class="sxs-lookup"><span data-stu-id="e3505-139">Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="e3505-140">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3505-140">For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="e3505-141">如果您選取的現有 Wcf-oracleebs 傳送埠時，您需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e3505-141">If you selected an existing WCF-OracleEBS send port, you need not specify the binding properties.</span></span> <span data-ttu-id="e3505-142">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e3505-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="e3505-143">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="e3505-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="e3505-144">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3505-144">In such a case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="e3505-145">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="e3505-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

8. <span data-ttu-id="e3505-146">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="e3505-146">Click **OK**.</span></span>  

## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a><span data-ttu-id="e3505-147">指定繫結屬性從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="e3505-147">Specifying Binding Properties from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="e3505-148">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定的繫結屬性，Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="e3505-148">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the binding properties as part of the WCF-Custom or WCF-OracleEBS port configuration.</span></span>  

#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="e3505-149">若要指定 WCF 自訂連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e3505-149">To specify binding properties for the WCF-Custom port</span></span>  

1. <span data-ttu-id="e3505-150">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e3505-150">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="e3505-151">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="e3505-151">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="e3505-152">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e3505-152">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="e3505-153">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e3505-153">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="e3505-154">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="e3505-154">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

4. <span data-ttu-id="e3505-155">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e3505-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  

5. <span data-ttu-id="e3505-156">從**繫結的型別**清單中，選取**oracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="e3505-156">From the **Binding Type** list, select **oracleEBSBinding**.</span></span>  

6. <span data-ttu-id="e3505-157">在 **組態**方塊，指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e3505-157">In the **Configuration** box, specify the values for the different binding properties, and then click **OK**.</span></span>  

#### <a name="to-specify-binding-properties-for-the-wcf-oracleebs-port"></a><span data-ttu-id="e3505-158">若要指定 Wcf-oracleebs 連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e3505-158">To specify binding properties for the WCF-OracleEBS port</span></span>  

1. <span data-ttu-id="e3505-159">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e3505-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="e3505-160">新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e3505-160">Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="e3505-161">如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="e3505-161">For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="e3505-162">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="e3505-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="e3505-163">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e3505-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="e3505-164">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-oracleebs 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e3505-164">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleEBS adapter you added earlier, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="e3505-165">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="e3505-165">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="e3505-166">在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e3505-166">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="e3505-167">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="e3505-167">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="e3505-168">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="e3505-168">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e3505-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3505-169">See Also</span></span>  
 [<span data-ttu-id="e3505-170">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="e3505-170">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)