---
title: 連接到 SQL Server 在 Visual Studio 使用新增配接器服務參考外掛程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fc3b824-d20b-4531-81f3-89b4a1ff3216
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9998acf89bd036230dceb3a06f950497677490b9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018260"
---
# <a name="connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="862fd-102">連接到 SQL Server 在 Visual Studio 使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="862fd-102">Connect to SQL Server in Visual Studio Using Add Adapter Service Reference Plug-in</span></span>
<span data-ttu-id="862fd-103">若要使用 SQL Server 驗證連接[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在.NET 程式設計解決方案中，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="862fd-103">To connect to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET programming solution, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="862fd-104">本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="862fd-104">This topic provides instructions on how to use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

## <a name="connecting-to-sql-server-using-add-adapter-service-reference-plug-in"></a><span data-ttu-id="862fd-105">連接到 SQL Server 使用新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="862fd-105">Connecting to SQL Server Using Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="862fd-106">執行下列步驟來連接 SQL Server 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="862fd-106">Perform the following steps to connect to SQL Server using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

#### <a name="to-connect-to-sql-server"></a><span data-ttu-id="862fd-107">若要連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="862fd-107">To connect to SQL Server</span></span>  

1. <span data-ttu-id="862fd-108">若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]程式設計方案中：</span><span class="sxs-lookup"><span data-stu-id="862fd-108">To connect using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] in a programming solution:</span></span>  

   1. <span data-ttu-id="862fd-109">建立的專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="862fd-109">Create a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  

   2. <span data-ttu-id="862fd-110">以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。</span><span class="sxs-lookup"><span data-stu-id="862fd-110">Right-click the project in Solution Explorer, and then click **Add Adapter Service Reference**.</span></span> <span data-ttu-id="862fd-111">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="862fd-111">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] opens.</span></span>  

2. <span data-ttu-id="862fd-112">從**選取的繫結**下拉式清單中，選取**sqlBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="862fd-112">From the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.</span></span>  

3. <span data-ttu-id="862fd-113">在**設定介面卡** 對話方塊中，按一下**安全性**索引標籤上，以及從**用戶端認證類型**下拉式清單，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="862fd-113">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential  type** drop-down list, do one of the following:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="862fd-114">如果您要連接到 SQL Server 使用 Windows 驗證，Windows 您登入，必須將的使用者加入至 SQL Server 中所述[連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="862fd-114">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  

   |  <span data-ttu-id="862fd-115">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="862fd-115">Click this</span></span>  |                                                                                                                                                               <span data-ttu-id="862fd-116">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="862fd-116">To do this</span></span>                                                                                                                                                               |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   <span data-ttu-id="862fd-117">**無**</span><span class="sxs-lookup"><span data-stu-id="862fd-117">**None**</span></span>   |                                                                                                                                         <span data-ttu-id="862fd-118">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="862fd-118">Connect to SQL Server by using Windows authentication.</span></span>                                                                                                                                         |
   | <span data-ttu-id="862fd-119">**視窗**</span><span class="sxs-lookup"><span data-stu-id="862fd-119">**Windows**</span></span>  |                                                                                                                                         <span data-ttu-id="862fd-120">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="862fd-120">Connect to SQL Server by using Windows authentication.</span></span>                                                                                                                                         |
   | <span data-ttu-id="862fd-121">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="862fd-121">**Username**</span></span> | <span data-ttu-id="862fd-122">指定的使用者名稱和密碼來連接到 SQL Server，藉由指定 SQL Server 資料庫中定義的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="862fd-122">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="862fd-123">請注意，使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="862fd-123">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="862fd-124">**注意：** 如果您離開**使用者名稱**並**密碼**空白欄位，配接器連接至使用 Windows 驗證的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="862fd-124">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span> |


4. <span data-ttu-id="862fd-125">按一下  **URI 屬性**索引標籤，然後指定 連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="862fd-125">Click the **URI Properties** tab, and then specify values for the connection parameters.</span></span> <span data-ttu-id="862fd-126">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="862fd-126">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="862fd-127">如果連接參數可以包含任何保留的字元，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="862fd-127">If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="862fd-128">不過，如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="862fd-128">However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="862fd-129">如果您在 [URI 屬性] 索引標籤中未指定任何值[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將做為 URI `mssql://.//`。</span><span class="sxs-lookup"><span data-stu-id="862fd-129">If you do not specify any values in the URI property tab, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] puts the URI as `mssql://.//`.</span></span> <span data-ttu-id="862fd-130">在這種情況下，配接器會連接到預設的資料庫和本機電腦上的預設資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="862fd-130">In such a case, the adapter connects to the default database and the default database instance on the local computer.</span></span>  

5. <span data-ttu-id="862fd-131">按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="862fd-131">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span>  

6. <span data-ttu-id="862fd-132">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="862fd-132">Click **OK**.</span></span>  

7. <span data-ttu-id="862fd-133">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="862fd-133">Click **Connect**.</span></span> <span data-ttu-id="862fd-134">建立連線之後，連線狀態會顯示為**Connected**。</span><span class="sxs-lookup"><span data-stu-id="862fd-134">After the connection is established, the connection status is shown as **Connected**.</span></span>  

    <span data-ttu-id="862fd-135">下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]立即建立連線之後。</span><span class="sxs-lookup"><span data-stu-id="862fd-135">The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.</span></span> <span data-ttu-id="862fd-136">圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="862fd-136">The graphical user interface is same for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

    <span data-ttu-id="862fd-137">![連接到 SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")</span><span class="sxs-lookup"><span data-stu-id="862fd-137">![Connect to SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")</span></span>  

    <span data-ttu-id="862fd-138">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]顯示不同的節點，其中包含可以在 SQL Server 執行的各種作業。</span><span class="sxs-lookup"><span data-stu-id="862fd-138">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] displays different nodes containing various operations that can be performed on SQL Server.</span></span> <span data-ttu-id="862fd-139">例如，**程序**節點包含所有可供您連接之資料庫的程序。</span><span class="sxs-lookup"><span data-stu-id="862fd-139">For example, the **Procedures** node contains all the procedures available for the database you connected to.</span></span> <span data-ttu-id="862fd-140">同樣地，**資料表**節點包含您連接的資料庫，以及可以在資料表執行的作業中的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="862fd-140">Similarly, the **Tables** node contains all the tables in the database you connected to, and the operations that can be performed on a table.</span></span> <span data-ttu-id="862fd-141">如需有關這些節點的詳細資訊，請參閱 <<c0> [ 中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。</span><span class="sxs-lookup"><span data-stu-id="862fd-141">For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="862fd-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="862fd-142">See Also</span></span>  
 [<span data-ttu-id="862fd-143">連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="862fd-143">Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in</span></span>](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)