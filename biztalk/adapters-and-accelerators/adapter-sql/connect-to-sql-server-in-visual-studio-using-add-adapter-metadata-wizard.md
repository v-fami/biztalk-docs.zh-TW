---
title: "連接到 SQL Server 中使用 Visual Studio 新增配接器中繼資料精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2169722d-beba-4d96-a54b-54986ece9bf8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ffe323321db217fdc81b288cee9029161841fa1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-in-visual-studio-using-add-adapter-metadata-wizard"></a><span data-ttu-id="7ce17-102">連接到 SQL Server 中使用 Visual Studio 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="7ce17-102">Connect to SQL Server in Visual Studio Using Add Adapter Metadata Wizard</span></span>
<span data-ttu-id="7ce17-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也會公開成 BizTalk 配接器，因此，您可以使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述您想要使用配接器的 SQL Server 上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="7ce17-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is also exposed as a BizTalk adapter and, therefore, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on SQL Server using the adapter.</span></span>  
  
## <a name="connecting-to-sql-server-using-add-adapter-metadata-wizard"></a><span data-ttu-id="7ce17-104">連接到 SQL Server 使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="7ce17-104">Connecting to SQL Server Using Add Adapter Metadata Wizard</span></span>  
 <span data-ttu-id="7ce17-105">執行下列步驟來連接 SQL Server 使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7ce17-105">Perform the following steps to connect to SQL Server using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-connect-to-sql-server"></a><span data-ttu-id="7ce17-106">若要連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ce17-106">To connect to SQL Server</span></span>  
  
1.  <span data-ttu-id="7ce17-107">若要使用連接[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]BizTalk 解決方案中：</span><span class="sxs-lookup"><span data-stu-id="7ce17-107">To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:</span></span>  
  
    1.  <span data-ttu-id="7ce17-108">建立 BizTalk 專案，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7ce17-108">Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="7ce17-109">以滑鼠右鍵按一下方案總管] 中的專案名稱，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-109">Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
    3.  <span data-ttu-id="7ce17-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7ce17-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="7ce17-111">使用</span><span class="sxs-lookup"><span data-stu-id="7ce17-111">Use this</span></span>|<span data-ttu-id="7ce17-112">動作</span><span class="sxs-lookup"><span data-stu-id="7ce17-112">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="7ce17-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="7ce17-113">**Categories**</span></span>|<span data-ttu-id="7ce17-114">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-114">Click **Add Adapter**.</span></span>|  
        |<span data-ttu-id="7ce17-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="7ce17-115">**Templates**</span></span>|<span data-ttu-id="7ce17-116">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-116">Click **Add Adapter Metadata**.</span></span>|  
  
    4.  <span data-ttu-id="7ce17-117">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-117">Click **Add**.</span></span> <span data-ttu-id="7ce17-118">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7ce17-118">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
    5.  <span data-ttu-id="7ce17-119">在 新增配接器精靈 中，選取  **WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-119">In the Add Adapter Wizard, select **WCF-SQL**.</span></span> <span data-ttu-id="7ce17-120">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ce17-120">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="7ce17-121">如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="7ce17-121">If you already have a WCF-SQL port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
    6.  <span data-ttu-id="7ce17-122">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-122">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="7ce17-123">從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-123">From the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
3.  <span data-ttu-id="7ce17-124">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7ce17-124">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential  type** drop-down list, do one of the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ce17-125">如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce17-125">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="7ce17-126">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="7ce17-126">Click this</span></span>|<span data-ttu-id="7ce17-127">動作</span><span class="sxs-lookup"><span data-stu-id="7ce17-127">To do this</span></span>|  
    |----------------|----------------|  
    |<span data-ttu-id="7ce17-128">**無**</span><span class="sxs-lookup"><span data-stu-id="7ce17-128">**None**</span></span>|<span data-ttu-id="7ce17-129">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="7ce17-129">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="7ce17-130">**視窗**</span><span class="sxs-lookup"><span data-stu-id="7ce17-130">**Windows**</span></span>|<span data-ttu-id="7ce17-131">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="7ce17-131">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="7ce17-132">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="7ce17-132">**Username**</span></span>|<span data-ttu-id="7ce17-133">指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。</span><span class="sxs-lookup"><span data-stu-id="7ce17-133">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="7ce17-134">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7ce17-134">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="7ce17-135">**注意：**如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="7ce17-135">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span>|  
  
4.  <span data-ttu-id="7ce17-136">按一下**URI 屬性**索引標籤，然後再指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="7ce17-136">Click the **URI Properties** tab, and then specify values for the connection parameters.</span></span> <span data-ttu-id="7ce17-137">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce17-137">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ce17-138">如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="7ce17-138">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="7ce17-139">不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="7ce17-139">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ce17-140">如果您在 [URI 屬性] 索引標籤中未指定任何值[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將做為 URI `mssql://.//`。</span><span class="sxs-lookup"><span data-stu-id="7ce17-140">If you do not specify any values in the URI property tab, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] puts the URI as `mssql://.//`.</span></span> <span data-ttu-id="7ce17-141">在這種情況下，配接器連接到預設的資料庫和本機電腦上的預設資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ce17-141">In such a case, the adapter connects to the default database and the default database instance on the local computer.</span></span>  
  
5.  <span data-ttu-id="7ce17-142">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="7ce17-142">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="7ce17-143">如需有關繫結內容，請參閱 <<c0> [ 閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce17-143">For more information about binding properties see, [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ce17-144">如果產生的中繼資料使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]且您選取現有的 WCF SQL 傳送埠，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="7ce17-144">If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-SQL send port, you need not specify the binding properties.</span></span> <span data-ttu-id="7ce17-145">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="7ce17-145">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="7ce17-146">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="7ce17-146">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="7ce17-147">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7ce17-147">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="7ce17-148">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="7ce17-148">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
6.  <span data-ttu-id="7ce17-149">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-149">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="7ce17-150">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-150">Click **Connect**.</span></span> <span data-ttu-id="7ce17-151">建立連接之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="7ce17-151">After the connection is established, the connection status is shown as **Connected**.</span></span>  
  
     <span data-ttu-id="7ce17-152">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。</span><span class="sxs-lookup"><span data-stu-id="7ce17-152">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="7ce17-153">圖形化使用者介面是相同的[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7ce17-153">The graphical user interface is same for the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
     <span data-ttu-id="7ce17-154">![連接到 SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")</span><span class="sxs-lookup"><span data-stu-id="7ce17-154">![Connect to SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")</span></span>  
  
     <span data-ttu-id="7ce17-155">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示不同的節點，包含可在 SQL Server 上執行各種作業。</span><span class="sxs-lookup"><span data-stu-id="7ce17-155">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on SQL Server.</span></span> <span data-ttu-id="7ce17-156">例如，**程序**節點包含所有可供您所連接之資料庫的程序。</span><span class="sxs-lookup"><span data-stu-id="7ce17-156">For example, the **Procedures** node contains all the procedures available for the database you connected to.</span></span> <span data-ttu-id="7ce17-157">同樣地，**資料表**節點包含您連接的資料庫，並可以在資料表執行的作業中的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="7ce17-157">Similarly, the **Tables** node contains all the tables in the database you connected to, and the operations that can be performed on a table.</span></span> <span data-ttu-id="7ce17-158">如需有關這些節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce17-158">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce17-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ce17-159">See Also</span></span>  
 [<span data-ttu-id="7ce17-160">連接到 SQL Server 使用配接器服務增益集所使用的 Visual Studio 中</span><span class="sxs-lookup"><span data-stu-id="7ce17-160">Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in</span></span>](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)