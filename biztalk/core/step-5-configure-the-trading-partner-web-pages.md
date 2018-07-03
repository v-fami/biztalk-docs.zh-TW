---
title: 步驟 5： 設定交易夥伴網頁 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38c3054d-932a-42b6-a821-8b30604d8426
caps.latest.revision: 38
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd0a9be1a7df1b506c169935d12b7636155615c1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001191"
---
# <a name="step-5-configure-the-trading-partner-web-pages"></a><span data-ttu-id="8885e-102">步驟 5： 設定交易夥伴網頁</span><span class="sxs-lookup"><span data-stu-id="8885e-102">Step 5: Configure the Trading Partner Web Pages</span></span>
<span data-ttu-id="8885e-103">![步驟 5 的 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")</span><span class="sxs-lookup"><span data-stu-id="8885e-103">![Step 5 of 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")</span></span>  
  
 <span data-ttu-id="8885e-104">在此步驟中，您會執行下列工作來設定交易夥伴網頁：</span><span class="sxs-lookup"><span data-stu-id="8885e-104">In this step, you perform the following tasks to set up trading partner Web pages:</span></span>  
  
-   <span data-ttu-id="8885e-105">啟用 HTTP 傳輸所需的 BTS HTTP 接收 ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="8885e-105">Enable the BTS HTTP Receive ISAPI filter that is required for HTTP transport.</span></span>  
  
-   <span data-ttu-id="8885e-106">設定資料夾及 aspx 頁，使用 HTTP 傳輸將 997 通知傳送至夥伴組織 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="8885e-106">Set up a folder and an aspx page to route the 997 acknowledgment to the partner organization Fabrikam using HTTP transport.</span></span> <span data-ttu-id="8885e-107">Fabrikam 虛擬目錄會卸除到 997 通知\\_997ToFabrikam 資料夾，在 997 傳送埠的 Destination_URL 設定中叫出。</span><span class="sxs-lookup"><span data-stu-id="8885e-107">The Fabrikam virtual directory drops the 997 acknowledgment into the \\_997ToFabrikam folder, which is called out in the Destination_URL setting of the 997 send port.</span></span>  
  
-   <span data-ttu-id="8885e-108">設定 ASPX 頁將原始訊息傳送至主要組織 Contoso。</span><span class="sxs-lookup"><span data-stu-id="8885e-108">Set up the ASPX page to route the original message to the home organization Contoso.</span></span> <span data-ttu-id="8885e-109">Contoso 虛擬目錄會使用 BTSHttpReceive.dll 接收 AS2 訊息，並將它提交至接收位置。</span><span class="sxs-lookup"><span data-stu-id="8885e-109">The Contoso virtual directory uses BTSHttpReceive.dll to receive the AS2 message and submit it to the receive location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8885e-110">本主題提供的程序是有關於 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="8885e-110">The procedures provided in this topic are for IIS 7.0.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8885e-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="8885e-111">Prerequisites</span></span>  
 <span data-ttu-id="8885e-112">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="8885e-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-enable-the-bts-isapi-filter"></a><span data-ttu-id="8885e-113">若要啟用 BTS ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="8885e-113">To enable the BTS ISAPI Filter</span></span>  
  
1. <span data-ttu-id="8885e-114">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="8885e-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2. <span data-ttu-id="8885e-115">選取根 Web 伺服器項目並在**功能檢視**，按兩下**處理常式對應**，然後在**動作**窗格中，按一下 **新增指令碼對應**.</span><span class="sxs-lookup"><span data-stu-id="8885e-115">Select the root Web server entry and in the **Features View**, double-click **Handler Mappings** and then in the **Actions** pane, click **Add Script Map**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8885e-116">在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。</span><span class="sxs-lookup"><span data-stu-id="8885e-116">Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites.</span></span> <span data-ttu-id="8885e-117">若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8885e-117">If you wish to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.</span></span>  
  
3. <span data-ttu-id="8885e-118">在 **新增指令碼對應**對話方塊方塊中，輸入`BtsHttpReceive.dll`中**要求路徑**欄位。</span><span class="sxs-lookup"><span data-stu-id="8885e-118">In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.</span></span>  
  
4. <span data-ttu-id="8885e-119">在 **可執行檔**欄位中，按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="8885e-119">In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span> <span data-ttu-id="8885e-120">選取  **BtsHttpReceive.dll**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8885e-120">Select **BtsHttpReceive.dll**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="8885e-121">請輸入`BizTalk HTTP Receive`中`Name`欄位，，然後按一下**要求限制**。</span><span class="sxs-lookup"><span data-stu-id="8885e-121">Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.</span></span>  
  
6. <span data-ttu-id="8885e-122">在 **要求限制**對話方塊中，選取**動詞**索引標籤，然後選取**其中一個下列的指令動詞**。</span><span class="sxs-lookup"><span data-stu-id="8885e-122">In the **Request Restrictions** dialog box, select the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="8885e-123">輸入`POST`作為動詞。</span><span class="sxs-lookup"><span data-stu-id="8885e-123">Enter `POST` as the verb.</span></span>  
  
7. <span data-ttu-id="8885e-124">在上**存取**索引標籤上，選取**指令碼**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8885e-124">On the **Access** tab, select **Script**, and then click **OK**.</span></span>  
  
8. <span data-ttu-id="8885e-125">按一下  **確定**當系統提示您允許 ISAPI 延伸模組時，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="8885e-125">Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
9. <span data-ttu-id="8885e-126">以滑鼠右鍵按一下 [BTSHttpReceive.dll] 項目，然後按**編輯功能權限**。</span><span class="sxs-lookup"><span data-stu-id="8885e-126">Right-click the BTSHttpReceive.dll entry, and then select **Edit Feature Permissions**.</span></span>  
  
10. <span data-ttu-id="8885e-127">請確認**讀取**，**指令碼**並**Execute**已選取，然後再按 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8885e-127">Ensure that **Read**, **Script** and **Execute** are selected, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="8885e-128">按一下 **功能檢視**，然後按兩下**ISAPI 及 CGI 限制**。</span><span class="sxs-lookup"><span data-stu-id="8885e-128">Click **Features View**, and then double-click **ISAPI and CGI Restrictions**.</span></span>  
  
12. <span data-ttu-id="8885e-129">請確認 BTSHTTPReceive.dll 項目存在，且**限制**設為**允許**。</span><span class="sxs-lookup"><span data-stu-id="8885e-129">Ensure that an entry for BTSHTTPReceive.dll exists, and that **Restriction** is set to **Allowed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8885e-130">當您建立指令碼對應時，會自動建立 BTSHTTPReceive.dll 的 [ISAPI 及 CGI 限制] 項目。</span><span class="sxs-lookup"><span data-stu-id="8885e-130">The ISAPI and CGI Restriction entry for BTSHTTPReceive.dll is created automatically when you create the script map.</span></span>  
  
### <a name="to-configure-the-fabrikam-web-page"></a><span data-ttu-id="8885e-131">若要設定 Fabrikam 網頁</span><span class="sxs-lookup"><span data-stu-id="8885e-131">To configure the Fabrikam Web page</span></span>  
  
1. <span data-ttu-id="8885e-132">在 [IIS 管理員] 中，以滑鼠右鍵按一下**應用程式集區**，然後選取**新增應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="8885e-132">In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.</span></span>  
  
2. <span data-ttu-id="8885e-133">在**新增的應用程式集區**對話方塊方塊中，輸入**BizTalkAppPool**中**名稱**，然後選取 **.NET Framework v4.0.30210**中 **.NET framework 版本**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8885e-133">In the **Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** drop-down list.</span></span> <span data-ttu-id="8885e-134">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8885e-134">Click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8885e-135">版本號碼可能會依據電腦上安裝的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8885e-135">The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.</span></span>  
  
3. <span data-ttu-id="8885e-136">選取**應用程式集區**，請在**功能檢視**選取**BizTalkAppPool**，然後按一下**進階設定**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8885e-136">Select **Application Pools**, in the **Features View** select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.</span></span>  
  
4. <span data-ttu-id="8885e-137">在 **進階設定**  對話方塊中，將**啟用 32 位元應用程式**來 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="8885e-137">In the **Advanced Settings** dialog box, set **Enable 32-Bit Applications** to **True**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8885e-138">如果您希望在 64 位元的電腦上以 32 位元模式執行 IIS，才需要此步驟。</span><span class="sxs-lookup"><span data-stu-id="8885e-138">This step is required only on a 64-bit machine if you want IIS to run in a 32-bit mode.</span></span>  
  
5. <span data-ttu-id="8885e-139">選取 **身分識別**，然後按一下 **省略符號 （...）**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="8885e-139">Select **Identity** and then click the **ellipsis (…)** button.</span></span>  
  
6. <span data-ttu-id="8885e-140">在 **應用程式集區身分識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8885e-140">In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.</span></span>  
  
7. <span data-ttu-id="8885e-141">輸入**使用者名**並**密碼**使用者帳戶，系統管理員群組的成員，請輸入中的密碼**確認密碼**，然後按一下  **確定**三次，以返回 IIS 管理員。</span><span class="sxs-lookup"><span data-stu-id="8885e-141">Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.</span></span>  
  
8. <span data-ttu-id="8885e-142">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8885e-142">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="8885e-143">以滑鼠右鍵按一下**Default Web Site**，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8885e-143">Right-click the **Default Web Site**, and then select **Add Application**.</span></span>  
  
9. <span data-ttu-id="8885e-144">在 **新增應用程式**對話方塊方塊中，輸入**Fabrikam**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="8885e-144">In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.</span></span>  
  
10. <span data-ttu-id="8885e-145">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="8885e-145">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
11. <span data-ttu-id="8885e-146">按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 tutorial\fabrikam 做為**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="8885e-146">Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam for the **Physical path**.</span></span>  
  
12. <span data-ttu-id="8885e-147">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8885e-147">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="8885e-148">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8885e-148">Click **Close**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="8885e-149">在 [IIS 管理員] 中，選取 Fabrikam 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8885e-149">In IIS Manager, select the Fabrikam virtual directory and in **Features View**, double-click **Authentication**.</span></span>  
  
14. <span data-ttu-id="8885e-150">在 **驗證**，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="8885e-150">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="8885e-151">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8885e-151">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
### <a name="to-configure-the-contoso-web-page"></a><span data-ttu-id="8885e-152">若要設定 Contoso 網頁</span><span class="sxs-lookup"><span data-stu-id="8885e-152">To configure the Contoso Web page</span></span>  
  
1. <span data-ttu-id="8885e-153">在 [IIS 管理員] 中，開啟**站台**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8885e-153">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="8885e-154">以滑鼠右鍵按一下**Default Web Site** ，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8885e-154">Right-click the **Default Web Site** and then select **Add Application**.</span></span>  
  
2. <span data-ttu-id="8885e-155">在 **新增應用程式**對話方塊方塊中，輸入**Contoso**中**別名**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="8885e-155">In the **Add Application** dialog box, enter **Contoso** in **Alias**, and then click **Select**.</span></span>  
  
3. <span data-ttu-id="8885e-156">在 **選取應用程式集區** 對話方塊中，選取**BizTalkAppPool** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="8885e-156">In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8885e-157">BizTalkAppPool 在之前設定 Fabrikam 網頁時就已建立，且應設為屬於系統管理員群組成員之使用者的識別。</span><span class="sxs-lookup"><span data-stu-id="8885e-157">The BizTalkAppPool was created previously when configuring the Fabrikam Web page, and should be set to the identity of a user that is a member of the administrators group.</span></span>  
  
4. <span data-ttu-id="8885e-158">按一下 **省略符號 （...）** 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="8885e-158">Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
5. <span data-ttu-id="8885e-159">按一下 [**測試設定**，並確認沒有顯示在錯誤**測試連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8885e-159">Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="8885e-160">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8885e-160">Click **Close**, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="8885e-161">在 [IIS 管理員] 中，選取 Contoso 虛擬目錄並在**功能檢視**，按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8885e-161">In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.</span></span>  
  
7. <span data-ttu-id="8885e-162">在 **驗證**，選取**匿名驗證**，並確認**狀態**是**已啟用**。</span><span class="sxs-lookup"><span data-stu-id="8885e-162">In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**.</span></span> <span data-ttu-id="8885e-163">如果**狀態**是**停用**，按一下 **啟用**中**動作**窗格。</span><span class="sxs-lookup"><span data-stu-id="8885e-163">If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8885e-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8885e-164">Next Steps</span></span>  
 <span data-ttu-id="8885e-165">您設定接收位置 (**Receive_AS2**) 中所述，從 Fabrikam 接收 AS2 訊息[步驟 6： 設定 EDI-AS2 接收位置](../core/step-6-configure-the-edi-as2-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="8885e-165">You configure the receive location (**Receive_AS2**) to receive the AS2 message from Fabrikam, as described in [Step 6: Configure the EDI-AS2 Receive Location](../core/step-6-configure-the-edi-as2-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8885e-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8885e-166">See Also</span></span>  
 [<span data-ttu-id="8885e-167">教學課程 3: AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="8885e-167">Tutorial 3: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)
