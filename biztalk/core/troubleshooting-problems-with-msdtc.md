---
title: MSDTC 問題疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f39cde52-da8f-4cc1-bdc5-e4b828891a79
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c244ec27cd3e584f7fb22a34effeaf0033c3e78a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280502"
---
# <a name="troubleshooting-problems-with-msdtc"></a><span data-ttu-id="e5320-102">MSDTC 問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="e5320-102">Troubleshooting Problems with MSDTC</span></span>
<span data-ttu-id="e5320-103">大部分 BizTalk Server 執行階段作業都需要 Microsoft 分散式交易協調器 (MSDTC) 支援，以確保作業在交易上的一致。</span><span class="sxs-lookup"><span data-stu-id="e5320-103">Most BizTalk Server runtime operations require Microsoft Distributed Transaction Coordinator (MSDTC) support to ensure that the operations are transactionally consistent.</span></span> <span data-ttu-id="e5320-104">如果沒有 MSDTC 交易支援，則關聯的 BizTalk Server 執行階段作業將無法繼續。</span><span class="sxs-lookup"><span data-stu-id="e5320-104">If MSDTC transaction support is not available, then the associated BizTalk Server runtime operations cannot proceed.</span></span> <span data-ttu-id="e5320-105">未正確設定 MSDTC 交易支援時，通常會受到影響的 BizTalk 元件包括 (但不限於) 單一登入服務、BizTalk 主控件執行個體，以及任何經由 BizTalk Server 所連接的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5320-105">The components of BizTalk that are commonly affected when MSDTC transaction support is not configured correctly include (but are not limited to) the Single Sign-On Service, BizTalk host instances, and any SQL Server instances that are connected to by BizTalk Server.</span></span> <span data-ttu-id="e5320-106">本節包含描述 MSDTC 相關錯誤的資訊，以及可供遵循以診斷和解決 MSDTC 問題的步驟。</span><span class="sxs-lookup"><span data-stu-id="e5320-106">This section contains information that describes MSDTC related errors and steps that can be followed to diagnose and resolve problems with MSDTC.</span></span>  
  
## <a name="errors-that-can-occur-if-msdtc-transaction-support-is-not-configured-correctly"></a><span data-ttu-id="e5320-107">未正確設定 MSDTC 交易支援時可能發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="e5320-107">Errors that can occur if MSDTC transaction support is not configured correctly</span></span>  
 <span data-ttu-id="e5320-108">當 BizTalk 環境中之電腦上的 MSDTC 交易支援設定不正確時，可能會發生類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="e5320-108">Errors similar to the following may occur on BizTalk Server when MSDTC transaction support is not configured correctly on the computers in a BizTalk environment:</span></span>  
  
-   <span data-ttu-id="e5320-109">「Microsoft 分散式交易協調器 (DTC) 的問題導致無法連線到組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="e5320-109">"A Microsoft Distributed Transaction Coordinator problem prevented connection to the Configuration database.</span></span> <span data-ttu-id="e5320-110">交易管理員已停用對遠端/網路交易的支援」。</span><span class="sxs-lookup"><span data-stu-id="e5320-110">The transaction manager has disabled its support for remote/network transactions".</span></span>  
  
-   <span data-ttu-id="e5320-111">「Microsoft 分散式交易協調器 (DTC) 的問題導致無法連線到組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="e5320-111">"A Microsoft Distributed Transaction Coordinator problem prevented connection to the Configuration database.</span></span> <span data-ttu-id="e5320-112">已隱含或明確地認可或中止交易」。</span><span class="sxs-lookup"><span data-stu-id="e5320-112">The transaction has already been implicitly or explicitly committed or aborted".</span></span>  
  
-   <span data-ttu-id="e5320-113">「錯誤碼：0x8004d00a - 無法在指定的異動協調器中編列異動」。</span><span class="sxs-lookup"><span data-stu-id="e5320-113">"Error Code: 0x8004d00a, New transaction cannot enlist in the specified transaction coordinator".</span></span>  
  
-   <span data-ttu-id="e5320-114">「無法從組態存放區擷取接收位置 'MySample ReceiveLocation' 的傳輸類型資料。</span><span class="sxs-lookup"><span data-stu-id="e5320-114">"Could not retrieve transport type data for Receive Location 'MySample ReceiveLocation' from config store.</span></span> <span data-ttu-id="e5320-115">主要 SSO Server 'MyServer' 失敗。</span><span class="sxs-lookup"><span data-stu-id="e5320-115">Primary SSO Server 'MyServer' failed.</span></span> <span data-ttu-id="e5320-116">RPC 伺服器無法使用」。</span><span class="sxs-lookup"><span data-stu-id="e5320-116">The RPC server is unavailable".</span></span>  
  
-   <span data-ttu-id="e5320-117">「錯誤碼：0x8004d025，協力電腦異動管理員已經停用了對遠端/網路異動的支援」。</span><span class="sxs-lookup"><span data-stu-id="e5320-117">"Error Code: 0x8004d025, The partner transaction manager has disabled its support for remote/network transactions".</span></span>  
  
-   <span data-ttu-id="e5320-118">「錯誤碼：0xc0002a24，無法匯入 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="e5320-118">"Error Code: 0xc0002a24, Could not import a DTC transaction.</span></span> <span data-ttu-id="e5320-119">請檢查 MSDTC 是否已正確設定為支援遠端作業」。</span><span class="sxs-lookup"><span data-stu-id="e5320-119">Please check that MSDTC is configured correctly for remote operation".</span></span>  
  
-   <span data-ttu-id="e5320-120">「0x8004d01c</span><span class="sxs-lookup"><span data-stu-id="e5320-120">"0x8004d01c</span></span>  
  
     <span data-ttu-id="e5320-121">[0x1705] 建立內部工作項目時發生失敗。</span><span class="sxs-lookup"><span data-stu-id="e5320-121">[0x1705] There was a failure creating the internal work item.</span></span>  
  
     <span data-ttu-id="e5320-122">請確定 SQL Server 正在執行」。</span><span class="sxs-lookup"><span data-stu-id="e5320-122">Make sure that SQL Server is running."</span></span>  
  
 <span data-ttu-id="e5320-123">若要解決 MSDTC 組態錯誤，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="e5320-123">To resolve MSDTC configuration errors, follow the steps below.</span></span>  
  
## <a name="ensure-netbios-name-resolution-between-the-biztalk-server-and-remote-servers-is-successful"></a><span data-ttu-id="e5320-124">確定 BizTalk Server 與遠端伺服器之間的 NetBIOS 名稱解析成功</span><span class="sxs-lookup"><span data-stu-id="e5320-124">Ensure NetBIOS name resolution between the BizTalk Server and remote servers is successful</span></span>  
 <span data-ttu-id="e5320-125">用戶端電腦必須能夠將伺服器電腦的 NetBIOS 名稱解析為正確的 IP 位址，而且伺服器電腦也能夠將用戶端電腦的 NetBIOS 名稱解析為正確的 IP 位址，電腦之間的 MSDTC 交易才會成功。</span><span class="sxs-lookup"><span data-stu-id="e5320-125">Successful MSDTC transactions between computers require that the client computer is able to resolve the NetBIOS name of the server computer to the correct IP address and the server computer is able to resolve the NetBIOS name of the client computer to the correct IP address.</span></span> <span data-ttu-id="e5320-126">若要確認 NetBIOS 名稱解析在兩個方向 (用戶端至伺服器以及伺服器至用戶端) 上都運作正常，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e5320-126">To verify that NetBIOS name resolution works in both directions (client to server and server to client) follow these steps:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5320-127">NetBIOS 名稱又常稱為 **網路** 名稱。</span><span class="sxs-lookup"><span data-stu-id="e5320-127">The NetBIOS name is also commonly referred to as the **Network** name.</span></span>  
  
1.  <span data-ttu-id="e5320-128">判斷每一台電腦的 NetBIOS 名稱：</span><span class="sxs-lookup"><span data-stu-id="e5320-128">Determine the NetBIOS name of each computer:</span></span>  
  
    1.  <span data-ttu-id="e5320-129">在 **[我的電腦]** 上按一下滑鼠右鍵顯示 **[系統內容]** 對話方塊，再按一下 **[電腦名稱]** 索引標籤檢視指派給電腦的 **[完整電腦名稱]** 。</span><span class="sxs-lookup"><span data-stu-id="e5320-129">Right-click **My Computer** to display the **System Properties** dialog and click the **Computer Name** tab to view the **Full computer name** assigned to the computer.</span></span>  
  
    2.  <span data-ttu-id="e5320-130">NetBIOS 名稱是指派為 **[完整電腦名稱]** 的第一個部分；例如，如果 **[完整電腦名稱]** 列出的是 myserver.company.domain.com，則電腦的 NetBIOS 名稱就是 **myserver**。</span><span class="sxs-lookup"><span data-stu-id="e5320-130">The NetBIOS name is the first portion of the name designated as the **Full computer name** so for example if the **Full computer name** is listed as myserver.company.domain.com, then the NetBIOS name of the computer is **myserver**.</span></span>  
  
2.  <span data-ttu-id="e5320-131">判斷 IP 位址或與每台電腦關聯的位址：</span><span class="sxs-lookup"><span data-stu-id="e5320-131">Determine the IP Address or addresses that are associated with each computer:</span></span>  
  
    1.  <span data-ttu-id="e5320-132">在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-132">Launch a command prompt on the client computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ipconfig /all  
        ```  
  
    2.  <span data-ttu-id="e5320-133">命令提示字元視窗會列出 IP 位址或與每台電腦關聯的位址。</span><span class="sxs-lookup"><span data-stu-id="e5320-133">The IP address or addresses associated with the client computer are listed in the command prompt window.</span></span>  
  
    3.  <span data-ttu-id="e5320-134">在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-134">Launch a command prompt on the server computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ipconfig /all  
        ```  
  
    4.  <span data-ttu-id="e5320-135">命令提示字元視窗會列出 IP 位址或與伺服器電腦關聯的位址。</span><span class="sxs-lookup"><span data-stu-id="e5320-135">The IP address or addresses associated with the server computer are listed in the command prompt window.</span></span>  
  
3.  <span data-ttu-id="e5320-136">確認每一台電腦的 NetBIOS 名稱已解析為其中一個與電腦關聯的 IP 位址：</span><span class="sxs-lookup"><span data-stu-id="e5320-136">Verify that the NetBIOS name of each computer is resolved to one of the IP addresses associated with the computer:</span></span>  
  
    1.  <span data-ttu-id="e5320-137">在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-137">Launch a command prompt on the client computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ping <NetBIOS name of server computer>  
        ```  
  
         <span data-ttu-id="e5320-138">ping 命令的結果應該會傳回與伺服器電腦關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e5320-138">The results of the ping command should return an IP address associated with the server computer.</span></span>  
  
    2.  <span data-ttu-id="e5320-139">在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-139">Launch a command prompt on the server computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ping <NetBIOS name of client computer>  
        ```  
  
         <span data-ttu-id="e5320-140">ping 命令的結果應該會傳回與用戶端電腦關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e5320-140">The results of the ping command should return an IP address associated with the client computer.</span></span>  
  
4.  <span data-ttu-id="e5320-141">確認與每一台電腦的 NetBIOS 名稱相關聯的反向名稱查詢都會解析為正確的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="e5320-141">Verify that reverse name lookup of the IP address associated with the NetBIOS name on each computer resolves to the correct computer name.</span></span>  
  
    1.  <span data-ttu-id="e5320-142">在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-142">Launch a command prompt on the client computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ping -a <IP Address associated with client computer NetBIOS name>  
        ```  
  
         <span data-ttu-id="e5320-143">ping 命令的結果會傳回 NetBIOS 名稱，或與用於步驟 3a 中的 NetBIOS 名稱相對應的完整格式網域名稱。</span><span class="sxs-lookup"><span data-stu-id="e5320-143">The results of the ping command should return a NetBIOS name or fully qualified domain name that corresponds to the NetBIOS name that was used in step 3a.</span></span> <span data-ttu-id="e5320-144">如果傳回的名稱與步驟 3a 中使用的 NetBIOS 名稱不符合或與該名稱不對應，則 IP 位址的反向查詢會失敗，而這可能導致 MSDTC 交易失敗。</span><span class="sxs-lookup"><span data-stu-id="e5320-144">If the name returned does not match or correspond to the NetBIOS name used in step 3a then IP address reverse lookup will fail which can cause MSDTC transactions to fail.</span></span>  
  
    2.  <span data-ttu-id="e5320-145">在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e5320-145">Launch a command prompt on the server computer, type the following command, and then press ENTER:</span></span>  
  
        ```  
        ping -a <IP Address associated with server computer NetBIOS name>  
        ```  
  
         <span data-ttu-id="e5320-146">ping 命令的結果會傳回 NetBIOS 名稱，或與用於步驟 3b 中的 NetBIOS 名稱相對應的完整格式網域名稱。</span><span class="sxs-lookup"><span data-stu-id="e5320-146">The results of the ping command should return a NetBIOS name or fully qualified domain name that corresponds to the NetBIOS name that was used in step 3b.</span></span> <span data-ttu-id="e5320-147">如果傳回的名稱與步驟 3b 中使用的 NetBIOS 名稱不符合或與該名稱不對應，則 IP 位址的反向查詢會失敗，而這可能導致 MSDTC 交易失敗。</span><span class="sxs-lookup"><span data-stu-id="e5320-147">If the name returned does not match or correspond to the NetBIOS name used in step 3b then IP address reverse lookup will fail which can cause MSDTC transactions to fail.</span></span>  
  
 <span data-ttu-id="e5320-148">如果 NetBIOS 名稱解析在兩個方向上都不成功，或者如果反向名稱查詢失敗，請在 DNS 伺服器、NetBIOS 名稱伺服器、HOSTS 檔案或 LMHOSTS 檔案中輸入適當的項目以修正問題。</span><span class="sxs-lookup"><span data-stu-id="e5320-148">If NetBIOS name resolution is not successful in either direction or if reverse name lookup fails then make the appropriate entries in the DNS server, NetBIOS name server, HOSTS file, or LMHOSTS file to correct the problem.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5320-149">電腦使用的名稱解析方法因電腦的 NetBIOS 節點類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e5320-149">The method of name resolution used by the computer varies depending on the NetBIOS node type of the computer.</span></span> <span data-ttu-id="e5320-150">如需 NetBIOS 節點類型的詳細資訊，請參閱 [NetBIOS 名稱解析](http://go.microsoft.com/fwlink/?LinkId=201638)。</span><span class="sxs-lookup"><span data-stu-id="e5320-150">For more information about NetBIOS node types, see [NetBIOS Name Resolution](http://go.microsoft.com/fwlink/?LinkId=201638).</span></span>  
  
## <a name="ensure-that-a-firewall-between-the-biztalk-server-and-remote-servers-is-not-blocking-ports-required-for-rpc-dynamic-port-allocation"></a><span data-ttu-id="e5320-151">確定 BizTalk Server 和遠端伺服器之間的防火牆沒有封鎖 RPC 動態連接埠配置所需的連接埠</span><span class="sxs-lookup"><span data-stu-id="e5320-151">Ensure that a firewall between the BizTalk Server and remote servers is not blocking ports required for RPC dynamic port allocation</span></span>  
 <span data-ttu-id="e5320-152">網路上的 MSDTC 功能依存於網路上的 RPC 功能。</span><span class="sxs-lookup"><span data-stu-id="e5320-152">MSDTC functionality over the network depends upon RPC functionality over the network.</span></span> <span data-ttu-id="e5320-153">您必須開啟特定連接埠以配合 RPC 動態連接埠配置，才能透過防火牆使用 RPC 功能。</span><span class="sxs-lookup"><span data-stu-id="e5320-153">RPC functionality through a firewall requires that specific ports are open to accommodate RPC dynamic port allocation.</span></span> <span data-ttu-id="e5320-154">如果防火牆位於 BizTalk Server 和遠端伺服器之間，請依照 [如何設定 RPC 動態連接埠配置以使用防火牆](http://go.microsoft.com/fwlink/?LinkId=66831) 中的步驟來配合 RPC 動態連接埠配置。</span><span class="sxs-lookup"><span data-stu-id="e5320-154">If a firewall is in place between the BizTalk Server and remote servers, follow the steps in [How to configure RPC dynamic port allocation to work with firewalls](http://go.microsoft.com/fwlink/?LinkId=66831) to accommodate RPC dynamic port allocation.</span></span>  
  
## <a name="set-the-appropriate-msdtc-security-configuration-options"></a><span data-ttu-id="e5320-155">設定適當的 MSDTC 安全性組態選項</span><span class="sxs-lookup"><span data-stu-id="e5320-155">Set the appropriate MSDTC Security Configuration options</span></span>  
 <span data-ttu-id="e5320-156">Windows 提供安全性增強功能來控管如何透過網路存取 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="e5320-156">Windows provides security enhancements that govern how MSDTC is accessed over a network.</span></span> <span data-ttu-id="e5320-157">您可以藉由修改 MSDTC 安全性設定，控制遠端電腦在網路上與 MSDTC 的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="e5320-157">By modifying the MSDTC security settings, you control how MSDTC communicates with remote computers over the network.</span></span> <span data-ttu-id="e5320-158">下表列出進行 MSDTC 安全性設定時，針對可用選項的建議值：</span><span class="sxs-lookup"><span data-stu-id="e5320-158">This table lists the recommended values for the options that are available when configuring MSDTC security settings:</span></span>  
  
|<span data-ttu-id="e5320-159">組態選項</span><span class="sxs-lookup"><span data-stu-id="e5320-159">Configuration Option</span></span>|<span data-ttu-id="e5320-160">預設值</span><span class="sxs-lookup"><span data-stu-id="e5320-160">Default Value</span></span>|<span data-ttu-id="e5320-161">建議值</span><span class="sxs-lookup"><span data-stu-id="e5320-161">Recommended Value</span></span>|  
|--------------------------|-------------------|-----------------------|  
|<span data-ttu-id="e5320-162">網路 DTC 存取</span><span class="sxs-lookup"><span data-stu-id="e5320-162">Network DTC Access</span></span>|<span data-ttu-id="e5320-163">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-163">Disabled</span></span>|<span data-ttu-id="e5320-164">已啟用</span><span class="sxs-lookup"><span data-stu-id="e5320-164">Enabled</span></span>|  
|<span data-ttu-id="e5320-165">**用戶端和管理**</span><span class="sxs-lookup"><span data-stu-id="e5320-165">**Client and Administration**</span></span>|||  
|<span data-ttu-id="e5320-166">允許遠端用戶端</span><span class="sxs-lookup"><span data-stu-id="e5320-166">Allow Remote Clients</span></span>|<span data-ttu-id="e5320-167">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-167">Disabled</span></span>|<span data-ttu-id="e5320-168">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-168">Disabled</span></span>|  
|<span data-ttu-id="e5320-169">允許遠端系統管理</span><span class="sxs-lookup"><span data-stu-id="e5320-169">Allow Remote Administration</span></span>|<span data-ttu-id="e5320-170">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-170">Disabled</span></span>|<span data-ttu-id="e5320-171">已停用</span><span class="sxs-lookup"><span data-stu-id="e5320-171">Disabled</span></span>|  
|<span data-ttu-id="e5320-172">**交易管理員通訊**</span><span class="sxs-lookup"><span data-stu-id="e5320-172">**Transaction Manager Communication**</span></span>|||  
|<span data-ttu-id="e5320-173">允許輸入</span><span class="sxs-lookup"><span data-stu-id="e5320-173">Allow Inbound</span></span>|<span data-ttu-id="e5320-174">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-174">Disabled</span></span>|<span data-ttu-id="e5320-175">已啟用</span><span class="sxs-lookup"><span data-stu-id="e5320-175">Enabled</span></span>|  
|<span data-ttu-id="e5320-176">允許輸出</span><span class="sxs-lookup"><span data-stu-id="e5320-176">Allow Outbound</span></span>|<span data-ttu-id="e5320-177">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-177">Disabled</span></span>|<span data-ttu-id="e5320-178">已啟用</span><span class="sxs-lookup"><span data-stu-id="e5320-178">Enabled</span></span>|  
|<span data-ttu-id="e5320-179">需要相互驗證</span><span class="sxs-lookup"><span data-stu-id="e5320-179">Mutual Authentication Required</span></span>|<span data-ttu-id="e5320-180">已啟用</span><span class="sxs-lookup"><span data-stu-id="e5320-180">Enabled</span></span>|<span data-ttu-id="e5320-181">如果所有的遠端電腦都在執行 Windows Server 2003 SP1、Windows XP SP2 或更新版本，並且設定為「需要相互驗證」，則為已啟用。</span><span class="sxs-lookup"><span data-stu-id="e5320-181">Enabled if all remote machines are running Windows Server 2003 SP1 or Windows XP SP2 or higher, and are configured with “Mutual Authentication Required”.</span></span>|  
|<span data-ttu-id="e5320-182">要求對連入呼叫者驗證</span><span class="sxs-lookup"><span data-stu-id="e5320-182">Incoming Caller Authentication Required</span></span>|<span data-ttu-id="e5320-183">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-183">Disabled</span></span>|<span data-ttu-id="e5320-184">如果在叢集上執行 MSDTC，則啟用此項。</span><span class="sxs-lookup"><span data-stu-id="e5320-184">Enabled if running MSDTC on cluster.</span></span>|  
|<span data-ttu-id="e5320-185">不需要驗證</span><span class="sxs-lookup"><span data-stu-id="e5320-185">No Authentication Required</span></span>|<span data-ttu-id="e5320-186">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-186">Disabled</span></span>|<span data-ttu-id="e5320-187">如果遠端電腦是 Windows Server 2003 SP1 之前的版本或 Windows XP SP2 之前的版本，則啟用此項。</span><span class="sxs-lookup"><span data-stu-id="e5320-187">Enabled if remote machines are pre-Windows Server 2003 SP1 or pre- Windows XP SP2.</span></span>|  
|<span data-ttu-id="e5320-188">啟用 TIP</span><span class="sxs-lookup"><span data-stu-id="e5320-188">Enable TIP</span></span>|<span data-ttu-id="e5320-189">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-189">Disabled</span></span>|<span data-ttu-id="e5320-190">如果執行 BAM 入口網站，則啟用此項。</span><span class="sxs-lookup"><span data-stu-id="e5320-190">Enabled if running the BAM Portal.</span></span>|  
|<span data-ttu-id="e5320-191">啟用 XA 交易</span><span class="sxs-lookup"><span data-stu-id="e5320-191">Enable XA Transactions</span></span>|<span data-ttu-id="e5320-192">Disabled</span><span class="sxs-lookup"><span data-stu-id="e5320-192">Disabled</span></span>|<span data-ttu-id="e5320-193">如果是與使用 MQSeries 配接器的 XA 交易系統進行通訊 (例如與 IBM WebSphere MQ 通訊時)，則啟用此項。</span><span class="sxs-lookup"><span data-stu-id="e5320-193">Enabled if communicating with an XA based transactional system such as when communicating with IBM WebSphere MQ using the MQSeries adapter.</span></span>|  
  
 <span data-ttu-id="e5320-194">在套用這些變更後，MSDTC 服務就會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e5320-194">After applying these changes, the MSDTC service will be restarted.</span></span>  
  
 <span data-ttu-id="e5320-195">若要存取 MSDTC 安全性組態選項，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="e5320-195">To access the MSDTC security configuration options follow these steps:</span></span>  
  
1.  <span data-ttu-id="e5320-196">依序按一下 [開始] 與 [執行] ，然後輸入 **dcomcnfg** ，以啟動 [元件服務] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e5320-196">Click **Start**, click **Run**, and type **dcomcnfg** to launch the **Component Services**Management console.</span></span>  
  
2.  <span data-ttu-id="e5320-197">按一下以展開 **[元件服務]** ，然後再按一下以展開 **[電腦]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-197">Click to expand **Component Services** and click to expand **Computers**.</span></span>  
  
3.  <span data-ttu-id="e5320-198">依按一下 [我的電腦] 與 [分散式交易協調器] 加以展開，再於 [本機 DTC] 上按一下滑鼠右鍵，然後按一下 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="e5320-198">Click to expand **My Computer**, click to expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e5320-199">按一下 [本機 DTC 內容]  對話方塊中的 [安全性]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5320-199">Click the **Security** tab of the **Local DTC Properties** dialog.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5320-200">依照所做的變更，您可能需要重新啟動電腦以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5320-200">Depending on the changes that were made, you may need to reboot the computer to enact the changes.</span></span> <span data-ttu-id="e5320-201">如果在套用變更及重新啟動 MSDTC 服務之後仍遭遇問題，請將其上進行了變更的電腦重新啟動，以確保這些變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5320-201">If you are still encountering problems after applying changes and restarting the MSDTC service, reboot the computer on which the changes were made to ensure that the changes take effect.</span></span>  
  
 <span data-ttu-id="e5320-202">如果啟用 **[要求相互驗證]** 或 **[要求對連入呼叫者驗證]** 組態選項，則必須對用戶端電腦帳戶授與 **[從網路存取這台電腦]** 使用者權限。</span><span class="sxs-lookup"><span data-stu-id="e5320-202">If either the **Mutual Authentication Required** or the **Incoming Caller Authentication Required** configuration options are enabled then the client(s) computer account must be granted the **Access this computer from the network** user right.</span></span> <span data-ttu-id="e5320-203">如果並未對用戶端電腦的電腦帳戶授與 **[從網路存取這台電腦]** 使用者權限，或者該帳戶是包含在 **[拒絕從網路存取這台電腦]** 使用者權限中，則用戶端和伺服器電腦之間的 DTC 通訊會失敗。</span><span class="sxs-lookup"><span data-stu-id="e5320-203">If the computer account for a client computer is not granted the **Access this computer from the network** user right, or is included in the **Deny access to this computer from the network** user right, then DTC communication between the client and server computer will fail.</span></span>  
  
 <span data-ttu-id="e5320-204">預設設定是對 Everyone 群組授與 **[從網路存取這台電腦]** 使用者權限。</span><span class="sxs-lookup"><span data-stu-id="e5320-204">The default setting is to grant the Everyone group the **Access this computer from the network** user right.</span></span> <span data-ttu-id="e5320-205">因此，這個使用者權限不需變更，除非預設設定已經修改。</span><span class="sxs-lookup"><span data-stu-id="e5320-205">Therefore this user right will not need to be changed unless the default setting has been modified.</span></span> <span data-ttu-id="e5320-206">如果已啟用 **[不需要驗證]** 組態選項，則 **[從網路存取這台電腦]** 使用者權限就不會套用至用戶端電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="e5320-206">If the **No Authentication Required** configuration option is enabled then the **Access this computer from the network** user right does not apply to the client(s) computer account.</span></span>  
  
 <span data-ttu-id="e5320-207">若要變更被授與 [從網路存取這台電腦] 使用者權限的使用者或群組，請依照下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="e5320-207">To change the users or groups that are granted the "Access this computer from the network" user right, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e5320-208">依序按一下 **[開始]**、 **[執行]**，然後輸入 **Gpedit.msc**，再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-208">Click **Start**, click **Run**, type **Gpedit.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="e5320-209">展開 [本機電腦原則] 清單中的下列項目：</span><span class="sxs-lookup"><span data-stu-id="e5320-209">Expand the following items in the Local Computer Policy list:</span></span>  
  
    -   <span data-ttu-id="e5320-210">電腦組態</span><span class="sxs-lookup"><span data-stu-id="e5320-210">Computer Configuration</span></span>  
  
    -   <span data-ttu-id="e5320-211">Windows 設定</span><span class="sxs-lookup"><span data-stu-id="e5320-211">Windows Settings</span></span>  
  
    -   <span data-ttu-id="e5320-212">安全性設定</span><span class="sxs-lookup"><span data-stu-id="e5320-212">Security Settings</span></span>  
  
    -   <span data-ttu-id="e5320-213">本機原則</span><span class="sxs-lookup"><span data-stu-id="e5320-213">Local Policies</span></span>  
  
3.  <span data-ttu-id="e5320-214">按一下 **[使用者權限指派]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-214">Click **User Rights Assignment**.</span></span>  
  
4.  <span data-ttu-id="e5320-215">按兩下 **[從網路存取這台電腦]**，然後按一下 **[新增使用者或群組]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-215">Double-click **Access this computer from the network**, and then click **Add User or Group**.</span></span>  
  
5.  <span data-ttu-id="e5320-216">按一下 **[物件類型]**，選取 **[電腦]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-216">Click **Object Types**, select **Computers** and click **OK**.</span></span>  
  
6.  <span data-ttu-id="e5320-217">在 **[輸入物件名稱來選取]** 區域中，輸入電腦名稱或群組名稱。</span><span class="sxs-lookup"><span data-stu-id="e5320-217">Add the computer name or the group name in the **Enter the object names to select** area.</span></span>  
  
7.  <span data-ttu-id="e5320-218">按一下 **[檢查名稱]** 來確認項目。</span><span class="sxs-lookup"><span data-stu-id="e5320-218">Click **Check Names** to verify the entry.</span></span>  
  
8.  <span data-ttu-id="e5320-219">按兩次 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e5320-219">Click **OK** twice.</span></span>  
  
 <span data-ttu-id="e5320-220">若要變更包含在 **[拒絕從網路存取這台電腦]** 使用者權限中的使用者或群組，請依照下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="e5320-220">To change the users or groups that are included in the **Deny access to this computer from the network** user right, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e5320-221">展開 [本機電腦原則] 清單中的下列項目：</span><span class="sxs-lookup"><span data-stu-id="e5320-221">Expand the following items in the Local Computer Policy list:</span></span>  
  
    -   <span data-ttu-id="e5320-222">電腦組態</span><span class="sxs-lookup"><span data-stu-id="e5320-222">Computer Configuration</span></span>  
  
    -   <span data-ttu-id="e5320-223">Windows 設定</span><span class="sxs-lookup"><span data-stu-id="e5320-223">Windows Settings</span></span>  
  
    -   <span data-ttu-id="e5320-224">安全性設定</span><span class="sxs-lookup"><span data-stu-id="e5320-224">Security Settings</span></span>  
  
    -   <span data-ttu-id="e5320-225">本機原則</span><span class="sxs-lookup"><span data-stu-id="e5320-225">Local Policies</span></span>  
  
2.  <span data-ttu-id="e5320-226">按一下 **[使用者權限指派]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-226">Click **User Rights Assignment**.</span></span>  
  
3.  <span data-ttu-id="e5320-227">按兩下 **[拒絕從網路存取這台電腦]**，然後按一下以選取要從這個使用者權限移除的電腦名稱或群組。</span><span class="sxs-lookup"><span data-stu-id="e5320-227">Double-click **Deny access this computer from the network**, and then click to select the computer name or group that you want to remove from this user right.</span></span>  
  
4.  <span data-ttu-id="e5320-228">按一下 **[移除]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-228">Click **Remove** and then click **OK**.</span></span>  
  
## <a name="set-the-appropriate-values-for-the-enableauthepresolution-and-restrictremoteclients-options"></a><span data-ttu-id="e5320-229">設定 EnableAuthEpResolution 和 RestrictRemoteClients 選項的適當值</span><span class="sxs-lookup"><span data-stu-id="e5320-229">Set the appropriate values for the EnableAuthEpResolution and RestrictRemoteClients options</span></span>  
 <span data-ttu-id="e5320-230">Windows 要求在對 RPC 介面進行呼叫時需要驗證，大大增加了安全性。</span><span class="sxs-lookup"><span data-stu-id="e5320-230">Windows enhances security by requiring authenticated calls to the RPC interface.</span></span> <span data-ttu-id="e5320-231">透過 **EnableAuthEpResolution** 和 **RestrictRemoteClients** 登錄機碼，可設定這項功能。</span><span class="sxs-lookup"><span data-stu-id="e5320-231">This functionality is configurable through the **EnableAuthEpResolution** and **RestrictRemoteClients** registry keys.</span></span> <span data-ttu-id="e5320-232">為確保遠端電腦能夠存取 RPC 介面，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e5320-232">To ensure that remote computers are able to access the RPC interface, follow these steps:</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e5320-233">不正確使用登錄編輯程式可能會造成問題，需要重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="e5320-233">Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system.</span></span> <span data-ttu-id="e5320-234">您必須自行負擔使用「登錄編輯程式」的風險。</span><span class="sxs-lookup"><span data-stu-id="e5320-234">Use Registry Editor at your own risk.</span></span> <span data-ttu-id="e5320-235">如需有關如何備份、還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文件＜Microsoft Windows 登錄說明＞，位在 [Microsoft Windows 登錄說明](http://go.microsoft.com/fwlink/?LinkId=62729)。</span><span class="sxs-lookup"><span data-stu-id="e5320-235">For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article "Description of the Microsoft Windows registry" at [Description of the Microsoft Windows registry](http://go.microsoft.com/fwlink/?LinkId=62729).</span></span>  
  
1.  <span data-ttu-id="e5320-236">按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。</span><span class="sxs-lookup"><span data-stu-id="e5320-236">Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.</span></span>  
  
     <span data-ttu-id="e5320-237">瀏覽至 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT**</span><span class="sxs-lookup"><span data-stu-id="e5320-237">Navigate to **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT**</span></span>  
  
2.  <span data-ttu-id="e5320-238">在 **RPC** 機碼下，以指示的值建立下列 DWORD 項目。</span><span class="sxs-lookup"><span data-stu-id="e5320-238">Under the **RPC** key, create the following DWORD entries with the indicated values.</span></span> <span data-ttu-id="e5320-239">如果 **RPC** 機碼不存在，則必須建立它。</span><span class="sxs-lookup"><span data-stu-id="e5320-239">If the **RPC** key does not exist then it must be created.</span></span>  
  
    |<span data-ttu-id="e5320-240">DWORD 項目</span><span class="sxs-lookup"><span data-stu-id="e5320-240">DWORD entry</span></span>|<span data-ttu-id="e5320-241">預設值</span><span class="sxs-lookup"><span data-stu-id="e5320-241">Default value</span></span>|<span data-ttu-id="e5320-242">建議值</span><span class="sxs-lookup"><span data-stu-id="e5320-242">Recommended value</span></span>|  
    |-----------------|-------------------|-----------------------|  
    |<span data-ttu-id="e5320-243">EnableAuthEpResolution</span><span class="sxs-lookup"><span data-stu-id="e5320-243">EnableAuthEpResolution</span></span>|<span data-ttu-id="e5320-244">0 (停用)</span><span class="sxs-lookup"><span data-stu-id="e5320-244">0 (disabled)</span></span>|<span data-ttu-id="e5320-245">1</span><span class="sxs-lookup"><span data-stu-id="e5320-245">1</span></span>|  
    |<span data-ttu-id="e5320-246">RestrictRemoteClients</span><span class="sxs-lookup"><span data-stu-id="e5320-246">RestrictRemoteClients</span></span>|<span data-ttu-id="e5320-247">1 (啟用)</span><span class="sxs-lookup"><span data-stu-id="e5320-247">1 (enabled)</span></span>|<span data-ttu-id="e5320-248">0</span><span class="sxs-lookup"><span data-stu-id="e5320-248">0</span></span>|  
  
3.  <span data-ttu-id="e5320-249">關閉 [登錄編輯程式]。</span><span class="sxs-lookup"><span data-stu-id="e5320-249">Close Registry Editor.</span></span>  
  
4.  <span data-ttu-id="e5320-250">重新啟動 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="e5320-250">Restart the MSDTC Service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5320-251">依照所做的變更，您可能需要重新啟動電腦以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5320-251">Depending on the changes that were made, you may need to reboot the computer to enact the changes.</span></span> <span data-ttu-id="e5320-252">如果在套用變更及重新啟動 MSDTC 服務之後仍遭遇問題，請將其上進行了變更的電腦重新啟動，以確保這些變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5320-252">If you are still encountering problems after applying changes and restarting the MSDTC service, reboot the computer on which the changes were made to ensure that the changes take effect.</span></span>  
  
## <a name="if-windows-firewall-is-running-add-an-exception-for-the-msdtc-service"></a><span data-ttu-id="e5320-253">如果 Windows 防火牆正在執行，請為 MSDTC 服務新增例外。</span><span class="sxs-lookup"><span data-stu-id="e5320-253">If Windows Firewall is running, add an exception for the MSDTC service</span></span>  
 <span data-ttu-id="e5320-254">Windows 防火牆服務可以封鎖電腦之間的 MSDTC 通訊。</span><span class="sxs-lookup"><span data-stu-id="e5320-254">The Windows Firewall service may block MSDTC communications between computers.</span></span> <span data-ttu-id="e5320-255">為了確保電腦之間的 MSDTC 通訊不會封鎖，請將 msdtc.exe 新增至 Windows 防火牆的例外清單 (如果 Windows 防火牆服務正在執行)。</span><span class="sxs-lookup"><span data-stu-id="e5320-255">To ensure that MSDTC communications are not blocked between computers, add msdtc.exe to the Windows Firewall exception list if the Windows Firewall service is running.</span></span>  
  
1.  <span data-ttu-id="e5320-256">依序按一下 **[開始]** 和 **[執行]**，輸入 **firewall.cpl**，再按一下 **[確定]** 顯示 **[Windows 防火牆]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e5320-256">Click **Start**, click **Run**, type **firewall.cpl**, and then click **OK** to display the **Windows Firewall** dialog box.</span></span>  
  
2.  <span data-ttu-id="e5320-257">按一下 [允許程式通過 Windows 防火牆]  ，以顯示 [Windows 防火牆設定]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e5320-257">Click **Allow a program through the Windows Firewall** to display the **Windows Firewall Settings** dialog box.</span></span>  
  
3.  <span data-ttu-id="e5320-258">按一下 [Windows 防火牆]  對話方塊中的 [例外]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5320-258">Click the **Exceptions** tab of the **Windows Firewall Settings** dialog box.</span></span>  
  
4.  <span data-ttu-id="e5320-259">按一下 **[新增程式]** ，顯示 **[新增程式]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e5320-259">Click **Add Program** to display the **Add a Program** dialog box.</span></span>  
  
5.  <span data-ttu-id="e5320-260">按一下 **[瀏覽]** ，並瀏覽到 *%system32%* \msdtc.exe。</span><span class="sxs-lookup"><span data-stu-id="e5320-260">Click **Browse** and navigate to *%system32%* \msdtc.exe.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5320-261">啟動命令提示字元，輸入 **echo %system32%** ，然後按 **ENTER** 以判斷此電腦上的 \System32 目錄位置。</span><span class="sxs-lookup"><span data-stu-id="e5320-261">Launch a command prompt, type **echo %system32%** and press **Enter** to determine the location of the \System32 directory on this computer.</span></span>  
  
6.  <span data-ttu-id="e5320-262">按一下以選取 **msdtc.exe** ，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-262">Click to select **msdtc.exe** and click **Open**.</span></span>  
  
7.  <span data-ttu-id="e5320-263">按一下 **[變更領域]** ，以指定應該允許 MSDTC 通訊的電腦集，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e5320-263">Click **Change scope** to specify the set of computers for which MSDTC communications should be allowed and click **OK**.</span></span>  
  
8.  <span data-ttu-id="e5320-264">在 [新增程式]  對話方塊中按一下 [確定]  ，然後再按一下 [Windows 防火牆]  對話方塊中的 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e5320-264">Click **OK** in the **Add a Program** dialog box and click **OK** in the **Windows Firewall Settings** dialog box.</span></span>  
  
9. <span data-ttu-id="e5320-265">關閉 [Windows 防火牆]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e5320-265">Close the **Windows Firewall** dialog box.</span></span>  
  
10. <span data-ttu-id="e5320-266">停止分散式交易協調器服務，然後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e5320-266">Stop and restart the Distributed Transaction Coordinator service.</span></span>  
  
    -   <span data-ttu-id="e5320-267">啟動命令提示字元，輸入 **net stop msdtc** ，然後按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="e5320-267">Launch a command prompt, type **net stop msdtc** and press **Enter**.</span></span>  
  
    -   <span data-ttu-id="e5320-268">在分散式交易協調器服務停止之後，輸入 **net start msdtc** ，然後按 **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="e5320-268">After the Distributed Transaction Coordinator service has stopped, type **net start msdtc** and press **Enter**.</span></span>  
  
## <a name="use-dtctester-or-dtcping-to-verify-msdtc-functionality-over-the-network"></a><span data-ttu-id="e5320-269">使用 DTCTester 或 DTCPing 以驗證網路上的 MSDTC 功能</span><span class="sxs-lookup"><span data-stu-id="e5320-269">Use DTCTester or DTCPing to verify MSDTC functionality over the network</span></span>  
 <span data-ttu-id="e5320-270">如果 SQL Server 安裝在兩台電腦中的任一台，使用 DTCTester 公用程式來驗證這兩台電腦之間的交易支援。</span><span class="sxs-lookup"><span data-stu-id="e5320-270">Use the DTCTester utility to verify transaction support between two computers if SQL Server is installed on one of the computers.</span></span> <span data-ttu-id="e5320-271">DTCTester 公用程式使用 ODBC 來驗證對 SQL Server 資料庫的交易支援。</span><span class="sxs-lookup"><span data-stu-id="e5320-271">The DTCTester utility uses ODBC to verify transaction support against a SQL Server database.</span></span> <span data-ttu-id="e5320-272">如需 DTCTester 的詳細資訊，請參閱 [如何使用 DTCTester 工具](http://go.microsoft.com/fwlink/?LinkId=66232)。</span><span class="sxs-lookup"><span data-stu-id="e5320-272">For more information about DTCTester see [How to Use DTCTester Tool](http://go.microsoft.com/fwlink/?LinkId=66232).</span></span>  
  
 <span data-ttu-id="e5320-273">如果 SQL Server 安裝在兩台電腦中的任一台，使用 DTCPing 公用程式來驗證這兩台電腦之間的交易支援。</span><span class="sxs-lookup"><span data-stu-id="e5320-273">Use DTCPing to verify transaction support between two computers if SQL Server is not installed on either computer.</span></span> <span data-ttu-id="e5320-274">當用戶端及伺服器電腦都沒有 SQL Server 時，這兩台電腦都必須執行 DTCPing 工具，而這也是 DTCTester 公用程式的良好替代工具。</span><span class="sxs-lookup"><span data-stu-id="e5320-274">The DTCPing tool must be run on both the client and server computer and is a good alternative to the DTCTester utility when SQL Server is not installed on either computer.</span></span> <span data-ttu-id="e5320-275">如需有關 DTCPing 的詳細資訊，請參閱[如何疑難排解 MS DTC 防火牆問題](http://go.microsoft.com/fwlink/?LinkId=61915)。</span><span class="sxs-lookup"><span data-stu-id="e5320-275">For more information about DTCPing, see [How to troubleshoot MS DTC firewall issues](http://go.microsoft.com/fwlink/?LinkId=61915).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5320-276">如果 DTCPing 傳回「警告：兩部測試機器的 CID 值相同」警告，請遵循 **「確定 MSDTC 獲派唯一的 CID 值」** 一節中的步驟，讓測試機器之間能正常執行 MSDTC 功能。</span><span class="sxs-lookup"><span data-stu-id="e5320-276">If DTCPing returns the warning that “WARNING:the CID values for both test machines are the same” then follow the steps in the section **Ensure that MSDTC is assigned a unique CID value** to accommodate proper MSDTC functionality between the test machines.</span></span>  
  
## <a name="ensure-that-msdtc-is-assigned-a-unique-cid-value"></a><span data-ttu-id="e5320-277">「確定 MSDTC 獲派唯一的 CID 值」</span><span class="sxs-lookup"><span data-stu-id="e5320-277">Ensure that MSDTC is assigned a unique CID value</span></span>  
 <span data-ttu-id="e5320-278">Windows 作業系統的 MSDTC 功能需要有唯一的 CID 值，才能確保電腦之間的 MSDTC 功能運作正常。</span><span class="sxs-lookup"><span data-stu-id="e5320-278">The MSDTC feature of the Windows operating system requires unique CID values to ensure that MSDTC functionality between computers works correctly.</span></span> <span data-ttu-id="e5320-279">Windows 安裝的磁碟複製影像必須有唯一的 CID 值，否則 MSDTC 功能可能無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="e5320-279">Disk duplicate images of Windows installations must have unique CID values or MSDTC functionality may be impaired.</span></span> <span data-ttu-id="e5320-280">使用虛擬硬碟將作業系統部署到虛擬電腦時，可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="e5320-280">This can occur when using virtual hard disks to deploy an operating system to a virtual machine.</span></span>  
  
 <span data-ttu-id="e5320-281">若要判斷執行 Windows 作業系統之電腦的 MSDTC CID 值是否為唯一的，請檢查兩部電腦上 HKEY_CLASSES_ROOT\CID 登錄機碼底下項目的值。</span><span class="sxs-lookup"><span data-stu-id="e5320-281">To determine if MSDTC CID values for computers that are running the Windows operating system are unique, check the values for the entries under the HKEY_CLASSES_ROOT\CID registry key on both computers.</span></span> <span data-ttu-id="e5320-282">如果每部電腦上的這些值不是唯一的，請遵循 **「如果其他疑難排解步驟均無法成功解決問題，請考慮重新安裝分散式交易協調器服務」** 一節的步驟，在其中一部電腦上重新安裝 MSDTC，這樣就會針對該電腦產生唯一的 MSDTC CID 值，因而讓 MSDTC 作業能夠正常執行。</span><span class="sxs-lookup"><span data-stu-id="e5320-282">If these values are not unique for each computer then follow the steps in the section **Consider reinstalling the Distributed Transaction Coordinator service if other troubleshooting steps are not successful** to reinstall MSDTC on one of the computers, which will then generate unique MSDTC CID values for that computer and accommodate proper MSDTC operations.</span></span>  
  
## <a name="error-new-transaction-cannot-enlist-in-the-specified-transaction-coordinator-0x8004d00a-occurs-if-the-msdtc-connection-between-a-client-computer-and-a-server-computer-is-closed"></a><span data-ttu-id="e5320-283">如果用戶端電腦和伺服器電腦之間的連線已關閉，即會發生「無法在指定的異動協調器中編列異動 (0x8004d00a)」錯誤。</span><span class="sxs-lookup"><span data-stu-id="e5320-283">Error “New transaction cannot enlist in the specified transaction coordinator (0x8004d00a)” occurs if the MSDTC connection between a client computer and a server computer is closed</span></span>  
 <span data-ttu-id="e5320-284">在某些情況下，可能會關閉現有 MSDTC 連線用戶端與伺服器之間，並使用此連接的後續嘗試會導致下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="e5320-284">In certain scenarios, it is possible that an existing MSDTC connection between a client and server is closed and subsequent attempts to use this connection will result in the following error message:</span></span>  
<span data-ttu-id="e5320-285">新的交易無法登錄於指定的交易協調器 (0x8004d00a)</span><span class="sxs-lookup"><span data-stu-id="e5320-285">New transaction cannot enlist in the specified transaction coordinator (0x8004d00a)</span></span>  
<span data-ttu-id="e5320-286">如需詳細資訊，請參閱[當您嘗試在 MS DTC 中啟動交易時的錯誤訊息: 「 新的交易無法登錄於指定的交易協調器 」](http://support.microsoft.com/kb/922430)。</span><span class="sxs-lookup"><span data-stu-id="e5320-286">For more information, see [Error message when you try to start a transaction in MS DTC: "New transaction cannot enlist in the specified transaction coordinator"](http://support.microsoft.com/kb/922430).</span></span>  
  
## <a name="consider-reinstalling-the-distributed-transaction-coordinator-service-if-other-troubleshooting-steps-are-not-successful"></a><span data-ttu-id="e5320-287">「如果其他疑難排解步驟均無法成功解決問題，請考慮重新安裝分散式交易協調器服務」</span><span class="sxs-lookup"><span data-stu-id="e5320-287">Consider reinstalling the Distributed Transaction Coordinator service if other troubleshooting steps are not successful</span></span>  
 <span data-ttu-id="e5320-288">若其他嘗試疑難排解 MSDTC 問題的措施也不成功，請考慮解除安裝再重新安裝 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="e5320-288">If other attempts at troubleshooting problems with MSDTC are not successful consider uninstalling and reinstalling MSDTC.</span></span> <span data-ttu-id="e5320-289">請遵循下列步驟來解除安裝再重新安裝 MSDTC：</span><span class="sxs-lookup"><span data-stu-id="e5320-289">Follow these steps to uninstall and reinstall MSDTC:</span></span>  
  
1.  <span data-ttu-id="e5320-290">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e5320-290">Open a command prompt as Administrator.</span></span>  
  
2.  <span data-ttu-id="e5320-291">在命令提示字元中輸入如下，以解除安裝分散式交易協調器服務：</span><span class="sxs-lookup"><span data-stu-id="e5320-291">At the command prompt, type the following to uninstall the Distributed Transaction Coordinator service:</span></span>  
    `msdtc -uninstall`  
  
3.  <span data-ttu-id="e5320-292">在命令提示字元中輸入如下，以安裝分散式交易協調器服務：</span><span class="sxs-lookup"><span data-stu-id="e5320-292">At the command prompt, type the following to install the Distributed Transaction Coordinator service:</span></span>  
    `msdtc –install`  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5320-293">重新安裝 MSDTC 可能會變更分散式交易協調器服務的預設行為。</span><span class="sxs-lookup"><span data-stu-id="e5320-293">Reinstalling MSDTC may change the default behavior of the Distributed Transaction Coordinator service.</span></span> <span data-ttu-id="e5320-294">重新安裝 MSDTC 之後，請遵循下列步驟，以確保分散式交易協調器服務能夠正常運作：</span><span class="sxs-lookup"><span data-stu-id="e5320-294">Follow these steps after reinstalling MSDTC to ensure that the Distributed Transaction Coordinator service works correctly:</span></span>  
>   
>  -   <span data-ttu-id="e5320-295">重新安裝 MSDTC 可能會將 MSDTC 安全性組態選項重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="e5320-295">Reinstalling MSDTC may reset MSDTC Security Configuration options back to default values.</span></span> <span data-ttu-id="e5320-296">請確認 MSDTC 安全性組態選項值的設定在重新安裝 MSDTC 之後仍然正確。</span><span class="sxs-lookup"><span data-stu-id="e5320-296">Verify that the MSDTC Security Configuration options are set to the appropriate values after reinstalling MSDTC.</span></span>  
> -   <span data-ttu-id="e5320-297">重新安裝 MSDTC 可能會變更分散式交易協調器服務的 **啟動類型** 值。</span><span class="sxs-lookup"><span data-stu-id="e5320-297">Reinstalling MSDTC may change the **Startup Type** value for the Distributed Transaction Coordinator service.</span></span> <span data-ttu-id="e5320-298">確認重新安裝 MSDTC 之後，分散式交易協調器服務的 **啟動類型** 值設定為 **自動** 。</span><span class="sxs-lookup"><span data-stu-id="e5320-298">Verify that the **Startup Type** value for the Distributed Transaction Coordinator service is set to **Automatic** after reinstalling MSDTC.</span></span>  
> -   <span data-ttu-id="e5320-299">重新安裝 MSDTC 之後，電腦可能需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="e5320-299">Reinstalling MSDTC may require a reboot of the computer.</span></span> <span data-ttu-id="e5320-300">為確保分散式交易協調器服務能夠正常運作，重新安裝 MSDTC 之後，請將電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="e5320-300">To ensure that the Distributed Transaction Coordinator service works correctly, reboot the computer after reinstalling MSDTC.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5320-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5320-301">See Also</span></span>  
 <span data-ttu-id="e5320-302">[工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="e5320-302">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="e5320-303">疑難排解 Windows Server 叢集</span><span class="sxs-lookup"><span data-stu-id="e5320-303">Troubleshooting a Windows Server Cluster</span></span>](../core/troubleshooting-a-windows-server-cluster.md)