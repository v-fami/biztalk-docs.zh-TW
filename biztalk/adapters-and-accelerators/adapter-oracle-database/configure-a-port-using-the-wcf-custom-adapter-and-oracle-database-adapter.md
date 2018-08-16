---
title: 設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠 |Microsoft Docs
description: 建立 WCF 自訂傳送和接收 BizTalk Server 中使用 Oracle DB 配接器的連接埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c99ff526-ad97-4095-812f-0ce88b071e7f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 513d848d9bf95e75b8b6b983dde7019ce24ecf46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006479"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter"></a><span data-ttu-id="1ffdd-103">設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="1ffdd-103">Configure a port using the WCF-custom adapter and Oracle Database adapter</span></span>
<span data-ttu-id="1ffdd-104">如何設定 Wcf-custom 傳送埠和接收埠，以執行傳出和傳入作業上 Oracle 資料庫使用[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-104">How to configure WCF-Custom send and receive ports to perform outbound and inbound operations on the Oracle database using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1ffdd-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ffdd-105">Prerequisites</span></span>  
<span data-ttu-id="1ffdd-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="1ffdd-107">請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)指導方針的權限。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-107">See [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) for permissions guidance.</span></span>
  
## <a name="deploy-adapters-for-sending-messages-to-an-oracle-database"></a><span data-ttu-id="1ffdd-108">部署配接器將訊息傳送至 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ffdd-108">Deploy adapters for sending messages to an Oracle database</span></span>  
  
1. <span data-ttu-id="1ffdd-109">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="1ffdd-110">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-110">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="1ffdd-111">展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-111">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
4. <span data-ttu-id="1ffdd-112">以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據的模式之間的通訊設定的連接埠類型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-112">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.</span></span>  
  
5. <span data-ttu-id="1ffdd-113">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-113">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6. <span data-ttu-id="1ffdd-114">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-114">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7. <span data-ttu-id="1ffdd-115">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-115">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="1ffdd-116">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 Oracle 資料庫的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-116">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database.</span></span> <span data-ttu-id="1ffdd-117">如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-117">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="1ffdd-118">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-118">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="1ffdd-119">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-119">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) for a list of actions for each operation.</span></span> <span data-ttu-id="1ffdd-120">例如，叫用插入作業在 Oracle 資料庫中的 HR 結構描述下的員工資料表的動作是：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-120">For example, the action to invoke the Insert operation an EMPLOYEE table under the HR schema in an Oracle database is:</span></span>  
  
      ```  
      http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
      ```  
  
   3. <span data-ttu-id="1ffdd-121">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-121">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span> <span data-ttu-id="1ffdd-122">您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-122">You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="1ffdd-123">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-123">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
   4. <span data-ttu-id="1ffdd-124">按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-124">Click the **Credentials** tab and do one of the following:</span></span>  
  
      - <span data-ttu-id="1ffdd-125">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-125">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="1ffdd-126">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-126">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="1ffdd-127">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-127">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
      - <span data-ttu-id="1ffdd-128">選取 **使用單一登入**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-128">Select the **Use Single Sign-On** option, and specify an affiliate SSO application.</span></span>  
  
        <span data-ttu-id="1ffdd-129">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Oracle 資料庫配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-129">For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span></span>  
  
        <span data-ttu-id="1ffdd-130">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-130">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8. <span data-ttu-id="1ffdd-131">從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-131">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="1ffdd-132">如果您選擇**靜態單向傳送埠**在步驟 4 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-132">If you chose **Static One-Way Send Port** in step 4, specify a send pipeline.</span></span> <span data-ttu-id="1ffdd-133">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-133">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="1ffdd-134">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-134">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="1ffdd-135">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-135">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="1ffdd-136">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-136">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
11. <span data-ttu-id="1ffdd-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-137">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-for-receiving-messages-from-an-oracle-database"></a><span data-ttu-id="1ffdd-138">部署用於從 Oracle 資料庫接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="1ffdd-138">Deploy adapters for receiving messages from an Oracle database</span></span>  
  
1. <span data-ttu-id="1ffdd-139">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-139">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="1ffdd-140">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-140">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="1ffdd-141">展開您要在其下部署的應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-141">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
4. <span data-ttu-id="1ffdd-142">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**，取決於BizTalk Server 和 Oracle 資料庫之間的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-142">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between BizTalk Server and the Oracle database.</span></span>  
  
5. <span data-ttu-id="1ffdd-143">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-143">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6. <span data-ttu-id="1ffdd-144">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-144">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="1ffdd-145">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-145">The **Receive Location Properties** dialog box appears.</span></span>  
  
7. <span data-ttu-id="1ffdd-146">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-146">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="1ffdd-147">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-147">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="1ffdd-148">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-148">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="1ffdd-149">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-149">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="1ffdd-150">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 Oracle 資料庫的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-150">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database.</span></span> <span data-ttu-id="1ffdd-151">如需連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-151">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="1ffdd-152">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-152">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span> <span data-ttu-id="1ffdd-153">您可以指定不同的繫結屬性所公開[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-153">You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="1ffdd-154">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-154">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
   3. <span data-ttu-id="1ffdd-155">按一下 **其他人**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1ffdd-155">Click the **Others** tab, and do one of the following:</span></span>  
  
      - <span data-ttu-id="1ffdd-156">選取 **使用者帳戶**，並指定使用者名稱和密碼以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-156">Select **User account**, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="1ffdd-157">若要使用的 Oracle 資料庫的認證連線，請輸入中的資料庫認證**使用者名稱**並**密碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-157">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="1ffdd-158">若要使用 Windows 驗證進行連接，請輸入**/** 中**使用者名稱**文字方塊中，並保留**密碼**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-158">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
      - <span data-ttu-id="1ffdd-159">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-159">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
        <span data-ttu-id="1ffdd-160">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[Oracle 資料庫配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-160">For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span></span>
  
        <span data-ttu-id="1ffdd-161">若要返回**接收位置屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-161">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="1ffdd-162">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-162">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="1ffdd-163">如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-163">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="1ffdd-164">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-164">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="1ffdd-165">如果您選擇**要求回應接收埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-165">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="1ffdd-166">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-166">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="1ffdd-167">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-167">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="1ffdd-168">在 [**接收位置屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-168">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
13. <span data-ttu-id="1ffdd-169">在 [**接收埠屬性**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1ffdd-169">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffdd-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ffdd-170">See Also</span></span>  
<span data-ttu-id="1ffdd-171">[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="1ffdd-171">[Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md) </span></span>  
 [<span data-ttu-id="1ffdd-172">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="1ffdd-172">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)