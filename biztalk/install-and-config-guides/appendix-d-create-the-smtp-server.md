---
title: 附錄 d： 建立 SMTP 伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7441ba9-a498-42ec-a04d-7f2731407373
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f4d4acc35f5cb38be5f783ee7c4017c8ada83e2
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22300134"
---
# <a name="appendix-d-create-the-smtp-server"></a><span data-ttu-id="3cd74-102">附錄 D︰建立 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-102">Appendix D: Create the SMTP Server</span></span>
<span data-ttu-id="3cd74-103">建立 SQL Server Database Mail 所使用的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-103">Create the SMTP Server used by SQL Server Database Mail.</span></span>  
  
<span data-ttu-id="3cd74-104">使用下列任何 SQL 版本，需要有 SQL Server Database Mail 才能設定 BAM 警示：</span><span class="sxs-lookup"><span data-stu-id="3cd74-104">SQL Server Database Mail is required to configure BAM Alerts when using any of the following SQL versions:</span></span> 

* [!INCLUDE[sqlserver2016_md](../includes/sqlserver2016-md.md)]
* [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]
* [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 
  
 <span data-ttu-id="3cd74-105">SQL Server Database Mail 使用 SMTP 伺服器傳送 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="3cd74-105">SQL Server Database Mail uses an SMTP Server to send BAM Alerts.</span></span> <span data-ttu-id="3cd74-106">SMTP 伺服器隨附於網際網路資訊服務 (IIS)。</span><span class="sxs-lookup"><span data-stu-id="3cd74-106">SMTP Server is included with Internet Information Services (IIS).</span></span> <span data-ttu-id="3cd74-107">SMTP 可以安裝在本機 BizTalk Server 上，或安裝在已安裝 IIS 的另一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="3cd74-107">SMTP can be installed locally on the BizTalk Server or on another server with IIS installed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3cd74-108">一般而言，用戶端作業系統 (例如 Windows 10、Windows 7 等) 都不包含 SMTP 伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="3cd74-108">Typically, client operating systems like Windows 10, Windows 7, and so on, do not include SMTP Server capabilities.</span></span> <span data-ttu-id="3cd74-109">您可以在 IIS 內使用 [SMTP 電子郵件] 功能，連接至 Windows Server 上的現有 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-109">You can connect to an existing SMTP Server on a Windows Server using the *SMTP E-mail* feature within IIS.</span></span> <span data-ttu-id="3cd74-110">[SMTP 電子郵件] 功能不是 SQL Server Database Mail 所需的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-110">The *SMTP E-mail* feature is NOT an SMTP Server, which is required for SQL Server Database Mail.</span></span> <span data-ttu-id="3cd74-111">因此，本主題不包含在用戶端作業系統上安裝和設定 SMTP 伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="3cd74-111">As a result, this topic does not include the steps to install and configure an SMTP Server on client operating systems.</span></span>  

## <a name="install-and-configure-the-smtp-server"></a><span data-ttu-id="3cd74-112">安裝和設定 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-112">Install and configure the SMTP server</span></span>  
  
<span data-ttu-id="3cd74-113">這些步驟適用於：</span><span class="sxs-lookup"><span data-stu-id="3cd74-113">These steps apply to:</span></span>

* <span data-ttu-id="3cd74-114">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3cd74-114">Windows Server 2016</span></span>
* <span data-ttu-id="3cd74-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3cd74-115">Windows Server 2012 R2</span></span>
* <span data-ttu-id="3cd74-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3cd74-116">Windows Server 2012</span></span>
  
### <a name="install-smtp-server"></a><span data-ttu-id="3cd74-117">安裝 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-117">Install SMTP Server</span></span>  
   
1.  <span data-ttu-id="3cd74-118">在 [伺服器管理員] 中，選取左窗格中的 [儀表板]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-118">In **Server Manager**, select **Dashboard** in the left pane.</span></span>  
  
3.  <span data-ttu-id="3cd74-119">選取 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-119">Select **Add roles and features**.</span></span> <span data-ttu-id="3cd74-120">您也可以從右上角的 [管理] 功能表開啟 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-120">**Add Roles and Features** can also be opened from the **Manage** menu in the top right-hand corner.</span></span>  
  
4.  <span data-ttu-id="3cd74-121">在 [開始之前]中，選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-121">In **Before You Begin**, select **Next**.</span></span>  
  
5.  <span data-ttu-id="3cd74-122">選取 [角色型或功能型安裝]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-122">Select **Role-based or feature-based installation**, and select **Next**.</span></span>  
  
6.  <span data-ttu-id="3cd74-123">選取 [從伺服器集區選取伺服器]，並選取所需的伺服器，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-123">Select **Select a server from the server pool**, select the desired server, and select **Next**.</span></span> <span data-ttu-id="3cd74-124">[伺服器選取項目] 視窗會列出已使用 [伺服器管理員] 中的 [新增伺服器] 所新增的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-124">The **Server Selection** window lists the servers that have been added using **Add Server** in **Server Manager**.</span></span> <span data-ttu-id="3cd74-125">根據預設，它會選取本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-125">By default, it selects the local server.</span></span>  
  
7.  <span data-ttu-id="3cd74-126">在 [伺服器角色] 中，選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-126">In **Server Roles**, select **Next**.</span></span>  
  
8.  <span data-ttu-id="3cd74-127">在 [功能] 中，核取 [SMTP 伺服器]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-127">In **Features**, check **SMTP Server**.</span></span> <span data-ttu-id="3cd74-128">系統出現提示時，請選取 [新增功能]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-128">If prompted, select **Add Features**.</span></span> <span data-ttu-id="3cd74-129">選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-129">Select **Next**.</span></span>  
  
9. <span data-ttu-id="3cd74-130">在 [確認] 中，選取 [必要時自動重新啟動目的地伺服器]，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-130">In **Confirmation**, select **Restart the destination server automatically if required**, and select **Install**.</span></span> <span data-ttu-id="3cd74-131">完成後，請選取 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-131">When complete, select **Close**.</span></span>  

### <a name="configure-the-smtp-server"></a><span data-ttu-id="3cd74-132">設定 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-132">Configure the SMTP Server</span></span>  
 <span data-ttu-id="3cd74-133">下列步驟使用 IIS 6.0 管理員來設定 SMTP 虛擬伺服器︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-133">The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:</span></span>  
  
1.  <span data-ttu-id="3cd74-134">開啟 IIS 管理員︰在 [開始] 中，搜尋 **inetmgr6.exe**，並開啟它。</span><span class="sxs-lookup"><span data-stu-id="3cd74-134">Open the IIS Manager: In Start, search for **inetmgr6.exe**, and open it.</span></span>  
  
2.  <span data-ttu-id="3cd74-135">展開電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3cd74-135">Expand the computer name.</span></span> <span data-ttu-id="3cd74-136">以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-136">Right-click **[SMTP Virtual Server #1]**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3cd74-137">在 [存取] 索引標籤中，選取 [轉送] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cd74-137">In the **Access** tab, select the **Relay** button.</span></span>  
  
4.  <span data-ttu-id="3cd74-138">選取 [新增]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-138">Select **Add**.</span></span> <span data-ttu-id="3cd74-139">在 [單一電腦] 中，輸入 `127.0.0.1`，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-139">For **Single Computer**, enter `127.0.0.1`, and select **OK**.</span></span>  
  
     <span data-ttu-id="3cd74-140">新增 127.0.0.1，即允許本機伺服器傳送來自這個 SMTP 伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="3cd74-140">By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server.</span></span> <span data-ttu-id="3cd74-141">如果您想要其他電腦傳送來自這個 SMTP 伺服器的訊息，請輸入其 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3cd74-141">If you want additional computers to send messages from this SMTP server, enter their IP addresses.</span></span>  
  
5.  <span data-ttu-id="3cd74-142">在 [傳遞] 索引標籤中，選取 [輸出安全性]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-142">In the **Delivery** tab, select **Outbound Security**.</span></span> <span data-ttu-id="3cd74-143">選擇下列項目：</span><span class="sxs-lookup"><span data-stu-id="3cd74-143">Choose from the following:</span></span>  
  
     <span data-ttu-id="3cd74-144">**匿名存取**︰不需要帳戶名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="3cd74-144">**Anonymous access**: An account name or password is not required.</span></span> <span data-ttu-id="3cd74-145">這個選項會停用 SMTP 伺服器的驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-145">This option disables authentication for the SMTP Server.</span></span>  
  
     <span data-ttu-id="3cd74-146">**基本驗證**︰您要連接之伺服器的帳戶名稱和密碼會以純文字傳送。</span><span class="sxs-lookup"><span data-stu-id="3cd74-146">**Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text.</span></span> <span data-ttu-id="3cd74-147">您輸入的這個帳戶會傳輸電子郵件。</span><span class="sxs-lookup"><span data-stu-id="3cd74-147">This account you enter transmits the e-mails.</span></span> <span data-ttu-id="3cd74-148">將電子郵件傳送至個人帳戶或 Exchange 帳戶時，可以選取基本驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-148">Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account.</span></span> <span data-ttu-id="3cd74-149">因為這些認證會以純文字傳遞，所以建議啟用 **TLS 加密**。</span><span class="sxs-lookup"><span data-stu-id="3cd74-149">Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.</span></span>  
  
     <span data-ttu-id="3cd74-150">**整合式 Windows 驗證**：使用 Windows 網域帳戶名稱和密碼進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-150">**Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate.</span></span> <span data-ttu-id="3cd74-151">您輸入的帳戶會傳輸電子郵件。</span><span class="sxs-lookup"><span data-stu-id="3cd74-151">The account you enter transmits the e-mails.</span></span>  
  
     <span data-ttu-id="3cd74-152">**TLS 加密**：與 SSL 類似，TLS 會保護連接安全。</span><span class="sxs-lookup"><span data-stu-id="3cd74-152">**TLS encryption**: Similar to SSL, TLS secures the connection.</span></span> <span data-ttu-id="3cd74-153">需要在這部伺服器上安裝有效的 SSL 伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-153">Requires a valid SSL server certificate installed on this server.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="3cd74-154">若要使用個人電子郵件帳戶來測試核心 SMTP 功能 (包含 Exchange 帳戶)，請選取 [匿名存取]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-154">To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**.</span></span> <span data-ttu-id="3cd74-155">選取 [基本驗證] 時，SMTP 會使用 AUTH 命令。</span><span class="sxs-lookup"><span data-stu-id="3cd74-155">When Basic authentication is selected, SMTP uses the AUTH command.</span></span> <span data-ttu-id="3cd74-156">某些電子郵件提供者可能會因 AUTH 命令而失敗。</span><span class="sxs-lookup"><span data-stu-id="3cd74-156">Some e-mail providers may fail because of the AUTH command.</span></span> <span data-ttu-id="3cd74-157">如果 AUTH 命令失敗，可能會在 SMTP 伺服器的 Windows 事件記錄檔中記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cd74-157">If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.</span></span>  
  
6.  <span data-ttu-id="3cd74-158">在 [傳遞] 索引標籤中，選取 [輸出連線]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-158">In the **Delivery** tab, select **Outbound connections**.</span></span> <span data-ttu-id="3cd74-159">TCP 通訊埠預設為 25。</span><span class="sxs-lookup"><span data-stu-id="3cd74-159">By default, the TCP Port is 25.</span></span> <span data-ttu-id="3cd74-160">如果您在防火牆內開啟不同的通訊埠，則可以輸入該連接埠。</span><span class="sxs-lookup"><span data-stu-id="3cd74-160">A different port can be entered if it is open within your firewall.</span></span> <span data-ttu-id="3cd74-161">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-161">Select **OK**.</span></span>  
  
7.  <span data-ttu-id="3cd74-162">在 [傳遞] 索引標籤中，選取 [進階]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-162">In the **Delivery** tab, select **Advanced**.</span></span> <span data-ttu-id="3cd74-163">預設會列出本機伺服器的 [完整網域名稱]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-163">By default, the **Fully Qualified Domain Name** of the local server is listed.</span></span> <span data-ttu-id="3cd74-164">根據網際網路提供者，[智慧主機] 屬性可以空白。</span><span class="sxs-lookup"><span data-stu-id="3cd74-164">Depending on the internet provider, the **Smart Host** property can remain empty.</span></span> <span data-ttu-id="3cd74-165">您可能需要連絡網際網路提供者，確認是否需要智慧主機。</span><span class="sxs-lookup"><span data-stu-id="3cd74-165">You may need to contact the internet provider to confirm if a Smart Host is required.</span></span> <span data-ttu-id="3cd74-166">否則，您可以輸入 smtp.*EMailProvider*.com。</span><span class="sxs-lookup"><span data-stu-id="3cd74-166">Otherwise, you may be able to enter smtp.*EMailProvider*.com.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3cd74-167">「智慧主機」 (也稱為轉送主機) 是 Exchange 伺服器用來路由傳送所有外寄訊息的專用伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-167">A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages.</span></span> <span data-ttu-id="3cd74-168">「智慧主機」接收到訊息時，「智慧主機」會將訊息轉送至遠端網域。</span><span class="sxs-lookup"><span data-stu-id="3cd74-168">When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain.</span></span> <span data-ttu-id="3cd74-169">「智慧主機」的目的是要改善 Exchange Server 的效能。</span><span class="sxs-lookup"><span data-stu-id="3cd74-169">The goal of a **Smart Host** is to improve performance of an Exchange Server.</span></span> <span data-ttu-id="3cd74-170">Exchange Server 只會傳輸至智慧主機；而不是重複連絡遠端網域直到建立連線。</span><span class="sxs-lookup"><span data-stu-id="3cd74-170">The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.</span></span>  
  
8.  <span data-ttu-id="3cd74-171">選取 [確定] 關閉所有視窗。</span><span class="sxs-lookup"><span data-stu-id="3cd74-171">Select **OK** to close all windows.</span></span>  
  
9. <span data-ttu-id="3cd74-172">重新啟動 SMTP 伺服器︰ 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，並選取 [停止]，然後選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-172">Restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**.</span></span> <span data-ttu-id="3cd74-173">需要重新啟動，才能套用 SMTP 伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="3cd74-173">A restart is needed to apply the SMTP Server settings.</span></span> 

  
## <a name="windows-server-2008-r2-install-and-configure-smtp-server"></a><span data-ttu-id="3cd74-174">Windows Server 2008 R2：安裝和設定 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-174">Windows Server 2008 R2: Install and Configure SMTP Server</span></span>  
  
### <a name="install-smtp-server"></a><span data-ttu-id="3cd74-175">安裝 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-175">Install SMTP Server</span></span>  
 <span data-ttu-id="3cd74-176">下列步驟會安裝 SMTP 伺服器功能︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-176">The following steps install the SMTP Server feature:</span></span>  
  
1.  <span data-ttu-id="3cd74-177">在 [伺服器管理員] 中，選取 [功能]，然後選取 [新增功能]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-177">In **Server Manager**, select **Features**, and select **Add Features**.</span></span>  
  
3.  <span data-ttu-id="3cd74-178">在 [新增功能] 中，選取 [SMTP 伺服器]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-178">In **Add Features**, select **SMTP Server**.</span></span> <span data-ttu-id="3cd74-179">系統出現提示，請選取 [新增所需的角色服務]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-179">If prompted, select **Add Required Role Services**, and select **Next**.</span></span>  
  
4.  <span data-ttu-id="3cd74-180">選取 [下一步]，以繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="3cd74-180">Continue with the installation by selecting **Next**.</span></span>  
  
5.  <span data-ttu-id="3cd74-181">在 [確認安裝選項] 視窗中，選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-181">In the **Confirm Installation Selections** window, select **Install**.</span></span> <span data-ttu-id="3cd74-182">完成後，請選取 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-182">When complete, select **Close**.</span></span>  
  
### <a name="configure-the-smtp-server"></a><span data-ttu-id="3cd74-183">設定 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-183">Configure the SMTP Server</span></span>  
 <span data-ttu-id="3cd74-184">下列步驟使用 IIS 6.0 管理員來設定 SMTP 虛擬伺服器︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-184">The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:</span></span>  
  
1.  <span data-ttu-id="3cd74-185">開啟 IIS 6.0 管理員：在 [開始] 中，搜尋 **IIS**，然後選取 [網際網路資訊服務 (IIS) 6.0 管理員]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-185">Open the IIS 6.0 Manager: In **Start**, search for **IIS**, and select **Internet Information Services (IIS) 6.0 Manager**.</span></span>  
  
2.  <span data-ttu-id="3cd74-186">展開電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3cd74-186">Expand the computer name.</span></span> <span data-ttu-id="3cd74-187">以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-187">Right-click **[SMTP Virtual Server #1]**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3cd74-188">在 [存取] 索引標籤中，選取 [轉送] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cd74-188">In the **Access** tab, select the **Relay** button.</span></span>  
  
4.  <span data-ttu-id="3cd74-189">選取 [新增]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-189">Select **Add**.</span></span> <span data-ttu-id="3cd74-190">在 [單一電腦] 中，輸入 `127.0.0.1`，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-190">For **Single Computer**, enter `127.0.0.1`, and select **OK**.</span></span>  
  
     <span data-ttu-id="3cd74-191">新增 127.0.0.1，即允許本機伺服器傳送來自這個 SMTP 伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="3cd74-191">By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server.</span></span> <span data-ttu-id="3cd74-192">如果您想要其他電腦傳送來自這個 SMTP 伺服器的訊息，請輸入其 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3cd74-192">If you want additional computers to send messages from this SMTP server, enter their IP addresses.</span></span>  
  
5.  <span data-ttu-id="3cd74-193">在 [傳遞] 索引標籤中，選取 [輸出安全性]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-193">In the **Delivery** tab, select **Outbound Security**.</span></span> <span data-ttu-id="3cd74-194">選擇下列項目：</span><span class="sxs-lookup"><span data-stu-id="3cd74-194">Choose from the following:</span></span>  
  
     <span data-ttu-id="3cd74-195">**匿名存取**︰不需要帳戶名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="3cd74-195">**Anonymous access**: An account name or password is not required.</span></span> <span data-ttu-id="3cd74-196">這個選項會停用 SMTP 伺服器的驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-196">This option disables authentication for the SMTP Server.</span></span>  
  
     <span data-ttu-id="3cd74-197">**基本驗證**︰您要連接之伺服器的帳戶名稱和密碼會以純文字傳送。</span><span class="sxs-lookup"><span data-stu-id="3cd74-197">**Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text.</span></span> <span data-ttu-id="3cd74-198">將電子郵件傳送至個人帳戶或 Exchange 帳戶時，可以選取基本驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-198">Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account.</span></span> <span data-ttu-id="3cd74-199">因為這些認證會以純文字傳遞，所以建議啟用 **TLS 加密**。</span><span class="sxs-lookup"><span data-stu-id="3cd74-199">Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.</span></span>  
  
     <span data-ttu-id="3cd74-200">**整合式 Windows 驗證**：使用 Windows 網域帳戶名稱和密碼進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-200">**Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate.</span></span> <span data-ttu-id="3cd74-201">您輸入的帳戶會傳輸電子郵件。</span><span class="sxs-lookup"><span data-stu-id="3cd74-201">The account you enter transmits the e-mails.</span></span>  
  
     <span data-ttu-id="3cd74-202">**TLS 加密**：與 SSL 類似，TLS 會保護連接安全。</span><span class="sxs-lookup"><span data-stu-id="3cd74-202">**TLS encryption**: Similar to SSL, TLS secures the connection.</span></span> <span data-ttu-id="3cd74-203">需要在這部伺服器上安裝有效的 SSL 伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="3cd74-203">Requires a valid SSL server certificate installed on this server.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="3cd74-204">若要使用個人電子郵件帳戶來測試核心 SMTP 功能 (包含 Exchange 帳戶)，請選取 [匿名存取]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-204">To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**.</span></span> <span data-ttu-id="3cd74-205">選取 [基本驗證] 時，SMTP 會使用 AUTH 命令。</span><span class="sxs-lookup"><span data-stu-id="3cd74-205">When Basic authentication is selected, SMTP uses the AUTH command.</span></span> <span data-ttu-id="3cd74-206">某些電子郵件提供者可能會因 AUTH 命令而失敗。</span><span class="sxs-lookup"><span data-stu-id="3cd74-206">Some e-mail providers may fail because of the AUTH command.</span></span> <span data-ttu-id="3cd74-207">如果 AUTH 命令失敗，可能會在 SMTP 伺服器的 Windows 事件記錄檔中記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cd74-207">If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.</span></span>  
  
6.  <span data-ttu-id="3cd74-208">在 [傳遞] 索引標籤中，選取 [輸出連線]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-208">In the **Delivery** tab, select **Outbound connections**.</span></span> <span data-ttu-id="3cd74-209">TCP 通訊埠預設為 25。</span><span class="sxs-lookup"><span data-stu-id="3cd74-209">By default, the TCP Port is 25.</span></span> <span data-ttu-id="3cd74-210">如果您在防火牆內開啟不同的通訊埠，則可以輸入該連接埠。</span><span class="sxs-lookup"><span data-stu-id="3cd74-210">A different port can be entered if it is open within your firewall.</span></span> <span data-ttu-id="3cd74-211">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-211">Select **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="3cd74-212">TCP 通訊埠可以用於傳入連接和傳出連接。</span><span class="sxs-lookup"><span data-stu-id="3cd74-212">The TCP Port can be used for Inbound connections and Outbound connections.</span></span>  
  
7.  <span data-ttu-id="3cd74-213">在 [傳遞] 索引標籤中，選取 [進階]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-213">In the **Delivery** tab, select **Advanced**.</span></span> <span data-ttu-id="3cd74-214">預設會列出本機伺服器的 [完整網域名稱]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-214">By default, the **Fully Qualified Domain Name** of the local server is listed.</span></span> <span data-ttu-id="3cd74-215">根據網際網路提供者，[智慧主機] 屬性可以空白。</span><span class="sxs-lookup"><span data-stu-id="3cd74-215">Depending on the internet provider, the **Smart Host** property can remain empty.</span></span> <span data-ttu-id="3cd74-216">您可能需要連絡網際網路提供者，確認是否需要智慧主機。</span><span class="sxs-lookup"><span data-stu-id="3cd74-216">You may need to contact the internet provider to confirm if a Smart Host is required.</span></span> <span data-ttu-id="3cd74-217">否則，您可以輸入 smtp.*EMailProvider*.com。</span><span class="sxs-lookup"><span data-stu-id="3cd74-217">Otherwise, you may be able to enter smtp.*EMailProvider*.com.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3cd74-218">「智慧主機」 (也稱為轉送主機) 是 Exchange 伺服器用來路由傳送所有外寄訊息的專用伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cd74-218">A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages.</span></span> <span data-ttu-id="3cd74-219">「智慧主機」接收到訊息時，「智慧主機」會將訊息轉送至遠端網域。</span><span class="sxs-lookup"><span data-stu-id="3cd74-219">When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain.</span></span> <span data-ttu-id="3cd74-220">「智慧主機」的目的是要改善 Exchange Server 的效能。</span><span class="sxs-lookup"><span data-stu-id="3cd74-220">The goal of a **Smart Host** is to improve performance of an Exchange Server.</span></span> <span data-ttu-id="3cd74-221">Exchange Server 只會傳輸至智慧主機；而不是重複連絡遠端網域直到建立連線。</span><span class="sxs-lookup"><span data-stu-id="3cd74-221">The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.</span></span>  
  
8.  <span data-ttu-id="3cd74-222">選取 [確定] 關閉所有視窗。</span><span class="sxs-lookup"><span data-stu-id="3cd74-222">Select **OK** to close all windows.</span></span>  
  
9. <span data-ttu-id="3cd74-223">需要重新啟動，才能套用 SMTP 伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="3cd74-223">A restart is needed to apply the SMTP Server settings.</span></span> <span data-ttu-id="3cd74-224">重新啟動 SMTP 伺服器︰ 以滑鼠右鍵按一下 [SMTP 虛擬伺服器 #1]，並選取 [停止]，然後選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="3cd74-224">To restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**.</span></span>  
  
  
## <a name="test-the-smtp-server"></a><span data-ttu-id="3cd74-225">測試 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="3cd74-225">Test the SMTP Server</span></span>  
 <span data-ttu-id="3cd74-226">Telnet 可以用來測試 SMTP 伺服器組態。</span><span class="sxs-lookup"><span data-stu-id="3cd74-226">Telnet can be used to test the SMTP Server configuration.</span></span> <span data-ttu-id="3cd74-227">下列步驟使用您設定的 SMTP 伺服器將訊息傳送至電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="3cd74-227">The following steps send a message using your configured SMTP Server to an e-mail address.</span></span> <span data-ttu-id="3cd74-228">[http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) 提供的 telnet 命令的描述。</span><span class="sxs-lookup"><span data-stu-id="3cd74-228">[http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) provides descriptions of the telnet commands.</span></span>  
  
1.  <span data-ttu-id="3cd74-229">以系統管理員身分開啟命令視窗。</span><span class="sxs-lookup"><span data-stu-id="3cd74-229">Open a command window as Administrator.</span></span>
  
2.  <span data-ttu-id="3cd74-230">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3cd74-230">In the command prompt, type:</span></span>  
  
     `telnet localhost 25`  
  
     <span data-ttu-id="3cd74-231">如果未安裝 telnet，請輸入下列命令進行安裝︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-231">If telnet is not installed, install it by typing:</span></span>  
  
     `pkgmgr /iu:"TelnetClient"`  
  
3.  <span data-ttu-id="3cd74-232">輸入下列命令開始通訊︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-232">Start communication by typing:</span></span>  
  
     `EHLO server`  
  
4.  <span data-ttu-id="3cd74-233">輸入郵件寄件者地址︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-233">Enter the Mail From address:</span></span>  
  
     `MAIL FROM: *YourEmailAddress*@*YourProvider*.com`  
  
     <span data-ttu-id="3cd74-234">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="3cd74-234">For example, enter:</span></span>  
  
     `MAIL FROM: EmailAddress@outlook.com`  
  
5.  <span data-ttu-id="3cd74-235">輸入郵件收件者地址︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-235">Enter the Mail To address:</span></span>  
  
     `RCPT TO: *YourEmailAddress*@*YourProvider*.com`  
  
     <span data-ttu-id="3cd74-236">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="3cd74-236">For example, enter:</span></span>  
  
     `RCPT TO: EmailAddress@outlook.com`  
  
6.  <span data-ttu-id="3cd74-237">輸入下列命令，告知準備好要傳送資料的 SMTP 伺服器︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-237">Tell the SMTP Server you are ready to send data by typing:</span></span>  
  
     `DATA`  
  
7.  <span data-ttu-id="3cd74-238">輸入下列命令，輸入主旨︰</span><span class="sxs-lookup"><span data-stu-id="3cd74-238">Enter the Subject by typing:</span></span>  
  
     `Subject: Test Message`  
  
8.  <span data-ttu-id="3cd74-239">按 Enter 兩次。</span><span class="sxs-lookup"><span data-stu-id="3cd74-239">Hit Enter twice.</span></span>  
  
9. <span data-ttu-id="3cd74-240">輸入下列命令，輸入訊息主體：</span><span class="sxs-lookup"><span data-stu-id="3cd74-240">Enter the message body by typing:</span></span>  
  
     `This is the message body of the test message.`  
  
10. <span data-ttu-id="3cd74-241">按 Enter，並輸入句號 (.)，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3cd74-241">Hit Enter, type a period (.), and hit Enter.</span></span>  
  
 <span data-ttu-id="3cd74-242">檢查電子郵件訊息的 RCPT TO 位址。</span><span class="sxs-lookup"><span data-stu-id="3cd74-242">Check the RCPT TO address for the e-mail message.</span></span> <span data-ttu-id="3cd74-243">如果未傳遞電子郵件 (請檢查您的收件匣和垃圾郵件資料夾)，則不會成功傳送訊息，而訊息可能位在 SMTP Queue 資料夾 (C:\inetpub\mailroot\Queue) 中。</span><span class="sxs-lookup"><span data-stu-id="3cd74-243">If the e-mail is not delivered (Check your Inbox and Spam folder), then the message was not successfully sent, and may reside in the SMTP Queue folder (C:\inetpub\mailroot\Queue).</span></span>  
  