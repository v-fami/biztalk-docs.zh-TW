---
title: 設定使用 wcf-custom 配接器和 SAP 配接器在 BizTalk 中的連接埠 |Microsoft Docs
description: 建立 WCF 自訂連接埠來傳送或接收訊息，從使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中的 SAP
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3962456-e9ac-4575-8266-b35e892dd428
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9baf552efc102d13b83b28f5c5b0c473147b2812
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982943"
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-sap-adapter"></a><span data-ttu-id="82173-103">設定使用 wcf-custom 配接器和 SAP 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="82173-103">Configure a port using the WCF-custom adapter and SAP adapter</span></span>
<span data-ttu-id="82173-104">本主題說明如何設定 Wcf-custom 傳送埠和接收埠來執行 SAP 系統使用的傳出和傳入作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="82173-104">This topic provides instructions on how to configure WCF-Custom send and receive ports to perform outbound and inbound operations on SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82173-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="82173-105">Prerequisites</span></span>  
<span data-ttu-id="82173-106">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="82173-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="82173-107">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性使用者權限](../../core/minimum-security-user-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security User Rights](../../core/minimum-security-user-rights.md).</span></span> 
  
## <a name="deploy-adapters-to-send-messages-to-sap"></a><span data-ttu-id="82173-108">部署配接器將訊息傳送至 SAP</span><span class="sxs-lookup"><span data-stu-id="82173-108">Deploy adapters to send messages to SAP</span></span>  
<span data-ttu-id="82173-109">完成下列步驟來設定 Wcf-custom 傳送埠將訊息傳送至 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="82173-109">Complete the following steps to configure a WCF-Custom send port for sending messages to SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="82173-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="82173-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="82173-111">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="82173-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="82173-112">展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="82173-112">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
4. <span data-ttu-id="82173-113">以滑鼠右鍵按一下**傳送埠**，指向**新增**，並指向您想要根據 BizTalk Server 與 SAP 系統之間的通訊模式所設定的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="82173-113">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
5. <span data-ttu-id="82173-114">在 **傳送埠屬性**對話方塊的 **一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="82173-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6. <span data-ttu-id="82173-115">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="82173-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7. <span data-ttu-id="82173-116">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="82173-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="82173-117">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 SAP 系統的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="82173-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system.</span></span> <span data-ttu-id="82173-118">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-118">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
   2. <span data-ttu-id="82173-119">在 **一般**索引標籤中，於**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="82173-119">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="82173-120">請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)的每個作業的動作清單。</span><span class="sxs-lookup"><span data-stu-id="82173-120">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) for a list of actions for each operation.</span></span> <span data-ttu-id="82173-121">比方說，是叫用 RFC_CUSTOMER_GET 的動作：</span><span class="sxs-lookup"><span data-stu-id="82173-121">For example, the action to invoke the RFC_CUSTOMER_GET would be:</span></span>  
  
      ```  
      http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
      ```  
  
   3. <span data-ttu-id="82173-122">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="82173-122">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="82173-123">您可以指定不同的繫結屬性所公開[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="82173-123">You can specify the different binding properties exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="82173-124">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-124">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
   4. <span data-ttu-id="82173-125">按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="82173-125">Click the **Credentials** tab and do one of the following:</span></span>  
  
      -   <span data-ttu-id="82173-126">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="82173-126">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
      -   <span data-ttu-id="82173-127">選取 **使用單一登入**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="82173-127">Select the **Use Single Sign-On** option, and specify an affiliate SSO application.</span></span>  
  
           <span data-ttu-id="82173-128">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-128">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
           <span data-ttu-id="82173-129">若要返回**傳送埠屬性** 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="82173-129">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8. <span data-ttu-id="82173-130">從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="82173-130">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="82173-131">如果您在步驟 4 中選擇靜態單向傳送埠，指定傳送管線。</span><span class="sxs-lookup"><span data-stu-id="82173-131">If you chose Static One-Way Send Port in step 4, specify a send pipeline.</span></span> <span data-ttu-id="82173-132">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-132">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="82173-133">如果您選擇**靜態請求-回應連接埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="82173-133">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="82173-134">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-134">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="82173-135">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-135">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="82173-136">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="82173-136">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-sap"></a><span data-ttu-id="82173-137">部署至從 SAP 接收訊息的配接器</span><span class="sxs-lookup"><span data-stu-id="82173-137">Deploy adapters to receive messages from SAP</span></span>
<span data-ttu-id="82173-138">完成下列步驟來設定 Wcf-custom 接收連接埠來接收訊息，從 SAP 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="82173-138">Complete the following steps to configure a WCF-Custom receive port for receiving messages from SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1. <span data-ttu-id="82173-139">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="82173-139">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="82173-140">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="82173-140">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="82173-141">展開您要在其下部署的應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="82173-141">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
4. <span data-ttu-id="82173-142">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**或**要求回應接收埠**取決於BizTalk Server 與 SAP 系統之間的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="82173-142">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port** depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
5. <span data-ttu-id="82173-143">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="82173-143">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6. <span data-ttu-id="82173-144">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="82173-144">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="82173-145">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="82173-145">The **Receive Location Properties** dialog box appears.</span></span>  
  
7. <span data-ttu-id="82173-146">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="82173-146">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="82173-147">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="82173-147">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="82173-148">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="82173-148">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="82173-149">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="82173-149">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="82173-150">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定 SAP 系統的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="82173-150">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system.</span></span> <span data-ttu-id="82173-151">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-151">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
   2.  <span data-ttu-id="82173-152">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="82173-152">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="82173-153">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-153">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
   3.  <span data-ttu-id="82173-154">按一下 **其他人**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="82173-154">Click the **Others** tab, and do one of the following:</span></span>  
  
       -   <span data-ttu-id="82173-155">選取 **使用者帳戶**，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="82173-155">Select **User account**, and specify the user name and password to connect to an SAP system.</span></span>  
  
       -   <span data-ttu-id="82173-156">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="82173-156">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
            <span data-ttu-id="82173-157">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="82173-157">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
            <span data-ttu-id="82173-158">按一下 [ **[確定]** 以返回**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="82173-158">Click **OK** to return to the **Receive Location Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="82173-159">從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="82173-159">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="82173-160">如果您選擇**單向接收埠**在步驟 4 中，指定接收管線。</span><span class="sxs-lookup"><span data-stu-id="82173-160">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="82173-161">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-161">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="82173-162">如果您選擇**要求回應接收埠**在步驟 4 中，請指定傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="82173-162">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="82173-163">從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-163">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="82173-164">從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="82173-164">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="82173-165">按一下 [**確定 i**n**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="82173-165">Click **OK i**n the **Receive Location Properties** dialog box.</span></span>  
  
13. <span data-ttu-id="82173-166">按一下 [ **[確定]** 中**接收埠屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="82173-166">Click **OK** in the **Receive Port Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82173-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82173-167">See Also</span></span>  
[<span data-ttu-id="82173-168">以手動方式設定 SAP 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="82173-168">Manually configure a physical port binding to the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)