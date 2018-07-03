---
title: 設定 SAP 配接器的繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at design time
- binding properties, specifying at run time
ms.assetid: 259a5895-c19d-409c-b2fc-bfdf59d5d74b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ef599f91675d4604d9e9f56aafdef3677d2583a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001967"
---
# <a name="configure-the-binding-properties-for-the-sap-adapter"></a><span data-ttu-id="56ee2-102">設定 SAP 配接器的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-102">Configure the binding properties for the SAP adapter</span></span>
<span data-ttu-id="56ee2-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現可讓您控制其行為特性的數個繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="56ee2-104">本節提供有關設定繫結屬性，從 Visual Studio （設計階段） 和資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]（執行階段） 的管理主控台。</span><span class="sxs-lookup"><span data-stu-id="56ee2-104">This section provides information about setting the binding properties from Visual Studio (design time) and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console (run time).</span></span> <span data-ttu-id="56ee2-105">在設計階段，您必須指定要產生結構描述的特定作業的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-105">At design time, you must specify the binding properties to generate schema for specific operations.</span></span> <span data-ttu-id="56ee2-106">在執行階段，必須指定的繫結屬性一部分傳送或接收埠的傳送或接收訊息，從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="56ee2-106">At run time, you must specify the binding properties as part of the send or receive port for sending or receiving messages from the SAP system.</span></span>  

 <span data-ttu-id="56ee2-107">如需繫結屬性的資訊，包括一份的繫結屬性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="56ee2-107">For information about the binding properties, including a list of binding properties for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  

## <a name="enter-binding-properties-at-design-time"></a><span data-ttu-id="56ee2-108">在設計階段中輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-108">Enter Binding Properties at Design Time</span></span>  
 <span data-ttu-id="56ee2-109">設計階段，您可以指定使用的繫結屬性[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56ee2-109">For design time, you can specify the binding properties using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="56ee2-110">輸入 取用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-110">Enter binding properties using Consume Adapter Service Add-in</span></span>  

1.  <span data-ttu-id="56ee2-111">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-111">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2.  <span data-ttu-id="56ee2-112">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56ee2-112">In the **Add Generated Items** dialog box, do the following:</span></span>  

    |<span data-ttu-id="56ee2-113">使用</span><span class="sxs-lookup"><span data-stu-id="56ee2-113">Use this</span></span>|<span data-ttu-id="56ee2-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="56ee2-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="56ee2-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="56ee2-115">**Categories**</span></span>|<span data-ttu-id="56ee2-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="56ee2-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="56ee2-117">**Templates**</span></span>|<span data-ttu-id="56ee2-118">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-118">Click **Consume Adapter Service**.</span></span>|  

3.  <span data-ttu-id="56ee2-119">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4.  <span data-ttu-id="56ee2-120">在**取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="56ee2-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  

5.  <span data-ttu-id="56ee2-121">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後再指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and then specify the different binding properties.</span></span>  

6.  <span data-ttu-id="56ee2-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="56ee2-122">Click **OK**.</span></span>  

### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="56ee2-123">輸入繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="56ee2-123">Enter binding properties using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="56ee2-124">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-124">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2. <span data-ttu-id="56ee2-125">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56ee2-125">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="56ee2-126">使用</span><span class="sxs-lookup"><span data-stu-id="56ee2-126">Use this</span></span>    |           <span data-ttu-id="56ee2-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="56ee2-127">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="56ee2-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="56ee2-128">**Categories**</span></span> |     <span data-ttu-id="56ee2-129">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-129">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="56ee2-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="56ee2-130">**Templates**</span></span>  | <span data-ttu-id="56ee2-131">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-131">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="56ee2-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-132">Click **Add**.</span></span> <span data-ttu-id="56ee2-133">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="56ee2-133">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="56ee2-134">在 [新增配接器精靈] 中，選取**WCF-SAP**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-134">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="56ee2-135">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="56ee2-135">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="56ee2-136">如果您已經在 BizTalk 中設定的 WCF SAP 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="56ee2-136">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="56ee2-137">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="56ee2-137">Click **Next**.</span></span>  

6. <span data-ttu-id="56ee2-138">在**取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="56ee2-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  

7. <span data-ttu-id="56ee2-139">按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="56ee2-139">Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="56ee2-140">例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**才會產生從 SAP 系統接收 IDOC 的結構描述的屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-140">For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system.</span></span> <span data-ttu-id="56ee2-141">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="56ee2-141">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="56ee2-142">如果您選取現有的 WCF SAP 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-142">If you selected an existing WCF-SAP send port, you need not specify the binding properties.</span></span> <span data-ttu-id="56ee2-143">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="56ee2-143">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="56ee2-144">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="56ee2-144">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="56ee2-145">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56ee2-145">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="56ee2-146">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="56ee2-146">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

8. <span data-ttu-id="56ee2-147">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="56ee2-147">Click **OK**.</span></span>  

## <a name="enter-binding-properties-at-run-time"></a><span data-ttu-id="56ee2-148">在執行階段輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-148">Enter Binding Properties at Run Time</span></span>  
 <span data-ttu-id="56ee2-149">執行階段，您可以指定繫結內容 WCF 自訂連接埠或中的 WCF SAP 組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="56ee2-149">For run time, you can specify the binding properties as part of the WCF-Custom port or WCF-SAP configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

### <a name="enter-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="56ee2-150">輸入 WCF 自訂連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-150">Enter binding properties for the WCF-Custom port</span></span>  

1. <span data-ttu-id="56ee2-151">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="56ee2-151">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="56ee2-152">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-152">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="56ee2-153">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="56ee2-153">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="56ee2-154">在**連接埠屬性**  對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-154">In the **Port Properties** dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="56ee2-155">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-155">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

4. <span data-ttu-id="56ee2-156">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="56ee2-156">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  

5. <span data-ttu-id="56ee2-157">從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-157">From the **Binding Type** drop-down list, select **sapBinding**.</span></span>  

6. <span data-ttu-id="56ee2-158">在 **組態**方塊，指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-158">In the **Configuration** box, specify the values for the different binding properties, and then click **OK**.</span></span>  

### <a name="enter-binging-properties-for-the-wcf-sap-port"></a><span data-ttu-id="56ee2-159">輸入 WCF SAP 連接埠的繫結的屬性</span><span class="sxs-lookup"><span data-stu-id="56ee2-159">Enter binging properties for the WCF-SAP port</span></span>  

1. <span data-ttu-id="56ee2-160">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="56ee2-160">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="56ee2-161">新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="56ee2-161">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="56ee2-162">如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="56ee2-162">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="56ee2-163">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-163">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="56ee2-164">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="56ee2-164">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="56ee2-165">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-165">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="56ee2-166">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="56ee2-166">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="56ee2-167">在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="56ee2-167">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="56ee2-168">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="56ee2-168">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="56ee2-169">比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態</span><span class="sxs-lookup"><span data-stu-id="56ee2-169">For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.</span></span>  

6. <span data-ttu-id="56ee2-170">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="56ee2-170">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="56ee2-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56ee2-171">See Also</span></span>  
[<span data-ttu-id="56ee2-172">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="56ee2-172">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)