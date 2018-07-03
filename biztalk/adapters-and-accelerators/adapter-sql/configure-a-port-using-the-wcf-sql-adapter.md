---
title: 設定使用 WCF-SQL 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF SQL 傳送和接收 BizTalk Server 中使用 SQL Server 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8cdc032-3160-43de-9510-7ca69506083e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6a2484c23d4abf8fbe489c3b2fed3ced25b9313
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992071"
---
# <a name="configure-a-port-using-the-wcf-sql-adapter"></a><span data-ttu-id="fea97-103">設定使用 WCF-SQL 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="fea97-103">Configure a port using the WCF-SQL adapter</span></span>
<span data-ttu-id="fea97-104">本主題提供有關如何設定 WCF SQL 傳送和接收連接埠，以執行 SQL Server 使用的傳出和傳入作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fea97-104">This topic provides instructions on how to configure WCF-SQL send and receive ports to perform outbound and inbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fea97-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fea97-105">Prerequisites</span></span>  
<span data-ttu-id="fea97-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="fea97-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="fea97-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fea97-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-to-send-messages-to-sql-server"></a><span data-ttu-id="fea97-108">部署配接器將訊息傳送至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="fea97-108">Deploy adapters to send messages to SQL Server</span></span>  
 <span data-ttu-id="fea97-109">執行下列步驟來設定 WCF SQL 傳送埠將訊息傳送至 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-109">Perform the following steps to configure a WCF-SQL send port for sending messages to SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="fea97-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="fea97-111">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-111">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="fea97-112">如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-112">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="fea97-113">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fea97-113">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="fea97-114">展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fea97-114">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
5. <span data-ttu-id="fea97-115">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fea97-115">Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.</span></span>  
  
6. <span data-ttu-id="fea97-116">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="fea97-116">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7. <span data-ttu-id="fea97-117">從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-117">From the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="fea97-118">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fea97-118">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="fea97-119">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="fea97-119">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="fea97-120">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-120">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="fea97-121">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="fea97-121">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="fea97-122">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="fea97-122">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) for a list of actions for each operation.</span></span> <span data-ttu-id="fea97-123">例如，叫用 SQL Server 資料庫中的資料表的 Insert 作業的動作是：</span><span class="sxs-lookup"><span data-stu-id="fea97-123">For example, the action to invoke the Insert operation on a table in a SQL Server database is:</span></span>  
  
      ```  
      TableOp/Insert/dbo/Employee  
      ```  
  
      > [!NOTE]
      >  <span data-ttu-id="fea97-124">員工是 SQL Server 資料庫中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="fea97-124">Employee is the name of a table in SQL Server database.</span></span>  
  
   3. <span data-ttu-id="fea97-125">按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fea97-125">Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="fea97-126">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-126">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="fea97-127">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="fea97-127">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="fea97-128">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="fea97-128">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   4. <span data-ttu-id="fea97-129">按一下 **認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fea97-129">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
      -   <span data-ttu-id="fea97-130">選取 **不會使用單一登入**選項，以及指定的使用者名稱和密碼來連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fea97-130">Select the **Do not use Single Sign-On** option, and the specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="fea97-131">請注意，使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fea97-131">Note that the user name and password are case-sensitive.</span></span>  
  
          > [!NOTE]
          >  <span data-ttu-id="fea97-132">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="fea97-132">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="fea97-133">這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-133">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
      -   <span data-ttu-id="fea97-134">選取 **使用單一登入**選項，然後再指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="fea97-134">Select the **Use Single Sign-On** option, and then specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
           <span data-ttu-id="fea97-135">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-135">For more information about security with respect to BizTalk Server, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).</span></span>  
  
   5. <span data-ttu-id="fea97-136">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-136">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="fea97-137">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="fea97-137">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="fea97-138">如果您選擇要建立**靜態單向傳送埠**在步驟 5 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-138">If you chose to create **Static One-Way Send Port** in step 5, specify a send pipeline.</span></span> <span data-ttu-id="fea97-139">從**傳送管線**清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-139">From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="fea97-140">如果您選擇要建立**靜態請求-回應連接埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-140">If you chose to create **Static Solicit-Response Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="fea97-141">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-141">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="fea97-142">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-142">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
12. <span data-ttu-id="fea97-143">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="fea97-143">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-sql-server"></a><span data-ttu-id="fea97-144">部署 SQL Server 從接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="fea97-144">Deploy adapters to receive messages from SQL Server</span></span>  
 <span data-ttu-id="fea97-145">執行下列步驟來設定 WCF SQL 接收埠接收訊息，從 SQL Server 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-145">Perform the following steps to configure a WCF-SQL receive port for receiving messages from SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="fea97-146">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-146">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="fea97-147">新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fea97-147">Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="fea97-148">如需相關指示，請參閱 <<c0> [ 將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-148">For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="fea97-149">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fea97-149">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="fea97-150">展開您要在其下部署的應用程式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fea97-150">Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
5. <span data-ttu-id="fea97-151">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fea97-151">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.</span></span>  
  
6. <span data-ttu-id="fea97-152">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="fea97-152">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
7. <span data-ttu-id="fea97-153">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fea97-153">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="fea97-154">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fea97-154">The **Receive Location Properties** dialog box appears.</span></span>  
  
8. <span data-ttu-id="fea97-155">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fea97-155">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="fea97-156">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="fea97-156">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="fea97-157">從**型別**下拉式清單中，選取您稍早新增 WCF-SQL 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-157">From the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.</span></span>  
  
9. <span data-ttu-id="fea97-158">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fea97-158">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="fea97-159">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="fea97-159">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="fea97-160">如需有關連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-160">For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="fea97-161">按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fea97-161">Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="fea97-162">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-162">For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="fea97-163">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="fea97-163">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="fea97-164">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="fea97-164">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   3. <span data-ttu-id="fea97-165">按一下 **行為**索引標籤以設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="fea97-165">Click the **Behavior** tab to set the transaction isolation level.</span></span> <span data-ttu-id="fea97-166">如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-166">For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).</span></span>  
  
   4. <span data-ttu-id="fea97-167">按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fea97-167">Click the **Other** tab, and do one of the following:</span></span>  
  
      - <span data-ttu-id="fea97-168">選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fea97-168">Select **User account**, and specify the user name and password to connect to SQL Server.</span></span> <span data-ttu-id="fea97-169">請注意，使用者名稱和密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fea97-169">Note that the user name and password are case-sensitive.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fea97-170">如果您想要連接到 SQL Server 使用 Windows 驗證，請指定空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="fea97-170">If you want to connect to SQL Server using Windows authentication, specify a blank user name and password.</span></span> <span data-ttu-id="fea97-171">這麼做之前，Windows 您登入，必須將的使用者加入到 SQL Server 中所述[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-171">Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
      - <span data-ttu-id="fea97-172">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="fea97-172">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
         <span data-ttu-id="fea97-173">如需有關安全性相對於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 < [SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fea97-173">For more information about security with respect to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).</span></span>  
  
   5. <span data-ttu-id="fea97-174">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-174">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
10. <span data-ttu-id="fea97-175">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="fea97-175">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
11. <span data-ttu-id="fea97-176">如果您選擇要建立**單向接收埠**在步驟 5 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-176">If you chose to create **One-way Receive Port** in step 5, specify a receive pipeline.</span></span> <span data-ttu-id="fea97-177">從**接收管線**清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-177">From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="fea97-178">如果您選擇要建立**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-178">If you chose to create **Request Response Receive Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="fea97-179">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-179">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="fea97-180">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="fea97-180">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
13. <span data-ttu-id="fea97-181">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-181">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="fea97-182">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fea97-182">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea97-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fea97-183">See Also</span></span>  
[<span data-ttu-id="fea97-184">手動設定 SQL 配接器的實體連接埠繫結 </span><span class="sxs-lookup"><span data-stu-id="fea97-184">Manually configure a physical port binding to the SQL adapter </span></span>](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)