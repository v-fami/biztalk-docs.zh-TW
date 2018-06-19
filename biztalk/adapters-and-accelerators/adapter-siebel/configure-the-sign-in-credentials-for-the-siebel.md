---
title: 設定登入認證，siebel |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, specify credentials for the Siebel system at run time
- credentials, specifying
- how to, specify credentials for the Siebel system at design time
ms.assetid: a9fef2ba-c38e-44f7-84a3-b6a95d4dc210
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e29f79830a3b76c094ebf8b70d533bfd36218f95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223190"
---
# <a name="configure-the-sign-in-credentials-for-the-siebel"></a><span data-ttu-id="f2dab-102">設定登入認證，siebel</span><span class="sxs-lookup"><span data-stu-id="f2dab-102">Configure the sign in credentials for the Siebel</span></span>
<span data-ttu-id="f2dab-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]需要配接器用戶端提供用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="f2dab-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="f2dab-104">配接器使用這些認證來驗證具有 Siebel 系統的使用者，並建立連接。</span><span class="sxs-lookup"><span data-stu-id="f2dab-104">The adapter uses these credentials to authenticate the user with the Siebel system and to establish a connection.</span></span>  
  
 <span data-ttu-id="f2dab-105">配接器用戶端可以提供用戶端認證是在設計階段或執行階段。</span><span class="sxs-lookup"><span data-stu-id="f2dab-105">Adapter clients can provide the client credentials either at design time or run time.</span></span> <span data-ttu-id="f2dab-106">在設計階段需要認證才能產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f2dab-106">At design time, credentials are required to generate the metadata.</span></span> <span data-ttu-id="f2dab-107">在執行階段，認證才能在 Siebel 系統上執行作業。</span><span class="sxs-lookup"><span data-stu-id="f2dab-107">At run time, credentials are required to perform operations on the Siebel system.</span></span> <span data-ttu-id="f2dab-108">本節提供在設計階段和執行的階段指定用戶端認證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2dab-108">This section provides information about specifying client credentials at design time and run time.</span></span>  
  
## <a name="enter-the-client-credentials-at-design-time"></a><span data-ttu-id="f2dab-109">在設計階段中輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="f2dab-109">Enter the client credentials at design time</span></span>  
 <span data-ttu-id="f2dab-110">設計階段，您必須指定使用的認證[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f2dab-110">For design time, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="enter-client-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="f2dab-111">輸入使用配接器服務增益集所使用的用戶端認證</span><span class="sxs-lookup"><span data-stu-id="f2dab-111">Enter client credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="f2dab-112">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-112">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="f2dab-113">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f2dab-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f2dab-114">使用</span><span class="sxs-lookup"><span data-stu-id="f2dab-114">Use this</span></span>|<span data-ttu-id="f2dab-115">動作</span><span class="sxs-lookup"><span data-stu-id="f2dab-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f2dab-116">**類別**</span><span class="sxs-lookup"><span data-stu-id="f2dab-116">**Categories**</span></span>|<span data-ttu-id="f2dab-117">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="f2dab-118">**範本**</span><span class="sxs-lookup"><span data-stu-id="f2dab-118">**Templates**</span></span>|<span data-ttu-id="f2dab-119">按一下**取用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="f2dab-120">若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="f2dab-121">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**siebelBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f2dab-122">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼，以連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  
  
6.  <span data-ttu-id="f2dab-123">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-123">Click **OK**.</span></span>  
  
#### <a name="enter-client-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="f2dab-124">輸入用戶端認證，使用 新增配接器中繼資料精靈</span><span class="sxs-lookup"><span data-stu-id="f2dab-124">Enter client credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="f2dab-125">以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-125">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="f2dab-126">在**新增產生的項目**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f2dab-126">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f2dab-127">使用</span><span class="sxs-lookup"><span data-stu-id="f2dab-127">Use this</span></span>|<span data-ttu-id="f2dab-128">動作</span><span class="sxs-lookup"><span data-stu-id="f2dab-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f2dab-129">**類別**</span><span class="sxs-lookup"><span data-stu-id="f2dab-129">**Categories**</span></span>|<span data-ttu-id="f2dab-130">按一下**新增介面卡**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-130">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="f2dab-131">**範本**</span><span class="sxs-lookup"><span data-stu-id="f2dab-131">**Templates**</span></span>|<span data-ttu-id="f2dab-132">按一下**新增配接器中繼資料**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-132">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="f2dab-133">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-133">Click **Add**.</span></span> <span data-ttu-id="f2dab-134">[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f2dab-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="f2dab-135">在 新增配接器精靈 中，選取  **Wcf-siebel**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-135">In the Add Adapter Wizard, select **WCF-Siebel**.</span></span> <span data-ttu-id="f2dab-136">選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2dab-136">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f2dab-137">如果您已設定在 BizTalk Wcf-siebel 連接埠，選取從連接埠**連接埠**清單。</span><span class="sxs-lookup"><span data-stu-id="f2dab-137">If you already have a WCF-Siebel port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="f2dab-138">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f2dab-139">在**取用配接器服務**對話方塊中，從**選取繫結**清單中，選取**siebelBinding**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="f2dab-140">在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼，以連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-140">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  
  
8.  <span data-ttu-id="f2dab-141">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-141">Click **OK**.</span></span>  
  
## <a name="enter-client-credentials-at-run-time"></a><span data-ttu-id="f2dab-142">在執行階段輸入用戶端認證</span><span class="sxs-lookup"><span data-stu-id="f2dab-142">Enter client credentials at run time</span></span>  
 <span data-ttu-id="f2dab-143">執行階段，您必須指定用戶端認證中的 WCF 自訂 」 或 「 Wcf-siebel 連接埠組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f2dab-143">For run time, you must specify the client credentials as part of the WCF-Custom or WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
#### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="f2dab-144">WCF 自訂連接埠輸入認證</span><span class="sxs-lookup"><span data-stu-id="f2dab-144">Enter credentials for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="f2dab-145">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f2dab-145">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f2dab-146">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="f2dab-146">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="f2dab-147">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f2dab-147">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="f2dab-148">在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-148">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="f2dab-149">傳送埠，在**Wcf-custom 傳輸屬性**對話方塊中，按一下 **認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f2dab-149">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f2dab-150">選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-150">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
    -   <span data-ttu-id="f2dab-151">選取**使用單一登入**選項，並指定分支機構 ESSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2dab-151">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
5.  <span data-ttu-id="f2dab-152">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-152">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="f2dab-153">也支援企業單一登入 (ESSO) 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-153"> also supports the Enterprise Single Sign-On (ESSO) system.</span></span> <span data-ttu-id="f2dab-154">ESSO 僅適用於 BizTalk 案例中，WCF 配接器並知道與 ESSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2dab-154">ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications.</span></span> <span data-ttu-id="f2dab-155">如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f2dab-155">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>
  
#### <a name="enter-credentials-for-the-wcf-siebel-port"></a><span data-ttu-id="f2dab-156">輸入認證 Wcf-siebel 連接埠</span><span class="sxs-lookup"><span data-stu-id="f2dab-156">Enter credentials for the WCF-Siebel port</span></span>  
  
1.  <span data-ttu-id="f2dab-157">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f2dab-157">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f2dab-158">新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f2dab-158">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f2dab-159">如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="f2dab-159">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="f2dab-160">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="f2dab-160">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="f2dab-161">在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f2dab-161">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="f2dab-162">在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 Wcf-siebel 連接埠，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-162">In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel port you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f2dab-163">傳送埠，在傳輸屬性] 對話方塊中，按一下 [**認證**索引標籤，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f2dab-163">For a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f2dab-164">選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-164">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
    -   <span data-ttu-id="f2dab-165">選取**使用單一登入**選項，並指定分支機構 ESSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2dab-165">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
6.  <span data-ttu-id="f2dab-166">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f2dab-166">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="f2dab-167">也支援企業單一登入 (ESSO) 系統。</span><span class="sxs-lookup"><span data-stu-id="f2dab-167"> also supports the Enterprise Single Sign-On (ESSO) system.</span></span> <span data-ttu-id="f2dab-168">ESSO 僅適用於 BizTalk 案例中，WCF 配接器並知道與 ESSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2dab-168">ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications.</span></span> <span data-ttu-id="f2dab-169">如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f2dab-169">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2dab-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2dab-170">See Also</span></span>  
[<span data-ttu-id="f2dab-171">若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="f2dab-171">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)