---
title: 連接至 Siebel 系統在 Visual Studio 中使用新增配接器服務參考外掛程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d27121be-6407-4bb6-acb5-37dc8a3785c0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdf3ea907ba5905965188d17b3a7493788ef123e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991343"
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="8904d-102">連接至 Siebel 系統在 Visual Studio 中使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="8904d-102">Connect to the Siebel System in Visual Studio Using Add Adapter Service Reference Plug-in</span></span>
<span data-ttu-id="8904d-103">若要連接到 Siebel 系統，使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在.NET 程式設計解決方案中，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8904d-103">To connect to a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in a .NET programming solution, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="8904d-104">本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8904d-104">This topic provides instructions on how to use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="8904d-105">連接至 Siebel 系統，請使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="8904d-105">Connecting to a Siebel System Using Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="8904d-106">執行下列步驟來連接到 Siebel 系統使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8904d-106">Perform the following steps to connect to a Siebel system using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
#### <a name="to-connect-to-a-siebel-system"></a><span data-ttu-id="8904d-107">若要連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="8904d-107">To connect to a Siebel system</span></span>  
  
1. <span data-ttu-id="8904d-108">若要使用連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="8904d-108">To connect using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] in a BizTalk solution:</span></span>  
  
   1. <span data-ttu-id="8904d-109">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8904d-109">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
   2. <span data-ttu-id="8904d-110">以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。</span><span class="sxs-lookup"><span data-stu-id="8904d-110">Right-click the project in Solution Explorer, and then click **Add Adapter Service Reference**.</span></span> <span data-ttu-id="8904d-111">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="8904d-111">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] opens.</span></span>  
  
2. <span data-ttu-id="8904d-112">從**選取的繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8904d-112">From the **Select a binding** drop-down list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
3. <span data-ttu-id="8904d-113">中**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**.</span><span class="sxs-lookup"><span data-stu-id="8904d-113">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username**.</span></span>  
  
4. <span data-ttu-id="8904d-114">指定的使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="8904d-114">Specify the user name and password to connect to the Siebel system.</span></span>  
  
5. <span data-ttu-id="8904d-115">按一下  **URI 屬性**索引標籤，然後指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="8904d-115">Click the **URI Properties** tab, and specify values for the connection parameters.</span></span> <span data-ttu-id="8904d-116">如需有關連線 URI 的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="8904d-116">For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8904d-117">如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="8904d-117">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="8904d-118">不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="8904d-118">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
6. <span data-ttu-id="8904d-119">按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="8904d-119">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="8904d-120">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8904d-120">For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
7. <span data-ttu-id="8904d-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8904d-121">Click **OK**.</span></span>  
  
8. <span data-ttu-id="8904d-122">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="8904d-122">Click **Connect**.</span></span> <span data-ttu-id="8904d-123">一旦建立連線之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="8904d-123">Once the connection is established, the connection status is shown as **Connected**.</span></span>  
  
    <span data-ttu-id="8904d-124">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。</span><span class="sxs-lookup"><span data-stu-id="8904d-124">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="8904d-125">圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8904d-125">The graphical user interface is same for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    <span data-ttu-id="8904d-126">![使用配接器服務 對話方塊已連線](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span><span class="sxs-lookup"><span data-stu-id="8904d-126">![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")</span></span>  
  
    <span data-ttu-id="8904d-127">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]顯示不同的節點，其中包含可對 Siebel 系統的各種作業。</span><span class="sxs-lookup"><span data-stu-id="8904d-127">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] displays different nodes containing various operations that can be performed on the Siebel system.</span></span> <span data-ttu-id="8904d-128">例如，**商務物件**節點包含所有的商務物件和可叫用 Siebel 系統的商務元件。</span><span class="sxs-lookup"><span data-stu-id="8904d-128">For example, the **Business Objects** node contains all the business objects and business components that can be invoked on the Siebel system.</span></span> <span data-ttu-id="8904d-129">同樣地，**商務服務**節點包含在您連接至 Siebel 系統的所有商務服務。</span><span class="sxs-lookup"><span data-stu-id="8904d-129">Similarly, the **Business Services**  node contains all the business services in the Siebel system you connected to.</span></span> <span data-ttu-id="8904d-130">如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。</span><span class="sxs-lookup"><span data-stu-id="8904d-130">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>