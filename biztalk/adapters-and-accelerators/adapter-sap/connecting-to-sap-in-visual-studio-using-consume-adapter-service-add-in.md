---
title: "在 Visual Studio 中使用連接至 SAP 使用配接器服務增益集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4f7d57a-fd88-4420-b893-49f42b449597
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb63593beb93555e8bc868a9bb3afdc121252350
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="connecting-to-sap-in-visual-studio-using-consume-adapter-service-add-in"></a><span data-ttu-id="5e5f8-102">在 Visual Studio 中使用連接至 SAP 使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="5e5f8-102">Connecting to SAP in Visual Studio Using Consume Adapter Service Add-in</span></span>
<span data-ttu-id="5e5f8-103">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]安裝 WCF LOB 配接器 SDK 時安裝。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-103">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] is installed when you install WCF LOB Adapter SDK.</span></span> <span data-ttu-id="5e5f8-104">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]載入電腦上安裝的所有 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-104">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] loads all the WCF-Custom bindings installed on the computer.</span></span> <span data-ttu-id="5e5f8-105">若要連接到 SAP 系統使用 WCF 型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在 BizTalk 專案中，您必須使用**sapbinding**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-105">To connect to SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in a BizTalk project, you must use the **sapbinding**.</span></span>  
  
 <span data-ttu-id="5e5f8-106">本主題說明如何使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-106">This topic provides instructions on how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
## <a name="connecting-to-an-sap-system-using-consume-adapter-service-add-in"></a><span data-ttu-id="5e5f8-107">連接到 SAP 系統使用使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="5e5f8-107">Connecting to an SAP System Using Consume Adapter Service Add-in</span></span>  
 <span data-ttu-id="5e5f8-108">執行下列步驟來連接 SAP 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-108">Perform the following steps to connect to an SAP system using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
#### <a name="to-connect-to-an-sap-system"></a><span data-ttu-id="5e5f8-109">若要連接至 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="5e5f8-109">To connect to an SAP system</span></span>  
  
1.  <span data-ttu-id="5e5f8-110">若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="5e5f8-110">To connect using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="5e5f8-111">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-111">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="5e5f8-112">以滑鼠右鍵按一下方案總管] 中的專案名稱，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-112">Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    3.  <span data-ttu-id="5e5f8-113">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5e5f8-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="5e5f8-114">使用</span><span class="sxs-lookup"><span data-stu-id="5e5f8-114">Use this</span></span>|<span data-ttu-id="5e5f8-115">動作</span><span class="sxs-lookup"><span data-stu-id="5e5f8-115">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="5e5f8-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="5e5f8-116">**Categories**</span></span>|<span data-ttu-id="5e5f8-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-117">Click **Consume Adapter Service**.</span></span>|  
        |<span data-ttu-id="5e5f8-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="5e5f8-118">**Templates**</span></span>|<span data-ttu-id="5e5f8-119">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-119">Click **Consume Adapter Service**.</span></span>|  
  
    4.  <span data-ttu-id="5e5f8-120">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-120">Click **Add**.</span></span> <span data-ttu-id="5e5f8-121">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-121">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] opens.</span></span>  
  
2.  <span data-ttu-id="5e5f8-122">從**選取繫結**下拉式清單中選取**sapBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-122">From the **Select a binding** drop-down list, select **sapBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="5e5f8-123">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-123">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5e5f8-124">如果您使用 SAP 安全網路連線 (SNC) 程式庫連接到 SAP 系統，請勿指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-124">If you are using the SAP Secure Network Connection (SNC) library to connect to an SAP system, do not specify a username and password.</span></span>  
  
4.  <span data-ttu-id="5e5f8-125">按一下**URI 屬性**索引標籤上，指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-125">Click the **URI Properties** tab and specify values for the connection parameters.</span></span> <span data-ttu-id="5e5f8-126">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-126">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5e5f8-127">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**UseSnc**連接屬性設**True**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-127">If you are using the SAP SNC library to connect to an SAP system, set the **UseSnc** connection property to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e5f8-128">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-128">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="5e5f8-129">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-129">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
5.  <span data-ttu-id="5e5f8-130">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-130">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="5e5f8-131">例如，如果您要當做目標 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-131">For example, if you want to target a ReceiveIdoc operation you must set the **ReceiveIdocFormat** binding property to String.</span></span> <span data-ttu-id="5e5f8-132">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-132">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5e5f8-133">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**SncLibrary**和**SncPartnerName**至適當的值。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-133">If you are using the SAP SNC library to connect to an SAP system, set the **SncLibrary** and **SncPartnerName** to appropriate values.</span></span>  
    >   
    >  <span data-ttu-id="5e5f8-134">**SncLibrary**繫結屬性會使用路徑和檔名使用 SNC 連接到 SAP 系統所需的 dll。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-134">The **SncLibrary** binding property takes the path and the filename of the DLLs required for using SNC to connect to an SAP system.</span></span> <span data-ttu-id="5e5f8-135">這些 Dll 必須要有與 SAP 用戶端電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-135">These DLLs must be present on the computer with the SAP client and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installed.</span></span> <span data-ttu-id="5e5f8-136">如需詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南位於\<安裝指南\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-136">For more information see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide available at \<installation guide\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
    >   
    >  <span data-ttu-id="5e5f8-137">**SncPartnerName**繫結屬性會採用 SNC 通訊夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-137">The **SncPartnerName** binding property takes the SNC name of the communication partner.</span></span>  
  
6.  <span data-ttu-id="5e5f8-138">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="5e5f8-139">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-139">Click **Connect**.</span></span> <span data-ttu-id="5e5f8-140">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-140">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="5e5f8-141">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-141">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span>  
  
     <span data-ttu-id="5e5f8-142">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span><span class="sxs-lookup"><span data-stu-id="5e5f8-142">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span></span>  
  
     <span data-ttu-id="5e5f8-143">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會顯示包含各種不同成品可以叫用 SAP 系統中的不同節點。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-143">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various artifacts that can be invoked in an SAP system.</span></span> <span data-ttu-id="5e5f8-144">例如， **RFC**節點包含所有您連接到 SAP 系統所提供的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-144">For example, the **RFC** node contains all the RFCs available in the SAP system you connected to.</span></span> <span data-ttu-id="5e5f8-145">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5f8-145">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5f8-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e5f8-146">See Also</span></span>  
 [<span data-ttu-id="5e5f8-147">在 Visual Studio 中連接到 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="5e5f8-147">Connect to the SAP System in Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)