---
title: 設定登入 SAP 系統的認證 |Microsoft 文件
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
ms.openlocfilehash: 2a6ace75f66bb7fdd4cfb3362f7d019ab99d73bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217806"
---
# <a name="configure-the-sign-in-credentials-for-the-sap-system"></a><span data-ttu-id="7974f-102">設定登入 SAP 系統的認證</span><span class="sxs-lookup"><span data-stu-id="7974f-102">Configure the sign in credentials for the SAP system</span></span>
<span data-ttu-id="7974f-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]需要配接器用戶端提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="7974f-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="7974f-104">配接器使用這些認證來驗證與 SAP 系統的使用者，並建立連接。</span><span class="sxs-lookup"><span data-stu-id="7974f-104">The adapter uses these credentials to authenticate the user with the SAP system and to establish a connection.</span></span>  
  
 <span data-ttu-id="7974f-105">配接器用戶端會提供用戶端認證，這兩個設計階段或執行階段。</span><span class="sxs-lookup"><span data-stu-id="7974f-105">Adapter clients can provide the client credentials both at design time or run time.</span></span> <span data-ttu-id="7974f-106">在設計階段需要認證才能產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7974f-106">At design time, credentials are required to generate the metadata.</span></span> <span data-ttu-id="7974f-107">在執行階段，認證才能執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="7974f-107">At run time, credentials are required to perform operations on the SAP system.</span></span> <span data-ttu-id="7974f-108">本節提供在設計階段和執行的階段指定用戶端認證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7974f-108">This section provides information about specifying client credentials at design time and run time.</span></span>  
  
## <a name="enter-the-client-credentials-at-design-time"></a><span data-ttu-id="7974f-109">在設計階段中輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="7974f-109">Enter the client credentials at design time</span></span>  
 <span data-ttu-id="7974f-110">設計階段，您可以指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7974f-110">For design time, you can specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="enter-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="7974f-111">輸入使用配接器服務增益集所使用的認證</span><span class="sxs-lookup"><span data-stu-id="7974f-111">Enter credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="7974f-112">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="7974f-112">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="7974f-113">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7974f-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="7974f-114">使用</span><span class="sxs-lookup"><span data-stu-id="7974f-114">Use this</span></span>|<span data-ttu-id="7974f-115">動作</span><span class="sxs-lookup"><span data-stu-id="7974f-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7974f-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="7974f-116">**Categories**</span></span>|<span data-ttu-id="7974f-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="7974f-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="7974f-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="7974f-118">**Templates**</span></span>|<span data-ttu-id="7974f-119">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="7974f-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="7974f-120">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="7974f-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="7974f-121">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sapBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7974f-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="7974f-122">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
6.  <span data-ttu-id="7974f-123">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-123">Click **OK**.</span></span>  
  
### <a name="enter-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="7974f-124">輸入認證，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="7974f-124">Enter credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="7974f-125">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="7974f-125">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="7974f-126">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7974f-126">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="7974f-127">使用</span><span class="sxs-lookup"><span data-stu-id="7974f-127">Use this</span></span>|<span data-ttu-id="7974f-128">動作</span><span class="sxs-lookup"><span data-stu-id="7974f-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7974f-129">**類別**</span><span class="sxs-lookup"><span data-stu-id="7974f-129">**Categories**</span></span>|<span data-ttu-id="7974f-130">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="7974f-130">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="7974f-131">**範本**</span><span class="sxs-lookup"><span data-stu-id="7974f-131">**Templates**</span></span>|<span data-ttu-id="7974f-132">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="7974f-132">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="7974f-133">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-133">Click **Add**.</span></span> <span data-ttu-id="7974f-134">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7974f-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="7974f-135">在 新增配接器精靈 中，選取  **WCF SAP**。</span><span class="sxs-lookup"><span data-stu-id="7974f-135">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="7974f-136">選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="7974f-136">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7974f-137">如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="7974f-137">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="7974f-138">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="7974f-139">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**sapBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7974f-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="7974f-140">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-140">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
8.  <span data-ttu-id="7974f-141">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-141">Click **OK**.</span></span>  
  
## <a name="enter-client-credentials-at-run-time"></a><span data-ttu-id="7974f-142">在執行階段輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="7974f-142">Enter client credentials at run time</span></span>  
 <span data-ttu-id="7974f-143">執行階段，您可以指定用戶端認證中的 WCF 自訂 」 或 「 WCF SAP 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7974f-143">For run time, you can specify the client credentials as part of the WCF-Custom or WCF-SAP port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="7974f-144">WCF 自訂連接埠輸入認證</span><span class="sxs-lookup"><span data-stu-id="7974f-144">Enter credentials for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="7974f-145">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7974f-145">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="7974f-146">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="7974f-146">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="7974f-147">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7974f-147">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="7974f-148">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7974f-148">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7974f-149">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="7974f-149">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="7974f-150">傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7974f-150">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="7974f-151">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-151">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="7974f-152">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7974f-152">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="7974f-153">接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7974f-153">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="7974f-154">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-154">Select **User account** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="7974f-155">選取**取得認證從分支機構應用程式**選項，並指定分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="7974f-155">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
6.  <span data-ttu-id="7974f-156">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-156">Click **OK**.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-sap-port"></a><span data-ttu-id="7974f-157">輸入 WCF SAP 連接埠的認證</span><span class="sxs-lookup"><span data-stu-id="7974f-157">Enter credentials for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="7974f-158">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7974f-158">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="7974f-159">加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7974f-159">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="7974f-160">如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="7974f-160">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="7974f-161">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="7974f-161">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="7974f-162">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7974f-162">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="7974f-163">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7974f-163">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7974f-164">若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="7974f-164">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="7974f-165">如果您要建立傳送埠，在 [傳輸屬性] 對話方塊中，按一下**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7974f-165">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="7974f-166">選取**不會使用單一登入**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-166">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="7974f-167">選取**使用單一登入**選項，並指定分支機構企業單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7974f-167">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
6.  <span data-ttu-id="7974f-168">如果您要建立接收埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **其他**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7974f-168">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="7974f-169">選取**使用者帳戶**選項，並指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-169">Select **User account** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="7974f-170">選取**取得認證從分支機構應用程式**選項，並指定 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="7974f-170">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
7.  <span data-ttu-id="7974f-171">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7974f-171">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="7974f-172">也支援 「 企業單一登入 (SSO) 系統。</span><span class="sxs-lookup"><span data-stu-id="7974f-172"> also supports the Enterprise Single Sign-On (SSO) system.</span></span> <span data-ttu-id="7974f-173">SSO 選項只適用於 BizTalk 案例中，在其中[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]所知的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="7974f-173">SSO is only applicable in the BizTalk scenario, in which the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] is aware of SSO affiliate applications.</span></span> <span data-ttu-id="7974f-174">如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[安全性與 SAP 配接器和 BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7974f-174">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7974f-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7974f-175">See Also</span></span>  
[<span data-ttu-id="7974f-176">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="7974f-176">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)