---
title: "Windows 帳戶的安全分散式的 BizTalk Server 部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, Windows groups
- user accounts, naming conventions
- user accounts
- access control, Windows groups
- security, access control
- architecture, security
- security, Windows accounts
- administrator accounts
- user accounts, administrators
- architecture, large distributions
ms.assetid: 2a0893ef-8bfb-481b-b024-7f7d6e2a6f09
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04c7e6e28cc0deb83eaa7868c6c4ee17da8bc563
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="windows-accounts-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="e9708-102">用於安全分散式 BizTalk Server 部署的 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="e9708-102">Windows Accounts for a Secure Distributed BizTalk Server Deployment</span></span>
<span data-ttu-id="e9708-103">完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="e9708-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="e9708-104">本節提供在分散式 BizTalk Server 環境中建立 Windows 群組與帳戶的建議。</span><span class="sxs-lookup"><span data-stu-id="e9708-104">This section provides recommendations for creating Windows groups and accounts in a distributed BizTalk Server environment.</span></span> <span data-ttu-id="e9708-105">群組與帳戶名稱是根據群組與帳戶的功能而建議的。</span><span class="sxs-lookup"><span data-stu-id="e9708-105">The group and account names are suggestions based on the function of the groups and accounts.</span></span> <span data-ttu-id="e9708-106">而您可以選擇這些群組與帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="e9708-106">You can choose the name of these groups and accounts.</span></span> <span data-ttu-id="e9708-107">如需有關分散式 BizTalk Server 架構的詳細資訊，請參閱[大型分散式架構](../core/large-distributed-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="e9708-107">For more information about distributed BizTalk Server architectures, see [Large Distributed Architecture](../core/large-distributed-architecture.md).</span></span>  
  
## <a name="windows-groups-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="e9708-108">用於安全分散式 BizTalk Server 部署的 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="e9708-108">Windows Groups for a Secure Distributed BizTalk Server Deployment</span></span>  
 <span data-ttu-id="e9708-109">下列清單是建議網域系統管理員，應在資料層的網域控制站中建立的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-109">The following list describes the recommended Windows groups for the domain administrator to create in the domain controller in the data tier.</span></span>  
  
-   <span data-ttu-id="e9708-110">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-110">SSO Administrators</span></span>  
  
-   <span data-ttu-id="e9708-111">SSO 分支機構系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-111">SSO Affiliate Administrators</span></span>  
  
-   <span data-ttu-id="e9708-112">BizTalk Server 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-112">BizTalk Server Administrators</span></span>  
  
-   <span data-ttu-id="e9708-113">BizTalk Server 操作員</span><span class="sxs-lookup"><span data-stu-id="e9708-113">BizTalk Server Operators</span></span>  
  
 <span data-ttu-id="e9708-114">如需 BizTalk Server 使用的 Windows 群組的完整資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e9708-114">For complete information about the Windows groups that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="e9708-115">除了先前的網域群組之外，下表列出在資料層的網域控制站中，為了保護網域的安全部署，系統管理員要建立的其他群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-115">In addition to the previous domain groups, the following table lists additional groups specific to secure deployment for the domain administrator to create in the domain controller in the data tier.</span></span>  
  
|<span data-ttu-id="e9708-116">群組名稱 (建議)</span><span class="sxs-lookup"><span data-stu-id="e9708-116">Group name (suggested)</span></span>|<span data-ttu-id="e9708-117">目的</span><span class="sxs-lookup"><span data-stu-id="e9708-117">Purpose</span></span>|  
|------------------------------|-------------|  
|<span data-ttu-id="e9708-118">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="e9708-118">BizTalk Processing Host Users 1</span></span>|<span data-ttu-id="e9708-119">用來處理訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-119">Group for the host instances of a specific in-process host that you use for processing messages.</span></span> <span data-ttu-id="e9708-120">為您在 BizTalk Server 環境中要用來處理訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-120">Create a group for each in-process host that you use for processing messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="e9708-121">BizTalk 傳送主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="e9708-121">BizTalk Send Host Users 1</span></span>|<span data-ttu-id="e9708-122">用來傳送訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-122">Group for the host instance of a specific in-process host that you use for sending messages.</span></span> <span data-ttu-id="e9708-123">為您在 BizTalk Server 環境中要用來傳送訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-123">Create a group for each in-process host that you use for sending messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="e9708-124">BizTalk 接收主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="e9708-124">BizTalk Receive Host Users 1</span></span>|<span data-ttu-id="e9708-125">用來接收訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-125">Group for the host instance of a specific in-process host that you use for receiving messages.</span></span> <span data-ttu-id="e9708-126">為您要在 BizTalk Server 環境中用來接收訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-126">Create a group for each in-process host that you use for receiving messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="e9708-127">BizTalk 追蹤主控件使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-127">BizTalk Tracking Host Users</span></span>|<span data-ttu-id="e9708-128">專門用來追蹤的 BizTalk 主控件群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-128">Group for the BizTalk host that you dedicate for tracking.</span></span>|  
|<span data-ttu-id="e9708-129">BizTalk SOAP 使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-129">BizTalk SOAP Users</span></span>|<span data-ttu-id="e9708-130">用於 SOAP 配接器的外掛式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-130">Group for the host instances of the isolated host you use for the SOAP adapter.</span></span>|  
|<span data-ttu-id="e9708-131">BizTalk HTTP 使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-131">BizTalk HTTP Users</span></span>|<span data-ttu-id="e9708-132">用於 HTTP 配接器的外掛式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e9708-132">Group for the host instances of the isolated hosts you use for the HTTP adapter.</span></span>|  
  
 <span data-ttu-id="e9708-133">網域系統管理員必須在服務介面網域的網域控制站中建立下列群組：</span><span class="sxs-lookup"><span data-stu-id="e9708-133">The domain administrator must create the following groups in the domain controller of the service interfaces domain:</span></span>  
  
-   <span data-ttu-id="e9708-134">BizTalk BAM 入口網站使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-134">BizTalk BAM Portal Users</span></span>  
  
## <a name="windows-user-or-service-accounts-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="e9708-135">用於安全分散式 BizTalk Server 部署的 Windows 使用者或服務帳戶</span><span class="sxs-lookup"><span data-stu-id="e9708-135">Windows User or Service Accounts for a Secure Distributed BizTalk Server Deployment</span></span>  
 <span data-ttu-id="e9708-136">下表列出在資料網域的網域控制站中，建議要為網域系統管理員建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9708-136">The following table lists the recommended accounts for the domain administrator to create in the domain controller of the data domain.</span></span> <span data-ttu-id="e9708-137">網域系統管理員必須確定這些帳戶是指定群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e9708-137">The domain administrator must ensure the accounts are members of the groups indicated.</span></span>  
  
 <span data-ttu-id="e9708-138">完成 BizTalk Server 使用的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e9708-138">For complete information about the user accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
|<span data-ttu-id="e9708-139">帳戶名稱 (範例)</span><span class="sxs-lookup"><span data-stu-id="e9708-139">Account name (example)</span></span>|<span data-ttu-id="e9708-140">類型</span><span class="sxs-lookup"><span data-stu-id="e9708-140">Type</span></span>|<span data-ttu-id="e9708-141">群組成員</span><span class="sxs-lookup"><span data-stu-id="e9708-141">Member of group</span></span>|  
|------------------------------|----------|---------------------|  
|<span data-ttu-id="e9708-142">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-142">SSO administrator</span></span>|<span data-ttu-id="e9708-143">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-143">User</span></span>|<span data-ttu-id="e9708-144">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-144">SSO Administrators</span></span>|  
|<span data-ttu-id="e9708-145">SSO 服務</span><span class="sxs-lookup"><span data-stu-id="e9708-145">SSO service</span></span>|<span data-ttu-id="e9708-146">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-146">Service</span></span>|<span data-ttu-id="e9708-147">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-147">SSO Administrators</span></span>|  
|<span data-ttu-id="e9708-148">SSO 主要密碼</span><span class="sxs-lookup"><span data-stu-id="e9708-148">SSO master secret</span></span>|<span data-ttu-id="e9708-149">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-149">Service</span></span>|<span data-ttu-id="e9708-150">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-150">SSO Administrators</span></span>|  
|<span data-ttu-id="e9708-151">BizTalk 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-151">BizTalk administrator</span></span>|<span data-ttu-id="e9708-152">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-152">User</span></span>|<span data-ttu-id="e9708-153">BizTalk 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-153">BizTalk Administrators</span></span><br /><br /> <span data-ttu-id="e9708-154">SSO 分支機構系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-154">SSO Affiliate Administrators</span></span>|  
|<span data-ttu-id="e9708-155">BizTalk 操作員</span><span class="sxs-lookup"><span data-stu-id="e9708-155">BizTalk operator</span></span>|<span data-ttu-id="e9708-156">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-156">User</span></span>|<span data-ttu-id="e9708-157">BizTalk 操作員</span><span class="sxs-lookup"><span data-stu-id="e9708-157">BizTalk Operators</span></span>|  
|<span data-ttu-id="e9708-158">BizTalk 處理 1</span><span class="sxs-lookup"><span data-stu-id="e9708-158">BizTalk Processing 1</span></span>|<span data-ttu-id="e9708-159">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-159">Service</span></span>|<span data-ttu-id="e9708-160">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="e9708-160">BizTalk Processing Host Users 1</span></span>|  
|<span data-ttu-id="e9708-161">BizTalk 處理 2**附註：**您可以針對每個處理主控件建立多個帳戶，您的環境中。</span><span class="sxs-lookup"><span data-stu-id="e9708-161">BizTalk Processing 2 **Note:**  You can create multiple accounts for each processing host in your environment.</span></span>|<span data-ttu-id="e9708-162">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-162">Service</span></span>|<span data-ttu-id="e9708-163">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="e9708-163">BizTalk Processing Host Users 1</span></span>|  
|<span data-ttu-id="e9708-164">BizTalk 追蹤</span><span class="sxs-lookup"><span data-stu-id="e9708-164">BizTalk Tracking</span></span>|<span data-ttu-id="e9708-165">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-165">Service</span></span>|<span data-ttu-id="e9708-166">BizTalk 追蹤主控件使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-166">BizTalk Tracking Host Users</span></span>|  
|<span data-ttu-id="e9708-167">SOAP adapter (SOAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="e9708-167">SOAP adapter</span></span>|<span data-ttu-id="e9708-168">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-168">Service</span></span>|<span data-ttu-id="e9708-169">BizTalk SOAP 使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-169">BizTalk SOAP Users</span></span>|  
|<span data-ttu-id="e9708-170">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="e9708-170">HTTP adapter</span></span>|<span data-ttu-id="e9708-171">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-171">Service</span></span>|<span data-ttu-id="e9708-172">BizTalk HTTP 使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-172">BizTalk HTTP Users</span></span>|  
|<span data-ttu-id="e9708-173">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="e9708-173">Rule Engine Update Service</span></span>|<span data-ttu-id="e9708-174">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-174">Service</span></span>||  
|<span data-ttu-id="e9708-175">安裝</span><span class="sxs-lookup"><span data-stu-id="e9708-175">Installation</span></span>|<span data-ttu-id="e9708-176">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-176">User</span></span>|<span data-ttu-id="e9708-177">SSO 系統管理員 (僅限設定主要密碼伺服器)</span><span class="sxs-lookup"><span data-stu-id="e9708-177">SSO Administrators (only for configuring the master secret server)</span></span><br /><br /> <span data-ttu-id="e9708-178">本機系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-178">local Administrators</span></span><br /><br /> <span data-ttu-id="e9708-179">系統管理員 (sysadmin) SQL Server 角色</span><span class="sxs-lookup"><span data-stu-id="e9708-179">sysadmin SQL Server Role</span></span><br /><br /> <span data-ttu-id="e9708-180">OLAP 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-180">OLAP Administrator</span></span>|  
|<span data-ttu-id="e9708-181">BAM 應用程式集區</span><span class="sxs-lookup"><span data-stu-id="e9708-181">BAM Application pool</span></span>|<span data-ttu-id="e9708-182">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-182">Service</span></span>|<span data-ttu-id="e9708-183">IIS_WPG</span><span class="sxs-lookup"><span data-stu-id="e9708-183">IIS_WPG</span></span>|  
|<span data-ttu-id="e9708-184">BAM 管理</span><span class="sxs-lookup"><span data-stu-id="e9708-184">BAM Management</span></span>|<span data-ttu-id="e9708-185">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-185">Service</span></span>|<span data-ttu-id="e9708-186">IIS_WPG</span><span class="sxs-lookup"><span data-stu-id="e9708-186">IIS_WPG</span></span>|  
|<span data-ttu-id="e9708-187">BAM 通知</span><span class="sxs-lookup"><span data-stu-id="e9708-187">BAM Notification</span></span>|<span data-ttu-id="e9708-188">服務</span><span class="sxs-lookup"><span data-stu-id="e9708-188">Service</span></span>|<span data-ttu-id="e9708-189">SQLServer2005NotificationServicesUser$\<**ComputerName**\></span><span class="sxs-lookup"><span data-stu-id="e9708-189">SQLServer2005NotificationServicesUser$\<**ComputerName**\></span></span>|  
  
 <span data-ttu-id="e9708-190">下表所列帳戶是建議網域系統管理員，應在企業網域的網域控制站中建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9708-190">The following table lists the recommended accounts for the domain administrator to create in the domain controller of the corporate domain.</span></span>  
  
|<span data-ttu-id="e9708-191">帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="e9708-191">Account name</span></span>|<span data-ttu-id="e9708-192">類型</span><span class="sxs-lookup"><span data-stu-id="e9708-192">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="e9708-193">SharePoint 系統管理員</span><span class="sxs-lookup"><span data-stu-id="e9708-193">SharePoint administrator</span></span>|<span data-ttu-id="e9708-194">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-194">User</span></span>|  
|<span data-ttu-id="e9708-195">SharePoint 網站認證</span><span class="sxs-lookup"><span data-stu-id="e9708-195">SharePoint Site credential</span></span>|<span data-ttu-id="e9708-196">使用者</span><span class="sxs-lookup"><span data-stu-id="e9708-196">User</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9708-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9708-197">See Also</span></span>  
 <span data-ttu-id="e9708-198">[大型分散式的架構](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="e9708-198">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="e9708-199">[最低安全性使用者權限](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="e9708-199">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 <span data-ttu-id="e9708-200">[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9708-200">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="e9708-201">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="e9708-201">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)