---
title: "連接至 Siebel 系統在 Visual Studio 使用新增配接器服務參考外掛程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d27121be-6407-4bb6-acb5-37dc8a3785c0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 696e91d689bfc7bc058ce0c512e8fa09b91b18a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="4d501-102">連接至 Siebel 系統在 Visual Studio 使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="4d501-102">Connect to the Siebel System in Visual Studio Using Add Adapter Service Reference Plug-in</span></span>
<span data-ttu-id="4d501-103">若要連接至 Siebel 系統使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d501-103">To connect to a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in a .NET programming solution, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="4d501-104">本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d501-104">This topic provides instructions on how to use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="4d501-105">連接到使用 Siebel 系統新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="4d501-105">Connecting to a Siebel System Using Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="4d501-106">執行下列步驟來連接使用 Siebel 系統[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d501-106">Perform the following steps to connect to a Siebel system using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
#### <a name="to-connect-to-a-siebel-system"></a><span data-ttu-id="4d501-107">連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="4d501-107">To connect to a Siebel system</span></span>  
  
1.  <span data-ttu-id="4d501-108">若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="4d501-108">To connect using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="4d501-109">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d501-109">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="4d501-110">以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。</span><span class="sxs-lookup"><span data-stu-id="4d501-110">Right-click the project in Solution Explorer, and then click **Add Adapter Service Reference**.</span></span> <span data-ttu-id="4d501-111">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4d501-111">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] opens.</span></span>  
  
2.  <span data-ttu-id="4d501-112">從**選取繫結**下拉式清單中選取**siebelBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="4d501-112">From the **Select a binding** drop-down list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
3.  <span data-ttu-id="4d501-113">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.</span><span class="sxs-lookup"><span data-stu-id="4d501-113">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username**.</span></span>  
  
4.  <span data-ttu-id="4d501-114">指定的使用者名稱和密碼，以連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="4d501-114">Specify the user name and password to connect to the Siebel system.</span></span>  
  
5.  <span data-ttu-id="4d501-115">按一下**URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="4d501-115">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="4d501-116">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="4d501-116">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d501-117">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="4d501-117">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="4d501-118">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="4d501-118">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
6.  <span data-ttu-id="4d501-119">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="4d501-119">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="4d501-120">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4d501-120">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
7.  <span data-ttu-id="4d501-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4d501-121">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="4d501-122">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="4d501-122">Click **Connect**.</span></span> <span data-ttu-id="4d501-123">一旦建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="4d501-123">Once the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="4d501-124">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="4d501-124">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="4d501-125">圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d501-125">The graphical user interface is same for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
     <span data-ttu-id="4d501-126">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span><span class="sxs-lookup"><span data-stu-id="4d501-126">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span></span>  
  
     <span data-ttu-id="4d501-127">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]顯示不同的節點包含各種可以 Siebel 系統執行的作業。</span><span class="sxs-lookup"><span data-stu-id="4d501-127">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] displays different nodes containing various operations that can be performed on the Siebel system.</span></span> <span data-ttu-id="4d501-128">例如，**商務物件**節點包含所有的商務物件和 Siebel 系統叫用的商務元件。</span><span class="sxs-lookup"><span data-stu-id="4d501-128">For example, the **Business Objects** node contains all the business objects and business components that can be invoked on the Siebel system.</span></span> <span data-ttu-id="4d501-129">同樣地，**商務服務**節點包含您連接至 Siebel 系統中的所有商務服務。</span><span class="sxs-lookup"><span data-stu-id="4d501-129">Similarly, the **Business Services**  node contains all the business services in the Siebel system you connected to.</span></span> <span data-ttu-id="4d501-130">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。</span><span class="sxs-lookup"><span data-stu-id="4d501-130">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>