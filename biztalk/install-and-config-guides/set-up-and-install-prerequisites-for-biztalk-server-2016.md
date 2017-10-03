---
title: "設定並安裝 BizTalk Server 2016 的必要條件 |Microsoft 文件"
description: "安裝及設定必要的軟體和設定 BizTalk Server 2016 的逐步指示"
author: MandiOhlinger
manager: anneta
ms.prod: biztalk-server
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b621-903a-4cfa-9cb0-c6a82ed8f733
caps.latest.revision: "11"
ms.author: mandia
ms.openlocfilehash: bee25a841d7f434fd5366f483b0b5544462d29fd
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
---
# <a name="set-up-and-install-prerequisites-for-biztalk-server-2016"></a><span data-ttu-id="8f14e-103">設定及安裝 BizTalk Server 2016 的必要元件</span><span class="sxs-lookup"><span data-stu-id="8f14e-103">Set up and install prerequisites for BizTalk Server 2016</span></span>
<span data-ttu-id="8f14e-104">設定伺服器，以及安裝與設定軟體必要條件。</span><span class="sxs-lookup"><span data-stu-id="8f14e-104">Set up the server, and install and configure the software prerequisites.</span></span>

## <a name="join-the-local-administrators-group"></a><span data-ttu-id="8f14e-105">加入本機系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="8f14e-105">Join the Local Administrators Group</span></span>
<span data-ttu-id="8f14e-106">若要安裝與設定 BizTalk Server，請登入本機電腦上使用系統管理員帳戶的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f14e-106">To install and configure BizTalk Server, sign in to the server using an administrator account on the local computer.</span></span> <span data-ttu-id="8f14e-107">將任何管理 BizTalk Server 的使用者帳戶加入本機系統管理員群組︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-107">Add any user accounts that are administering the BizTalk Server to the local Administrators group:</span></span>

1.  <span data-ttu-id="8f14e-108">在 [開始] 功能表中，開啟 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-108">In the Start menu, open **Computer Management**.</span></span>

    * <span data-ttu-id="8f14e-109">或開啟 [系統管理工具]，然後選取 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-109">Or, open **Administrative Tools**, and then select **Computer Management**.</span></span>
    * <span data-ttu-id="8f14e-110">或開啟 [伺服器管理員]，然後依序選取 [工具] 及 [電腦管理]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-110">Or, open **Server Manager**, select **Tools**, and then select **Computer Management**.</span></span>
  
2.  <span data-ttu-id="8f14e-111">展開 [本機使用者和群組]，然後選取 [群組]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-111">Expand **Local Users and Groups**, and select **Groups**.</span></span>
3.  <span data-ttu-id="8f14e-112">以滑鼠右鍵按一下**系統管理員**群組，並選取 [加入群組]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-112">Right-click the **Administrators** group, and select **Add to Group**.</span></span> <span data-ttu-id="8f14e-113">[新增] 您的帳戶，然後選取 [確定] 儲存變更。</span><span class="sxs-lookup"><span data-stu-id="8f14e-113">**Add** your accounts, and select **OK** to save your changes.</span></span> 

## <a name="change-the-computer-name-to-less-than-15-characters-optional"></a><span data-ttu-id="8f14e-114">將電腦名稱變更為少於 15 個字元 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-114">Change the computer name to less than 15 characters (optional)</span></span>
<span data-ttu-id="8f14e-115">如果您的電腦名稱長度超過 15 個字元，BizTalk Server 組態失敗。</span><span class="sxs-lookup"><span data-stu-id="8f14e-115">If your computer name is longer than 15 characters, then BizTalk Server configuration fails.</span></span> <span data-ttu-id="8f14e-116">變更電腦名稱︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-116">To change the computer name:</span></span>

1.  <span data-ttu-id="8f14e-117">在 [伺服器管理員] > [儀表板] 中，選取 [本機伺服器]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-117">In **Server Manager** > **Dashboard**, select **Local Server**.</span></span> 
2.  <span data-ttu-id="8f14e-118">在 [內容] 中選取電腦名稱屬性予以變更。</span><span class="sxs-lookup"><span data-stu-id="8f14e-118">In **Properties**, select the Computer name property to change it.</span></span>
3. <span data-ttu-id="8f14e-119">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-119">Restart the computer.</span></span> 

<span data-ttu-id="8f14e-120">**另請參閱**：Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)</span><span class="sxs-lookup"><span data-stu-id="8f14e-120">**SEE ALSO** : Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)</span></span>

## <a name="enable-network-dtc-access"></a><span data-ttu-id="8f14e-121">啟用網路 DTC 存取</span><span class="sxs-lookup"><span data-stu-id="8f14e-121">Enable Network DTC Access</span></span>
<span data-ttu-id="8f14e-122">如果 BizTalk 和 SQL Server 安裝在不同的電腦上，請啟用 BizTalk Server 和 SQL Server 上的網路 DTC 存取。</span><span class="sxs-lookup"><span data-stu-id="8f14e-122">If BizTalk and SQL Server are installed on separate computers, then enable Network DTC Access on the BizTalk Server and the SQL Server.</span></span> 

1. <span data-ttu-id="8f14e-123">在 [開始] 功能表中，開啟 "dcomcnfg"。</span><span class="sxs-lookup"><span data-stu-id="8f14e-123">In the Start menu, open "dcomcnfg".</span></span>

    * <span data-ttu-id="8f14e-124">或開啟 [系統管理工具]，然後選取 [Component Services]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-124">Or, open **Administrative Tools**, and then select **Component Services**.</span></span>
    * <span data-ttu-id="8f14e-125">或開啟 [伺服器管理員]，然後依序選取 [工具] 及 [Component Services]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-125">Or, open **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>
  
2. <span data-ttu-id="8f14e-126">依序展開 [Component Services]、[電腦]、[我的電腦] 和 [分散式交易協調器]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-126">Expand **Component Services**, expand **Computers**, expand **My Computer**,  and expand **Distributed Transaction Coordinator**.</span></span>
3. <span data-ttu-id="8f14e-127">以滑鼠右鍵按一下 [本機 DTC]，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-127">Right-click **Local DTC**, and select **Properties**.</span></span>
4. <span data-ttu-id="8f14e-128">在 [安全性] 索引標籤上，檢查以下項目：</span><span class="sxs-lookup"><span data-stu-id="8f14e-128">Go to the **Security** tab, and check the following:</span></span>  
    * <span data-ttu-id="8f14e-129">網路 DTC 存取</span><span class="sxs-lookup"><span data-stu-id="8f14e-129">Network DTC Access</span></span>
    * <span data-ttu-id="8f14e-130">允許輸入</span><span class="sxs-lookup"><span data-stu-id="8f14e-130">Allow Inbound</span></span>
    * <span data-ttu-id="8f14e-131">允許輸出</span><span class="sxs-lookup"><span data-stu-id="8f14e-131">Allow Outbound</span></span>
    * <span data-ttu-id="8f14e-132">不需要驗證</span><span class="sxs-lookup"><span data-stu-id="8f14e-132">No Authentication Required</span></span>
5. <span data-ttu-id="8f14e-133">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-133">Select **OK**.</span></span> <span data-ttu-id="8f14e-134">如果提示您重新啟動 MS DTC，請選取**是**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-134">If prompted to restart MS DTC, select **Yes**.</span></span> 

<span data-ttu-id="8f14e-135">如需可能需要的其他設定，請參閱 [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-135">For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>

## <a name="configure-the-application-event-log-optional"></a><span data-ttu-id="8f14e-136">設定應用程式事件記錄檔 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="8f14e-136">Configure the Application Event Log (optional)</span></span>

<span data-ttu-id="8f14e-137">BizTalk Server 安裝程式會將事件記錄保留在應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="8f14e-137">BizTalk Server setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="8f14e-138">隨安裝的 BizTalk Server 功能而定，記錄檔需要的空間量可能會超過其限制。</span><span class="sxs-lookup"><span data-stu-id="8f14e-138">Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="8f14e-139">如果應用程式事件記錄檔在安裝期間用盡空間，安裝就會失敗。</span><span class="sxs-lookup"><span data-stu-id="8f14e-139">If the application event log runs out of space during the setup, the installation fails.</span></span> <span data-ttu-id="8f14e-140">變更應用程式事件記錄檔設定可防止此失敗。</span><span class="sxs-lookup"><span data-stu-id="8f14e-140">Changing the Application Event Log settings prevents this failure.</span></span>

1. <span data-ttu-id="8f14e-141">在 [開始] 功能表中，開啟 [事件檢視器]：</span><span class="sxs-lookup"><span data-stu-id="8f14e-141">In the Start menu, open **Event Viewer**:</span></span>

    * <span data-ttu-id="8f14e-142">或開啟 [系統管理工具]，然後選取 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-142">Or, open **Administrative Tools**, and then select **Event Viewer**.</span></span>
    * <span data-ttu-id="8f14e-143">或開啟 [伺服器管理員]，然後依序選取 [工具] 和 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-143">Or, open **Server Manager**, select **Tools**, and then select **Event Viewer**.</span></span>
  
2. <span data-ttu-id="8f14e-144">展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-144">Expand **Windows Logs**, right-click **Application**, and then select **Properties**.</span></span> 
3. <span data-ttu-id="8f14e-145">若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。</span><span class="sxs-lookup"><span data-stu-id="8f14e-145">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span> 

    * <span data-ttu-id="8f14e-146">若要增加空間，請在 [最大記錄檔大小] 中輸入較大的數字。</span><span class="sxs-lookup"><span data-stu-id="8f14e-146">To add space, enter a higher number in **Maximum log size**.</span></span>
    * <span data-ttu-id="8f14e-147">若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-147">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>
    * <span data-ttu-id="8f14e-148">若要清除記錄檔事件，請選取 [清除記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-148">To clear the log events, select **Clear log**.</span></span>

4. <span data-ttu-id="8f14e-149">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-149">Select **OK**.</span></span>

## <a name="edge-cant-be-opened-using-the-built-in-administrator-account-optional"></a><span data-ttu-id="8f14e-150">無法開啟邊緣，使用內建系統管理員帳戶 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="8f14e-150">Edge can’t be opened using the Built-in Administrator account (optional)</span></span>

<span data-ttu-id="8f14e-151">當使用 Edge 時，會顯示下列訊息︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-151">When using Edge, the following message displays:</span></span>  
`Microsoft Edge can't be opened using the Built-in Administrator account. Sign in with a different account and try again.`

<span data-ttu-id="8f14e-152">允許使用內建的系統管理員帳戶開啟 Edge：</span><span class="sxs-lookup"><span data-stu-id="8f14e-152">To allow Edge to open using the built-in administrator account:</span></span>

1. <span data-ttu-id="8f14e-153">在 [開始] 功能表中開啟 [本機安全性原則]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-153">In the Start menu, open **Local Security Policy**.</span></span> <span data-ttu-id="8f14e-154">或開啟 [伺服器管理員]，然後依序選取 [工具] 和 [本機安全性原則]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-154">Or, open **Server Manager**, select **Tools**, and then select **Local Security Policy**.</span></span>
2.  <span data-ttu-id="8f14e-155">展開 [本機原則]，然後選取 [安全性選項]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-155">Expand **Local Policies**, and select **Security Options**.</span></span> 
3.  <span data-ttu-id="8f14e-156">在 [使用者帳戶控制: 內建的 Administrator 帳戶的管理員核准模式] 原則中 [啟用] 原則。</span><span class="sxs-lookup"><span data-stu-id="8f14e-156">Go to the **User Account Control: Admin Approval Mode for the Built-in Administrator account** policy, and **Enable** the policy.</span></span> 
4. <span data-ttu-id="8f14e-157">選取 [確定] 重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-157">Select **OK**, and restart your computer.</span></span>

## <a name="install-windows-updates"></a><span data-ttu-id="8f14e-158">安裝 Windows 更新</span><span class="sxs-lookup"><span data-stu-id="8f14e-158">Install Windows Updates</span></span>

<span data-ttu-id="8f14e-159">請務必安裝最新的 Windows 重大更新。</span><span class="sxs-lookup"><span data-stu-id="8f14e-159">Be sure to install the latest critical Windows updates.</span></span> 

1. <span data-ttu-id="8f14e-160">在 [開始] 功能表中，開啟 [Windows Update] 並檢查更新。</span><span class="sxs-lookup"><span data-stu-id="8f14e-160">On the Start menu, open **Windows Updates**, and check for updates.</span></span> <span data-ttu-id="8f14e-161">您也可以開啟 [設定]，然後選取 [更新與安全性]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-161">You can also open **Settings**, and select **Update and security**.</span></span>
2. <span data-ttu-id="8f14e-162">安裝更新之後，您可能需要重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-162">After installing updates, you may need to restart the computer.</span></span>

## <a name="enable-internet-information-services-iis"></a><span data-ttu-id="8f14e-163">啟用 Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="8f14e-163">Enable Internet Information Services (IIS)</span></span>
<span data-ttu-id="8f14e-164">BizTalk Server 的下列功能需要 IIS：</span><span class="sxs-lookup"><span data-stu-id="8f14e-164">BizTalk Server requires IIS for the following features:</span></span>

- <span data-ttu-id="8f14e-165">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="8f14e-165">HTTP adapter</span></span>
- <span data-ttu-id="8f14e-166">SOAP adapter (SOAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="8f14e-166">SOAP adapter</span></span>
- <span data-ttu-id="8f14e-167">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8f14e-167">Windows SharePoint Services adapter</span></span>
- <span data-ttu-id="8f14e-168">安全通訊端層 (SSL) 加密</span><span class="sxs-lookup"><span data-stu-id="8f14e-168">Secure Sockets Layer (SSL) encryption</span></span>
- <span data-ttu-id="8f14e-169">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="8f14e-169">BAM Portal</span></span>
- <span data-ttu-id="8f14e-170">EDI</span><span class="sxs-lookup"><span data-stu-id="8f14e-170">EDI</span></span>

<span data-ttu-id="8f14e-171">IIS 是隨附於作業系統的**角色**或**功能**，視作業系統而定。</span><span class="sxs-lookup"><span data-stu-id="8f14e-171">IIS is included with the operating system as a **Role** or a **Feature**, depending on the OS.</span></span> <span data-ttu-id="8f14e-172">安裝：</span><span class="sxs-lookup"><span data-stu-id="8f14e-172">To install:</span></span>

1. <span data-ttu-id="8f14e-173">在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-173">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="8f14e-174">或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-174">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="8f14e-175">選取 [Internet Information Services] 或 [網頁伺服器 (IIS)]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-175">Select **Internet Information Services** or **Web Server (IIS)**.</span></span> <span data-ttu-id="8f14e-176">除了預設已核取的選項之外，另請選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="8f14e-176">In addition to the default checked options, also select the following:</span></span> 

    <span data-ttu-id="8f14e-177">**Windows 10**</span><span class="sxs-lookup"><span data-stu-id="8f14e-177">**Windows 10**</span></span>
    - <span data-ttu-id="8f14e-178">在 **Web 管理工具**中亦請核取：</span><span class="sxs-lookup"><span data-stu-id="8f14e-178">In **Web Management Tools**, also check:</span></span>  
        - <span data-ttu-id="8f14e-179">IIS 6 管理相容性</span><span class="sxs-lookup"><span data-stu-id="8f14e-179">IIS 6 Management Compatibility</span></span>
        - <span data-ttu-id="8f14e-180">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="8f14e-180">IIS 6 Management Console</span></span>
        - <span data-ttu-id="8f14e-181">IIS 6 指令碼工具 (安裝 adsutil.vbs)</span><span class="sxs-lookup"><span data-stu-id="8f14e-181">IIS 6 Scripting Tools (Installs adsutil.vbs)</span></span>
        - <span data-ttu-id="8f14e-182">IIS Metabase 及 IIS 6 設定相容性</span><span class="sxs-lookup"><span data-stu-id="8f14e-182">IIS Metabase and IIS 6 configuration compatibility</span></span>
        - <span data-ttu-id="8f14e-183">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="8f14e-183">IIS Management Console</span></span>
    - <span data-ttu-id="8f14e-184">在 **World Wide Web 服務**中展開 [安全性] 再一併核取：</span><span class="sxs-lookup"><span data-stu-id="8f14e-184">In **World Wide Web Services**, expand **Security** and also check:</span></span>
        - <span data-ttu-id="8f14e-185">基本驗證</span><span class="sxs-lookup"><span data-stu-id="8f14e-185">Basic Authentication</span></span>
        - <span data-ttu-id="8f14e-186">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="8f14e-186">Windows Authentication</span></span>    

    <span data-ttu-id="8f14e-187">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="8f14e-187">**Windows Server**</span></span>
    - <span data-ttu-id="8f14e-188">在 [安全性] 中亦請核取︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-188">In **Security**, also check:</span></span> 
        - <span data-ttu-id="8f14e-189">基本驗證</span><span class="sxs-lookup"><span data-stu-id="8f14e-189">Basic Authentication</span></span>
        - <span data-ttu-id="8f14e-190">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="8f14e-190">Windows Authentication</span></span>    
    - <span data-ttu-id="8f14e-191">在 [管理工具] 中亦請核取：</span><span class="sxs-lookup"><span data-stu-id="8f14e-191">In **Management Tools**, also check:</span></span>  
        - <span data-ttu-id="8f14e-192">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="8f14e-192">IIS Management Console</span></span>
        - <span data-ttu-id="8f14e-193">IIS 6 管理相容性</span><span class="sxs-lookup"><span data-stu-id="8f14e-193">IIS 6 Management Compatibility</span></span>
        - <span data-ttu-id="8f14e-194">IIS 6 Metabase 相容性</span><span class="sxs-lookup"><span data-stu-id="8f14e-194">IIS 6 Metabase compatibility</span></span>
        - <span data-ttu-id="8f14e-195">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="8f14e-195">IIS 6 Management Console</span></span>
        - <span data-ttu-id="8f14e-196">IIS 6 指令碼工具 (安裝 adsutil.vbs)</span><span class="sxs-lookup"><span data-stu-id="8f14e-196">IIS 6 Scripting Tools (Installs adsutil.vbs)</span></span>

3. <span data-ttu-id="8f14e-197">繼續安裝作業，並在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-197">Continue with the installation, and restart the computer if prompted.</span></span> 

<span data-ttu-id="8f14e-198">**另請參閱**︰在 [Windows 8 或 Windows Server 2012 (英文)](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012) 上安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="8f14e-198">**SEE ALSO** : Install IIS on [Windows 8 or Windows Server 2012](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012).</span></span>


## <a name="running-the-bam-portal-in-a-64-bit-environment-optional"></a><span data-ttu-id="8f14e-199">在 64 位元環境中執行 BAM 入口網站 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-199">Running the BAM Portal in a 64-bit environment (optional)</span></span>
<span data-ttu-id="8f14e-200">如果您不使用 BAM 入口網站，然後您可以略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-200">If you don't use the BAM portal, then you can skip this section.</span></span> 

<span data-ttu-id="8f14e-201">BAM 入口網站在 32 位元模式中執行。</span><span class="sxs-lookup"><span data-stu-id="8f14e-201">The BAM Portal runs in 32-bit mode.</span></span> <span data-ttu-id="8f14e-202">如果您在 64 位元環境中使用網際網路資訊服務 (IIS)，然後設定在 32 位元模式中執行的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="8f14e-202">If you are using Internet Information Services (IIS) in a 64-bit environment, then set the application pool to run in 32-bit mode.</span></span> 

#### <a name="using-adsutilvbs"></a><span data-ttu-id="8f14e-203">使用 adsutil.vbs</span><span class="sxs-lookup"><span data-stu-id="8f14e-203">Using adsutil.vbs</span></span>
1.  <span data-ttu-id="8f14e-204">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="8f14e-204">Open a command prompt as administrator.</span></span> 
2.  <span data-ttu-id="8f14e-205">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="8f14e-205">In the command prompt, type:</span></span>  
    `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`
3. <span data-ttu-id="8f14e-206">選取 [輸入]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-206">Select Enter.</span></span>

#### <a name="using-iis-manager"></a><span data-ttu-id="8f14e-207">使用 IIS Manager</span><span class="sxs-lookup"><span data-stu-id="8f14e-207">Using IIS Manager</span></span>
1. <span data-ttu-id="8f14e-208">在 [開始] 功能表中，開啟 "inetmgr"。</span><span class="sxs-lookup"><span data-stu-id="8f14e-208">In the Start menu, open "inetmgr".</span></span>
2.  <span data-ttu-id="8f14e-209">展開電腦名稱，然後選取 [應用程式集區]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-209">Expand the computer name, and select **Application Pools**.</span></span>
3.  <span data-ttu-id="8f14e-210">以滑鼠右鍵按一下 [DefaultAppPool]，然後選取 [進階設定]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-210">Right-click **DefaultAppPool**, and select **Advanced Settings**.</span></span> 
4.  <span data-ttu-id="8f14e-211">將 [啟用 32 位元應用程式] 的值變更為 **True**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-211">Change the value of **Enable 32-bit Applications** to **True**.</span></span> 
5.  <span data-ttu-id="8f14e-212">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-212">Select **OK**.</span></span>

## <a name="install-windows-identity-foundation-wif-optional"></a><span data-ttu-id="8f14e-213">安裝 Windows Identity Foundation (WIF) (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-213">Install Windows Identity Foundation (WIF) (optional)</span></span>
<span data-ttu-id="8f14e-214">如果您使用 SharePoint Services 配接器，BizTalk Server 需要 WIF。</span><span class="sxs-lookup"><span data-stu-id="8f14e-214">If you use the SharePoint Services adapter, BizTalk Server requires WIF.</span></span> <span data-ttu-id="8f14e-215">如果不使用 SharePoint Services 配接器，您可以略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-215">If you don't use the SharePoint Services adapter, you can skip this section.</span></span>

<span data-ttu-id="8f14e-216">Windows Identity Foundation 是隨附於作業系統的**功能**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-216">Windows Identity Foundation is included with the operating system as a **Feature**.</span></span>

1. <span data-ttu-id="8f14e-217">在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-217">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="8f14e-218">或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-218">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="8f14e-219">選取 **Windows Identity Foundation 3.5** 並繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="8f14e-219">Select **Windows Identity Foundation 3.5**, and continue with the installation.</span></span> 
3. <span data-ttu-id="8f14e-220">出現提示時，請重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-220">Restart the computer if prompted.</span></span>

## <a name="install-and-configure-smtp-server-optional"></a><span data-ttu-id="8f14e-221">安裝及設定 SMTP 伺服器 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-221">Install and configure SMTP Server (optional)</span></span>
<span data-ttu-id="8f14e-222">如果您使用 BAM 警示時，BizTalk Server 需要 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f14e-222">If you use BAM Alerts, BizTalk Server requires SMTP Server.</span></span> <span data-ttu-id="8f14e-223">如果不使用 BAM 警示，您可以略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-223">If you don't use BAM Alerts, you can skip this section.</span></span>

<span data-ttu-id="8f14e-224">SQL Server Database Mail 使用 SMTP 伺服器傳送 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="8f14e-224">SQL Server Database Mail uses an SMTP Server to send BAM Alerts.</span></span> <span data-ttu-id="8f14e-225">SMTP 伺服器可以安裝在本機 BizTalk Server 上，或安裝在安裝了 IIS 的另一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8f14e-225">SMTP Server can be installed locally on the BizTalk Server or on another server with IIS installed.</span></span> <span data-ttu-id="8f14e-226">Windows 8.1 或 Windows 10 等用戶端作業系統無法使用 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f14e-226">SMTP Server is not available on client operating systems, such as Windows 8.1 or Windows 10.</span></span> 

<span data-ttu-id="8f14e-227">SMTP 伺服器是隨附於伺服器作業系統的**功能**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-227">SMTP Server is included with server operating systems as a **Feature**.</span></span>

1. <span data-ttu-id="8f14e-228">在 [開始] 功能表中，開啟 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-228">In the Start menu, open **Turn Windows Features on or off**.</span></span> <span data-ttu-id="8f14e-229">或者，開啟 [伺服器管理員]，依序選取 [管理] 及 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-229">Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.</span></span>
2. <span data-ttu-id="8f14e-230">選取 [SMTP 伺服器] 並繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="8f14e-230">Select **SMTP Server**, and continue with the installation.</span></span> 
3. <span data-ttu-id="8f14e-231">出現提示時，請重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-231">Restart the computer if prompted.</span></span>

## <a name="install-microsoft-office-excel-2016-or-excel-2013-optional"></a><span data-ttu-id="8f14e-232">安裝 Microsoft Office Excel 2016 或 Excel 2013 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-232">Install Microsoft Office Excel 2016 or Excel 2013 (optional)</span></span>
<span data-ttu-id="8f14e-233">如果您使用商務活動監控 (BAM)，BizTalk Server 需要 Excel。</span><span class="sxs-lookup"><span data-stu-id="8f14e-233">If you use Business Activity Monitoring (BAM), BizTalk Server requires Excel.</span></span> <span data-ttu-id="8f14e-234">如果不使用 BAM，您可以略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-234">If you don't use BAM, you can skip this section.</span></span>

<span data-ttu-id="8f14e-235">BAM Office Excel 活頁簿可定義您想監控的商務程序。</span><span class="sxs-lookup"><span data-stu-id="8f14e-235">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="8f14e-236">您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="8f14e-236">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>

> [!IMPORTANT] 
> * <span data-ttu-id="8f14e-237">BizTalk Server 只支援 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="8f14e-237">BizTalk Server supports only 32-bit version of Microsoft Office.</span></span> 
> * <span data-ttu-id="8f14e-238">若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用的功能] 下的 [Visual Basic for Applications]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-238">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** (under **Office Shared Features**).</span></span> <span data-ttu-id="8f14e-239">否則，您可能會收到錯誤︰`This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`</span><span class="sxs-lookup"><span data-stu-id="8f14e-239">Otherwise, you may get error: `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`</span></span>

#### <a name="install-excel-2016"></a><span data-ttu-id="8f14e-240">安裝 Excel 2016</span><span class="sxs-lookup"><span data-stu-id="8f14e-240">Install Excel 2016</span></span>

<span data-ttu-id="8f14e-241">Office 2016 是使用「隨選即用」或 "C2R Installer" 安裝。</span><span class="sxs-lookup"><span data-stu-id="8f14e-241">Office 2016 is installed using "Click-to-Run" or "C2R Installer".</span></span> <span data-ttu-id="8f14e-242">C2R 安裝會下載並安裝 Office 中的所有程式。</span><span class="sxs-lookup"><span data-stu-id="8f14e-242">The C2R installation downloads and installs all programs within Office.</span></span> <span data-ttu-id="8f14e-243">至於 BAM，我們只需要 Excel。</span><span class="sxs-lookup"><span data-stu-id="8f14e-243">For BAM, we only need Excel.</span></span> <span data-ttu-id="8f14e-244">為解決這個問題，請下載並安裝 [Office 2016 部署工具](https://www.microsoft.com/download/details.aspx?id=49117) 自訂 C2R Installer。</span><span class="sxs-lookup"><span data-stu-id="8f14e-244">To work around this, download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117) to customize the C2R installer.</span></span>

1. <span data-ttu-id="8f14e-245">下載並安裝 [Office 2016 部署工具](https://www.microsoft.com/download/details.aspx?id=49117)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-245">Download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117).</span></span>
2. <span data-ttu-id="8f14e-246">在 Office 2016 部署工具檔案解壓縮的資料夾中，使用記事本等文字編輯器開啟 **configuration.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="8f14e-246">In the folder with the Office 2016 Deployment Tool files you extracted, open the **configuration.xml** file with a text editor, such as notepad.</span></span>
3. <span data-ttu-id="8f14e-247">以下列內容取代 `<Configuration>` 區段：</span><span class="sxs-lookup"><span data-stu-id="8f14e-247">Replace the `<Configuration>` section with the following:</span></span>  

    ```
    <Configuration>
    <Add SourcePath="D:\" OfficeClientEdition="32">
    <Product ID="O365ProPlusRetail" >
      <Language ID="en-us" />
      <ExcludeApp ID="Access" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="InfoPath" />
      <ExcludeApp ID="Lync" />
      <ExcludeApp ID="OneDrive" />
      <ExcludeApp ID="OneNote" />
      <ExcludeApp ID="Outlook" />
      <ExcludeApp ID="PowerPoint" />
      <ExcludeApp ID="Project" />
      <ExcludeApp ID="Publisher" />
      <ExcludeApp ID="SharePointDesigner" />
      <ExcludeApp ID="Visio" />
      <ExcludeApp ID="Word" />
    </Product>
    </Add>
    </Configuration>
    ```
    
    <span data-ttu-id="8f14e-248">以 Office 2016 ISO 檔案的位置取代 "SourcePath"。</span><span class="sxs-lookup"><span data-stu-id="8f14e-248">Replace “SourcePath” with the location of your Office 2016 ISO file.</span></span>
4. <span data-ttu-id="8f14e-249">在 Office 2016 部署工具檔案所在資料夾中，按住 **SHIFT** 鍵，再以滑鼠右鍵按一下資料夾的空白區域。</span><span class="sxs-lookup"><span data-stu-id="8f14e-249">In the folder with the Office 2016 Deployment Tool files, hold down the **SHIFT** key, and right-click an empty area in the folder.</span></span> <span data-ttu-id="8f14e-250">選取 [在此處開啟命令視窗]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-250">Select **Open command window here**.</span></span> 
5. <span data-ttu-id="8f14e-251">輸入下列命令啟動 Excel 安裝︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-251">Start the Excel installation by entering the following:</span></span>  
  `setup.exe /configure configuration.xml`

    > [!TIP]
    > <span data-ttu-id="8f14e-252">`setup.exe /download configuration.xml`下載所需的 Office 安裝程式檔案。</span><span class="sxs-lookup"><span data-stu-id="8f14e-252">`setup.exe /download configuration.xml` downloads the required office setup files.</span></span>
 
6. <span data-ttu-id="8f14e-253">選取 Excel 並繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="8f14e-253">Select Excel, and continue with the installation.</span></span> 
 
<span data-ttu-id="8f14e-254">**另請參閱**：[Office 部署工具的設定選項](https://technet.microsoft.com/library/jj219426.aspx)和[安裝 Office 2016 或 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)</span><span class="sxs-lookup"><span data-stu-id="8f14e-254">**SEE ALSO** : [Configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx) and [Install Office 2016 or 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)</span></span>

#### <a name="install-excel-2013"></a><span data-ttu-id="8f14e-255">安裝 Excel 2013</span><span class="sxs-lookup"><span data-stu-id="8f14e-255">Install Excel 2013</span></span>
1. <span data-ttu-id="8f14e-256">執行 Microsoft Office 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8f14e-256">Run the Microsoft Office setup.</span></span>
2. <span data-ttu-id="8f14e-257">選取 [自訂安裝]，然後選取 Excel。</span><span class="sxs-lookup"><span data-stu-id="8f14e-257">Select a **Custom Install**, and select Excel.</span></span>
3. <span data-ttu-id="8f14e-258">繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="8f14e-258">Continue with the installation.</span></span>   

## <a name="install-visual-c-redistributable-package"></a><span data-ttu-id="8f14e-259">安裝 Visual c + + 可轉散發套件</span><span class="sxs-lookup"><span data-stu-id="8f14e-259">Install Visual C++ redistributable package</span></span>

<span data-ttu-id="8f14e-260">下載並安裝[Visual c + + 可轉散發套件](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-260">Download and install the [Visual C++ redistributable package](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package).</span></span> <span data-ttu-id="8f14e-261">即使使用 Visual Studio 2015，2013 還是必要版本。</span><span class="sxs-lookup"><span data-stu-id="8f14e-261">The 2013 version is required, even though Visual Studio 2015 is used.</span></span>

<span data-ttu-id="8f14e-262">[Visual c + + 下載](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)列出所有可用的版本。</span><span class="sxs-lookup"><span data-stu-id="8f14e-262">The [Visual C++ downloads](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) lists all the available versions.</span></span>

## <a name="install-visual-studio-2015-optional"></a><span data-ttu-id="8f14e-263">安裝 Visual Studio 2015 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-263">Install Visual Studio 2015 (optional)</span></span>
<span data-ttu-id="8f14e-264">BizTalk Server 需要 Visual Studio 才能使用開發工具建立 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="8f14e-264">BizTalk Server requires Visual Studio to create BizTalk projects using the development tools.</span></span> <span data-ttu-id="8f14e-265">如果這是暫存或實際執行伺服器，或您不進行任何 BizTalk 開發，請略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-265">If this is a staging or production server, or you're not doing any BizTalk development, then skip this section.</span></span>

<span data-ttu-id="8f14e-266">建議使用 Visual Studio Enterprise 版，但也支援 Professional 及 Community 版。</span><span class="sxs-lookup"><span data-stu-id="8f14e-266">Visual Studio Enterprise Edition is recommended, but Professional and Community editions are also supported.</span></span> 

1. <span data-ttu-id="8f14e-267">以系統管理員身分執行 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8f14e-267">Run the Visual Studio setup as Administrator.</span></span>
2. <span data-ttu-id="8f14e-268">選取**預設**安裝。</span><span class="sxs-lookup"><span data-stu-id="8f14e-268">Select a **Default** installation.</span></span> <span data-ttu-id="8f14e-269">BizTalk Server 不需要任何選用的功能。</span><span class="sxs-lookup"><span data-stu-id="8f14e-269">BizTalk Server does not require any of the optional features.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8f14e-270">如果您還有將 Visual Studio 用於 BizTalk 專案之外的工作，請選取 [自訂]安裝以安裝其他功能。</span><span class="sxs-lookup"><span data-stu-id="8f14e-270">If you use Visual Studio for more than BizTalk projects, then select the **Custom** installation to install other features.</span></span> <span data-ttu-id="8f14e-271">一些常用功能包括 Microsoft Web 開發人員工具、Microsoft Office 開發人員工具、PowerShell Tools for Visual Studio 和 ClickOnce 發行工具。</span><span class="sxs-lookup"><span data-stu-id="8f14e-271">Some commonly-used features include Microsoft Web Developer Tools, Microsoft Office Developer Tools, PowerShell Tools for Visual Studio, and ClickOnce Publishing Tools.</span></span>
 
3. <span data-ttu-id="8f14e-272">繼續安裝作業，並在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-272">Continue with the installation, and restart your computer if prompted.</span></span>

<span data-ttu-id="8f14e-273">**另請參閱**：[安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)</span><span class="sxs-lookup"><span data-stu-id="8f14e-273">**SEE ALSO** : [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)</span></span>

> [!IMPORTANT]
> - <span data-ttu-id="8f14e-274">如果您是先安裝 Visual Studio 之後才安裝 BizTalk Server，則升級至 Visual Studio Team Explorer 時，可能需要修復 BizTalk Server 安裝。</span><span class="sxs-lookup"><span data-stu-id="8f14e-274">If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation.</span></span>
> - <span data-ttu-id="8f14e-275">Visual Studio 會自動安裝 BizTalk Server 不使用的 Microsoft SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="8f14e-275">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server.</span></span> <span data-ttu-id="8f14e-276">解除安裝 Microsoft SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="8f14e-276">Uninstall Microsoft SQL Server Express.</span></span> <span data-ttu-id="8f14e-277">您也可以解除安裝 Microsoft SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="8f14e-277">You can also uninstall Microsoft SQL Server Compact.</span></span>  
> - <span data-ttu-id="8f14e-278">BizTalk Server 開發工具是以 Visual Studio 為基礎。</span><span class="sxs-lookup"><span data-stu-id="8f14e-278">The BizTalk Server development tools are based on Visual Studio.</span></span> <span data-ttu-id="8f14e-279">您至少要先安裝 Microsoft Visual C#® .NET 元件，再安裝 BizTalk Server 開發者工具與 SDK。</span><span class="sxs-lookup"><span data-stu-id="8f14e-279">At a minimum, install the Microsoft Visual C#® .NET component before you install the BizTalk Server Developer Tools and SDK.</span></span>
> - <span data-ttu-id="8f14e-280">BizTalk Server 執行階段需要 .NET Framework 4.6。</span><span class="sxs-lookup"><span data-stu-id="8f14e-280">The BizTalk Server runtime requires .NET Framework 4.6.</span></span> <span data-ttu-id="8f14e-281">如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，.NET Framework 3.0 則需要</span><span class="sxs-lookup"><span data-stu-id="8f14e-281">If the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed, then .NET Framework 3.0 is required</span></span>

#### <a name="uninstall-sql-server-express"></a><span data-ttu-id="8f14e-282">解除安裝 SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="8f14e-282">Uninstall SQL Server Express</span></span>
1. <span data-ttu-id="8f14e-283">在 [開始] 功能表中，開啟 [程式和功能]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-283">In the Start menu, open **Programs and Features**.</span></span> <span data-ttu-id="8f14e-284">或者，開啟 [控制台]，選取 [解除安裝程式]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-284">Or, open the **Control Panel**, and select **Uninstall a program**.</span></span>
2. <span data-ttu-id="8f14e-285">解除安裝：</span><span class="sxs-lookup"><span data-stu-id="8f14e-285">Uninstall:</span></span> 
    - <span data-ttu-id="8f14e-286">Microsoft SQL Server 2014 Express LocalDb</span><span class="sxs-lookup"><span data-stu-id="8f14e-286">Microsoft SQL Server 2014 Express LocalDb</span></span>
    - <span data-ttu-id="8f14e-287">Microsoft SQL Server Compact 4.0 SP1 x64 ENU</span><span class="sxs-lookup"><span data-stu-id="8f14e-287">Microsoft SQL Server Compact 4.0 SP1 x64 ENU</span></span>
    - <span data-ttu-id="8f14e-288">Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)</span><span class="sxs-lookup"><span data-stu-id="8f14e-288">Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)</span></span>
    
3. <span data-ttu-id="8f14e-289">繼續解除安裝，並在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-289">Continue with the uninstall, and restart your computer if prompted.</span></span> 

## <a name="install-sql-server-2016"></a><span data-ttu-id="8f14e-290">安裝 SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="8f14e-290">Install SQL Server 2016</span></span>
<span data-ttu-id="8f14e-291">BizTalk Server 需要 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8f14e-291">BizTalk Server requires SQL Server.</span></span> <span data-ttu-id="8f14e-292">SQL Server 和 BizTalk 可以安裝在同一部電腦或不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="8f14e-292">SQL Server can be installed on the same computer as BizTalk, or on a different computer.</span></span> <span data-ttu-id="8f14e-293">大部分的生產環境都會將 BizTalk 和 SQL 安裝在不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8f14e-293">Most production environments install BizTalk and SQL on separate servers.</span></span> 

> [!IMPORTANT]
> - <span data-ttu-id="8f14e-294">不建議或支援 SQL Server Express 版。</span><span class="sxs-lookup"><span data-stu-id="8f14e-294">SQL Server Express Edition is not recommended or supported.</span></span> <span data-ttu-id="8f14e-295">Express 版不包含 BizTalk Server 需要的特定功能。</span><span class="sxs-lookup"><span data-stu-id="8f14e-295">The Express edition does not include certain features needed by BizTalk Server.</span></span>
> - <span data-ttu-id="8f14e-296">BizTalk Server 支援 SQL 標準版。</span><span class="sxs-lookup"><span data-stu-id="8f14e-296">BizTalk Server supports SQL Standard Edition.</span></span> <span data-ttu-id="8f14e-297">不過，若要使用商務活動監控即時彙總 (BAM RTA)，請安裝 SQL Server Enterprise 版。</span><span class="sxs-lookup"><span data-stu-id="8f14e-297">However, to use Business Activity Monitoring real-time aggregation (BAM RTA), install SQL Server Enterprise Edition.</span></span> <span data-ttu-id="8f14e-298">SQL Server Standard Edition 不支援 BAM 即時彙總 (RTA)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-298">BAM real-time aggregation (RTA) is not supported in the Standard Edition of SQL Server.</span></span>
> - <span data-ttu-id="8f14e-299">若要充分運用 BizTalk Server SDK 或從 Visual Studio 部署 BizTalk Server 應用程式，請安裝 SQL Server 開發工具。</span><span class="sxs-lookup"><span data-stu-id="8f14e-299">To fully use the BizTalk Server SDK or deploy BizTalk Server applications from a Visual Studio, install the SQL Server Development Tools.</span></span>
> - <span data-ttu-id="8f14e-300">除了二進位定序之外，BizTalk Server 支援所有區分大小寫及不區分大小寫的 SQL Server 定序。</span><span class="sxs-lookup"><span data-stu-id="8f14e-300">BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="8f14e-301">不支援二進位定序。</span><span class="sxs-lookup"><span data-stu-id="8f14e-301">Binary collations are not supported.</span></span>

<span data-ttu-id="8f14e-302">**如需特定安裝步驟，請參閱**[安裝 SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup)或[安裝 SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-302">**For specific install steps, see** [Install SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) or [Install SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).</span></span>

1. <span data-ttu-id="8f14e-303">啟動 SQL Server 安裝。</span><span class="sxs-lookup"><span data-stu-id="8f14e-303">Start the SQL Server installation.</span></span> 
2. <span data-ttu-id="8f14e-304">在安裝功能時，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="8f14e-304">During the Feature setup, select the following:</span></span>
    - <span data-ttu-id="8f14e-305">Database Engine Services</span><span class="sxs-lookup"><span data-stu-id="8f14e-305">Database Engine Services</span></span>
        - <span data-ttu-id="8f14e-306">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="8f14e-306">SQL Server Replication</span></span>
        - <span data-ttu-id="8f14e-307">R 服務 （資料庫） (**選擇性**; 在資訊[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))</span><span class="sxs-lookup"><span data-stu-id="8f14e-307">R Services (in-Database) (**optional**; info at [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))</span></span>
        - <span data-ttu-id="8f14e-308">搜尋的全文檢索和語意擷取</span><span class="sxs-lookup"><span data-stu-id="8f14e-308">Full-Text and Semantic Extractions for Search</span></span>
    - <span data-ttu-id="8f14e-309">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="8f14e-309">Analysis Services</span></span>
    - <span data-ttu-id="8f14e-310">Reporting Services - 原生</span><span class="sxs-lookup"><span data-stu-id="8f14e-310">Reporting Services - Native</span></span>
    - <span data-ttu-id="8f14e-311">共用功能</span><span class="sxs-lookup"><span data-stu-id="8f14e-311">Shared Features</span></span>
        - <span data-ttu-id="8f14e-312">用戶端工具連接性</span><span class="sxs-lookup"><span data-stu-id="8f14e-312">Client Tools Connectivity</span></span>
        - <span data-ttu-id="8f14e-313">Integration Services</span><span class="sxs-lookup"><span data-stu-id="8f14e-313">Integration Services</span></span>

    > [!NOTE]
    > <span data-ttu-id="8f14e-314">SQL Server 預設安裝不包含 **SQL Server Data Tools**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-314">**SQL Server Data Tools** is not included in the default installation of SQL Server.</span></span> <span data-ttu-id="8f14e-315">它不是必要的，但可在 [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) 下載。</span><span class="sxs-lookup"><span data-stu-id="8f14e-315">It is not required, but can be downloaded at [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).</span></span> <span data-ttu-id="8f14e-316">下載適用於所有支援的 SQL Server 版本的 [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，包括 Azure SQL Database。</span><span class="sxs-lookup"><span data-stu-id="8f14e-316">Download [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) that works with all supported versions of SQL Server, including Azure SQL Database.</span></span> 

3. <span data-ttu-id="8f14e-317">繼續安裝作業，並在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="8f14e-317">Continue with the installation, and restart the computer if prompted.</span></span>

## <a name="disable-shared-memory"></a><span data-ttu-id="8f14e-318">停用共用的記憶體</span><span class="sxs-lookup"><span data-stu-id="8f14e-318">Disable Shared Memory</span></span>

1. <span data-ttu-id="8f14e-319">開啟 **SQL Server 組態管理員**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-319">Open **SQL Server Configuration Manager**.</span></span>
2. <span data-ttu-id="8f14e-320">在 「 SQL Server 組態管理員 」 中，展開**SQL Server 網路組態**，然後選取**MSSQLSERVER 的通訊協定**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-320">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>
3. <span data-ttu-id="8f14e-321">以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-321">Right-click **Shared Memory**, and then select **Disable**.</span></span>
4. <span data-ttu-id="8f14e-322">選取**SQL Server 服務**，以滑鼠右鍵按一下 SQL **Server (MSSQLSERVER)**，然後選取**停止**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-322">Select **SQL Server Services**, right-click SQL **Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="8f14e-323">服務已停止之後，以滑鼠右鍵按一下**SQL Server (MSSQLSERVER)**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8f14e-323">After the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and then select **Start**.</span></span>
5. <span data-ttu-id="8f14e-324">關閉 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-324">Close **SQL Server Configuration Manager**.</span></span>

<span data-ttu-id="8f14e-325">一般而言，共用記憶體通訊協定只會影響與 SQL Server 在相同電腦安裝的用戶端 (BizTalk Server)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-325">Typically, the Shared Memory protocol only impacts clients (BizTalk Server) that are installed on the same computer as SQL Server.</span></span> <span data-ttu-id="8f14e-326">某些壓力狀況下 （例如從同一部電腦存取 SQL Server 用戶端），SQL Server Shared Memory 通訊協定可能會降低執行 BizTalk Server 效能。</span><span class="sxs-lookup"><span data-stu-id="8f14e-326">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance.</span></span> <span data-ttu-id="8f14e-327">停用 Shared Memory 網路通訊協定會解決問題。</span><span class="sxs-lookup"><span data-stu-id="8f14e-327">Disabling the Shared Memory network protocol resolves this.</span></span>

> [!TIP]
> <span data-ttu-id="8f14e-328">SQL Server 代理程式無法停用 Shared Memory 之後, 啟動，然後確認[ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)安裝。</span><span class="sxs-lookup"><span data-stu-id="8f14e-328">If SQL Server Agent fails to start after disabling Shared Memory, then confirm [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) is installed.</span></span>

## <a name="install-sql-xml-4"></a><span data-ttu-id="8f14e-329">安裝 SQL XML 4</span><span class="sxs-lookup"><span data-stu-id="8f14e-329">Install SQL XML 4</span></span>
<span data-ttu-id="8f14e-330">BizTalk Server 執行階段、系統管理工具和 BAM 的必要項目。</span><span class="sxs-lookup"><span data-stu-id="8f14e-330">Required for BizTalk Server Runtime, Administrative Tools, and BAM.</span></span> 

<span data-ttu-id="8f14e-331">下載並安裝[SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-331">Download and install [SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>

## <a name="configure-sql-server-database-mail-optional"></a><span data-ttu-id="8f14e-332">設定 SQL Server Database Mail (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8f14e-332">Configure SQL Server Database Mail (optional)</span></span>
<span data-ttu-id="8f14e-333">如果您使用 BAM 警示時，BizTalk Server 需要 SQL Server Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8f14e-333">If you use BAM Alerts, BizTalk Server requires SQL Server Database Mail.</span></span> <span data-ttu-id="8f14e-334">如果不使用 BAM 警示，您可以略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-334">If you don't use BAM Alerts, then skip this section.</span></span> 

<span data-ttu-id="8f14e-335">**另請參閱**︰更多 [Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail) 資訊。</span><span class="sxs-lookup"><span data-stu-id="8f14e-335">**SEE ALSO** : More on [Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail).</span></span>

> [!IMPORTANT]
> - <span data-ttu-id="8f14e-336">您需要知道 SMTP 伺服器的伺服器名稱和 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8f14e-336">You need to know the server name and TCP port number for the SMTP Server.</span></span> <span data-ttu-id="8f14e-337">如果 IIS 和 SMTP 伺服器都安裝在這部電腦上，您使用的是本機 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f14e-337">If you installed IIS and SMTP Server on this same computer, then you use the local SMTP Server.</span></span> <span data-ttu-id="8f14e-338">如果 SMTP 伺服器需要驗證，請準備好使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8f14e-338">If the SMTP server requires authentication, then have the user name and password ready.</span></span>
> - <span data-ttu-id="8f14e-339">BAM 入口網站和 BAM 警示是不同的功能。</span><span class="sxs-lookup"><span data-stu-id="8f14e-339">The BAM portal and BAM Alerts are separate features.</span></span> <span data-ttu-id="8f14e-340">如果使用 BAM 警示，則需要 SQL Server Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8f14e-340">If you are using BAM Alerts, then SQL Server Database Mail is required.</span></span> <span data-ttu-id="8f14e-341">如果不使用 BAM 警示，則不需要 SQL Server Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8f14e-341">If you are not using BAM Alerts, then SQL Server Database Mail is not required.</span></span>

<span data-ttu-id="8f14e-342">**針對特定的設定步驟，請參閱**： 設定[SQL Server 2016 Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail)或[SQL Server 2014 Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-342">**For specific configuration steps, see**: Configure [SQL Server 2016 Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail) or [SQL Server 2014 Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx).</span></span>

   
<span data-ttu-id="8f14e-343">傳送測試電子郵件︰</span><span class="sxs-lookup"><span data-stu-id="8f14e-343">To send a test email:</span></span> 
1.  <span data-ttu-id="8f14e-344">以滑鼠右鍵按一下 **Database Mail**，然後選取 [傳送測試電子郵件]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-344">Right-click **Database Mail**, and select **Send Test E-Mail**.</span></span> 
2.  <span data-ttu-id="8f14e-345">輸入**收件者**電子郵件地址，然後選取 [傳送測試電子郵件]。</span><span class="sxs-lookup"><span data-stu-id="8f14e-345">Enter a **To:** email address, and select **Send Test E-Mail**.</span></span>  
 
<span data-ttu-id="8f14e-346">如果「收件者」收信人收到電子郵件，即表示已設定 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="8f14e-346">If the **To:** recipient receives the email, then Database Mail is configured.</span></span> 

## <a name="install-winscp-optional"></a><span data-ttu-id="8f14e-347">安裝 WinSCP （選擇性）</span><span class="sxs-lookup"><span data-stu-id="8f14e-347">Install WinSCP (optional)</span></span>
<span data-ttu-id="8f14e-348">所需的 FTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="8f14e-348">Required by the FTP adapter.</span></span> <span data-ttu-id="8f14e-349">如果您不使用 FTP 配接器，然後略過本節。</span><span class="sxs-lookup"><span data-stu-id="8f14e-349">If you don't use the FTP adapter, then skip this section.</span></span> 

<span data-ttu-id="8f14e-350">下載並安裝[WinSCP](http://winscp.net)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-350">Download and install [WinSCP](http://winscp.net).</span></span> 

## <a name="next-step"></a><span data-ttu-id="8f14e-351">下一步</span><span class="sxs-lookup"><span data-stu-id="8f14e-351">Next step</span></span>
<span data-ttu-id="8f14e-352">安裝 [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="8f14e-352">Install [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md).</span></span>
