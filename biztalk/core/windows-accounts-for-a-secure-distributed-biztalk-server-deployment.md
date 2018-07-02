---
title: 用於安全分散式的 BizTalk Server 部署的 Windows 帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e05753c1693de75bbe6fa8422162a8c6e284bcff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985695"
---
# <a name="windows-accounts-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="0d9ce-102">用於安全分散式 BizTalk Server 部署的 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="0d9ce-102">Windows Accounts for a Secure Distributed BizTalk Server Deployment</span></span>
<span data-ttu-id="0d9ce-103">完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="0d9ce-104">本節提供在分散式 BizTalk Server 環境中建立 Windows 群組與帳戶的建議。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-104">This section provides recommendations for creating Windows groups and accounts in a distributed BizTalk Server environment.</span></span> <span data-ttu-id="0d9ce-105">群組與帳戶名稱是根據群組與帳戶的功能而建議的。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-105">The group and account names are suggestions based on the function of the groups and accounts.</span></span> <span data-ttu-id="0d9ce-106">而您可以選擇這些群組與帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-106">You can choose the name of these groups and accounts.</span></span> <span data-ttu-id="0d9ce-107">如需有關分散式 BizTalk Server 架構的詳細資訊，請參閱 <<c0> [ 大型分散式架構](../core/large-distributed-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-107">For more information about distributed BizTalk Server architectures, see [Large Distributed Architecture](../core/large-distributed-architecture.md).</span></span>  
  
## <a name="windows-groups-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="0d9ce-108">用於安全分散式 BizTalk Server 部署的 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="0d9ce-108">Windows Groups for a Secure Distributed BizTalk Server Deployment</span></span>  
 <span data-ttu-id="0d9ce-109">下列清單是建議網域系統管理員，應在資料層的網域控制站中建立的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-109">The following list describes the recommended Windows groups for the domain administrator to create in the domain controller in the data tier.</span></span>  
  
- <span data-ttu-id="0d9ce-110">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-110">SSO Administrators</span></span>  
  
- <span data-ttu-id="0d9ce-111">SSO 分支機構系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-111">SSO Affiliate Administrators</span></span>  
  
- <span data-ttu-id="0d9ce-112">BizTalk Server 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-112">BizTalk Server Administrators</span></span>  
  
- <span data-ttu-id="0d9ce-113">BizTalk Server 操作員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-113">BizTalk Server Operators</span></span>  
  
  <span data-ttu-id="0d9ce-114">完成 BizTalk Server 使用的 Windows 群組的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-114">For complete information about the Windows groups that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
  <span data-ttu-id="0d9ce-115">除了先前的網域群組之外，下表列出在資料層的網域控制站中，為了保護網域的安全部署，系統管理員要建立的其他群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-115">In addition to the previous domain groups, the following table lists additional groups specific to secure deployment for the domain administrator to create in the domain controller in the data tier.</span></span>  
  
|<span data-ttu-id="0d9ce-116">群組名稱 (建議)</span><span class="sxs-lookup"><span data-stu-id="0d9ce-116">Group name (suggested)</span></span>|<span data-ttu-id="0d9ce-117">目的</span><span class="sxs-lookup"><span data-stu-id="0d9ce-117">Purpose</span></span>|  
|------------------------------|-------------|  
|<span data-ttu-id="0d9ce-118">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-118">BizTalk Processing Host Users 1</span></span>|<span data-ttu-id="0d9ce-119">用來處理訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-119">Group for the host instances of a specific in-process host that you use for processing messages.</span></span> <span data-ttu-id="0d9ce-120">為您在 BizTalk Server 環境中要用來處理訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-120">Create a group for each in-process host that you use for processing messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="0d9ce-121">BizTalk 傳送主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-121">BizTalk Send Host Users 1</span></span>|<span data-ttu-id="0d9ce-122">用來傳送訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-122">Group for the host instance of a specific in-process host that you use for sending messages.</span></span> <span data-ttu-id="0d9ce-123">為您在 BizTalk Server 環境中要用來傳送訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-123">Create a group for each in-process host that you use for sending messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="0d9ce-124">BizTalk 接收主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-124">BizTalk Receive Host Users 1</span></span>|<span data-ttu-id="0d9ce-125">用來接收訊息的特定內含式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-125">Group for the host instance of a specific in-process host that you use for receiving messages.</span></span> <span data-ttu-id="0d9ce-126">為您要在 BizTalk Server 環境中用來接收訊息的每個內含式主控件建立群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-126">Create a group for each in-process host that you use for receiving messages in your BizTalk Server environment.</span></span>|  
|<span data-ttu-id="0d9ce-127">BizTalk 追蹤主控件使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-127">BizTalk Tracking Host Users</span></span>|<span data-ttu-id="0d9ce-128">專門用來追蹤的 BizTalk 主控件群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-128">Group for the BizTalk host that you dedicate for tracking.</span></span>|  
|<span data-ttu-id="0d9ce-129">BizTalk SOAP 使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-129">BizTalk SOAP Users</span></span>|<span data-ttu-id="0d9ce-130">用於 SOAP 配接器的外掛式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-130">Group for the host instances of the isolated host you use for the SOAP adapter.</span></span>|  
|<span data-ttu-id="0d9ce-131">BizTalk HTTP 使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-131">BizTalk HTTP Users</span></span>|<span data-ttu-id="0d9ce-132">用於 HTTP 配接器的外掛式主控件的主控件執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-132">Group for the host instances of the isolated hosts you use for the HTTP adapter.</span></span>|  
  
 <span data-ttu-id="0d9ce-133">網域系統管理員必須在服務介面網域的網域控制站中建立下列群組：</span><span class="sxs-lookup"><span data-stu-id="0d9ce-133">The domain administrator must create the following groups in the domain controller of the service interfaces domain:</span></span>  
  
-   <span data-ttu-id="0d9ce-134">BizTalk BAM 入口網站使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-134">BizTalk BAM Portal Users</span></span>  
  
## <a name="windows-user-or-service-accounts-for-a-secure-distributed-biztalk-server-deployment"></a><span data-ttu-id="0d9ce-135">用於安全分散式 BizTalk Server 部署的 Windows 使用者或服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0d9ce-135">Windows User or Service Accounts for a Secure Distributed BizTalk Server Deployment</span></span>  
 <span data-ttu-id="0d9ce-136">下表列出在資料網域的網域控制站中，建議要為網域系統管理員建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-136">The following table lists the recommended accounts for the domain administrator to create in the domain controller of the data domain.</span></span> <span data-ttu-id="0d9ce-137">網域系統管理員必須確定這些帳戶是指定群組的成員。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-137">The domain administrator must ensure the accounts are members of the groups indicated.</span></span>  
  
 <span data-ttu-id="0d9ce-138">完成 BizTalk Server 使用的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-138">For complete information about the user accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
|<span data-ttu-id="0d9ce-139">帳戶名稱 (範例)</span><span class="sxs-lookup"><span data-stu-id="0d9ce-139">Account name (example)</span></span>|<span data-ttu-id="0d9ce-140">類型</span><span class="sxs-lookup"><span data-stu-id="0d9ce-140">Type</span></span>|<span data-ttu-id="0d9ce-141">群組成員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-141">Member of group</span></span>|  
|------------------------------|----------|---------------------|  
|<span data-ttu-id="0d9ce-142">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-142">SSO administrator</span></span>|<span data-ttu-id="0d9ce-143">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-143">User</span></span>|<span data-ttu-id="0d9ce-144">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-144">SSO Administrators</span></span>|  
|<span data-ttu-id="0d9ce-145">SSO 服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-145">SSO service</span></span>|<span data-ttu-id="0d9ce-146">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-146">Service</span></span>|<span data-ttu-id="0d9ce-147">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-147">SSO Administrators</span></span>|  
|<span data-ttu-id="0d9ce-148">SSO 主要密碼</span><span class="sxs-lookup"><span data-stu-id="0d9ce-148">SSO master secret</span></span>|<span data-ttu-id="0d9ce-149">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-149">Service</span></span>|<span data-ttu-id="0d9ce-150">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-150">SSO Administrators</span></span>|  
|<span data-ttu-id="0d9ce-151">BizTalk 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-151">BizTalk administrator</span></span>|<span data-ttu-id="0d9ce-152">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-152">User</span></span>|<span data-ttu-id="0d9ce-153">BizTalk 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-153">BizTalk Administrators</span></span><br /><br /> <span data-ttu-id="0d9ce-154">SSO 分支機構系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-154">SSO Affiliate Administrators</span></span>|  
|<span data-ttu-id="0d9ce-155">BizTalk 操作員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-155">BizTalk operator</span></span>|<span data-ttu-id="0d9ce-156">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-156">User</span></span>|<span data-ttu-id="0d9ce-157">BizTalk 操作員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-157">BizTalk Operators</span></span>|  
|<span data-ttu-id="0d9ce-158">BizTalk 處理 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-158">BizTalk Processing 1</span></span>|<span data-ttu-id="0d9ce-159">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-159">Service</span></span>|<span data-ttu-id="0d9ce-160">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-160">BizTalk Processing Host Users 1</span></span>|  
|<span data-ttu-id="0d9ce-161">BizTalk 處理 2**附註：** 您可以為每個處理主控件建立多個帳戶，您的環境中。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-161">BizTalk Processing 2 **Note:**  You can create multiple accounts for each processing host in your environment.</span></span>|<span data-ttu-id="0d9ce-162">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-162">Service</span></span>|<span data-ttu-id="0d9ce-163">BizTalk 處理主控件使用者 1</span><span class="sxs-lookup"><span data-stu-id="0d9ce-163">BizTalk Processing Host Users 1</span></span>|  
|<span data-ttu-id="0d9ce-164">BizTalk 追蹤</span><span class="sxs-lookup"><span data-stu-id="0d9ce-164">BizTalk Tracking</span></span>|<span data-ttu-id="0d9ce-165">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-165">Service</span></span>|<span data-ttu-id="0d9ce-166">BizTalk 追蹤主控件使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-166">BizTalk Tracking Host Users</span></span>|  
|<span data-ttu-id="0d9ce-167">SOAP adapter (SOAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="0d9ce-167">SOAP adapter</span></span>|<span data-ttu-id="0d9ce-168">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-168">Service</span></span>|<span data-ttu-id="0d9ce-169">BizTalk SOAP 使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-169">BizTalk SOAP Users</span></span>|  
|<span data-ttu-id="0d9ce-170">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="0d9ce-170">HTTP adapter</span></span>|<span data-ttu-id="0d9ce-171">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-171">Service</span></span>|<span data-ttu-id="0d9ce-172">BizTalk HTTP 使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-172">BizTalk HTTP Users</span></span>|  
|<span data-ttu-id="0d9ce-173">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-173">Rule Engine Update Service</span></span>|<span data-ttu-id="0d9ce-174">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-174">Service</span></span>||  
|<span data-ttu-id="0d9ce-175">安裝</span><span class="sxs-lookup"><span data-stu-id="0d9ce-175">Installation</span></span>|<span data-ttu-id="0d9ce-176">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-176">User</span></span>|<span data-ttu-id="0d9ce-177">SSO 系統管理員 (僅限設定主要密碼伺服器)</span><span class="sxs-lookup"><span data-stu-id="0d9ce-177">SSO Administrators (only for configuring the master secret server)</span></span><br /><br /> <span data-ttu-id="0d9ce-178">本機系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-178">local Administrators</span></span><br /><br /> <span data-ttu-id="0d9ce-179">系統管理員 (sysadmin) SQL Server 角色</span><span class="sxs-lookup"><span data-stu-id="0d9ce-179">sysadmin SQL Server Role</span></span><br /><br /> <span data-ttu-id="0d9ce-180">OLAP 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-180">OLAP Administrator</span></span>|  
|<span data-ttu-id="0d9ce-181">BAM 應用程式集區</span><span class="sxs-lookup"><span data-stu-id="0d9ce-181">BAM Application pool</span></span>|<span data-ttu-id="0d9ce-182">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-182">Service</span></span>|<span data-ttu-id="0d9ce-183">IIS_WPG</span><span class="sxs-lookup"><span data-stu-id="0d9ce-183">IIS_WPG</span></span>|  
|<span data-ttu-id="0d9ce-184">BAM 管理</span><span class="sxs-lookup"><span data-stu-id="0d9ce-184">BAM Management</span></span>|<span data-ttu-id="0d9ce-185">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-185">Service</span></span>|<span data-ttu-id="0d9ce-186">IIS_WPG</span><span class="sxs-lookup"><span data-stu-id="0d9ce-186">IIS_WPG</span></span>|  
|<span data-ttu-id="0d9ce-187">BAM 通知</span><span class="sxs-lookup"><span data-stu-id="0d9ce-187">BAM Notification</span></span>|<span data-ttu-id="0d9ce-188">服務</span><span class="sxs-lookup"><span data-stu-id="0d9ce-188">Service</span></span>|<span data-ttu-id="0d9ce-189">SQLServer2005NotificationServicesUser$\<**ComputerName**\></span><span class="sxs-lookup"><span data-stu-id="0d9ce-189">SQLServer2005NotificationServicesUser$\<**ComputerName**\></span></span>|  
  
 <span data-ttu-id="0d9ce-190">下表所列帳戶是建議網域系統管理員，應在企業網域的網域控制站中建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="0d9ce-190">The following table lists the recommended accounts for the domain administrator to create in the domain controller of the corporate domain.</span></span>  
  
|<span data-ttu-id="0d9ce-191">帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="0d9ce-191">Account name</span></span>|<span data-ttu-id="0d9ce-192">類型</span><span class="sxs-lookup"><span data-stu-id="0d9ce-192">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="0d9ce-193">SharePoint 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d9ce-193">SharePoint administrator</span></span>|<span data-ttu-id="0d9ce-194">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-194">User</span></span>|  
|<span data-ttu-id="0d9ce-195">SharePoint 網站認證</span><span class="sxs-lookup"><span data-stu-id="0d9ce-195">SharePoint Site credential</span></span>|<span data-ttu-id="0d9ce-196">使用者</span><span class="sxs-lookup"><span data-stu-id="0d9ce-196">User</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d9ce-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9ce-197">See Also</span></span>  
 <span data-ttu-id="0d9ce-198">[大型分散式的架構](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="0d9ce-198">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="0d9ce-199">[最低安全性使用者權限](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="0d9ce-199">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 <span data-ttu-id="0d9ce-200">[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="0d9ce-200">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="0d9ce-201">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="0d9ce-201">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)