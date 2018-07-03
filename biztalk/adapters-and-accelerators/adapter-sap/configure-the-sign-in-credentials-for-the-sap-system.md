---
title: 設定登入認證的 SAP 系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb41106b-b673-4fcf-a56e-6208e3113469
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c788bf8c98fc06511ce692c84600f040443dd993
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989167"
---
# <a name="configure-the-sign-in-credentials-for-the-sap-system"></a><span data-ttu-id="fb77a-102">設定登入 SAP 系統的認證</span><span class="sxs-lookup"><span data-stu-id="fb77a-102">Configure the sign in credentials for the SAP system</span></span>
<span data-ttu-id="fb77a-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]需要配接器用戶端，以提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="fb77a-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="fb77a-104">配接器會使用這些認證來驗證使用者與 SAP 系統，並建立連線。</span><span class="sxs-lookup"><span data-stu-id="fb77a-104">The adapter uses these credentials to authenticate the user with the SAP system and to establish a connection.</span></span>  

 <span data-ttu-id="fb77a-105">配接器用戶端可以提供用戶端認證，這兩個設計階段或執行階段。</span><span class="sxs-lookup"><span data-stu-id="fb77a-105">Adapter clients can provide the client credentials both at design time or run time.</span></span> <span data-ttu-id="fb77a-106">在設計階段認證，才能產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fb77a-106">At design time, credentials are required to generate the metadata.</span></span> <span data-ttu-id="fb77a-107">在執行階段，認證才能執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="fb77a-107">At run time, credentials are required to perform operations on the SAP system.</span></span> <span data-ttu-id="fb77a-108">本節提供在設計階段和執行的階段指定用戶端認證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fb77a-108">This section provides information about specifying client credentials at design time and run time.</span></span>  

## <a name="enter-the-client-credentials-at-design-time"></a><span data-ttu-id="fb77a-109">在設計階段中輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="fb77a-109">Enter the client credentials at design time</span></span>  
 <span data-ttu-id="fb77a-110">設計階段，您可以指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb77a-110">For design time, you can specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  

### <a name="enter-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="fb77a-111">輸入取用配接器服務增益集所使用的認證</span><span class="sxs-lookup"><span data-stu-id="fb77a-111">Enter credentials using Consume Adapter Service Add-in</span></span>  

1.  <span data-ttu-id="fb77a-112">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-112">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2.  <span data-ttu-id="fb77a-113">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fb77a-113">In the **Add Generated Items** dialog box, do the following:</span></span>  

    |<span data-ttu-id="fb77a-114">使用</span><span class="sxs-lookup"><span data-stu-id="fb77a-114">Use this</span></span>|<span data-ttu-id="fb77a-115">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="fb77a-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fb77a-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="fb77a-116">**Categories**</span></span>|<span data-ttu-id="fb77a-117">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="fb77a-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="fb77a-118">**Templates**</span></span>|<span data-ttu-id="fb77a-119">按一下 **取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-119">Click **Consume Adapter Service**.</span></span>|  

3.  <span data-ttu-id="fb77a-120">若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  

4.  <span data-ttu-id="fb77a-121">在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**sapBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  

5.  <span data-ttu-id="fb77a-122">中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  

6.  <span data-ttu-id="fb77a-123">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="fb77a-123">Click **OK**.</span></span>  

### <a name="enter-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="fb77a-124">輸入認證，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="fb77a-124">Enter credentials using Add Adapter Metadata Wizard</span></span>  

1. <span data-ttu-id="fb77a-125">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-125">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  

2. <span data-ttu-id="fb77a-126">在 **加入產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fb77a-126">In the **Add Generated Items** dialog box, do the following:</span></span>  


   |    <span data-ttu-id="fb77a-127">使用</span><span class="sxs-lookup"><span data-stu-id="fb77a-127">Use this</span></span>    |           <span data-ttu-id="fb77a-128">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="fb77a-128">To do this</span></span>            |
   |----------------|---------------------------------|
   | <span data-ttu-id="fb77a-129">**類別**</span><span class="sxs-lookup"><span data-stu-id="fb77a-129">**Categories**</span></span> |     <span data-ttu-id="fb77a-130">按一下 **新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-130">Click **Add Adapter**.</span></span>      |
   | <span data-ttu-id="fb77a-131">**範本**</span><span class="sxs-lookup"><span data-stu-id="fb77a-131">**Templates**</span></span>  | <span data-ttu-id="fb77a-132">按一下 **新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-132">Click **Add Adapter Metadata**.</span></span> |


3. <span data-ttu-id="fb77a-133">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-133">Click **Add**.</span></span> <span data-ttu-id="fb77a-134">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fb77a-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  

4. <span data-ttu-id="fb77a-135">在 [新增配接器精靈] 中，選取**WCF-SAP**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-135">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="fb77a-136">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb77a-136">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="fb77a-137">如果您已經在 BizTalk 中設定的 WCF SAP 連接埠，請選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="fb77a-137">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  

5. <span data-ttu-id="fb77a-138">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fb77a-138">Click **Next**.</span></span>  

6. <span data-ttu-id="fb77a-139">在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**sapBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  

7. <span data-ttu-id="fb77a-140">中**設定介面卡** 對話方塊中，按一下**安全性** 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-140">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  

8. <span data-ttu-id="fb77a-141">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="fb77a-141">Click **OK**.</span></span>  

## <a name="enter-client-credentials-at-run-time"></a><span data-ttu-id="fb77a-142">在執行階段輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="fb77a-142">Enter client credentials at run time</span></span>  
 <span data-ttu-id="fb77a-143">執行階段，您可以指定用戶端認證中的 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fb77a-143">For run time, you can specify the client credentials as part of the WCF-Custom or WCF-SAP port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="fb77a-144">WCF 自訂連接埠輸入認證</span><span class="sxs-lookup"><span data-stu-id="fb77a-144">Enter credentials for the WCF-Custom port</span></span>  

1. <span data-ttu-id="fb77a-145">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fb77a-145">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="fb77a-146">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-146">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="fb77a-147">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fb77a-147">In the right pane, you can choose to create a port or select an existing port.</span></span>  

3. <span data-ttu-id="fb77a-148">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-148">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="fb77a-149">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-149">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

4. <span data-ttu-id="fb77a-150">傳送埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fb77a-150">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="fb77a-151">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-151">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  

   -   <span data-ttu-id="fb77a-152">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="fb77a-152">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

5. <span data-ttu-id="fb77a-153">接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fb77a-153">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  

   -   <span data-ttu-id="fb77a-154">選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-154">Select **User account** option, and specify the user name and password to connect to an SAP system.</span></span>  

   -   <span data-ttu-id="fb77a-155">選取 **取得認證，從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb77a-155">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  

6. <span data-ttu-id="fb77a-156">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="fb77a-156">Click **OK**.</span></span>  

### <a name="enter-credentials-for-the-wcf-sap-port"></a><span data-ttu-id="fb77a-157">輸入認證的 WCF SAP 連接埠</span><span class="sxs-lookup"><span data-stu-id="fb77a-157">Enter credentials for the WCF-SAP port</span></span>  

1. <span data-ttu-id="fb77a-158">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fb77a-158">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

2. <span data-ttu-id="fb77a-159">新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fb77a-159">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="fb77a-160">如需相關指示，請參閱 < [SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="fb77a-160">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  

3. <span data-ttu-id="fb77a-161">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-161">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="fb77a-162">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fb77a-162">In the right pane, you can choose to create a port or select an existing port.</span></span>  

4. <span data-ttu-id="fb77a-163">在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增的 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-163">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="fb77a-164">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fb77a-164">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  

5. <span data-ttu-id="fb77a-165">如果您要建立傳送埠，在傳輸屬性對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fb77a-165">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  

   1.  <span data-ttu-id="fb77a-166">選取 **不會使用單一登入**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-166">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.</span></span>  

   2.  <span data-ttu-id="fb77a-167">選取 **使用單一登入**選項，並指定分支機構應用程式企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="fb77a-167">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  

6. <span data-ttu-id="fb77a-168">如果您要建立接收埠，在**Wcf-custom 傳輸屬性** 對話方塊中，按一下**其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fb77a-168">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  

   1.  <span data-ttu-id="fb77a-169">選取 **使用者帳戶**選項，並指定使用者名稱和密碼來連線到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-169">Select **User account** option, and specify the user name and password to connect to the SAP system.</span></span>  

   2.  <span data-ttu-id="fb77a-170">選取 **取得認證，從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb77a-170">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  

7. <span data-ttu-id="fb77a-171">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="fb77a-171">Click **OK**.</span></span>  

> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="fb77a-172"> 也支援 「 企業單一登入 (SSO) 系統。</span><span class="sxs-lookup"><span data-stu-id="fb77a-172"> also supports the Enterprise Single Sign-On (SSO) system.</span></span> <span data-ttu-id="fb77a-173">SSO 選項只適用於 BizTalk 案例中，在其中[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]所知的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb77a-173">SSO is only applicable in the BizTalk scenario, in which the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] is aware of SSO affiliate applications.</span></span> <span data-ttu-id="fb77a-174">如需安全性相對於 BizTalk Server 的詳細資訊，請參閱[SAP 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fb77a-174">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb77a-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb77a-175">See Also</span></span>  
[<span data-ttu-id="fb77a-176">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="fb77a-176">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)