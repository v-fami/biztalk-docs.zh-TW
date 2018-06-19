---
title: 設定 SAP 配接器的繫結屬性 |Microsoft 文件
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
ms.openlocfilehash: a16a95818ed4d63fd97b9fca1f9ea86ebd14de80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217438"
---
# <a name="configure-the-binding-properties-for-the-sap-adapter"></a><span data-ttu-id="2df3f-102">設定 SAP 配接器的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-102">Configure the binding properties for the SAP adapter</span></span>
<span data-ttu-id="2df3f-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。</span><span class="sxs-lookup"><span data-stu-id="2df3f-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="2df3f-104">本節提供從 Visual Studio （設計階段），然後從設定的繫結屬性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 （執行時間）。</span><span class="sxs-lookup"><span data-stu-id="2df3f-104">This section provides information about setting the binding properties from Visual Studio (design time) and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console (run time).</span></span> <span data-ttu-id="2df3f-105">在設計階段，您必須指定要產生結構描述的特定作業的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="2df3f-105">At design time, you must specify the binding properties to generate schema for specific operations.</span></span> <span data-ttu-id="2df3f-106">在執行階段，必須指定的繫結屬性一部分傳送或接收埠的傳送或接收訊息從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="2df3f-106">At run time, you must specify the binding properties as part of the send or receive port for sending or receiving messages from the SAP system.</span></span>  
  
 <span data-ttu-id="2df3f-107">如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2df3f-107">For information about the binding properties, including a list of binding properties for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
## <a name="enter-binding-properties-at-design-time"></a><span data-ttu-id="2df3f-108">在設計階段輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-108">Enter Binding Properties at Design Time</span></span>  
 <span data-ttu-id="2df3f-109">設計階段，您可以指定繫結屬性使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2df3f-109">For design time, you can specify the binding properties using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="2df3f-110">輸入使用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-110">Enter binding properties using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="2df3f-111">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-111">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="2df3f-112">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2df3f-112">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2df3f-113">使用</span><span class="sxs-lookup"><span data-stu-id="2df3f-113">Use this</span></span>|<span data-ttu-id="2df3f-114">動作</span><span class="sxs-lookup"><span data-stu-id="2df3f-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2df3f-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="2df3f-115">**Categories**</span></span>|<span data-ttu-id="2df3f-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="2df3f-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="2df3f-117">**Templates**</span></span>|<span data-ttu-id="2df3f-118">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-118">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="2df3f-119">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="2df3f-120">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="2df3f-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="2df3f-121">在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤，然後再指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="2df3f-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and then specify the different binding properties.</span></span>  
  
6.  <span data-ttu-id="2df3f-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-122">Click **OK**.</span></span>  
  
### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="2df3f-123">輸入繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="2df3f-123">Enter binding properties using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="2df3f-124">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-124">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="2df3f-125">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2df3f-125">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2df3f-126">使用</span><span class="sxs-lookup"><span data-stu-id="2df3f-126">Use this</span></span>|<span data-ttu-id="2df3f-127">動作</span><span class="sxs-lookup"><span data-stu-id="2df3f-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2df3f-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="2df3f-128">**Categories**</span></span>|<span data-ttu-id="2df3f-129">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-129">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="2df3f-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="2df3f-130">**Templates**</span></span>|<span data-ttu-id="2df3f-131">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-131">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="2df3f-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-132">Click **Add**.</span></span> <span data-ttu-id="2df3f-133">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2df3f-133">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="2df3f-134">在 新增配接器精靈 中，選取  **WCF SAP**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-134">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="2df3f-135">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2df3f-135">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2df3f-136">如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="2df3f-136">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="2df3f-137">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="2df3f-138">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="2df3f-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.</span></span>  
  
7.  <span data-ttu-id="2df3f-139">按一下**繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。</span><span class="sxs-lookup"><span data-stu-id="2df3f-139">Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="2df3f-140">例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**屬性，才能產生從 SAP 系統接收 IDOC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2df3f-140">For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system.</span></span> <span data-ttu-id="2df3f-141">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2df3f-141">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2df3f-142">如果您選取現有的 WCF SAP 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="2df3f-142">If you selected an existing WCF-SAP send port, you need not specify the binding properties.</span></span> <span data-ttu-id="2df3f-143">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="2df3f-143">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="2df3f-144">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="2df3f-144">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="2df3f-145">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2df3f-145">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="2df3f-146">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="2df3f-146">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
8.  <span data-ttu-id="2df3f-147">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-147">Click **OK**.</span></span>  
  
## <a name="enter-binding-properties-at-run-time"></a><span data-ttu-id="2df3f-148">在執行階段輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-148">Enter Binding Properties at Run Time</span></span>  
 <span data-ttu-id="2df3f-149">對於執行階段，您可以指定繫結屬性為 WCF 自訂連接埠或中的 WCF SAP 組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2df3f-149">For run time, you can specify the binding properties as part of the WCF-Custom port or WCF-SAP configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="enter-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="2df3f-150">輸入 WCF 自訂連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-150">Enter binding properties for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="2df3f-151">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2df3f-151">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2df3f-152">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-152">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="2df3f-153">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2df3f-153">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="2df3f-154">在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-154">In the **Port Properties** dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2df3f-155">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-155">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2df3f-156">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2df3f-156">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
5.  <span data-ttu-id="2df3f-157">從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-157">From the **Binding Type** drop-down list, select **sapBinding**.</span></span>  
  
6.  <span data-ttu-id="2df3f-158">在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-158">In the **Configuration** box, specify the values for the different binding properties, and then click **OK**.</span></span>  
  
### <a name="enter-binging-properties-for-the-wcf-sap-port"></a><span data-ttu-id="2df3f-159">輸入 WCF SAP 連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="2df3f-159">Enter binging properties for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="2df3f-160">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2df3f-160">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2df3f-161">加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2df3f-161">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="2df3f-162">如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="2df3f-162">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="2df3f-163">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-163">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="2df3f-164">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2df3f-164">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="2df3f-165">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-165">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2df3f-166">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-166">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="2df3f-167">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="2df3f-167">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2df3f-168">根據您要設定傳送埠或接收埠會繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="2df3f-168">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="2df3f-169">比方說，繫結內容相關的輸入都無法使用作業時設定的傳送埠，因為輸入的操作需要接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="2df3f-169">For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.</span></span>  
  
6.  <span data-ttu-id="2df3f-170">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2df3f-170">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df3f-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df3f-171">See Also</span></span>  
[<span data-ttu-id="2df3f-172">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="2df3f-172">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)