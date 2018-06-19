---
title: 設定登入認證 SQL 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c20e177-0e64-4df3-a3dd-dca3fcf314db
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f07a3840524988e5f643ca89799b7c7f23ff0fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226238"
---
# <a name="configure-the-sign-in-credentials-for-the-sql-adapter"></a><span data-ttu-id="2dcc5-102">設定登入認證 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="2dcc5-102">Configure the sign in credentials for the SQL adapter</span></span>
<span data-ttu-id="2dcc5-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]需要配接器用戶端提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="2dcc5-104">配接器使用這些認證來驗證與 SQL Server 使用者並建立連接。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-104">The adapter uses these credentials to authenticate the user with SQL Server and to establish a connection.</span></span>  
  
 <span data-ttu-id="2dcc5-105">配接器用戶端可以使用時的用戶端認證同時提供[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及何時使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-105">Adapter clients can provide the client credentials both when using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and when using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="2dcc5-106">當使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，產生的中繼資料所需的認證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-106">When using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], credentials are required to generate the metadata.</span></span> <span data-ttu-id="2dcc5-107">當使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，不需要的認證來執行 SQL Server 上的作業。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-107">When using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, credentials are required to perform operations on SQL Server.</span></span>  
  
 <span data-ttu-id="2dcc5-108">本節提供有關指定在用戶端認證的詳細資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-108">This section provides information about specifying client credentials in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="enter-credentials-from-visual-studio"></a><span data-ttu-id="2dcc5-109">從 Visual Studio 中輸入認證</span><span class="sxs-lookup"><span data-stu-id="2dcc5-109">Enter credentials from Visual Studio</span></span>  
 <span data-ttu-id="2dcc5-110">從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-110">From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="using-consume-adapter-service-add-in"></a><span data-ttu-id="2dcc5-111">使用會耗用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="2dcc5-111">Using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="2dcc5-112">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-112">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="2dcc5-113">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2dcc5-114">使用</span><span class="sxs-lookup"><span data-stu-id="2dcc5-114">Use this</span></span>|<span data-ttu-id="2dcc5-115">動作</span><span class="sxs-lookup"><span data-stu-id="2dcc5-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2dcc5-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-116">**Categories**</span></span>|<span data-ttu-id="2dcc5-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="2dcc5-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-118">**Templates**</span></span>|<span data-ttu-id="2dcc5-119">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="2dcc5-120">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="2dcc5-121">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sqlBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="2dcc5-122">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**清單中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-122">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, do one of the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dcc5-123">如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-123">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="2dcc5-124">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="2dcc5-124">Click this</span></span>|<span data-ttu-id="2dcc5-125">動作</span><span class="sxs-lookup"><span data-stu-id="2dcc5-125">To do this</span></span>|  
    |----------------|----------------|  
    |<span data-ttu-id="2dcc5-126">**無**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-126">**None**</span></span>|<span data-ttu-id="2dcc5-127">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-127">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="2dcc5-128">**視窗**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-128">**Windows**</span></span>|<span data-ttu-id="2dcc5-129">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-129">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="2dcc5-130">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-130">**Username**</span></span>|<span data-ttu-id="2dcc5-131">指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-131">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="2dcc5-132">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-132">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="2dcc5-133">**注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-133">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span>|  
  
6.  <span data-ttu-id="2dcc5-134">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-134">Click **OK**.</span></span>  
  
### <a name="using-add-adapter-metadata-wizard"></a><span data-ttu-id="2dcc5-135">使用新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="2dcc5-135">Using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="2dcc5-136">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-136">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="2dcc5-137">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-137">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="2dcc5-138">使用</span><span class="sxs-lookup"><span data-stu-id="2dcc5-138">Use this</span></span>|<span data-ttu-id="2dcc5-139">動作</span><span class="sxs-lookup"><span data-stu-id="2dcc5-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2dcc5-140">**類別**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-140">**Categories**</span></span>|<span data-ttu-id="2dcc5-141">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-141">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="2dcc5-142">**範本**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-142">**Templates**</span></span>|<span data-ttu-id="2dcc5-143">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-143">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="2dcc5-144">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-144">Click **Add**.</span></span> <span data-ttu-id="2dcc5-145">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-145">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="2dcc5-146">在 新增配接器精靈 中，選取  **WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-146">In the Add Adapter Wizard, select **WCF-SQL**.</span></span> <span data-ttu-id="2dcc5-147">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-147">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2dcc5-148">如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-148">If you already have a WCF-SQL port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="2dcc5-149">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-149">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="2dcc5-150">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sqlBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-150">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sqlBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="2dcc5-151">在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**清單中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-151">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, do one of the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dcc5-152">如果您要連接到 SQL Server 使用 Windows 驗證，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-152">If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="2dcc5-153">按一下此選項</span><span class="sxs-lookup"><span data-stu-id="2dcc5-153">Click this</span></span>|<span data-ttu-id="2dcc5-154">動作</span><span class="sxs-lookup"><span data-stu-id="2dcc5-154">To do this</span></span>|  
    |----------------|----------------|  
    |<span data-ttu-id="2dcc5-155">**無**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-155">**None**</span></span>|<span data-ttu-id="2dcc5-156">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-156">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="2dcc5-157">**視窗**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-157">**Windows**</span></span>|<span data-ttu-id="2dcc5-158">使用 Windows 驗證連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-158">Connect to SQL Server by using Windows authentication.</span></span>|  
    |<span data-ttu-id="2dcc5-159">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2dcc5-159">**Username**</span></span>|<span data-ttu-id="2dcc5-160">指定的使用者名稱和密碼來連接到 SQL Server 藉由指定使用者在 SQL Server 資料庫中定義的認證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-160">Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database.</span></span> <span data-ttu-id="2dcc5-161">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-161">Note that the user name and password are case-sensitive.</span></span> <span data-ttu-id="2dcc5-162">**注意：** 如果您離開**使用者名**和**密碼**空白欄位，配接器連接至 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-162">**Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication.</span></span>|  
  
8.  <span data-ttu-id="2dcc5-163">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-163">Click **OK**.</span></span>  
  
## <a name="enter-credentials-from-the-biztalk-server-administration-console"></a><span data-ttu-id="2dcc5-164">從 BizTalk Server 管理主控台中輸入認證</span><span class="sxs-lookup"><span data-stu-id="2dcc5-164">Enter credentials from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="2dcc5-165">從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的認證，Wcf-custom 或 WCF SQL 連接埠組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-165">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the credentials as part of the WCF-Custom or WCF-SQL port configuration.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="2dcc5-166">WCF 自訂連接埠輸入認證</span><span class="sxs-lookup"><span data-stu-id="2dcc5-166">Enter credentials for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="2dcc5-167">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-167">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2dcc5-168">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-168">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="2dcc5-169">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-169">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="2dcc5-170">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-170">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dcc5-171">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-171">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2dcc5-172">如果您要建立傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-172">If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="2dcc5-173">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-173">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2dcc5-174">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-174">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2dcc5-175">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-175">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2dcc5-176">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-176">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="2dcc5-177">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-177">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="2dcc5-178">如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-178">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="2dcc5-179">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-179">Select the **User account** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2dcc5-180">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-180">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2dcc5-181">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-181">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2dcc5-182">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-182">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="2dcc5-183">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-183">Select the **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
6.  <span data-ttu-id="2dcc5-184">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-184">Click **OK**.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-sql-port"></a><span data-ttu-id="2dcc5-185">輸入 WCF SQL 連接埠的認證</span><span class="sxs-lookup"><span data-stu-id="2dcc5-185">Enter credentials for the WCF-SQL port</span></span>  
  
1.  <span data-ttu-id="2dcc5-186">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-186">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2dcc5-187">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-187">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="2dcc5-188">如需指示，請參閱[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-188">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="2dcc5-189">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-189">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="2dcc5-190">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-190">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="2dcc5-191">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-191">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dcc5-192">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-192">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="2dcc5-193">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-193">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="2dcc5-194">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-194">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2dcc5-195">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-195">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2dcc5-196">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-196">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2dcc5-197">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-197">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="2dcc5-198">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-198">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
6.  <span data-ttu-id="2dcc5-199">如果您要建立接收埠，在 [傳輸屬性] 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2dcc5-199">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="2dcc5-200">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-200">Select the **User account** option, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2dcc5-201">請注意使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-201">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2dcc5-202">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-202">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2dcc5-203">這麼做之前，使用您登入的 Windows 使用者必須加入至 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-203">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    -   <span data-ttu-id="2dcc5-204">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-204">Select the **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
7.  <span data-ttu-id="2dcc5-205">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2dcc5-205">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcc5-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dcc5-206">See Also</span></span>  
[<span data-ttu-id="2dcc5-207">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="2dcc5-207">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)