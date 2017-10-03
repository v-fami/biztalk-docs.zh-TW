---
title: "連接至 Siebel 系統在 Visual Studio 使用新增配接器中繼資料精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0a82fcc-b3ac-4936-9210-03c99d3741d7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9fc38299ffdce6cf6227cacb7de0cae84b22091
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="cea99-102">連接至 Siebel 系統在 Visual Studio 使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="cea99-102">Connect to the Siebel System in Visual Studio Using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="cea99-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也會公開成 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述您想要使用配接器在 Siebel 系統上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="cea99-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is also exposed as a BizTalk adapter and hence, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on the Siebel system using the adapter.</span></span>  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-metadata-wizard"></a><span data-ttu-id="cea99-104">連接到使用 Siebel 系統新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="cea99-104">Connecting to a Siebel System Using Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="cea99-105">執行下列步驟來連接使用 Siebel 系統[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cea99-105">Perform the following steps to connect to a Siebel system using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-connect-to-a-siebel-system"></a><span data-ttu-id="cea99-106">連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="cea99-106">To connect to a Siebel system</span></span>  
  
1.  <span data-ttu-id="cea99-107">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="cea99-107">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="cea99-108">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cea99-108">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="cea99-109">以滑鼠右鍵按一下方案總管] 中的專案，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="cea99-109">Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    3.  <span data-ttu-id="cea99-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cea99-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="cea99-111">使用</span><span class="sxs-lookup"><span data-stu-id="cea99-111">Use this</span></span>|<span data-ttu-id="cea99-112">動作</span><span class="sxs-lookup"><span data-stu-id="cea99-112">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="cea99-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="cea99-113">**Categories**</span></span>|<span data-ttu-id="cea99-114">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="cea99-114">Click **Consume Adapter Service**.</span></span>|  
        |<span data-ttu-id="cea99-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="cea99-115">**Templates**</span></span>|<span data-ttu-id="cea99-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="cea99-116">Click **Consume Adapter Service**.</span></span>|  
  
    4.  <span data-ttu-id="cea99-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="cea99-117">Click **Add**.</span></span> <span data-ttu-id="cea99-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cea99-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
    5.  <span data-ttu-id="cea99-119">在[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取 Wcf-siebel。</span><span class="sxs-lookup"><span data-stu-id="cea99-119">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select WCF-Siebel.</span></span> <span data-ttu-id="cea99-120">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="cea99-120">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="cea99-121">如果您已經有**Wcf-siebel**通訊埠設定中的 BizTalk，請選取連接埠從**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="cea99-121">If you already have a **WCF-Siebel** port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
    6.  <span data-ttu-id="cea99-122">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="cea99-122">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="cea99-123">從**選取繫結**下拉式清單中選取**siebelBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cea99-123">From the **Select a binding** drop-down list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
3.  <span data-ttu-id="cea99-124">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.</span><span class="sxs-lookup"><span data-stu-id="cea99-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username**.</span></span>  
  
4.  <span data-ttu-id="cea99-125">指定的使用者名稱和密碼，以連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="cea99-125">Specify the user name and password to connect to the Siebel system.</span></span>  
  
5.  <span data-ttu-id="cea99-126">按一下**URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="cea99-126">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="cea99-127">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="cea99-127">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cea99-128">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="cea99-128">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="cea99-129">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="cea99-129">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
6.  <span data-ttu-id="cea99-130">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="cea99-130">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="cea99-131">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cea99-131">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cea99-132">如果產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]且您選取現有的 WCF Siebel 傳送埠，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cea99-132">If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-Siebel send port, you need not specify the binding properties.</span></span> <span data-ttu-id="cea99-133">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="cea99-133">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="cea99-134">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="cea99-134">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="cea99-135">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cea99-135">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="cea99-136">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="cea99-136">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
7.  <span data-ttu-id="cea99-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cea99-137">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="cea99-138">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="cea99-138">Click **Connect**.</span></span> <span data-ttu-id="cea99-139">一旦建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="cea99-139">Once the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="cea99-140">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="cea99-140">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  
  
     <span data-ttu-id="cea99-141">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span><span class="sxs-lookup"><span data-stu-id="cea99-141">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span></span>  
  
     <span data-ttu-id="cea99-142">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點包含各種可以 Siebel 系統執行的作業。</span><span class="sxs-lookup"><span data-stu-id="cea99-142">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on the Siebel system.</span></span> <span data-ttu-id="cea99-143">例如，**商務物件**節點包含所有的商務物件和 Siebel 系統叫用的商務元件。</span><span class="sxs-lookup"><span data-stu-id="cea99-143">For example, the **Business Objects** node contains all the business objects and business components that can be invoked on the Siebel system.</span></span> <span data-ttu-id="cea99-144">同樣地，**商務服務**節點包含您連接至 Siebel 系統中的所有商務服務。</span><span class="sxs-lookup"><span data-stu-id="cea99-144">Similarly, the **Business Services**  node contains all the business services in the Siebel system you connected to.</span></span> <span data-ttu-id="cea99-145">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。</span><span class="sxs-lookup"><span data-stu-id="cea99-145">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>