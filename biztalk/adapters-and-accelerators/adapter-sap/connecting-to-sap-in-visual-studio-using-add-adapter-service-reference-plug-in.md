---
title: "在 Visual Studio 中使用連接至 SAP 新增配接器服務參考外掛程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05116c2f-08a4-495b-a031-d377e7ca33e0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19dd824322906bdd148b96eb305e88fc35847947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connecting-to-sap-in-visual-studio-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="e77ca-102">在 Visual Studio 中使用連接至 SAP 新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="e77ca-102">Connecting to SAP in Visual Studio Using Add Adapter Service Reference Plug-in</span></span>
<span data-ttu-id="e77ca-103">若要連接到 SAP 系統使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e77ca-103">To connect to an SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in a .NET programming solution, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="e77ca-104">本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e77ca-104">This topic provides instructions on how to use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="connecting-to-an-sap-system-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="e77ca-105">連接到 SAP 系統使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="e77ca-105">Connecting to an SAP System Using Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="e77ca-106">執行下列步驟來連接 SAP 系統使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e77ca-106">Perform the following steps to connect to an SAP system using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
#### <a name="to-connect-to-an-sap-system"></a><span data-ttu-id="e77ca-107">若要連接至 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="e77ca-107">To connect to an SAP system</span></span>  
  
1.  <span data-ttu-id="e77ca-108">若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="e77ca-108">To connect using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="e77ca-109">建立的專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e77ca-109">Create a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="e77ca-110">以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-110">Right-click the project in Solution Explorer, and then click **Add Adapter Service Reference**.</span></span> <span data-ttu-id="e77ca-111">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e77ca-111">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] opens.</span></span>  
  
2.  <span data-ttu-id="e77ca-112">從**選取繫結**下拉式清單中選取**sapBinding**按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-112">From the **Select a binding** drop-down list, select **sapBinding** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="e77ca-113">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="e77ca-113">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e77ca-114">如果您使用 SAP 安全網路連線 (SNC) 程式庫連接到 SAP 系統，請勿指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="e77ca-114">If you are using the SAP Secure Network Connection (SNC) library to connect to an SAP system, do not specify a username and password.</span></span>  
  
4.  <span data-ttu-id="e77ca-115">按一下**URI 屬性**索引標籤上，指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="e77ca-115">Click the **URI Properties** tab and specify values for the connection parameters.</span></span> <span data-ttu-id="e77ca-116">如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="e77ca-116">For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e77ca-117">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**UseSnc**連接屬性設**True**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-117">If you are using the SAP SNC library to connect to an SAP system, set the **UseSnc** connection property to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e77ca-118">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="e77ca-118">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="e77ca-119">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="e77ca-119">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
5.  <span data-ttu-id="e77ca-120">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="e77ca-120">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="e77ca-121">例如，如果您要當做目標 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。</span><span class="sxs-lookup"><span data-stu-id="e77ca-121">For example, if you want to target a ReceiveIdoc operation you must set the **ReceiveIdocFormat** binding property to String.</span></span> <span data-ttu-id="e77ca-122">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e77ca-122">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e77ca-123">如果您使用 SAP SNC 程式庫連接到 SAP 系統，設定**SncLibrary**和**SncPartnerName**至適當的值。</span><span class="sxs-lookup"><span data-stu-id="e77ca-123">If you are using the SAP SNC library to connect to an SAP system, set the **SncLibrary** and **SncPartnerName** to appropriate values.</span></span>  
    >   
    >  <span data-ttu-id="e77ca-124">**SncLibrary**繫結屬性會使用路徑和檔名使用 SNC 連接到 SAP 系統所需的 dll。</span><span class="sxs-lookup"><span data-stu-id="e77ca-124">The **SncLibrary** binding property takes the path and the filename of the DLLs required for using SNC to connect to an SAP system.</span></span> <span data-ttu-id="e77ca-125">這些 Dll 必須要有與 SAP 用戶端電腦上和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="e77ca-125">These DLLs must be present on the computer with the SAP client and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installed.</span></span> <span data-ttu-id="e77ca-126">如需詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南位於\<安裝指南 >: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="e77ca-126">For more information see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide available at \<installation guide>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
    >   
    >  <span data-ttu-id="e77ca-127">**SncPartnerName**繫結屬性會採用 SNC 通訊夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="e77ca-127">The **SncPartnerName** binding property takes the SNC name of the communication partner.</span></span>  
  
6.  <span data-ttu-id="e77ca-128">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-128">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="e77ca-129">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-129">Click **Connect**.</span></span> <span data-ttu-id="e77ca-130">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="e77ca-130">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="e77ca-131">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="e77ca-131">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="e77ca-132">圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e77ca-132">The graphical user interface is same for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
     <span data-ttu-id="e77ca-133">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span><span class="sxs-lookup"><span data-stu-id="e77ca-133">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")</span></span>  
  
     <span data-ttu-id="e77ca-134">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]會顯示包含各種不同成品可以叫用 SAP 系統中的不同節點。</span><span class="sxs-lookup"><span data-stu-id="e77ca-134">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] displays different nodes containing various artifacts that can be invoked in an SAP system.</span></span> <span data-ttu-id="e77ca-135">例如， **RFC**節點包含所有您連接到 SAP 系統所提供的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="e77ca-135">For example, the **RFC** node contains all the RFCs available in the SAP system you connected to.</span></span> <span data-ttu-id="e77ca-136">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="e77ca-136">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77ca-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e77ca-137">See Also</span></span>  
 [<span data-ttu-id="e77ca-138">連接到 Visual Studio 中的 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="e77ca-138">Connect to the SAP System in Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)