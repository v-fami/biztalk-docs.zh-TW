---
title: 群組和服務帳戶的存取控制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- access control, service accounts
- user accounts, default accounts
- service accounts, security
- user accounts, unsupported
- access control, groups
- service accounts, access control
- groups, access control
- groups, security
ms.assetid: 411a7bfa-6675-4d09-9e37-83e2941df3c6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da1bb9a52bef2e81729a8b566e4af4dcbed89c2a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021788"
---
# <a name="access-control-for-groups-and-service-accounts"></a><span data-ttu-id="0f09d-102">群組和服務帳戶的存取控制</span><span class="sxs-lookup"><span data-stu-id="0f09d-102">Access Control for Groups and Service Accounts</span></span>
<span data-ttu-id="0f09d-103">每個 BizTalk 主控件執行個體會在使用者建立的服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="0f09d-103">Each BizTalk Host instance runs under a user-created service account.</span></span> <span data-ttu-id="0f09d-104">在電腦上建立主控件執行個體時，您必須提供服務帳戶及密碼。</span><span class="sxs-lookup"><span data-stu-id="0f09d-104">You must provide the service accounts and their passwords at the time you create the host instance on a computer.</span></span> <span data-ttu-id="0f09d-105">BizTalk Server 會接著確定帳戶擁有執行工作所需的最低使用者權限，其方法是新增這每一個服務帳戶到本機或網域的 Windows 群組，然後再將此群組加入至該主控件特定的「SQL Server 資料庫」角色。</span><span class="sxs-lookup"><span data-stu-id="0f09d-105">BizTalk Server then ensures that the accounts have the minimum user rights needed to do their jobs by adding each of these service accounts to a local or domain Windows group that, in turn, it adds to the SQL Server Database role specific to that host.</span></span>  
  
 <span data-ttu-id="0f09d-106">這種處理方式會產生下列好處：</span><span class="sxs-lookup"><span data-stu-id="0f09d-106">This approach offers the following benefits:</span></span>  
  
- <span data-ttu-id="0f09d-107">您可以賦予每個主控件執行個體各自不同的服務帳戶，讓每個主控件執行個體都可以變更密碼，而無須使伺服器離線。</span><span class="sxs-lookup"><span data-stu-id="0f09d-107">You can give each host instance a distinct service account, making it possible to change the passwords for each host instance without having to take servers offline.</span></span> <span data-ttu-id="0f09d-108">您可以執行輪替的密碼更新，而不會中斷服務。</span><span class="sxs-lookup"><span data-stu-id="0f09d-108">You can perform rolling password updates without interrupting service.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="0f09d-109">對於驗證為信任的主控件以及未驗證為信任的主控件，不可以兩邊都使用相同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="0f09d-109">You cannot use the same service account for hosts that are authentication trusted and hosts that are not authentication trusted.</span></span>  
  
- <span data-ttu-id="0f09d-110">如果是在 Microsoft SQL Server™ 層級將資源使用者權限授與本機或網域群組，您就可以增加或減少服務帳戶，而無須變更 SQL Server 所授與的使用者權限；因此可以減輕您的管理負擔和擁有帳戶的總成本。</span><span class="sxs-lookup"><span data-stu-id="0f09d-110">If you grant resource user rights to the local or domain group at the Microsoft SQL Server™ level, you can add and subtract service accounts without having to change the user rights granted in SQL Server, thus reducing your management burden and total cost of ownership.</span></span>  
  
  <span data-ttu-id="0f09d-111">為了確保服務帳戶擁有執行其工作所需的最低使用者權限，BizTalk Server 為服務帳戶建立的「SQL Server 資料庫」角色，在所有的 BizTalk Server 資料庫上都不盡相同。</span><span class="sxs-lookup"><span data-stu-id="0f09d-111">To ensure that the service accounts have the minimum user rights they need to do their jobs, the SQL Server Database roles that BizTalk Server creates for the service accounts are not identical on all the BizTalk Server databases.</span></span> <span data-ttu-id="0f09d-112">在「管理」和「追蹤」資料庫中，所有的主控件執行個體服務帳戶都必須存取相同的 SQL Server 物件，因此 BizTalk Server 建立名為 BTS_Host_User 的單一「SQL Server 資料庫」角色。</span><span class="sxs-lookup"><span data-stu-id="0f09d-112">For the Management and Tracking databases, all of the host instance service accounts need access to the same SQL Server objects, so BizTalk Server created a single SQL Server Database role named BTS_Host_User.</span></span> <span data-ttu-id="0f09d-113">BizTalk 會將針對 BizTalk 主控件而建立的所有 Windows 群組新增到這個「SQL Server 資料庫」角色。</span><span class="sxs-lookup"><span data-stu-id="0f09d-113">BizTalk adds all the Windows groups created for BizTalk hosts to this SQL Server Database role.</span></span>  
  
  <span data-ttu-id="0f09d-114">在 MessageBox 資料庫中，每個主控件都有一些本身專用的資源。</span><span class="sxs-lookup"><span data-stu-id="0f09d-114">For the MessageBox database, each host has some resources dedicated to that host.</span></span> <span data-ttu-id="0f09d-115">BizTalk Server 會建立 SQL Server 資料庫角色，每一部主機，命名為 Bts_&lt\<*hostname*\>（_u)，並新增到其個別的 SQL Server 資料庫角色的每個主控件 Windows 群組，以封鎖存取的其中一個由另一部主機的主機資源。</span><span class="sxs-lookup"><span data-stu-id="0f09d-115">BizTalk Server creates a SQL Server Database role per host, named BTS_\<*hostname*\>_User, and adds the Windows group for each host to its respective SQL Server Database role in order to block access of one host resources by another host.</span></span>  
  
## <a name="accounts-not-supported-by-biztalk-server"></a><span data-ttu-id="0f09d-116">BizTalk Server 不支援的帳戶</span><span class="sxs-lookup"><span data-stu-id="0f09d-116">Accounts not supported by BizTalk Server</span></span>  
 <span data-ttu-id="0f09d-117">BizTalk Server 不支援使用下列任何內建的 Windows 帳戶：</span><span class="sxs-lookup"><span data-stu-id="0f09d-117">BizTalk Server does not support using any of the following built-in Windows accounts:</span></span>  
  
-   <span data-ttu-id="0f09d-118">NT_AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="0f09d-118">NT_AUTHORITY\NetworkService</span></span>  
  
-   <span data-ttu-id="0f09d-119">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="0f09d-119">LocalSystem</span></span>  
  
-   <span data-ttu-id="0f09d-120">NT_AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="0f09d-120">NT_AUTHORITY\LocalService</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f09d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f09d-121">See Also</span></span>  
 <span data-ttu-id="0f09d-122">[系統管理角色的存取控制](../core/access-control-for-administrative-roles.md) </span><span class="sxs-lookup"><span data-stu-id="0f09d-122">[Access Control for Administrative Roles](../core/access-control-for-administrative-roles.md) </span></span>  
 <span data-ttu-id="0f09d-123">[最低安全性使用者權限](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="0f09d-123">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 <span data-ttu-id="0f09d-124">[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="0f09d-124">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="0f09d-125">存取控制和資料安全性</span><span class="sxs-lookup"><span data-stu-id="0f09d-125">Access Control and Data Security</span></span>](../core/access-control-and-data-security.md)