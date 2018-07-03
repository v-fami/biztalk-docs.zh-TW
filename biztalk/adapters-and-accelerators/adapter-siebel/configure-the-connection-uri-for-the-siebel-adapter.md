---
title: 設定 Siebel 配接器的連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, specifying
ms.assetid: b89b60e9-0f3b-4305-865e-9d3b40d04648
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070925b09cf4e4896097be1aa88bc57fcd625626
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992391"
---
# <a name="configure-the-connection-uri-for-the-siebel-adapter"></a><span data-ttu-id="718c4-102">設定 Siebel 配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="718c4-102">Configure the connection URI for the Siebel adapter</span></span>
<span data-ttu-id="718c4-103">連線 URI 是連接至 Siebel 系統的連接字串。</span><span class="sxs-lookup"><span data-stu-id="718c4-103">A connection URI is a connection string to connect to a Siebel system.</span></span> <span data-ttu-id="718c4-104">連線 URI 包含建立與 Siebel 系統的連線所需的各種參數。</span><span class="sxs-lookup"><span data-stu-id="718c4-104">The connection URI contains various parameters required to establish connection with a Siebel system.</span></span> <span data-ttu-id="718c4-105">您必須指定此連線在設計階段和執行的階段的 URI。</span><span class="sxs-lookup"><span data-stu-id="718c4-105">You must specify this connection URI both at the design time and the run time.</span></span> <span data-ttu-id="718c4-106">在設計階段，您必須指定要連接至 Siebel 系統產生的中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="718c4-106">At design time, you must specify the URI to connect to the Siebel system to generate the metadata.</span></span> <span data-ttu-id="718c4-107">在執行階段，您必須指定要連接至 Siebel 系統來執行作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="718c4-107">At run time, you must specify the URI to connect to the Siebel system to perform operations.</span></span>  

## <a name="enter-the-connection-uri-at-design-time"></a><span data-ttu-id="718c4-108">輸入連線 URI，在設計階段</span><span class="sxs-lookup"><span data-stu-id="718c4-108">Enter the connection URI at design time</span></span>  
 <span data-ttu-id="718c4-109">針對設計階段，您必須指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="718c4-109">For design time, you must specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="enter-the-connection-uri-using-consume-adapter-service-add-in"></a><span data-ttu-id="718c4-110">輸入連線 URI 使用取用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="718c4-110">Enter the connection URI using Consume Adapter Service Add-in</span></span>  

1. <span data-ttu-id="718c4-111">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="718c4-111">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  

2. <span data-ttu-id="718c4-112">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="718c4-112">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="718c4-113">使用</span><span class="sxs-lookup"><span data-stu-id="718c4-113">Use this</span></span>    |             <span data-ttu-id="718c4-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="718c4-114">To do this</span></span>             |
   |----------------|------------------------------------|
   | <span data-ttu-id="718c4-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="718c4-115">**Categories**</span></span> | <span data-ttu-id="718c4-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="718c4-116">Click **Consume Adapter Service**.</span></span> |
   | <span data-ttu-id="718c4-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="718c4-117">**Templates**</span></span>  | <span data-ttu-id="718c4-118">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="718c4-118">Click **Consume Adapter Service**.</span></span> |


3. <span data-ttu-id="718c4-119">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="718c4-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4. <span data-ttu-id="718c4-120">在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**siebelBinding**，，按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="718c4-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.</span></span>  

5. <span data-ttu-id="718c4-121">在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="718c4-121">In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  

6. <span data-ttu-id="718c4-122">在 [**設定介面卡**] 對話方塊中，按一下**URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="718c4-122">In the **Configure Adapter** dialog box, click the **URI Properties** tab and specify values for different parameters.</span></span> <span data-ttu-id="718c4-123">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-123">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  

7. <span data-ttu-id="718c4-124">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="718c4-124">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="718c4-125">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-125">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  

8. <span data-ttu-id="718c4-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="718c4-126">Click **OK**.</span></span>  

#### <a name="enter-the-connection-uri-using-add-adapter-metadata-wizard"></a><span data-ttu-id="718c4-127">輸入連線 URI，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="718c4-127">Enter the connection URI using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="718c4-128">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="718c4-128">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  

2. <span data-ttu-id="718c4-129">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="718c4-129">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="718c4-130">使用</span><span class="sxs-lookup"><span data-stu-id="718c4-130">Use this</span></span>    |           <span data-ttu-id="718c4-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="718c4-131">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="718c4-132">**類別**</span><span class="sxs-lookup"><span data-stu-id="718c4-132">**Categories**</span></span> |     <span data-ttu-id="718c4-133">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="718c4-133">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="718c4-134">**範本**</span><span class="sxs-lookup"><span data-stu-id="718c4-134">**Templates**</span></span>  | <span data-ttu-id="718c4-135">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="718c4-135">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="718c4-136">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="718c4-136">Click **Add**.</span></span> <span data-ttu-id="718c4-137">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="718c4-137">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="718c4-138">在 [新增配接器精靈] 中，選取**Wcf-siebel**。</span><span class="sxs-lookup"><span data-stu-id="718c4-138">In the Add Adapter Wizard, select **WCF-Siebel**.</span></span> <span data-ttu-id="718c4-139">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="718c4-139">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="718c4-140">如果您已經設定 biztalk Wcf-siebel 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="718c4-140">If you already have a WCF-Siebel port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="718c4-141">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="718c4-141">Click **Next**.</span></span>  

6. <span data-ttu-id="718c4-142">在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**siebelBinding**，，按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="718c4-142">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.</span></span>  

7. <span data-ttu-id="718c4-143">在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。從**用戶端認證類型**下拉式清單方塊中，選取**Username**和指定的使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="718c4-143">In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  

8. <span data-ttu-id="718c4-144">在 [**設定介面卡**] 對話方塊中，按一下**URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="718c4-144">In the **Configure Adapter** dialog box, click the **URI Properties** tab and specify values for different parameters.</span></span> <span data-ttu-id="718c4-145">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-145">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  

9. <span data-ttu-id="718c4-146">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，也就是必須指定才會產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="718c4-146">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema.</span></span> <span data-ttu-id="718c4-147">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-147">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="718c4-148">如果您選取現有的 Wcf-siebel 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="718c4-148">If you selected an existing WCF-Siebel send port, you need not specify the binding properties.</span></span> <span data-ttu-id="718c4-149">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="718c4-149">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="718c4-150">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="718c4-150">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="718c4-151">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="718c4-151">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="718c4-152">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="718c4-152">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

10. <span data-ttu-id="718c4-153">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="718c4-153">Click **OK**.</span></span>  

## <a name="enter-the-connection-uri-at-run-time"></a><span data-ttu-id="718c4-154">輸入連線 URI，在執行階段</span><span class="sxs-lookup"><span data-stu-id="718c4-154">Enter the connection URI at run time</span></span>  
 <span data-ttu-id="718c4-155">針對執行階段，您必須指定 URI 中的 WCF 自訂] 或 [Wcf-siebel 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="718c4-155">For run time, you must specify the URI as part of the WCF-Custom or WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  

#### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a><span data-ttu-id="718c4-156">輸入 WCF 自訂連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="718c4-156">Enter the connection URI for the WCF-Custom port</span></span>  

1. <span data-ttu-id="718c4-157">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="718c4-157">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="718c4-158">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開您要在其下建立連接埠，然後按一下 應用程式**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="718c4-158">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and the click **Send Ports**.</span></span> <span data-ttu-id="718c4-159">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="718c4-159">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="718c4-160">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="718c4-160">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

4. <span data-ttu-id="718c4-161">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="718c4-161">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  

5. <span data-ttu-id="718c4-162">在 **位址 (URI)** 文字方塊中，指定連線連接至 Siebel 系統的 URI。</span><span class="sxs-lookup"><span data-stu-id="718c4-162">In the **Address (URI)** text box, specify the connection URI to connect to the Siebel system.</span></span> <span data-ttu-id="718c4-163">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-163">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  

6. <span data-ttu-id="718c4-164">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。從**繫結的型別**下拉式清單中，選取**siebelBinding**。</span><span class="sxs-lookup"><span data-stu-id="718c4-164">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **siebelBinding**.</span></span>  

7. <span data-ttu-id="718c4-165">若要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="718c4-165">To create a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   1.  <span data-ttu-id="718c4-166">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="718c4-166">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  

   2.  <span data-ttu-id="718c4-167">選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="718c4-167">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  

8. <span data-ttu-id="718c4-168">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="718c4-168">Click **OK**.</span></span>  

#### <a name="enter-the-connection-uri-for-the-wcf-siebel-port"></a><span data-ttu-id="718c4-169">輸入連線 URI Wcf-siebel 連接埠</span><span class="sxs-lookup"><span data-stu-id="718c4-169">Enter the connection URI for the WCF-Siebel port</span></span>  

1. <span data-ttu-id="718c4-170">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="718c4-170">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="718c4-171">新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="718c4-171">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="718c4-172">如需相關指示，請參閱 < [Siebel 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-172">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="718c4-173">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開您要在其下建立連接埠，然後按一下 應用程式**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="718c4-173">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and the click **Send Ports**.</span></span> <span data-ttu-id="718c4-174">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="718c4-174">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="718c4-175">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-siebel 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="718c4-175">In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel adapter you added earlier, and then click **Configure**.</span></span>  

5. <span data-ttu-id="718c4-176">在 傳輸屬性 對話方塊中，按一下**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="718c4-176">In the transport properties dialog box, click the **General** tab.</span></span>  

6. <span data-ttu-id="718c4-177">按一下 **設定**按鈕，並提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="718c4-177">Click the **Configure** button and provide values for the connection parameters.</span></span> <span data-ttu-id="718c4-178">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="718c4-178">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  

7. <span data-ttu-id="718c4-179">在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="718c4-179">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  

8. <span data-ttu-id="718c4-180">若要建立傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="718c4-180">To create a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   1.  <span data-ttu-id="718c4-181">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="718c4-181">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  

   2.  <span data-ttu-id="718c4-182">選取 **使用單一登入**選項，並指定分支機構 ESSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="718c4-182">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  

9. <span data-ttu-id="718c4-183">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="718c4-183">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="718c4-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="718c4-184">See Also</span></span>  
[<span data-ttu-id="718c4-185">若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="718c4-185">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)