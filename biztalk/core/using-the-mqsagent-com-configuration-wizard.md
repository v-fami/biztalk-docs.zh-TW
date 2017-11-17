---
title: "使用 MQSAgent COM + 組態精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mqsagent.wizard
helpviewer_keywords:
- MQSeries adapters, MQSAgent COM+ Configuration Wizard
- configuring [MQSeries adapters], MQSAgent COM+ Configuration Wizard
- MQSAgent COM+ Configuration Wizard
ms.assetid: f106700a-7f57-4c83-9344-6525fc10544d
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6262b87f304a27b36ed1d7bc6a15b5e681331be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-mqsagent-com-configuration-wizard"></a><span data-ttu-id="81270-102">使用 MQSAgent COM + 組態精靈</span><span class="sxs-lookup"><span data-stu-id="81270-102">Using the MQSAgent COM+ Configuration Wizard</span></span>
<span data-ttu-id="81270-103">[MQSAgent COM+ 組態精靈] 可以設定 MQSAgent、配接器的 COM+ 應用程式 (MQSeries 元件) 部分。</span><span class="sxs-lookup"><span data-stu-id="81270-103">The MQSAgent COM+ Configuration Wizard configures the MQSAgent, the COM+ application (MQSeries component) part of the adapter.</span></span> <span data-ttu-id="81270-104">精靈會設定元件的應用程式識別，以及角色中包含的角色名稱和使用者。</span><span class="sxs-lookup"><span data-stu-id="81270-104">The wizard sets the application identity of the component, and the role name and users included in the role.</span></span> <span data-ttu-id="81270-105">使用 MQSAgent COM + 組態精靈所建立的 MQSAgent COM + 元件的名稱是**MQSAgent2**。</span><span class="sxs-lookup"><span data-stu-id="81270-105">The name of the MQSAgent COM+ component created with the MQSAgent COM+ Configuration Wizard is **MQSAgent2**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81270-106">64 位元 Windows server 支援 MQSAgent COM + 應用程式。</span><span class="sxs-lookup"><span data-stu-id="81270-106">The MQSAgent COM+ application is supported on a 64-bit Windows server.</span></span> <span data-ttu-id="81270-107">它會以 32 位元處理序在 WOW64 下執行。</span><span class="sxs-lookup"><span data-stu-id="81270-107">It will run as a 32-bit process under WOW64.</span></span> <span data-ttu-id="81270-108">在 64 位元版本的 Windows Server 上執行的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦可以和已安裝 MQSAgent 的遠端 32 位元電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="81270-108">A [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-based computer that is running on a 64-bit version of Windows Server can communicate with a remote 32-bit computer that has the MQSAgent installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81270-109">MQSeries 代理程式與 MQSAgent COM + 組態精靈執行檔**MQSConfigWiz.exe**不會安裝，如果您從 BizTalk Server 2009 到[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81270-109">The MQSeries Agent and the MQSAgent COM+ Configuration Wizard executable **MQSConfigWiz.exe** are not installed if you upgrade from BizTalk Server 2009 to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="81270-110">升級到之後[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]從 BizTalk Server 2009 重新執行安裝程式中，選取**修改**選項，然後選取要安裝這些元件的其他軟體在 MQSeries 代理程式。</span><span class="sxs-lookup"><span data-stu-id="81270-110">After upgrading to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] from BizTalk Server 2009 re-run setup, select the **Modify** option, and select the MQSeries Agent under the Additional Software to install these components.</span></span>  
  
## <a name="to-set-the-application-identity"></a><span data-ttu-id="81270-111">設定應用程式識別</span><span class="sxs-lookup"><span data-stu-id="81270-111">To set the application identity</span></span>  
  
-   <span data-ttu-id="81270-112">使用**應用程式識別**MQSAgent COM + 組態精靈，如下所示設定 MQSAgent 的應用程式識別頁面：</span><span class="sxs-lookup"><span data-stu-id="81270-112">Use the **Application Identity** page of the MQSAgent COM+ Configuration Wizard to set the application identity for the MQSAgent as follows:</span></span>  
  
    |<span data-ttu-id="81270-113">使用</span><span class="sxs-lookup"><span data-stu-id="81270-113">Use this</span></span>|<span data-ttu-id="81270-114">動作</span><span class="sxs-lookup"><span data-stu-id="81270-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="81270-115">**互動式的使用者**</span><span class="sxs-lookup"><span data-stu-id="81270-115">**Interactive User**</span></span>|<span data-ttu-id="81270-116">選取此選項以使用應用程式識別目前的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="81270-116">Select this option to use the current logon account for the application identity.</span></span>|  
    |<span data-ttu-id="81270-117">**本機服務**</span><span class="sxs-lookup"><span data-stu-id="81270-117">**Local Service**</span></span>|<span data-ttu-id="81270-118">將應用程式識別設定為內建服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="81270-118">Set the application identity to a built-in service account.</span></span>|  
    |<span data-ttu-id="81270-119">**網路服務**</span><span class="sxs-lookup"><span data-stu-id="81270-119">**Network Service**</span></span>|<span data-ttu-id="81270-120">將應用程式識別設定為具有網路存取的內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="81270-120">Set the application identity to a built-in account with network access.</span></span>|  
    |<span data-ttu-id="81270-121">**此使用者**</span><span class="sxs-lookup"><span data-stu-id="81270-121">**This user**</span></span>|<span data-ttu-id="81270-122">將應用程式識別設定為指示的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="81270-122">Set the application identity to the indicated user name.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="81270-123">不建議您在應用程式識別使用具有系統管理權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="81270-123">It is not recommended that you use an account with administrative permissions for the application identity.</span></span> <span data-ttu-id="81270-124">此帳戶必須具備基本的必要權限：MQSeries 佇列的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="81270-124">The account must have the minimal rights required: read and write permission for the MQSeries queues.</span></span>  
  
## <a name="to-name-the-role-and-add-users-to-it"></a><span data-ttu-id="81270-125">命名角色並將使用者加入角色中</span><span class="sxs-lookup"><span data-stu-id="81270-125">To name the role and add users to it</span></span>  
  
-   <span data-ttu-id="81270-126">使用**角色名稱**頁面 MQSAgent COM + 組態精靈，將指派的名稱和使用者角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="81270-126">Use the **Name of Role** page of the MQSAgent COM+ Configuration Wizard  to assign a name and users to the role as follows:</span></span>  
  
    |<span data-ttu-id="81270-127">使用</span><span class="sxs-lookup"><span data-stu-id="81270-127">Use this</span></span>|<span data-ttu-id="81270-128">動作</span><span class="sxs-lookup"><span data-stu-id="81270-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="81270-129">**角色名稱**</span><span class="sxs-lookup"><span data-stu-id="81270-129">**Name of role**</span></span>|<span data-ttu-id="81270-130">鍵入角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="81270-130">Type the name of the role.</span></span>|  
    |<span data-ttu-id="81270-131">**使用者**</span><span class="sxs-lookup"><span data-stu-id="81270-131">**Users**</span></span>|<span data-ttu-id="81270-132">顯示屬於角色的使用者。</span><span class="sxs-lookup"><span data-stu-id="81270-132">Display the users that belong to the role.</span></span>|  
    |<span data-ttu-id="81270-133">**加入**</span><span class="sxs-lookup"><span data-stu-id="81270-133">**Add**</span></span>|<span data-ttu-id="81270-134">新增使用者到角色中。</span><span class="sxs-lookup"><span data-stu-id="81270-134">Add users to the role.</span></span> <span data-ttu-id="81270-135">這些是使用配接器的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="81270-135">These are the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service accounts using the adapter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="81270-136">僅將要求存取配接器的帳戶新增至角色中。</span><span class="sxs-lookup"><span data-stu-id="81270-136">Add to the role only accounts requiring access to the adapter.</span></span>  
  
## <a name="to-set-the-msdtc-security-configuration-on-the-windows-server-2008-computer-to-no-authentication-required"></a><span data-ttu-id="81270-137">在 Windows Server 2008 電腦上將「MSDTC 安全性」組態設定為不需要驗證</span><span class="sxs-lookup"><span data-stu-id="81270-137">To set the MSDTC Security configuration on the Windows Server 2008 computer to No Authentication Required</span></span>  
 <span data-ttu-id="81270-138">如果 MQSAgent COM + 應用程式安裝在[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]電腦與 MQSeries 配接器 (在安裝[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]) 上安裝[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦、 上的 MSDTC 安全性組態[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦必須設為**不需要驗證**。</span><span class="sxs-lookup"><span data-stu-id="81270-138">If the MQSAgent COM+ application is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computer and the MQSeries Adapter (which is installed with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]) is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer, the MSDTC Security configuration on the [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer must be set to **No Authentication Required**.</span></span> <span data-ttu-id="81270-139">請依照以下步驟執行，將 MSDTC 安全性組態設定為 [不需要驗證]：</span><span class="sxs-lookup"><span data-stu-id="81270-139">Follow these steps to set the MSDTC security configuration to No Authentication Required:</span></span>  
  
1.  <span data-ttu-id="81270-140">按一下**啟動**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="81270-140">Click **Start** and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="81270-141">按兩下**系統管理工具**。</span><span class="sxs-lookup"><span data-stu-id="81270-141">Double-click **Administrative Tools**.</span></span>  
  
3.  <span data-ttu-id="81270-142">按兩下**元件服務**啟動**元件服務**管理介面。</span><span class="sxs-lookup"><span data-stu-id="81270-142">Double-click **Component Services** to launch the **Component Services** management interface.</span></span>  
  
4.  <span data-ttu-id="81270-143">展開**元件服務**，依序展開**電腦**，然後展開**我的電腦**。</span><span class="sxs-lookup"><span data-stu-id="81270-143">Expand **Component Services**, expand **Computers**, and then expand **My Computer**.</span></span>  
  
5.  <span data-ttu-id="81270-144">以滑鼠右鍵按一下**我的電腦**按一下**屬性**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="81270-144">Right-click **My Computer** and click the **Properties** menu item.</span></span>  
  
6.  <span data-ttu-id="81270-145">在**我的電腦**對話方塊中，按一下  **MSDTC**索引標籤，然後按一下 **安全性組態**。</span><span class="sxs-lookup"><span data-stu-id="81270-145">In the **My Computer** dialog box, click the **MSDTC** tab and then click **Security Configuration**.</span></span>  
  
7.  <span data-ttu-id="81270-146">在**安全性組態**對話方塊中，於**交易管理員通訊**區段中，選取**不需要驗證**。</span><span class="sxs-lookup"><span data-stu-id="81270-146">In the **Security Configuration** dialog box, in the **Transaction Manager Communication** section, select **No Authentication Required**.</span></span> <span data-ttu-id="81270-147">如果系統提示您使用對話方塊中，按一下**是**重新啟動 MS DTC 服務。</span><span class="sxs-lookup"><span data-stu-id="81270-147">If you are prompted with a dialog box, click **Yes** to restart the MS DTC Service.</span></span>  
  
8.  <span data-ttu-id="81270-148">MS DTC 服務已經重新啟動之後，請按一下**確定**按一下**確定** 以關閉 **我的電腦** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81270-148">After the MS DTC service has restarted, click **OK** and click **OK** again to close the **My Computer** dialog box.</span></span>  
  
9. <span data-ttu-id="81270-149">關閉**元件服務**管理介面。</span><span class="sxs-lookup"><span data-stu-id="81270-149">Close the **Component Services** management interface.</span></span>  
  
## <a name="to-configure-the-mqsagent-runtime-components-to-run-under-an-alternative-set-of-credentials"></a><span data-ttu-id="81270-150">設定 MQSAgent 執行階段元件在另一組認證上執行</span><span class="sxs-lookup"><span data-stu-id="81270-150">To configure the MQSAgent runtime components to run under an alternative set of credentials</span></span>  
 <span data-ttu-id="81270-151">MQSAgent COM+ 應用程式包含管理與執行階段的元件。</span><span class="sxs-lookup"><span data-stu-id="81270-151">The MQSAgent COM+ application includes components for both administration and runtime.</span></span> <span data-ttu-id="81270-152">如果您因為安全性考量，想要將此功能區分為不同的 COM+ 應用程式，請在安裝 MQSAgent COM+ 應用程式的電腦上依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="81270-152">If you want to separate this functionality into different COM+ applications for security purposes, follow these steps on the computer that the MQSAgent COM+ application is installed on:</span></span>  
  
1.  <span data-ttu-id="81270-153">啟用 MQSAgent COM+ 元件變更。</span><span class="sxs-lookup"><span data-stu-id="81270-153">Enable changes for the MQSAgent COM+ component.</span></span>  
  
    -   <span data-ttu-id="81270-154">按一下**啟動**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="81270-154">Click **Start** and then click **Control Panel**.</span></span>  
  
    -   <span data-ttu-id="81270-155">按兩下**系統管理工具**。</span><span class="sxs-lookup"><span data-stu-id="81270-155">Double-click **Administrative Tools**.</span></span>  
  
    -   <span data-ttu-id="81270-156">按兩下**元件服務**啟動**元件服務**管理介面。</span><span class="sxs-lookup"><span data-stu-id="81270-156">Double-click **Component Services** to launch the **Component Services** management interface.</span></span>  
  
    -   <span data-ttu-id="81270-157">展開**元件服務**，依序展開**我的電腦**，依序展開**COM + 應用程式**，以滑鼠右鍵按一下**MQSAgent2** COM + 應用程式然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="81270-157">Expand **Component Services**, expand **My Computer**, expand **COM+ Applications**, right-click the **MQSAgent2** COM+ application and then click **Properties**.</span></span>  
  
    -   <span data-ttu-id="81270-158">按一下**進階**索引標籤，然後取消核取**停用變更**。</span><span class="sxs-lookup"><span data-stu-id="81270-158">Click the **Advanced** tab and uncheck **Disable changes**.</span></span>  
  
    -   <span data-ttu-id="81270-159">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="81270-159">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="81270-160">為 MQSAgent 執行階段元件建立新的 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="81270-160">Create a new COM+ application for the MQSAgent runtime components.</span></span>  
  
    -   <span data-ttu-id="81270-161">以滑鼠右鍵按一下**COM + 應用程式**，按一下 **新增**，**應用程式**顯示**COM + 應用程式安裝精靈**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="81270-161">Right-click **COM+ Applications**, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="81270-162">按一下**建立空白的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="81270-162">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="81270-163">輸入名稱**MQSAgent2RunTime**，保留預設選項為**伺服器應用程式**啟用，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="81270-163">Enter the name **MQSAgent2RunTime**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="81270-164">選取的選項**這位使用者**，輸入適當的帳戶資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="81270-164">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="81270-165">此帳戶應該具備**連接**和**放**及/或**取得**適當的 IBM WebSphere MQ for Windows 佇列上的權限。</span><span class="sxs-lookup"><span data-stu-id="81270-165">This account should have **connect** and **put** and/or **get** permissions on the appropriate IBM WebSphere MQ for Windows queues.</span></span> <span data-ttu-id="81270-166">您可以設定此帳戶的適當權限**setmqaut**適用於 IBM WebSphere MQ 的命令。</span><span class="sxs-lookup"><span data-stu-id="81270-166">You can set the appropriate permissions for this account with the **setmqaut** command available with the IBM WebSphere MQ.</span></span> <span data-ttu-id="81270-167">如需有關**setmqaut**命令，請參閱 IBM WebSphere MQ 文件。</span><span class="sxs-lookup"><span data-stu-id="81270-167">For more information about the **setmqaut** command see the IBM WebSphere MQ documentation.</span></span>  
  
    -   <span data-ttu-id="81270-168">按一下**下一步**上**新增應用程式角色** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81270-168">Click **Next** on the **Add Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="81270-169">按一下**下一步**上**將使用者加入角色** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81270-169">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="81270-170">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="81270-170">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="81270-171">將執行階段元件移至新的 COM+ 應用程式</span><span class="sxs-lookup"><span data-stu-id="81270-171">Move the runtime components to the new COM+ application</span></span>  
  
    -   <span data-ttu-id="81270-172">展開**MQSAgent2** COM + 應用程式。</span><span class="sxs-lookup"><span data-stu-id="81270-172">Expand the **MQSAgent2** COM+ application.</span></span>  
  
    -   <span data-ttu-id="81270-173">展開**元件**。</span><span class="sxs-lookup"><span data-stu-id="81270-173">Expand **Components**.</span></span>  
  
    -   <span data-ttu-id="81270-174">以滑鼠右鍵按一下**mqsagent2.mqsagent.1**元件，再按一下**移動**顯示**移動元件 (s)**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81270-174">Right-click the **MQSAgent2.MQSAgent.1** component and click **Move** to display the **Move components(s)** dialog box.</span></span>  
  
    -   <span data-ttu-id="81270-175">選取**MQSAgent2RunTime**下**請選取目的地**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="81270-175">Select **MQSAgent2RunTime** under **Please select a destination** and click **OK**.</span></span>  
  
    -   <span data-ttu-id="81270-176">重複這些步驟**[mqsagent2.mqsbroker.1]**和**[mqsagent2.mqsproxy.1]**元件。</span><span class="sxs-lookup"><span data-stu-id="81270-176">Repeat these steps for the **MQSAgent2.MQSBroker.1** and **MQSAgent2.MQSProxy.1** components.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81270-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81270-177">See Also</span></span>  
 <span data-ttu-id="81270-178">[如何設定 MQSeries 配接器傳送和接收處理常式](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="81270-178">[How to Configure MQSeries Adapter Send and Receive Handlers](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md) </span></span>  
 [<span data-ttu-id="81270-179">設定 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="81270-179">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)