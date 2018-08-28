---
title: 設定使用 Wcf-oracledb 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 Wcf-oracledb 傳送和接收 BizTalk Server 中使用 Oracle DB 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9eafefb-9b30-4801-9be9-6034ae0d3b7d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee5b39d077c48317e557072c54ba032ebe82a24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009175"
---
# <a name="configure-a-port-using-the-wcf-oracledb-adapter"></a><span data-ttu-id="0a0ff-103">設定使用 Wcf-oracledb 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="0a0ff-103">Configure a port using the WCF-OracleDB adapter</span></span>
<span data-ttu-id="0a0ff-104">How to configure Wcf-oracledb 如何傳送和接收連接埠，以執行 Oracle 資料庫使用的輸入和輸出作業[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-104">How to configure WCF-OracleDB send and receive ports to perform outbound and inbound operations on the Oracle database using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a0ff-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="0a0ff-105">Prerequisites</span></span>  
<span data-ttu-id="0a0ff-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="0a0ff-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span> 
  
## <a name="deploy-adapters-to-send-messages-to-oracle-database"></a><span data-ttu-id="0a0ff-108">部署配接器將訊息傳送至 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="0a0ff-108">Deploy adapters to send messages to Oracle Database</span></span>  
  
1. <span data-ttu-id="0a0ff-109">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="0a0ff-110">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-110">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0a0ff-111">如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-111">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="0a0ff-112">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-112">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="0a0ff-113">展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-113">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
5. <span data-ttu-id="0a0ff-114">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-114">Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.</span></span>  
  
6. <span data-ttu-id="0a0ff-115">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-115">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7. <span data-ttu-id="0a0ff-116">從**型別**下拉式清單中，選取 Wcf-oracledb，，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-116">From the **Type** drop-down list, select WCF-OracleDB, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="0a0ff-117">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-117">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="0a0ff-118">按一下 **一般**索引標籤上，按一下**設定**按鈕，並提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-118">Click the **General** tab, click the **Configure** button and provide values for the connection parameters.</span></span> <span data-ttu-id="0a0ff-119">如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-119">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="0a0ff-120">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-120">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="0a0ff-121">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-121">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) for a list of actions for each operation.</span></span> <span data-ttu-id="0a0ff-122">例如，叫用插入作業在 Oracle 資料庫中的 HR 結構描述下的員工資料表的動作是：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-122">For example, the action to invoke the Insert operation an EMPLOYEE table under the HR schema in an Oracle database is:</span></span>  
  
      ```  
      http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
      ```  
  
   3. <span data-ttu-id="0a0ff-123">按一下 **繫結**索引標籤，然後指定所公開的繫結屬性的值[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-123">Click the **Binding** tab and specify values for the binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="0a0ff-124">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-124">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>
  
      > [!NOTE]
      >  <span data-ttu-id="0a0ff-125">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-125">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="0a0ff-126">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-126">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   4. <span data-ttu-id="0a0ff-127">按一下 **認證**索引標籤，然後再執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-127">Click the **Credentials** tab, and then do one of the following:</span></span>  
  
      -   <span data-ttu-id="0a0ff-128">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-128">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
          -   <span data-ttu-id="0a0ff-129">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-129">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
          -   <span data-ttu-id="0a0ff-130">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-130">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
      -   <span data-ttu-id="0a0ff-131">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-131">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
   5. <span data-ttu-id="0a0ff-132">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-132">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="0a0ff-133">從**傳送處理常式**清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-133">From the **Send handler** list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="0a0ff-134">如果您選擇**靜態單向傳送埠**在步驟 5 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-134">If you chose **Static One-Way Send Port** in step 5, specify a send pipeline.</span></span> <span data-ttu-id="0a0ff-135">從**傳送管線**清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-135">From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="0a0ff-136">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-136">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="0a0ff-137">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-137">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="0a0ff-138">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-138">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
12. <span data-ttu-id="0a0ff-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-139">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-oracle-database"></a><span data-ttu-id="0a0ff-140">將部署從 Oracle 資料庫接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="0a0ff-140">Deploy adapters to receive messages from Oracle Database</span></span>  
  
1. <span data-ttu-id="0a0ff-141">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-141">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="0a0ff-142">新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-142">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0a0ff-143">如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-143">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="0a0ff-144">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-144">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="0a0ff-145">展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-145">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
5. <span data-ttu-id="0a0ff-146">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於之間的通訊模式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-146">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.</span></span>  
  
6. <span data-ttu-id="0a0ff-147">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-147">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
7. <span data-ttu-id="0a0ff-148">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-148">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="0a0ff-149">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-149">The **Receive Location Properties** dialog box appears.</span></span>  
  
8. <span data-ttu-id="0a0ff-150">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-150">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="0a0ff-151">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-151">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="0a0ff-152">從**型別**下拉式清單中，選取 Wcf-oracledb，，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-152">From the **Type** drop-down list, select WCF-OracleDB, and then click **Configure**.</span></span>  
  
9. <span data-ttu-id="0a0ff-153">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-153">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="0a0ff-154">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-154">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="0a0ff-155">如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-155">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="0a0ff-156">按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-156">Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="0a0ff-157">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-157">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>
  
      > [!NOTE]
      >  <span data-ttu-id="0a0ff-158">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-158">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="0a0ff-159">比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-159">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
   3. <span data-ttu-id="0a0ff-160">按一下 **行為**索引標籤以設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-160">Click the **Behavior** tab to set the transaction isolation level.</span></span> <span data-ttu-id="0a0ff-161">如需有關設定交易隔離等級的詳細資訊，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-161">For more information about setting transaction isolation level, see [Configure transaction isolation level and transaction timeout](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).</span></span>  
  
   4. <span data-ttu-id="0a0ff-162">按一下 **其他人**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0a0ff-162">Click the **Others** tab, and do one of the following:</span></span>  
  
      -   <span data-ttu-id="0a0ff-163">選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-163">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
          -   <span data-ttu-id="0a0ff-164">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-164">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
          -   <span data-ttu-id="0a0ff-165">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-165">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
      -   <span data-ttu-id="0a0ff-166">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-166">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
   5. <span data-ttu-id="0a0ff-167">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-167">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
10. <span data-ttu-id="0a0ff-168">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-168">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
11. <span data-ttu-id="0a0ff-169">如果您選擇**單向接收埠**在步驟 5 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-169">If you chose **One-way Receive Port** in step 5, specify a receive pipeline.</span></span> <span data-ttu-id="0a0ff-170">從**接收管線**清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-170">From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="0a0ff-171">如果您選擇**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-171">If you chose **Request Response Receive Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="0a0ff-172">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-172">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="0a0ff-173">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-173">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
13. <span data-ttu-id="0a0ff-174">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-174">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="0a0ff-175">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a0ff-175">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0ff-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a0ff-176">See Also</span></span>  
   [<span data-ttu-id="0a0ff-177">手動設定 Oracle 資料庫配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="0a0ff-177">Manually configure a physical port binding to the Oracle Database Adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)
 
 [<span data-ttu-id="0a0ff-178">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0a0ff-178">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)