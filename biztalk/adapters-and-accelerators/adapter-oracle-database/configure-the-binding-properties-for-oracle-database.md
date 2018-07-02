---
title: 設定 Oracle 資料庫繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at run time
- binding properties, specifying at design time
ms.assetid: c59a1b5c-b52b-4161-82de-c4d89bfce5c7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96922feab7c343893bfaa04ccbccd7c7e2f6a743
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981079"
---
# <a name="configure-the-binding-properties-for-oracle-database"></a><span data-ttu-id="eab51-102">設定 Oracle 資料庫繫結屬性</span><span class="sxs-lookup"><span data-stu-id="eab51-102">Configure the binding properties for Oracle Database</span></span>
<span data-ttu-id="eab51-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現可讓您控制其行為特性的數個繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="eab51-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="eab51-104">本節提供設定的繫結屬性，從 Visual Studio 和 BizTalk Server 管理主控台的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eab51-104">This section provides information about setting the binding properties from Visual Studio and from the BizTalk Server Administration console.</span></span> <span data-ttu-id="eab51-105">從 Visual Studio 中，您必須產生針對特定作業的結構描述時指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="eab51-105">From Visual Studio, you must specify the binding properties while generating schema for specific operations.</span></span> <span data-ttu-id="eab51-106">從 BizTalk Server 中，必須指定的繫結屬性一部分傳送或接收埠的傳送或接收訊息，從 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="eab51-106">From BizTalk Server, you must specify the binding properties as part of the send or receive port for sending or receiving messages from the Oracle database.</span></span>  

 <span data-ttu-id="eab51-107">如需繫結屬性的資訊，包括一份的繫結屬性[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="eab51-107">For information about the binding properties, including a list of binding properties for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  

## <a name="specifying-binding-properties-from-visual-studio"></a><span data-ttu-id="eab51-108">指定繫結屬性，從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eab51-108">Specifying Binding Properties from Visual Studio</span></span>  
 <span data-ttu-id="eab51-109">從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eab51-109">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="eab51-110">若要指定使用配接器服務增益集所使用的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="eab51-110">To specify binding properties using Consume Adapter Service Add-in</span></span>  

1.  <span data-ttu-id="eab51-111">以滑鼠右鍵按一下 BizTalk 專案，然後選取**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="eab51-111">Right-click your BizTalk project and then select **Add Generated Items**.</span></span>  

2.  <span data-ttu-id="eab51-112">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="eab51-112">In the **Add Generated Items** dialog box, do the following:</span></span>  

    |<span data-ttu-id="eab51-113">使用</span><span class="sxs-lookup"><span data-stu-id="eab51-113">Use this</span></span>|<span data-ttu-id="eab51-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="eab51-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="eab51-115">**類別**</span><span class="sxs-lookup"><span data-stu-id="eab51-115">**Categories**</span></span>|<span data-ttu-id="eab51-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="eab51-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="eab51-117">**範本**</span><span class="sxs-lookup"><span data-stu-id="eab51-117">**Templates**</span></span>|<span data-ttu-id="eab51-118">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="eab51-118">Click **Consume Adapter Service**.</span></span>|  

3.  <span data-ttu-id="eab51-119">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="eab51-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4.  <span data-ttu-id="eab51-120">在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleDBBinding**，，按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="eab51-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.</span></span>  

5.  <span data-ttu-id="eab51-121">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定不同的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="eab51-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the different binding properties.</span></span>  

6.  <span data-ttu-id="eab51-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="eab51-122">Click **OK**.</span></span>  

#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="eab51-123">若要指定繫結屬性使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="eab51-123">To specify binding properties using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="eab51-124">以滑鼠右鍵按一下 BizTalk 專案，然後選取**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="eab51-124">Right-click your BizTalk project and then select **Add Generated Items**.</span></span>  

2. <span data-ttu-id="eab51-125">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="eab51-125">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="eab51-126">使用</span><span class="sxs-lookup"><span data-stu-id="eab51-126">Use this</span></span>    |           <span data-ttu-id="eab51-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="eab51-127">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="eab51-128">**類別**</span><span class="sxs-lookup"><span data-stu-id="eab51-128">**Categories**</span></span> |     <span data-ttu-id="eab51-129">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="eab51-129">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="eab51-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="eab51-130">**Templates**</span></span>  | <span data-ttu-id="eab51-131">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="eab51-131">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="eab51-132">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="eab51-132">Click **Add**.</span></span> <span data-ttu-id="eab51-133">[新增配接器中繼資料精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="eab51-133">The Add Adapter Metadata Wizard opens.</span></span>  

4. <span data-ttu-id="eab51-134">在 [新增配接器中繼資料精靈] 中，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="eab51-134">In the Add Adapter Metadata Wizard, select **WCF-OracleDB**.</span></span> <span data-ttu-id="eab51-135">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="eab51-135">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="eab51-136">如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="eab51-136">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="eab51-137">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="eab51-137">Click **Next**.</span></span>  

6. <span data-ttu-id="eab51-138">在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleDBBinding**，，按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="eab51-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.</span></span>  

7. <span data-ttu-id="eab51-139">在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。</span><span class="sxs-lookup"><span data-stu-id="eab51-139">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="eab51-140">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="eab51-140">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="eab51-141">如果您選取現有的 Wcf-oracledb 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="eab51-141">If you selected an existing WCF-OracleDB send port, you need not specify the binding properties.</span></span> <span data-ttu-id="eab51-142">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="eab51-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="eab51-143">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="eab51-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="eab51-144">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="eab51-144">In such a case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="eab51-145">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="eab51-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

8. <span data-ttu-id="eab51-146">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="eab51-146">Click **OK**.</span></span>  

## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a><span data-ttu-id="eab51-147">指定繫結屬性從 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="eab51-147">Specifying Binding Properties from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="eab51-148">從 BizTalk Server 管理主控台中，您必須指定的繫結屬性，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="eab51-148">From the BizTalk Server Administration console, you must specify the binding properties as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  

#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="eab51-149">若要指定 WCF 自訂連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="eab51-149">To specify binding properties for the WCF-Custom port</span></span>  

1. <span data-ttu-id="eab51-150">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="eab51-150">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="eab51-151">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="eab51-151">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="eab51-152">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="eab51-152">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="eab51-153">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="eab51-153">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="eab51-154">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="eab51-154">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

4. <span data-ttu-id="eab51-155">在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eab51-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  

5. <span data-ttu-id="eab51-156">從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="eab51-156">From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  

6. <span data-ttu-id="eab51-157">在 **組態**方塊中指定不同的繫結屬性的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="eab51-157">In the **Configuration** box, specify the values for the different binding properties and click **OK**.</span></span>  

#### <a name="to-specify-binding-properties-for-the-wcf-oracledb-port"></a><span data-ttu-id="eab51-158">若要指定 Wcf-oracledb 連接埠的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="eab51-158">To specify binding properties for the WCF-OracleDB port</span></span>  

1. <span data-ttu-id="eab51-159">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="eab51-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="eab51-160">新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="eab51-160">Add the WCF-OracleDB adapter to the BizTalk Server Administration console.</span></span> <span data-ttu-id="eab51-161">如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="eab51-161">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="eab51-162">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="eab51-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="eab51-163">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="eab51-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="eab51-164">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-oracledb 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="eab51-164">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB adapter you added earlier, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="eab51-165">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="eab51-165">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="eab51-166">在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="eab51-166">In the transport properties dialog box, click the **Binding** tab, and specify values for binding properties.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="eab51-167">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="eab51-167">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="eab51-168">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="eab51-168">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  

## <a name="see-also"></a><span data-ttu-id="eab51-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eab51-169">See Also</span></span>  
[<span data-ttu-id="eab51-170">若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="eab51-170">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)