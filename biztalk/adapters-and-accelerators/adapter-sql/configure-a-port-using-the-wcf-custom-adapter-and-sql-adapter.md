---
title: 設定使用 wcf-custom 配接器和 SQL 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF 自訂傳送和接收 BizTalk Server 中使用 SQL Server 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d44d9932-0a5e-4072-a480-2f8dc544ca79
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eafde28037b3c38dd36ec03907544a5ec23560f5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012607"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter"></a><span data-ttu-id="2b770-103">設定使用 wcf-custom 配接器和 SQL 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="2b770-103">Configure a port using the WCF-custom adapter and SQL adapter</span></span>
<span data-ttu-id="2b770-104">如何設定 Wcf-custom 傳送埠和接收埠來執行 SQL Server 使用的傳出和傳入作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b770-104">Steps to configure WCF-Custom send and receive ports to perform outbound and inbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2b770-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="2b770-105">Prerequisites</span></span>  
<span data-ttu-id="2b770-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="2b770-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="2b770-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2b770-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span> 
  
## <a name="deploy-adapters-to-send-messages-to-sql-server"></a><span data-ttu-id="2b770-108">部署配接器將訊息傳送至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2b770-108">Deploy adapters to send messages to SQL Server</span></span>  
 <span data-ttu-id="2b770-109">執行下列步驟來設定 Wcf-custom 傳送埠將訊息傳送至 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2b770-109">Perform the following steps to configure a WCF-Custom send port for sending messages to SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>    
 
1. <span data-ttu-id="2b770-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2b770-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="2b770-111">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2b770-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="2b770-112">展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b770-112">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
4. <span data-ttu-id="2b770-113">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2b770-113">Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.</span></span>  
  
5. <span data-ttu-id="2b770-114">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b770-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6. <span data-ttu-id="2b770-115">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7. <span data-ttu-id="2b770-116">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2b770-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="2b770-117">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="2b770-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for SQL Server.</span></span> <span data-ttu-id="2b770-118">如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-118">For more information about the connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="2b770-119">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="2b770-119">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="2b770-120">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="2b770-120">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) for a list of actions for each operation.</span></span> <span data-ttu-id="2b770-121">例如，叫用 SQL Server 資料庫中的資料表的 Insert 作業的動作是：</span><span class="sxs-lookup"><span data-stu-id="2b770-121">For example, the action to invoke the Insert operation on a table in a SQL Server database is:</span></span>  
  
      ```  
      TableOp/Insert/dbo/Employee  
      ```  
  
      > [!NOTE]
      >  <span data-ttu-id="2b770-122">員工是 SQL Server 資料庫中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b770-122">Employee is the name of a table in SQL Server database.</span></span>  
  
   3. <span data-ttu-id="2b770-123">按一下 **繫結**索引標籤上，以及從**繫結的型別**清單中，選取**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="2b770-123">Click the **Binding** tab, and from the **Binding Type** list, select **sqlBinding**.</span></span> <span data-ttu-id="2b770-124">您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b770-124">You can specify the different binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="2b770-125">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-125">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
   4. <span data-ttu-id="2b770-126">按一下 **認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2b770-126">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
      -   <span data-ttu-id="2b770-127">選取 **不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2b770-127">Select the **Do not use Single Sign-On** option, and the specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2b770-128">請注意，使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2b770-128">Note that the user name and password are case-sensitive.</span></span>  
  
          > [!NOTE]
          >  <span data-ttu-id="2b770-129">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2b770-129">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2b770-130">這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-130">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
      -   <span data-ttu-id="2b770-131">選取 **使用單一登入**選項，然後再指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="2b770-131">Select the **Use Single Sign-On** option, and then specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
           <span data-ttu-id="2b770-132">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-132">For more information about security with respect to BizTalk Server, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).</span></span>  
  
   5. <span data-ttu-id="2b770-133">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-133">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8. <span data-ttu-id="2b770-134">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="2b770-134">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="2b770-135">如果您選擇**靜態單向傳送埠**在步驟 4 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-135">If you chose **Static One-Way Send Port** in step 4, specify a send pipeline.</span></span> <span data-ttu-id="2b770-136">從**傳送管線**清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-136">From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="2b770-137">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-137">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="2b770-138">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-138">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="2b770-139">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-139">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
11. <span data-ttu-id="2b770-140">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="2b770-140">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-sql-server"></a><span data-ttu-id="2b770-141">部署 SQL Server 從接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="2b770-141">Deploy adapters to receive messages from SQL Server</span></span>
 <span data-ttu-id="2b770-142">執行下列步驟來設定 Wcf-custom 接收連接埠來接收訊息，從 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2b770-142">Perform the following steps to configure a WCF-Custom receive port for receiving messages from SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="2b770-143">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2b770-143">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="2b770-144">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2b770-144">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="2b770-145">展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b770-145">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
4. <span data-ttu-id="2b770-146">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2b770-146">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.</span></span>  
  
5. <span data-ttu-id="2b770-147">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b770-147">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6. <span data-ttu-id="2b770-148">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2b770-148">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="2b770-149">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2b770-149">The **Receive Location Properties** dialog box appears.</span></span>  
  
7. <span data-ttu-id="2b770-150">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2b770-150">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="2b770-151">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b770-151">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="2b770-152">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-152">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="2b770-153">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2b770-153">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="2b770-154">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 SQL Server 的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="2b770-154">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for SQL Server.</span></span> <span data-ttu-id="2b770-155">如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-155">For more information about the connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="2b770-156">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="2b770-156">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sqlBinding**.</span></span> <span data-ttu-id="2b770-157">您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b770-157">You can specify the different binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="2b770-158">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-158">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
   3. <span data-ttu-id="2b770-159">按一下 **行為**索引標籤以設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="2b770-159">Click the **Behavior** tab to set the transaction isolation level.</span></span> <span data-ttu-id="2b770-160">如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-160">For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).</span></span>  
  
   4. <span data-ttu-id="2b770-161">按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2b770-161">Click the **Other** tab, and do one of the following:</span></span>  
  
      - <span data-ttu-id="2b770-162">選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2b770-162">Select **User account**, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="2b770-163">請注意，使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2b770-163">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2b770-164">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2b770-164">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="2b770-165">這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-165">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
      - <span data-ttu-id="2b770-166">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b770-166">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
         <span data-ttu-id="2b770-167">如需有關安全性相對於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 < [SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b770-167">For more information about security with respect to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).</span></span>  
  
   5. <span data-ttu-id="2b770-168">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-168">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="2b770-169">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="2b770-169">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="2b770-170">如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-170">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="2b770-171">從**接收管線**清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-171">From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="2b770-172">如果您選擇**要求回應接收埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-172">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="2b770-173">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-173">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="2b770-174">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="2b770-174">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="2b770-175">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-175">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
13. <span data-ttu-id="2b770-176">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2b770-176">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b770-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b770-177">See Also</span></span>  
[<span data-ttu-id="2b770-178">手動設定 SQL 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="2b770-178">Manually configure a physical port binding to the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)