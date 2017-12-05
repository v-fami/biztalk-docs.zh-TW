---
title: "在 Visual Studio 中使用連接至 SAP 新增配接器中繼資料精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a442837b-e7d8-4edb-9c5e-5603d4c58fe5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db24d079dc428c69733e36141280504f97728b26
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="connecting-to-sap-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="28664-102">在 Visual Studio 中使用連接至 SAP 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="28664-102">Connecting to SAP in Visual Studio Using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="28664-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也會公開成 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述您想要在使用配接器的 SAP 系統上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="28664-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is also exposed as a BizTalk adapter and hence, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on an SAP system using the adapter.</span></span>  
  
## <a name="connecting-to-an-sap-system-using-add-adapter-metadata-wizard"></a><span data-ttu-id="28664-104">連接到 SAP 系統使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="28664-104">Connecting to an SAP System Using Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="28664-105">執行下列步驟來連接 SAP 系統使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28664-105">Perform the following steps to connect to an SAP system using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-connect-to-an-sap-system"></a><span data-ttu-id="28664-106">若要連接至 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="28664-106">To connect to an SAP system</span></span>  
  
1.  <span data-ttu-id="28664-107">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="28664-107">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="28664-108">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28664-108">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="28664-109">以滑鼠右鍵按一下方案總管] 中的專案名稱，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="28664-109">Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    3.  <span data-ttu-id="28664-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="28664-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="28664-111">使用</span><span class="sxs-lookup"><span data-stu-id="28664-111">Use this</span></span>|<span data-ttu-id="28664-112">動作</span><span class="sxs-lookup"><span data-stu-id="28664-112">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="28664-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="28664-113">**Categories**</span></span>|<span data-ttu-id="28664-114">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="28664-114">Click **Add Adapter**.</span></span>|  
        |<span data-ttu-id="28664-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="28664-115">**Templates**</span></span>|<span data-ttu-id="28664-116">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="28664-116">Click **Add Adapter Metadata**.</span></span>|  
  
    4.  <span data-ttu-id="28664-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="28664-117">Click **Add**.</span></span> <span data-ttu-id="28664-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="28664-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
    5.  <span data-ttu-id="28664-119">在 新增配接器精靈 中，選取  **WCF SAP**。</span><span class="sxs-lookup"><span data-stu-id="28664-119">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="28664-120">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="28664-120">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="28664-121">如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="28664-121">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
    6.  <span data-ttu-id="28664-122">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="28664-122">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="28664-123">從**選取繫結**下拉式清單中選取**sapBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="28664-123">From the **Select a binding** drop-down list, select **sapBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="28664-124">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="28664-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="28664-125">如果您使用 SAP 安全網路連線 (SNC) 程式庫連接到 SAP 系統，請勿指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="28664-125">If you are using the SAP Secure Network Connection (SNC) library to connect to an SAP system, do not specify a username and password.</span></span>  
  
4.  <span data-ttu-id="28664-126">按一下**URI 屬性**索引標籤上，指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="28664-126">Click the **URI Properties** tab and specify values for the connection parameters.</span></span> <span data-ttu-id="28664-127">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="28664-127">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="28664-128">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**UseSnc**連接屬性設**True**。</span><span class="sxs-lookup"><span data-stu-id="28664-128">If you are using the SAP SNC library to connect to an SAP system, set the **UseSnc** connection property to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28664-129">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="28664-129">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="28664-130">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="28664-130">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
5.  <span data-ttu-id="28664-131">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="28664-131">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="28664-132">例如，如果您要當做目標 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。</span><span class="sxs-lookup"><span data-stu-id="28664-132">For example, if you want to target a ReceiveIdoc operation you must set the **ReceiveIdocFormat** binding property to String.</span></span> <span data-ttu-id="28664-133">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="28664-133">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28664-134">如果產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]且您選取現有的 WCF SAP 傳送埠，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="28664-134">If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-SAP send port, you need not specify the binding properties.</span></span> <span data-ttu-id="28664-135">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="28664-135">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="28664-136">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="28664-136">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="28664-137">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="28664-137">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="28664-138">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="28664-138">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="28664-139">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**SncLibrary**和**SncPartnerName**至適當的值。</span><span class="sxs-lookup"><span data-stu-id="28664-139">If you are using the SAP SNC library to connect to an SAP system, set the **SncLibrary** and **SncPartnerName** to appropriate values.</span></span>  
    >   
    >  <span data-ttu-id="28664-140">**SncLibrary**繫結屬性會使用路徑和檔名使用 SNC 連接到 SAP 系統所需的 dll。</span><span class="sxs-lookup"><span data-stu-id="28664-140">The **SncLibrary** binding property takes the path and the filename of the DLLs required for using SNC to connect to an SAP system.</span></span> <span data-ttu-id="28664-141">這些 Dll 必須要有與 SAP 用戶端電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="28664-141">These DLLs must be present on the computer with the SAP client and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installed.</span></span> <span data-ttu-id="28664-142">如需詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南位於\<安裝指南\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="28664-142">For more information see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide available at \<installation guide\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
    >   
    >  <span data-ttu-id="28664-143">**SncPartnerName**繫結屬性會採用 SNC 通訊夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="28664-143">The **SncPartnerName** binding property takes the SNC name of the communication partner.</span></span>  
  
6.  <span data-ttu-id="28664-144">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="28664-144">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="28664-145">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="28664-145">Click **Connect**.</span></span> <span data-ttu-id="28664-146">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="28664-146">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="28664-147">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="28664-147">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="28664-148">圖形化使用者介面是相同的[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28664-148">The graphical user interface is same for the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
     <span data-ttu-id="28664-149">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span><span class="sxs-lookup"><span data-stu-id="28664-149">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span></span>  
  
     <span data-ttu-id="28664-150">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會顯示包含各種不同成品可以叫用 SAP 系統中的不同節點。</span><span class="sxs-lookup"><span data-stu-id="28664-150">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various artifacts that can be invoked in an SAP system.</span></span> <span data-ttu-id="28664-151">例如， **RFC**節點包含所有您連接到 SAP 系統所提供的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="28664-151">For example, the **RFC** node contains all the RFCs available in the SAP system you connected to.</span></span> <span data-ttu-id="28664-152">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="28664-152">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28664-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="28664-153">See Also</span></span>  
 [<span data-ttu-id="28664-154">在 Visual Studio 中連接到 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="28664-154">Connect to the SAP System in Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)