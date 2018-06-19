---
title: 設定 SQL 配接器的連線 URI |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6460b22-48e4-4b7e-b82e-151e7dab1e09
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9959a88f9799730cb60d2b05358f226b31d0f84c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226790"
---
# <a name="configure-the-connection-uri-for-the-sql-adapter"></a><span data-ttu-id="0bfad-102">設定 SQL 配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="0bfad-102">Configure the connection URI for the SQL adapter</span></span>
<span data-ttu-id="0bfad-103">連接字串，其中包含參數，才能連接到 SQL Server 連接 URI。</span><span class="sxs-lookup"><span data-stu-id="0bfad-103">A connection URI is a connection string that contains parameters required to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-104">同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要連接到 SQL Server 產生的中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="0bfad-104">While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the URI to connect to SQL Server to generate the metadata.</span></span> <span data-ttu-id="0bfad-105">而設定的傳送或接收埠使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定要連接到 SQL Server 以執行作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="0bfad-105">While configuring a send or receive port using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the URI to connect to SQL Server to perform operations.</span></span>  
  
## <a name="enter-the-connection-uri-from-visual-studio"></a><span data-ttu-id="0bfad-106">從 Visual Studio 輸入連線 URI</span><span class="sxs-lookup"><span data-stu-id="0bfad-106">Enter the connection URI from Visual Studio</span></span>  
 <span data-ttu-id="0bfad-107">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以指定連線 URI 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0bfad-107">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="use-the-consume-adapter-service-add-in"></a><span data-ttu-id="0bfad-108">使用使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="0bfad-108">Use the Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="0bfad-109">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-109">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="0bfad-110">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0bfad-110">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="0bfad-111">使用</span><span class="sxs-lookup"><span data-stu-id="0bfad-111">Use this</span></span>|<span data-ttu-id="0bfad-112">動作</span><span class="sxs-lookup"><span data-stu-id="0bfad-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0bfad-113">**類別**</span><span class="sxs-lookup"><span data-stu-id="0bfad-113">**Categories**</span></span>|<span data-ttu-id="0bfad-114">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-114">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="0bfad-115">**範本**</span><span class="sxs-lookup"><span data-stu-id="0bfad-115">**Templates**</span></span>|<span data-ttu-id="0bfad-116">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-116">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="0bfad-117">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-117">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="0bfad-118">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sqlBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-118">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="0bfad-119">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤。從**用戶端認證類型**清單中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-119">In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** list, do one of the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-120">如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-120">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="0bfad-121">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="0bfad-121">Click this</span></span>|<span data-ttu-id="0bfad-122">動作</span><span class="sxs-lookup"><span data-stu-id="0bfad-122">To do this</span></span>|  
    |----------------|----------------|  
    |<span data-ttu-id="0bfad-123">**無**</span><span class="sxs-lookup"><span data-stu-id="0bfad-123">**None**</span></span>|<span data-ttu-id="0bfad-124">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-124">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="0bfad-125">**視窗**</span><span class="sxs-lookup"><span data-stu-id="0bfad-125">**Windows**</span></span>|<span data-ttu-id="0bfad-126">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-126">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="0bfad-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0bfad-127">**Username**</span></span>|<span data-ttu-id="0bfad-128">指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。</span><span class="sxs-lookup"><span data-stu-id="0bfad-128">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="0bfad-129">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-129">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="0bfad-130">**注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="0bfad-130">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span>|  
  
6.  <span data-ttu-id="0bfad-131">按一下**URI 屬性**索引標籤，然後指定不同參數的值。</span><span class="sxs-lookup"><span data-stu-id="0bfad-131">Click the **URI Properties** tab, and specify values for different parameters.</span></span> <span data-ttu-id="0bfad-132">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-132">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
7.  <span data-ttu-id="0bfad-133">按一下**繫結屬性**索引標籤，然後指定的繫結屬性值，如果有的話，才會產生結構描述所需的。</span><span class="sxs-lookup"><span data-stu-id="0bfad-133">Click the **Binding Properties** tab, and specify values for the binding properties, if any, which are required before generating the schema.</span></span> <span data-ttu-id="0bfad-134">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-134">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
8.  <span data-ttu-id="0bfad-135">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-135">Click **OK**.</span></span>  
  
### <a name="use-the-add-adapter-metadata-wizard"></a><span data-ttu-id="0bfad-136">使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="0bfad-136">Use the Add Adapter Metadata wizard</span></span>  
  
1.  <span data-ttu-id="0bfad-137">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-137">Right-click the BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="0bfad-138">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0bfad-138">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="0bfad-139">使用</span><span class="sxs-lookup"><span data-stu-id="0bfad-139">Use this</span></span>|<span data-ttu-id="0bfad-140">動作</span><span class="sxs-lookup"><span data-stu-id="0bfad-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0bfad-141">**類別**</span><span class="sxs-lookup"><span data-stu-id="0bfad-141">**Categories**</span></span>|<span data-ttu-id="0bfad-142">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-142">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="0bfad-143">**範本**</span><span class="sxs-lookup"><span data-stu-id="0bfad-143">**Templates**</span></span>|<span data-ttu-id="0bfad-144">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-144">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="0bfad-145">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-145">Click **Add**.</span></span> <span data-ttu-id="0bfad-146">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0bfad-146">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="0bfad-147">在 新增配接器精靈 中，選取  **WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-147">In the Add Adapter Wizard, select **WCF-SQL**.</span></span> <span data-ttu-id="0bfad-148">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bfad-148">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0bfad-149">如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="0bfad-149">If you already have a WCF-SQL port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="0bfad-150">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-150">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0bfad-151">在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="0bfad-151">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="0bfad-152">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-152">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential  type** drop-down list box, do one of the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-153">如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-153">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="0bfad-154">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="0bfad-154">Click this</span></span>|<span data-ttu-id="0bfad-155">動作</span><span class="sxs-lookup"><span data-stu-id="0bfad-155">To do this</span></span>|  
    |----------------|----------------|  
    |<span data-ttu-id="0bfad-156">**無**</span><span class="sxs-lookup"><span data-stu-id="0bfad-156">**None**</span></span>|<span data-ttu-id="0bfad-157">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-157">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="0bfad-158">**視窗**</span><span class="sxs-lookup"><span data-stu-id="0bfad-158">**Windows**</span></span>|<span data-ttu-id="0bfad-159">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-159">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="0bfad-160">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0bfad-160">**Username**</span></span>|<span data-ttu-id="0bfad-161">指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。</span><span class="sxs-lookup"><span data-stu-id="0bfad-161">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="0bfad-162">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-162">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="0bfad-163">**注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="0bfad-163">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span>|  
  
8.  <span data-ttu-id="0bfad-164">按一下**URI 屬性**索引標籤，然後再指定連線參數的值。</span><span class="sxs-lookup"><span data-stu-id="0bfad-164">Click the **URI Properties** tab, and then specify values for the connection parameters.</span></span> <span data-ttu-id="0bfad-165">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-165">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
9. <span data-ttu-id="0bfad-166">按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。</span><span class="sxs-lookup"><span data-stu-id="0bfad-166">Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target.</span></span> <span data-ttu-id="0bfad-167">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-167">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-168">如果您選取現有的 WCF SQL 傳送埠時，您不需要指定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="0bfad-168">If you selected an existing WCF-SQL send port, you need not specify the binding properties.</span></span> <span data-ttu-id="0bfad-169">繫結屬性是從傳送埠組態中挑選。</span><span class="sxs-lookup"><span data-stu-id="0bfad-169">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="0bfad-170">不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="0bfad-170">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="0bfad-171">在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0bfad-171">In such case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="0bfad-172">不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。</span><span class="sxs-lookup"><span data-stu-id="0bfad-172">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
10. <span data-ttu-id="0bfad-173">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-173">Click **OK**.</span></span>  
  
## <a name="enter-the-connection-uri-from-the-biztalk-server-administration-console"></a><span data-ttu-id="0bfad-174">從 BizTalk Server 管理主控台中輸入連線 URI</span><span class="sxs-lookup"><span data-stu-id="0bfad-174">Enter the connection URI from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="0bfad-175">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定連線 URI Wcf-custom 或 WCF SQL 連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="0bfad-175">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the connection URI as part of the WCF-Custom or a WCF-SQL port configuration.</span></span>  
  
### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a><span data-ttu-id="0bfad-176">輸入 WCF 自訂連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="0bfad-176">Enter the connection URI for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="0bfad-177">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0bfad-177">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="0bfad-178">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-178">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="0bfad-179">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0bfad-179">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="0bfad-180">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-180">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-181">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-181">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="0bfad-182">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0bfad-182">In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="0bfad-183">在**位址 (URI)** 文字方塊中，指定連接到 SQL Server 連接 URI。</span><span class="sxs-lookup"><span data-stu-id="0bfad-183">In the **Address (URI)** text box, specify the connection URI to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-184">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-184">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
6.  <span data-ttu-id="0bfad-185">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。從**繫結的型別**下拉式清單中，選取**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-185">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **sqlBinding**.</span></span>  
  
7.  <span data-ttu-id="0bfad-186">如果您要建立傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-186">If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="0bfad-187">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-187">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-188">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-188">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0bfad-189">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0bfad-189">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="0bfad-190">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-190">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="0bfad-191">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfad-191">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
8.  <span data-ttu-id="0bfad-192">如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-192">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="0bfad-193">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-193">Select **User account** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-194">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-194">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0bfad-195">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0bfad-195">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="0bfad-196">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-196">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="0bfad-197">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfad-197">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
9. <span data-ttu-id="0bfad-198">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-198">Click **OK**.</span></span>  
  
### <a name="enter-the-connection-uri-for-the-wcf-sql-port"></a><span data-ttu-id="0bfad-199">輸入 WCF SQL 連接埠的連線 URI</span><span class="sxs-lookup"><span data-stu-id="0bfad-199">Enter the connection URI for the WCF-SQL port</span></span>  
  
1.  <span data-ttu-id="0bfad-200">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0bfad-200">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="0bfad-201">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0bfad-201">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0bfad-202">如需指示，請參閱[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-202">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="0bfad-203">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-203">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="0bfad-204">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0bfad-204">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="0bfad-205">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-205">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-206">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-206">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="0bfad-207">在 傳輸屬性對話方塊中，按一下 **一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0bfad-207">In the transport properties dialog box, click the **General** tab.</span></span>  
  
6.  <span data-ttu-id="0bfad-208">按一下**設定**按鈕，並提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="0bfad-208">Click the **Configure** button and provide values for the connection parameters.</span></span> <span data-ttu-id="0bfad-209">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-209">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
7.  <span data-ttu-id="0bfad-210">在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0bfad-210">In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bfad-211">根據您要設定傳送埠或接收埠會繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="0bfad-211">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="0bfad-212">例如，通知相關的繫結屬性沒有可用時設定的傳送埠，因為通知為輸入的作業，需要接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="0bfad-212">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
8.  <span data-ttu-id="0bfad-213">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-213">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="0bfad-214">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-214">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-215">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-215">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0bfad-216">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0bfad-216">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="0bfad-217">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-217">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="0bfad-218">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfad-218">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
9. <span data-ttu-id="0bfad-219">如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0bfad-219">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="0bfad-220">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0bfad-220">Select **User account** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="0bfad-221">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bfad-221">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0bfad-222">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0bfad-222">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="0bfad-223">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfad-223">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="0bfad-224">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfad-224">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
10. <span data-ttu-id="0bfad-225">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0bfad-225">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfad-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bfad-226">See Also</span></span>  
[<span data-ttu-id="0bfad-227">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="0bfad-227">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)