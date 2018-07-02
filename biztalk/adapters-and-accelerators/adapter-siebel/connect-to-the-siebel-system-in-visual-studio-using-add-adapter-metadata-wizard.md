---
title: 連接至 Siebel 系統在 Visual Studio 中使用新增配接器中繼資料精靈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0a82fcc-b3ac-4936-9210-03c99d3741d7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 700c2ad92cd03b50808f6a785b34b4d745482acb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983487"
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="d5c97-102">連接至 Siebel 系統在 Visual Studio 中使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="d5c97-102">Connect to the Siebel System in Visual Studio Using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="d5c97-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也會公開為 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生您想要使用配接器在 Siebel 系統上執行作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d5c97-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is also exposed as a BizTalk adapter and hence, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on the Siebel system using the adapter.</span></span>  

## <a name="connecting-to-a-siebel-system-using-add-adapter-metadata-wizard"></a><span data-ttu-id="d5c97-104">連接至 Siebel 系統，請使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="d5c97-104">Connecting to a Siebel System Using Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="d5c97-105">執行下列步驟來連接到 Siebel 系統使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5c97-105">Perform the following steps to connect to a Siebel system using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

#### <a name="to-connect-to-a-siebel-system"></a><span data-ttu-id="d5c97-106">若要連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="d5c97-106">To connect to a Siebel system</span></span>  

1. <span data-ttu-id="d5c97-107">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="d5c97-107">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  

   1. <span data-ttu-id="d5c97-108">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5c97-108">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  

   2. <span data-ttu-id="d5c97-109">以滑鼠右鍵按一下方案總管 中的專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-109">Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  

   3. <span data-ttu-id="d5c97-110">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d5c97-110">In the **Add Generated Items** dialog box, do the following:</span></span>  


      |    <span data-ttu-id="d5c97-111">使用</span><span class="sxs-lookup"><span data-stu-id="d5c97-111">Use this</span></span>    |             <span data-ttu-id="d5c97-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d5c97-112">To do this</span></span>             |
      |----------------|------------------------------------|
      | <span data-ttu-id="d5c97-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="d5c97-113">**Categories**</span></span> | <span data-ttu-id="d5c97-114">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-114">Click **Consume Adapter Service**.</span></span> |
      | <span data-ttu-id="d5c97-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="d5c97-115">**Templates**</span></span>  | <span data-ttu-id="d5c97-116">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-116">Click **Consume Adapter Service**.</span></span> |


   4. <span data-ttu-id="d5c97-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-117">Click **Add**.</span></span> <span data-ttu-id="d5c97-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d5c97-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

   5. <span data-ttu-id="d5c97-119">在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取 Wcf-siebel。</span><span class="sxs-lookup"><span data-stu-id="d5c97-119">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select WCF-Siebel.</span></span> <span data-ttu-id="d5c97-120">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5c97-120">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  

      > [!IMPORTANT]
      >  <span data-ttu-id="d5c97-121">如果您已經有**Wcf-siebel**連接埠中設定的 BizTalk，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="d5c97-121">If you already have a **WCF-Siebel** port configured in BizTalk, select the port from the **Port** list.</span></span>  

   6. <span data-ttu-id="d5c97-122">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d5c97-122">Click **Next**.</span></span>  

2. <span data-ttu-id="d5c97-123">從**選取的繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-123">From the **Select a binding** drop-down list, select **siebelBinding**, and then click **Configure**.</span></span>  

3. <span data-ttu-id="d5c97-124">中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.</span><span class="sxs-lookup"><span data-stu-id="d5c97-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username**.</span></span>  

4. <span data-ttu-id="d5c97-125">指定的使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="d5c97-125">Specify the user name and password to connect to the Siebel system.</span></span>  

5. <span data-ttu-id="d5c97-126">按一下  **URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="d5c97-126">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="d5c97-127">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c97-127">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="d5c97-128">如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="d5c97-128">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="d5c97-129">不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="d5c97-129">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  

6. <span data-ttu-id="d5c97-130">按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="d5c97-130">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="d5c97-131">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c97-131">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="d5c97-132">如果您要產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]並且選取現有的 Wcf-siebel 傳送埠，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c97-132">If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-Siebel send port, you need not specify the binding properties.</span></span> <span data-ttu-id="d5c97-133">從傳送埠組態，會挑選繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c97-133">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="d5c97-134">不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="d5c97-134">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="d5c97-135">在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d5c97-135">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="d5c97-136">不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="d5c97-136">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  

7. <span data-ttu-id="d5c97-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="d5c97-137">Click **OK**.</span></span>  

8. <span data-ttu-id="d5c97-138">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-138">Click **Connect**.</span></span> <span data-ttu-id="d5c97-139">一旦建立連線之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="d5c97-139">Once the connection is established, the connection status is shown as **Connected**.</span></span>  

    <span data-ttu-id="d5c97-140">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。</span><span class="sxs-lookup"><span data-stu-id="d5c97-140">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  

    <span data-ttu-id="d5c97-141">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span><span class="sxs-lookup"><span data-stu-id="d5c97-141">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span></span>  

    <span data-ttu-id="d5c97-142">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點，其中包含可對 Siebel 系統的各種作業。</span><span class="sxs-lookup"><span data-stu-id="d5c97-142">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on the Siebel system.</span></span> <span data-ttu-id="d5c97-143">例如，**商務物件**節點包含所有的商務物件和可叫用 Siebel 系統的商務元件。</span><span class="sxs-lookup"><span data-stu-id="d5c97-143">For example, the **Business Objects** node contains all the business objects and business components that can be invoked on the Siebel system.</span></span> <span data-ttu-id="d5c97-144">同樣地，**商務服務**節點包含在您連接至 Siebel 系統的所有商務服務。</span><span class="sxs-lookup"><span data-stu-id="d5c97-144">Similarly, the **Business Services**  node contains all the business services in the Siebel system you connected to.</span></span> <span data-ttu-id="d5c97-145">如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c97-145">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>