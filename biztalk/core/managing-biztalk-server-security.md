---
title: 管理 BizTalk Server 安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- security, user accounts
- security, passwords
- certificates, security
- security, certificates
- security, BizTalk Server
- passwords, security
- user accounts, security
ms.assetid: adc89b0a-9846-4c99-b0fc-a32fc56ed769
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f31ef3483661b20ff62cadb0ec601282a05af9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262854"
---
# <a name="managing-biztalk-server-security"></a><span data-ttu-id="de79b-102">管理 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="de79b-102">Managing BizTalk Server Security</span></span>
<span data-ttu-id="de79b-103">若要維護安全的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，您必須管理帳戶、憑證及密碼。</span><span class="sxs-lookup"><span data-stu-id="de79b-103">Maintaining a secure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment requires that you manage accounts, certificates, and passwords.</span></span> <span data-ttu-id="de79b-104">為了確保 BizTalk Server 所處理之商務文件的安全性，BizTalk Server 系統管理員必須管理下列帳戶及憑證：</span><span class="sxs-lookup"><span data-stu-id="de79b-104">To help ensure the security of the business documents handled by BizTalk Server, BizTalk Server administrators manage the following accounts and certificates:</span></span>  
  
-   <span data-ttu-id="de79b-105">**BizTalk Server 系統管理員群組**。</span><span class="sxs-lookup"><span data-stu-id="de79b-105">**BizTalk Server Administrators group**.</span></span> <span data-ttu-id="de79b-106">對於透過 BizTalk 管理主控台或使用 Microsoft Windows Management Instrumentation (WMI) 提供者執行系統管理工作的使用者而言，他們必須在 Microsoft SQL Server 及 Microsoft Windows 被授與適當的權限。</span><span class="sxs-lookup"><span data-stu-id="de79b-106">For users to perform administrative tasks either through the BizTalk Administration console or by using the Microsoft Windows Management Instrumentation (WMI) provider, they must be granted the proper privileges in Microsoft SQL Server and Microsoft Windows.</span></span> <span data-ttu-id="de79b-107">如需系統管理工作的權限的詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="de79b-107">For more information about the privileges for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
     <span data-ttu-id="de79b-108">新增使用者至 BizTalk Server 系統管理員群組，或從 BizTalk Server 系統管理員群組移除使用者的相關資訊，請參閱[如何管理 BizTalk Server 系統管理員群組](../core/how-to-manage-the-biztalk-server-administrators-group.md)。</span><span class="sxs-lookup"><span data-stu-id="de79b-108">For information about adding users to the BizTalk Server Administrators group or removing users from the BizTalk Server Administrators group, see [How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md).</span></span>  
  
     <span data-ttu-id="de79b-109">如需企業單一登入的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="de79b-109">For more information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).</span></span>  
  
-   <span data-ttu-id="de79b-110">**BizTalk Server 操作員群組**。</span><span class="sxs-lookup"><span data-stu-id="de79b-110">**BizTalk Server Operators group**.</span></span> <span data-ttu-id="de79b-111">BizTalk Server 操作員是具有低層級權限的角色，只能存取監視和疑難排解動作。</span><span class="sxs-lookup"><span data-stu-id="de79b-111">The BizTalk Server Operator is a low privileged role that only has access to monitoring and troubleshooting actions.</span></span>  
  
     <span data-ttu-id="de79b-112">BizTalk Server 操作員群組的成員可執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="de79b-112">Members of the BizTalk Server Operators group can do the following:</span></span>  
  
    -   <span data-ttu-id="de79b-113">檢視服務狀態及訊息流程。</span><span class="sxs-lookup"><span data-stu-id="de79b-113">View service state and message flow.</span></span>  
  
    -   <span data-ttu-id="de79b-114">啟動或停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="de79b-114">Start or stop applications.</span></span>  
  
    -   <span data-ttu-id="de79b-115">啟動或停止協調流程。</span><span class="sxs-lookup"><span data-stu-id="de79b-115">Start or stop orchestrations.</span></span>  
  
    -   <span data-ttu-id="de79b-116">啟動或停止傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="de79b-116">Start or stop send ports or send port groups.</span></span>  
  
    -   <span data-ttu-id="de79b-117">啟用或停用接收位置。</span><span class="sxs-lookup"><span data-stu-id="de79b-117">Enable or disable receive locations.</span></span> <span data-ttu-id="de79b-118">在下一個 60 秒 (預設值) 的快取重新整理間隔之前，變更不會生效。</span><span class="sxs-lookup"><span data-stu-id="de79b-118">The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default.</span></span> <span data-ttu-id="de79b-119">快取重新整理間隔視在 BizTalk Server 群組層級設定。</span><span class="sxs-lookup"><span data-stu-id="de79b-119">The cache refresh interval is set at the BizTalk Server group level.</span></span>  
  
    -   <span data-ttu-id="de79b-120">終止和繼續服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="de79b-120">Terminate and resume service instances.</span></span>  
  
     <span data-ttu-id="de79b-121">BizTalk Server 操作員群組的成員無法執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="de79b-121">Members of the BizTalk Server Operators group cannot do the following:</span></span>  
  
    -   <span data-ttu-id="de79b-122">修改 BizTalk Server 的組態。</span><span class="sxs-lookup"><span data-stu-id="de79b-122">Modify the configuration for BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="de79b-123">檢視分類為個人識別資訊 (PII) 的訊息內容屬性或訊息內文。</span><span class="sxs-lookup"><span data-stu-id="de79b-123">View message context properties classified as Personally Identifiable Information (PII) or message bodies.</span></span>  
  
    -   <span data-ttu-id="de79b-124">修改訊息路由過程，例如移除或新增新的訂閱到執行中的系統，包括將訊息發佈到 BizTalk Server 執行階段。</span><span class="sxs-lookup"><span data-stu-id="de79b-124">Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de79b-125">如果身為 BizTalk Server 操作員群組成員的使用者同時也是 BizTalk Server 電腦的本機系統管理員，則此使用者可存取這些電腦上之操作員群組角色外的資料。</span><span class="sxs-lookup"><span data-stu-id="de79b-125">If a user who is a member of the BizTalk Server Operators group is also a local administrator on the computers running BizTalk Server, this user can access data beyond the role of the Operators group on these computers.</span></span> <span data-ttu-id="de79b-126">如需詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="de79b-126">For more information, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de79b-127">如果您要允許 BizTalk Server 操作員群組成員的使用者監視遠端 BizTalk Server，此使用這必須也是遠端電腦上之本機系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="de79b-127">If you want to allow a user who is a member of the BizTalk Server Operators group to monitor remote BizTalk servers, this user must also be a member of the local Administrators group on the remote computers.</span></span>  
  
-   <span data-ttu-id="de79b-128">**主機和服務帳戶**。</span><span class="sxs-lookup"><span data-stu-id="de79b-128">**Hosts and service accounts**.</span></span> <span data-ttu-id="de79b-129">建立主控件及其關聯的主控件執行個體時，您必須提供主控件的 Windows 群組以及每個主控件執行個體的服務帳戶憑證。</span><span class="sxs-lookup"><span data-stu-id="de79b-129">When creating a host and its associated host instances, you must provide the Windows group for the host and the service account credentials for each host instance.</span></span> <span data-ttu-id="de79b-130">您必須確定主控件執行個體服務帳戶為主控件的 Windows 群組成員。</span><span class="sxs-lookup"><span data-stu-id="de79b-130">You must ensure that the host instance service accounts are members of the Windows group for the host.</span></span>  
  
-   <span data-ttu-id="de79b-131">**簽署憑證**。</span><span class="sxs-lookup"><span data-stu-id="de79b-131">**Signing certificates**.</span></span> <span data-ttu-id="de79b-132">BizTalk 群組已指定簽章憑證 (私用金鑰憑證)。</span><span class="sxs-lookup"><span data-stu-id="de79b-132">Signing certificates (private key certificates) are specified for the BizTalk group.</span></span> <span data-ttu-id="de79b-133">這些憑證是選擇性的，BizTalk Server 系統管理員可隨時變更這些憑證。</span><span class="sxs-lookup"><span data-stu-id="de79b-133">These are optional and can be changed at any time by a BizTalk Server administrator.</span></span>  
  
 <span data-ttu-id="de79b-134">如需更完整的 BizTalk Server 會使用 Windows 帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de79b-134">For more complete information about Windows accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de79b-135">本節內容</span><span class="sxs-lookup"><span data-stu-id="de79b-135">In This Section</span></span>  
  
-   [<span data-ttu-id="de79b-136">管理 Windows 群組和使用者帳戶的最佳作法</span><span class="sxs-lookup"><span data-stu-id="de79b-136">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)  
  
-   [<span data-ttu-id="de79b-137">管理憑證的最佳作法</span><span class="sxs-lookup"><span data-stu-id="de79b-137">Best Practices for Managing Certificates</span></span>](../core/best-practices-for-managing-certificates1.md)  
  
-   [<span data-ttu-id="de79b-138">管理 Windows 群組和使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de79b-138">Managing Windows Groups and User Accounts</span></span>](../core/managing-windows-groups-and-user-accounts.md)