---
title: 設定使用 WCF-SAP 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF SAP 連接埠來傳送或接收訊息，從使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中的 SAP
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 420683f8-2516-4c65-895d-fe535824d450
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a80c778e34505755a147dccf48e50ea9ea3a18d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992671"
---
# <a name="configure-a-port-using-the-wcf-sap-adapter"></a><span data-ttu-id="9ae98-103">設定使用 WCF-SAP 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="9ae98-103">Configure a port using the WCF-SAP adapter</span></span>
<span data-ttu-id="9ae98-104">本主題提供有關如何設定 WCF SAP 傳送和接收埠來執行 SAP 系統使用的傳出和傳入作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ae98-104">This topic provides instructions on how to configure WCF-SAP send and receive ports to perform outbound and inbound operations on SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9ae98-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="9ae98-105">Prerequisites</span></span>  
<span data-ttu-id="9ae98-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="9ae98-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="9ae98-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-to-send-messages-to-sap"></a><span data-ttu-id="9ae98-108">部署配接器將訊息傳送至 SAP</span><span class="sxs-lookup"><span data-stu-id="9ae98-108">Deploy adapters to send messages to SAP</span></span>  
<span data-ttu-id="9ae98-109">完成下列步驟來設定 WCF SAP 的傳送埠將訊息傳送至 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-109">Complete the following steps to configure a WCF-SAP send port for sending messages to SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="9ae98-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="9ae98-111">新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-111">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="9ae98-112">如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-112">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="9ae98-113">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-113">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="9ae98-114">展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ae98-114">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
5. <span data-ttu-id="9ae98-115">以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據 BizTalk Server 與 SAP 系統之間的通訊模式所設定的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="9ae98-115">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
6. <span data-ttu-id="9ae98-116">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae98-116">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7. <span data-ttu-id="9ae98-117">從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-117">From the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="9ae98-118">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9ae98-118">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="9ae98-119">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="9ae98-119">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="9ae98-120">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-120">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="9ae98-121">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="9ae98-121">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="9ae98-122">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="9ae98-122">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) for a list of actions for each operation.</span></span> <span data-ttu-id="9ae98-123">比方說，是叫用 RFC_CUSTOMER_GET 的動作：</span><span class="sxs-lookup"><span data-stu-id="9ae98-123">For example, the action to invoke the RFC_CUSTOMER_GET would be:</span></span>  
  
      ```  
      http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
      ```  
  
   3. <span data-ttu-id="9ae98-124">按一下 **繫結**索引標籤，然後指定的繫結所公開的屬性值[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ae98-124">Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="9ae98-125">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-125">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="9ae98-126">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="9ae98-126">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="9ae98-127">比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態</span><span class="sxs-lookup"><span data-stu-id="9ae98-127">For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.</span></span>  
  
   4. <span data-ttu-id="9ae98-128">按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9ae98-128">Click the **Credentials** tab and do one of the following:</span></span>  
  
   -   <span data-ttu-id="9ae98-129">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="9ae98-129">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
   -   <span data-ttu-id="9ae98-130">選取 **使用單一登入**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae98-130">Select the **Use Single Sign-On** option, and specify an affiliate SSO application.</span></span>  
  
        <span data-ttu-id="9ae98-131">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-131">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>  
  
        <span data-ttu-id="9ae98-132">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-132">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="9ae98-133">從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-133">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="9ae98-134">如果您選擇要建立**靜態單向傳送埠**在步驟 5 中，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-134">If you chose to create a **Static One-Way Send Port** in step 5, specify a send pipeline.</span></span> <span data-ttu-id="9ae98-135">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-135">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="9ae98-136">如果您選擇要建立**靜態請求-回應連接埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-136">If you chose to create a **Static Solicit-Response Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="9ae98-137">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-137">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="9ae98-138">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-138">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="9ae98-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="9ae98-139">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-sap"></a><span data-ttu-id="9ae98-140">部署至從 SAP 接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="9ae98-140">Deploy adapters to receive messages from SAP</span></span>  
<span data-ttu-id="9ae98-141">完成下列步驟來設定 WCF SAP 接收埠接收訊息，從 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-141">Complete the following steps to configure a WCF-SAP receive port for receiving messages from SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="9ae98-142">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-142">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="9ae98-143">新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ae98-143">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="9ae98-144">如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-144">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3. <span data-ttu-id="9ae98-145">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-145">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4. <span data-ttu-id="9ae98-146">展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ae98-146">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
5. <span data-ttu-id="9ae98-147">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**取決於BizTalk Server 與 SAP 系統之間的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="9ae98-147">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port** depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
6. <span data-ttu-id="9ae98-148">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae98-148">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
7. <span data-ttu-id="9ae98-149">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-149">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="9ae98-150">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="9ae98-150">The **Receive Location Properties** dialog box appears.</span></span>  
  
8. <span data-ttu-id="9ae98-151">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9ae98-151">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="9ae98-152">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae98-152">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="9ae98-153">從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-153">From the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
9. <span data-ttu-id="9ae98-154">在 [傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9ae98-154">In the transport properties dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="9ae98-155">按一下 **一般**索引標籤上，按一下**設定**按鈕，然後提供連接參數的值。</span><span class="sxs-lookup"><span data-stu-id="9ae98-155">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="9ae98-156">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-156">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="9ae98-157">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-157">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="9ae98-158">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-158">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="9ae98-159">繫結屬性會顯示根據您要設定傳送埠或接收埠。</span><span class="sxs-lookup"><span data-stu-id="9ae98-159">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="9ae98-160">比方說，繫結屬性與輸入相關的作業無法使用。 在設定傳送埠，因為輸入的作業需要接收埠組態</span><span class="sxs-lookup"><span data-stu-id="9ae98-160">For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.</span></span>  
  
   3. <span data-ttu-id="9ae98-161">按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9ae98-161">Click the **Other** tab, and do one of the following:</span></span>  
  
   4. <span data-ttu-id="9ae98-162">選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="9ae98-162">Select **User account**, and specify the user name and password to connect to an SAP system.</span></span>  
  
   5. <span data-ttu-id="9ae98-163">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ae98-163">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
       <span data-ttu-id="9ae98-164">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae98-164">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>  
  
       <span data-ttu-id="9ae98-165">按一下 [ **[確定]** 以返回**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ae98-165">Click **OK** to return to the **Receive Location Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="9ae98-166">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="9ae98-166">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
11. <span data-ttu-id="9ae98-167">如果您選擇要建立**單向接收埠**在步驟 5 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-167">If you chose to create **One-way Receive Port** in step 5, specify a receive pipeline.</span></span> <span data-ttu-id="9ae98-168">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-168">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="9ae98-169">如果您選擇要建立**要求回應接收埠**在步驟 5 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-169">If you chose to create **Request Response Receive Port** in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="9ae98-170">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-170">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="9ae98-171">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="9ae98-171">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
13. <span data-ttu-id="9ae98-172">按一下 [ **[確定]** 中**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ae98-172">Click **OK** in the **Receive Location Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="9ae98-173">按一下 [ **[確定]** 中**接收埠屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ae98-173">Click **OK** in the **Receive Port Properties** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ae98-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae98-174">See also</span></span>
[<span data-ttu-id="9ae98-175">以手動方式設定 SAP 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="9ae98-175">Manually configure a physical port binding to the SAP adapter</span></span>](manually-configure-a-physical-port-binding-to-the-sap-adapter.md)