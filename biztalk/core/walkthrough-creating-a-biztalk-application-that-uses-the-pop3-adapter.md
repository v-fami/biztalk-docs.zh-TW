---
title: "逐步解說： 建立 BizTalk 應用程式使用 POP3 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, POP3 adapters
- configuring [POP3 adapters], mailboxes
- configuring [POP3 adapters], tutorials
- POP3 adapters, mailboxes
- POP3 adapters, tutorials
- configuring [POP3 adapters], Outlook Express
ms.assetid: b44c3b1d-7b4f-425c-831a-1ce5f6379595
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e677a4fb68ad4f6991585c191c8065a60b3fc337
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter"></a><span data-ttu-id="6e051-102">逐步解說： 建立使用 POP3 配接器的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="6e051-102">Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter</span></span>
<span data-ttu-id="6e051-103">本節將帶領您使用 POP3 配接器來建立簡單的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e051-103">This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application using the POP3 adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e051-104">此應用程式假設您可以存取執行 Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 且已安裝與設定電子郵件服務的電腦。</span><span class="sxs-lookup"><span data-stu-id="6e051-104">The application assumes that you have access to a computer running Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services installed and configured.</span></span> <span data-ttu-id="6e051-105">如需設定具備電子郵件服務的 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 之相關資訊，請參閱 Windows Server 說明。</span><span class="sxs-lookup"><span data-stu-id="6e051-105">For information about configuring [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services see Windows Server Help.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e051-106">在此範例中，將使用 Microsoft Outlook Express 做為電子郵件用戶端，而 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 則做為電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="6e051-106">In this example Microsoft Outlook Express is used as the e-mail client and [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] is used as the e-mail server.</span></span> <span data-ttu-id="6e051-107">不過，任何 POP3 電子郵件用戶端與 RFC 相容 POP3 伺服器皆可以用於此實例。</span><span class="sxs-lookup"><span data-stu-id="6e051-107">However, any POP3 e-mail client and RFC-compliant POP3 server could be used for this scenario.</span></span>  
  
 <span data-ttu-id="6e051-108">此應用程式假設您尚未建立任何傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="6e051-108">This application assumes that you have not yet created any send ports or receive locations.</span></span> <span data-ttu-id="6e051-109">若您有現有的傳送埠或接收位置，當逐步進行這些步驟時請以適當的名稱來替代。</span><span class="sxs-lookup"><span data-stu-id="6e051-109">If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.</span></span>  
  
 <span data-ttu-id="6e051-110">此應用程式是一個簡單以內容為基礎的路由應用程式，只使用一個接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6e051-110">The application is a simple content-based routing application using only a receive location and a send port.</span></span> <span data-ttu-id="6e051-111">從執行的伺服器上的信箱讀取接收位置[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)](「 Windows 伺服器 」\)。</span><span class="sxs-lookup"><span data-stu-id="6e051-111">The receive location reads from a mailbox on the server running [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]("the Windows server"\).</span></span> <span data-ttu-id="6e051-112">傳送埠會從接收位置拾取訊息，然後將訊息傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之本機檔案系統上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e051-112">The send port takes the message from the receive location and sends it to a folder on the local file system of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6e051-113">若要建立應用程式，您必須建立信箱、設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和傳送埠、啟動傳送埠與啟用接收位置，以及傳送測試訊息到信箱。</span><span class="sxs-lookup"><span data-stu-id="6e051-113">To create the application, you have to create the mailbox, set up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port, start the send port and enable the receive location, and send a test message to the mailbox.</span></span> <span data-ttu-id="6e051-114">請遵循下列步驟來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e051-114">Follow the steps below to create the application.</span></span>  
  
## <a name="create-a-mailbox-on-windows-server-2003"></a><span data-ttu-id="6e051-115">在 Windows Server 2003 上建立信箱</span><span class="sxs-lookup"><span data-stu-id="6e051-115">Create a mailbox on Windows Server 2003</span></span>  
 <span data-ttu-id="6e051-116">若要在已安裝「電子郵件服務」的 Windows Server 2003 上安裝信箱，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6e051-116">To create a mailbox on Windows Server 2003 with Email Services installed, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6e051-117">按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下  **POP3 服務**。</span><span class="sxs-lookup"><span data-stu-id="6e051-117">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **POP3 Service**.</span></span>  
  
2.  <span data-ttu-id="6e051-118">展開 *\<servername\>*  ，按一下您想要建立信箱的網域。</span><span class="sxs-lookup"><span data-stu-id="6e051-118">Expand *\<servername\>* and click the domain where you would like to create a mailbox.</span></span>  
  
3.  <span data-ttu-id="6e051-119">在**POP3 服務**對話方塊中的，在右窗格中，按一下**新增信箱**選項。</span><span class="sxs-lookup"><span data-stu-id="6e051-119">In the **POP3 Service** dialog box, in the right pane, click the **Add Mailbox** option.</span></span>  
  
4.  <span data-ttu-id="6e051-120">在**新增信箱**對話方塊中，於**信箱名稱**方塊中，輸入**EmailTest**。</span><span class="sxs-lookup"><span data-stu-id="6e051-120">In the **Add Mailbox** dialog box, in the **Mailbox Name** box, type **EmailTest**.</span></span>  
  
5.  <span data-ttu-id="6e051-121">選取**建立關聯的使用者為此信箱**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6e051-121">Select the **Create associated user for this mailbox** check box.</span></span>  
  
6.  <span data-ttu-id="6e051-122">在**密碼**和**確認密碼** 方塊中，輸入密碼，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6e051-122">In the **Password** and **Confirm Password** boxes, type a password, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="6e051-123">請記下**帳戶名稱**和**郵件伺服器**登入使用純文字驗證中所顯示的資訊**POP3 服務**對話方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6e051-123">Make a note of the **Account name** and **Mail Server** log on information displayed for use with clear text authentication in the **POP3 Service** dialog box, and then click **OK**.</span></span> <span data-ttu-id="6e051-124">您以 POP3 傳輸類型設定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置將會使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="6e051-124">This information will be used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location that you configure with the POP3 transport type.</span></span>  
  
## <a name="create-the-receive-location"></a><span data-ttu-id="6e051-125">建立接收位置</span><span class="sxs-lookup"><span data-stu-id="6e051-125">Create the receive location</span></span>  
 <span data-ttu-id="6e051-126">請遵循下列步驟來建立接收位置：</span><span class="sxs-lookup"><span data-stu-id="6e051-126">Follow these steps to create the receive location:</span></span>  
  
1.  <span data-ttu-id="6e051-127">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中按兩下預設的資料庫 **\<**  *machine_name***\>。BizTalkMgmtDb.dbo**，其中*machine_name*是您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6e051-127">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console double-click the default database **\<***machine_name***\>.BizTalkMgmtDb.dbo**, where *machine_name* is the name of your computer.</span></span> <span data-ttu-id="6e051-128">按一下**應用程式**，然後按一下  **BizTalk.Application.1**。</span><span class="sxs-lookup"><span data-stu-id="6e051-128">Click **Applications**, then click **BizTalk.Application.1**.</span></span>  
  
2.  <span data-ttu-id="6e051-129">以滑鼠右鍵按一下**接收埠**，按一下 **新增**，按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6e051-129">Right-click **Receive Ports**, click **New**, click **One-way receive port**.</span></span>  
  
3.  <span data-ttu-id="6e051-130">在**接收埠屬性**對話方塊中，於**名稱**方塊中，輸入**POP3Receive**。</span><span class="sxs-lookup"><span data-stu-id="6e051-130">In the **Receive Port Properties** dialog box, in the **Name** box, type **POP3Receive**.</span></span>  
  
4.  <span data-ttu-id="6e051-131">按一下**接收位置**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="6e051-131">Click **Receive Locations**, and then click **New**.</span></span>  <span data-ttu-id="6e051-132">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**POP3Receive**。</span><span class="sxs-lookup"><span data-stu-id="6e051-132">In the **Receive Location Properties** dialog box, in the **Name** box, type **POP3Receive**.</span></span>  
  
5.  <span data-ttu-id="6e051-133">在**傳輸類型**方塊中，選取**POP3**。</span><span class="sxs-lookup"><span data-stu-id="6e051-133">In the **Transport Type** box, select **POP3**.</span></span>  
  
6.  <span data-ttu-id="6e051-134">在**接收處理常式**方塊中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="6e051-134">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
7.  <span data-ttu-id="6e051-135">在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="6e051-135">In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
8.  <span data-ttu-id="6e051-136">在**傳輸**方塊中，按一下**設定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e051-136">In the **Transport** box, click the **Configure** button.</span></span>  
  
9. <span data-ttu-id="6e051-137">在**POP3 傳輸屬性**對話方塊中，於**套用 MIME 解碼**方塊中，選取**False**。</span><span class="sxs-lookup"><span data-stu-id="6e051-137">In the **POP3 Transport Properties** dialog box, in the **Apply MIME Decoding** box, select **False**.</span></span>  
  
10. <span data-ttu-id="6e051-138">在**郵件伺服器**方塊中，輸入您在其中建立信箱之 Windows Server 型的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e051-138">In the **Mail Server** box, type the name of the Windows Server-based server where you created a mailbox.</span></span>  
  
11. <span data-ttu-id="6e051-139">在**驗證配置**方塊中，選取**基本**。</span><span class="sxs-lookup"><span data-stu-id="6e051-139">In the **Authentication Scheme** box, select **Basic**.</span></span>  
  
12. <span data-ttu-id="6e051-140">在**密碼**，按一下下拉箭號，然後輸入信箱的密碼。</span><span class="sxs-lookup"><span data-stu-id="6e051-140">In the **Password** box, click the drop-down arrow and type the password for the mailbox.</span></span>  
  
13. <span data-ttu-id="6e051-141">在**使用者名**方塊中，輸入信箱的完整格式的使用者名稱，例如 *username@host.domain.toplevel_domain。*</span><span class="sxs-lookup"><span data-stu-id="6e051-141">In the **User Name** box, type the fully qualified user name for the mailbox, for example *username@host.domain.toplevel_domain.*</span></span>  
  
14. <span data-ttu-id="6e051-142">在**輪詢間隔**方塊中，輸入**1**，按一下**確定**，然後按一下  **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="6e051-142">In the **Polling Interval** box, type **1**, click **OK**, and then click **OK** again.</span></span>  
  
## <a name="create-the-send-port-and-destination-folder-on-the-biztalk-server"></a><span data-ttu-id="6e051-143">在 BizTalk 伺服器上建立傳送埠與目的地資料夾</span><span class="sxs-lookup"><span data-stu-id="6e051-143">Create the send port and destination folder on the BizTalk server</span></span>  
 <span data-ttu-id="6e051-144">請遵循下列步驟，在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上建立傳送埠與目的資料夾：</span><span class="sxs-lookup"><span data-stu-id="6e051-144">Follow these steps to create the send port and destination folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="6e051-145">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 檔案系統上建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e051-145">Create a folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] file system.</span></span> <span data-ttu-id="6e051-146">這將是傳送埠的目的地。</span><span class="sxs-lookup"><span data-stu-id="6e051-146">This will be the destination for the send port.</span></span>  
  
2.  <span data-ttu-id="6e051-147">以滑鼠右鍵按一下**傳送埠**，按一下 **新增**然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="6e051-147">Right-click **Send Ports**, click **New,** then click **Static one-way Send Port.**</span></span>  
  
3.  <span data-ttu-id="6e051-148">在**傳送埠屬性**對話方塊中，於**傳輸類型**方塊中，選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="6e051-148">In the **Send Port Properties** dialog box, in the **Transport Type** box, select **FILE**.</span></span>  
  
4.  <span data-ttu-id="6e051-149">在**名稱**方塊中，輸入**SendToFile**。</span><span class="sxs-lookup"><span data-stu-id="6e051-149">In the **Name** box, type **SendToFile**.</span></span>  
  
5.  <span data-ttu-id="6e051-150">在**傳輸**方塊中，按一下**設定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e051-150">In the **Transport** box, click the **Configure** button.</span></span>  
  
6.  <span data-ttu-id="6e051-151">旁邊**目的地資料夾**方塊中，按一下**瀏覽**，選取您在建立的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下  **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e051-151">Next to the **Destination folder** box, click **Browse**, select the folder that you created on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="6e051-152">在**檔案名稱**方塊中，輸入**%MessageID%.txt**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6e051-152">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="6e051-153">在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="6e051-153">In the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
9. <span data-ttu-id="6e051-154">按一下 **[篩選]**。</span><span class="sxs-lookup"><span data-stu-id="6e051-154">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="6e051-155">在**屬性**方塊中，選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="6e051-155">In the **Property** box, select **BTS.ReceivePortName**.</span></span>  
  
11. <span data-ttu-id="6e051-156">在**值**方塊中，輸入**POP3Receive**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6e051-156">In the **Value** box, type **POP3Receive**, and then click **OK**.</span></span>  
  
## <a name="enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="6e051-157">啟用接收位置並啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="6e051-157">Enable the receive location and start the send port</span></span>  
 <span data-ttu-id="6e051-158">請依照以下步驟執行，啟用接收位置和啟動傳送埠：</span><span class="sxs-lookup"><span data-stu-id="6e051-158">Follow these steps to enable the receive location and start the send port:</span></span>  
  
1.  <span data-ttu-id="6e051-159">以滑鼠右鍵按一下**POP3Receive**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="6e051-159">Right-click the **POP3Receive** receive location, and then click **Enable**.</span></span>  
  
2.  <span data-ttu-id="6e051-160">以滑鼠右鍵按一下**SendToFile**傳送埠，然後**啟動**。</span><span class="sxs-lookup"><span data-stu-id="6e051-160">Right-click the **SendToFile** send port, and then click **Start**.</span></span>  
  
 <span data-ttu-id="6e051-161">下一個步驟會傳送測試訊息到接收位置監控的信箱來測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e051-161">The next step is to test the application by sending a test message to the mailbox monitored by the receive location.</span></span>  
  
## <a name="configure-outlook-express-to-send-an-e-mail-message-to-the-mailbox"></a><span data-ttu-id="6e051-162">設定 Outlook Express 以傳送一封電子郵件到信箱</span><span class="sxs-lookup"><span data-stu-id="6e051-162">Configure Outlook Express to send an e-mail message to the mailbox</span></span>  
 <span data-ttu-id="6e051-163">請遵循下列步驟設定 Outlook Express，將電子郵件訊息傳送至信箱：</span><span class="sxs-lookup"><span data-stu-id="6e051-163">Follow these steps to configure Outlook Express to send an e-mail message to the mailbox:</span></span>  
  
1.  <span data-ttu-id="6e051-164">按一下**啟動**，指向 **程式**，然後按一下  **Outlook Express**。</span><span class="sxs-lookup"><span data-stu-id="6e051-164">Click **Start**, point to **Programs**, and then click **Outlook Express**.</span></span>  
  
2.  <span data-ttu-id="6e051-165">在 Outlook Express 中，在**工具**功能表上，按一下 **帳戶**。</span><span class="sxs-lookup"><span data-stu-id="6e051-165">In Outlook Express, on the **Tools** menu, click **Accounts**.</span></span>  
  
3.  <span data-ttu-id="6e051-166">按一下**新增**，然後按一下 **郵件**。</span><span class="sxs-lookup"><span data-stu-id="6e051-166">Click **Add** and then click **Mail**.</span></span>  
  
4.  <span data-ttu-id="6e051-167">在**顯示名稱**方塊中輸入顯示名稱，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e051-167">In the **Display name** box, type a display name, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="6e051-168">在**網際網路電子郵件地址**對話方塊中，於**電子郵件地址**方塊中，輸入**EmailTest @< 網域名稱 >**，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="6e051-168">In the **Internet E-mail address** dialog box, in the **E-mail address** box, type **EmailTest@<domain_name>**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6e051-169">請務必輸入適當的值給*< 網域名稱 >*。</span><span class="sxs-lookup"><span data-stu-id="6e051-169">Make sure to enter the appropriate value for *<domain_name>*.</span></span> <span data-ttu-id="6e051-170">這個值應該符合在 Windows 伺服器上的 POP3 服務管理介面中建立此信箱時所依據的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6e051-170">This value should match the name of the domain under which this mailbox was created in the POP3 Service Administration interface on the Windows server.</span></span>  
  
6.  <span data-ttu-id="6e051-171">在**電子郵件伺服器名稱**對話方塊中，於**內送郵件**和**外寄郵件**] 方塊中，輸入伺服器名稱或 Windows server 的 IP 位址，然後按一下 [ **下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e051-171">In the **E-mail Server names** dialog box, in the **Incoming mail** and **Outgoing mail** boxes, type the server name or IP address of the Windows server, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="6e051-172">在**網際網路郵件登入**對話方塊中，於**帳戶名稱**方塊中，輸入**EmailTest**。</span><span class="sxs-lookup"><span data-stu-id="6e051-172">In the **Internet Mail Logon** dialog box, in the **Account name** box, type **EmailTest**.</span></span>  
  
8.  <span data-ttu-id="6e051-173">在**密碼**方塊中，輸入 EmailTest 帳戶密碼，選取**記住密碼**選項，請按一下**下一步**，然後按一下 **完成**.</span><span class="sxs-lookup"><span data-stu-id="6e051-173">In the **Password** box, type the password for the EmailTest account, select the **Remember password** option, click **Next**, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="6e051-174">按一下以選取您剛才建立的帳戶，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6e051-174">Click to select the account that you just created, and then click **Properties**.</span></span>  
  
10. <span data-ttu-id="6e051-175">在**屬性**對話方塊中，按一下**進階**] 索引標籤中，按一下以選取選項以**保留訊息的複本伺服器上**，然後按一下 [**確定**.</span><span class="sxs-lookup"><span data-stu-id="6e051-175">In the **Properties** dialog box, click the **Advanced** tab, click to select the option to **Leave a copy of messages on the server**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="6e051-176">在**網際網路帳戶**對話方塊中，按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="6e051-176">In the **Internet Accounts** dialog box, click **Close**.</span></span>  
  
12. <span data-ttu-id="6e051-177">使用 Outlook Express 來編輯測試訊息，型別**測試**到**主旨** 欄位中，然後輸入**EmailTest @< 網域名稱 >**到**至**欄位。</span><span class="sxs-lookup"><span data-stu-id="6e051-177">Use Outlook Express to compose a test message, type **Test** into the **Subject** field, and type **EmailTest@<domain_name>** into the **To** field.</span></span>  
  
13. <span data-ttu-id="6e051-178">按一下**傳送**傳送測試訊息。</span><span class="sxs-lookup"><span data-stu-id="6e051-178">Click **Send** to send the test message.</span></span> <span data-ttu-id="6e051-179">若要確定可 Outlook Express 會測試訊息傳送立即，**傳送/接收**Outlook Express 工具列中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e051-179">To ensure that Outlook Express sends the test message immediately, click the **Send/Recv** button in the Outlook Express toolbar.</span></span>  
  
## <a name="view-the-message"></a><span data-ttu-id="6e051-180">檢視訊息</span><span class="sxs-lookup"><span data-stu-id="6e051-180">View the message</span></span>  
 <span data-ttu-id="6e051-181">請依照以下步驟執行來檢視訊息：</span><span class="sxs-lookup"><span data-stu-id="6e051-181">Follow these steps to view the message:</span></span>  
  
1.  <span data-ttu-id="6e051-182">使用 Windows 檔案總管開啟資料夾指定為**目的地資料夾**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6e051-182">Use Windows Explorer to open the folder that you specified as the **Destination Folder** for the send port.</span></span>  
  
2.  <span data-ttu-id="6e051-183">按兩下資料夾中的文件，在 [記事本] 中檢視文件的內容。</span><span class="sxs-lookup"><span data-stu-id="6e051-183">Double click the document in the folder to view the contents of the document in Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e051-184">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e051-184">See Also</span></span>  
 [<span data-ttu-id="6e051-185">何謂 POP3 配接器？</span><span class="sxs-lookup"><span data-stu-id="6e051-185">What Is the POP3 Adapter?</span></span>](../core/what-is-the-pop3-adapter.md)