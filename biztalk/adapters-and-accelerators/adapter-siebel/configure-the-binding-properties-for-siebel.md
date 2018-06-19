---
title: 設定 siebel 繫結屬性 |Microsoft 文件
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
- how to, specify binding properties at design time
- how to, specify binding properties at run time
ms.assetid: 063e9507-8172-4fb0-8b9f-2f95e8a82f21
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b26e9e89319a14317113b730adb189f2f17587f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223134"
---
# <a name="configure-the-binding-properties-for-siebel"></a><span data-ttu-id="d3382-102">設定 siebel 繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-102">Configure the binding properties for Siebel</span></span>
<span data-ttu-id="d3382-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。</span><span class="sxs-lookup"><span data-stu-id="d3382-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="d3382-104">本節提供從 Visual Studio （設計階段），然後從設定的繫結屬性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 （執行時間）。</span><span class="sxs-lookup"><span data-stu-id="d3382-104">This section provides information about setting the binding properties from Visual Studio (design time) and from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console (run time).</span></span> <span data-ttu-id="d3382-105">在設計階段，您必須指定要產生結構描述的特定作業的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d3382-105">At design time, you must specify the binding properties to generate schema for specific operations.</span></span> <span data-ttu-id="d3382-106">在執行階段，您必須指定的繫結屬性的傳送埠將訊息傳送至 Siebel 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="d3382-106">At run time, you must specify the binding properties as part of the send port for sending messages to the Siebel system.</span></span>  
  
 <span data-ttu-id="d3382-107">如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d3382-107">For information about the binding properties, including a list of binding properties for [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
## <a name="enter-the-binding-properties-at-design-time"></a><span data-ttu-id="d3382-108">在設計階段輸入的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-108">Enter the binding properties at design time</span></span>  
 <span data-ttu-id="d3382-109">設計階段，您必須指定的繫結內容[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d3382-109">For design time, you must specify the binding properties from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dialog box.</span></span>  
  
#### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="d3382-110">輸入使用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-110">Enter binding properties using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="d3382-111">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d3382-111">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="d3382-112">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d3382-112">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d3382-113">使用</span><span class="sxs-lookup"><span data-stu-id="d3382-113">Use this</span></span>|<span data-ttu-id="d3382-114">動作</span><span class="sxs-lookup"><span data-stu-id="d3382-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d3382-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="d3382-115">**Categories**</span></span>|<span data-ttu-id="d3382-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d3382-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="d3382-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="d3382-117">**Templates**</span></span>|<span data-ttu-id="d3382-118">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d3382-118">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="d3382-119">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d3382-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="d3382-120">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="d3382-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="d3382-121">在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。</span><span class="sxs-lookup"><span data-stu-id="d3382-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="d3382-122">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d3382-122">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
6.  <span data-ttu-id="d3382-123">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d3382-123">Click **OK**.</span></span>  
  
#### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="d3382-124">輸入繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="d3382-124">Enter binding properties using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="d3382-125">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d3382-125">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="d3382-126">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d3382-126">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d3382-127">使用</span><span class="sxs-lookup"><span data-stu-id="d3382-127">Use this</span></span>|<span data-ttu-id="d3382-128">動作</span><span class="sxs-lookup"><span data-stu-id="d3382-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d3382-129">**類別**</span><span class="sxs-lookup"><span data-stu-id="d3382-129">**Categories**</span></span>|<span data-ttu-id="d3382-130">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="d3382-130">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="d3382-131">**範本**</span><span class="sxs-lookup"><span data-stu-id="d3382-131">**Templates**</span></span>|<span data-ttu-id="d3382-132">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="d3382-132">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="d3382-133">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="d3382-133">Click **Add**.</span></span> <span data-ttu-id="d3382-134">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3382-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="d3382-135">在 新增配接器精靈 中，選取  **Wcf-siebel**。</span><span class="sxs-lookup"><span data-stu-id="d3382-135">In the Add Adapter Wizard, select **WCF-Siebel**.</span></span> <span data-ttu-id="d3382-136">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3382-136">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d3382-137">如果您已設定在 BizTalk Wcf-siebel 連接埠，選取從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="d3382-137">If you already have a WCF-Siebel port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="d3382-138">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d3382-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d3382-139">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**.</span><span class="sxs-lookup"><span data-stu-id="d3382-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.</span></span>  
  
7.  <span data-ttu-id="d3382-140">在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。</span><span class="sxs-lookup"><span data-stu-id="d3382-140">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="d3382-141">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d3382-141">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3382-142">如果您選取現有的 WCF Siebel 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d3382-142">If you selected an existing WCF-Siebel send port, you need not specify the binding properties.</span></span> <span data-ttu-id="d3382-143">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="d3382-143">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="d3382-144">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="d3382-144">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="d3382-145">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d3382-145">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="d3382-146">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="d3382-146">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
8.  <span data-ttu-id="d3382-147">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d3382-147">Click **OK**.</span></span>  
  
## <a name="enter-binding-properties-at-run-time"></a><span data-ttu-id="d3382-148">在執行階段輸入繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-148">Enter binding properties at run time</span></span>  
 <span data-ttu-id="d3382-149">執行階段，您必須指定的繫結屬性，Wcf-custom 或 Wcf-siebel 連接埠組態中的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d3382-149">For run time, you must specify the binding properties as part of the WCF-Custom or the WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
#### <a name="enter-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="d3382-150">輸入 WCF 自訂連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-150">Enter binding properties for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="d3382-151">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d3382-151">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="d3382-152">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="d3382-152">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="d3382-153">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d3382-153">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="d3382-154">在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d3382-154">In the **Port Properties** dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="d3382-155">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d3382-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
5.  <span data-ttu-id="d3382-156">從**繫結的型別**下拉式清單中，選取**siebelBinding**。</span><span class="sxs-lookup"><span data-stu-id="d3382-156">From the **Binding Type** drop-down list, select **siebelBinding**.</span></span>  
  
6.  <span data-ttu-id="d3382-157">在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d3382-157">In the **Configuration** box, specify the values for the different binding properties and click **OK**.</span></span>  
  
#### <a name="enter-binding-properties-for-the-wcf-siebel-port"></a><span data-ttu-id="d3382-158">輸入 Wcf-siebel 連接埠繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d3382-158">Enter binding properties for the WCF-Siebel port</span></span>  
  
1.  <span data-ttu-id="d3382-159">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d3382-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="d3382-160">新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d3382-160">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="d3382-161">如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="d3382-161">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="d3382-162">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="d3382-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="d3382-163">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d3382-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="d3382-164">在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 Wcf-siebel 連接埠，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d3382-164">In the **Port Properties** dialog box, from the **Type** drop-down list, select the WCF-Siebel port you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="d3382-165">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d3382-165">In the transport properties dialog box, click the **Binding** tab and specify values for the binding properties.</span></span>  
  
6.  <span data-ttu-id="d3382-166">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d3382-166">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3382-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3382-167">See Also</span></span>  
[<span data-ttu-id="d3382-168">若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="d3382-168">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)