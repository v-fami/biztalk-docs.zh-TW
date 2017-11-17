---
title: "在 BizTalk 多伺服器安裝上實作 Active Directory 權限的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 315e25c4-b21d-4b5f-a1d2-1e2777b57f9e
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0f6f5cb6403c752b18cbfb1c4370cbe3ca95e65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-implementing-active-directory-permissions-on-multi-server-biztalk-installations"></a><span data-ttu-id="0acdb-102">在 BizTalk 多伺服器安裝上實作 Active Directory 權限的指導方針</span><span class="sxs-lookup"><span data-stu-id="0acdb-102">Guidelines for Implementing Active Directory Permissions on Multi Server BizTalk Installations</span></span>
<span data-ttu-id="0acdb-103">本主題描述建立 Active Directory 組織單位的指導方針，這些組織單位是由您在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝中使用的使用者帳戶和群組所構成的。</span><span class="sxs-lookup"><span data-stu-id="0acdb-103">This topic describes guidelines for creating Active Directory Organizational Units, which consist of the user accounts and groups that you use in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="0acdb-104">在此建立的帳戶不需要在一般使用者的網域以外具有權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-104">The accounts created herein do not need permissions in the domain beyond those of ordinary users.</span></span> <span data-ttu-id="0acdb-105">網域帳戶可能需要在以下信任界限內具有更高的權限：</span><span class="sxs-lookup"><span data-stu-id="0acdb-105">The domain accounts may need elevated privileges within the trust boundary that includes:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   <span data-ttu-id="0acdb-106">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 伺服器上)</span><span class="sxs-lookup"><span data-stu-id="0acdb-106">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] server)</span></span>  
  
-   <span data-ttu-id="0acdb-107">Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0acdb-107">Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="0acdb-108">外部資料庫一</span><span class="sxs-lookup"><span data-stu-id="0acdb-108">External Database One</span></span>  
  
-   <span data-ttu-id="0acdb-109">外部資料庫二</span><span class="sxs-lookup"><span data-stu-id="0acdb-109">External Database Two</span></span>  
  
-   <span data-ttu-id="0acdb-110">外部資料庫*N*</span><span class="sxs-lookup"><span data-stu-id="0acdb-110">External Database *N*</span></span>  
  
 <span data-ttu-id="0acdb-111">例如，對於網域帳戶可能需要授與權限，以便在裝載外部資料庫的系統上執行某些動作。</span><span class="sxs-lookup"><span data-stu-id="0acdb-111">For example, a domain account may need to be granted rights to perform certain actions on the systems hosting external databases.</span></span> <span data-ttu-id="0acdb-112">在另一種情況下，帳戶可能需要將檔案寫入檔案放置資料夾，因而需要該資料夾的寫入存取。</span><span class="sxs-lookup"><span data-stu-id="0acdb-112">In another case, an account may need to write a file to a file drop folder, requiring write access to the folder.</span></span>  
  
 <span data-ttu-id="0acdb-113">使用**Active Directory 使用者和電腦**主控台來建立及管理網域使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-113">Use the **Active Directory Users and Computers** console to create and manage domain user and group accounts.</span></span> <span data-ttu-id="0acdb-114">按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。</span><span class="sxs-lookup"><span data-stu-id="0acdb-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.</span></span>  
  
## <a name="biztalk-server-installation-and-configuration-account"></a><span data-ttu-id="0acdb-115">BizTalk Server 安裝和設定帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-115">BizTalk Server Installation and Configuration Account</span></span>  
 <span data-ttu-id="0acdb-116">在開發環境中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 都需要使用在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 系統上具有系統管理權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-116">In the development environment, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation program and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard require the use of an account with administrative rights on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] systems.</span></span> <span data-ttu-id="0acdb-117">在完成設定和組態之後，立即就可以叫用權限或停用帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-117">Rights can be revoked or the account disabled as soon as setup and configuration are complete.</span></span> <span data-ttu-id="0acdb-118">帳戶也必須屬於幾個 BizTalk 群組，以下幾節會對這些提供說明。</span><span class="sxs-lookup"><span data-stu-id="0acdb-118">The account must also belong to several BizTalk groups, covered in the following sections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-119">如果用於安裝的帳戶屬於不同伺服器的 Active Directory 樹系，您將無法設定 SSO 元件。</span><span class="sxs-lookup"><span data-stu-id="0acdb-119">You will not be able to configure SSO components if the account used for installation belongs to a different Active Directory forest than the server.</span></span> <span data-ttu-id="0acdb-120">如果沒有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式帳戶，請使用本機系統管理員帳戶進行 SSO 組態。</span><span class="sxs-lookup"><span data-stu-id="0acdb-120">If you do not have a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installer account, use a local administrator account for SSO configuration.</span></span> <span data-ttu-id="0acdb-121">這個方法可能會在安裝期間造成其他問題，例如需要使用不同的認證登入資源。</span><span class="sxs-lookup"><span data-stu-id="0acdb-121">This methodology may create other issues during installation, such as the need to log on to resources using different credentials.</span></span>  
  
## <a name="biztalk-server-development-accounts"></a><span data-ttu-id="0acdb-122">BizTalk Server 開發帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-122">BizTalk Server Development Accounts</span></span>  
 <span data-ttu-id="0acdb-123">進行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發的個人需要存取配接器、接收和傳送處理常式，以及接收位置。</span><span class="sxs-lookup"><span data-stu-id="0acdb-123">Individuals doing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development require access to adapters, receive and send handlers, and receive locations.</span></span> <span data-ttu-id="0acdb-124">這項存取需要網域開發人員群組的成員**BizTalk Server 系統管理員**和**SSO 分支機構系統管理員**群組。</span><span class="sxs-lookup"><span data-stu-id="0acdb-124">This access requires the domain developer group to be members of the **BizTalk Server Administrators** and **SSO Affiliate Administrators** groups.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-125">對於可以包含外部網域使用者的群組類型，以及可以包含在其他群組中的群組類型，Active Directory 都具有限制。</span><span class="sxs-lookup"><span data-stu-id="0acdb-125">Active Directory has restrictions regarding the types of groups that can contain foreign domain users, and the types of groups that can be contained in other groups.</span></span> <span data-ttu-id="0acdb-126">以下所建立的群組及帳戶都在單一網域上的多伺服器環境中經過測試。</span><span class="sxs-lookup"><span data-stu-id="0acdb-126">The groups and accounts created below are tested in a multiserver environment on a single domain.</span></span>  
  
## <a name="biztalk-server-deployment-accounts"></a><span data-ttu-id="0acdb-127">BizTalk Server 部署帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-127">BizTalk Server Deployment Accounts</span></span>  
 <span data-ttu-id="0acdb-128">部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式的個人將需要是本機系統上的系統管理員，而且可能需要在該環境中的其他權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-128">Individuals deploying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications will need to be administrators on the local systems and may require other permissions in the environment.</span></span> <span data-ttu-id="0acdb-129">BizTalk Server 部署帳戶是為此目的，本主題中參考。</span><span class="sxs-lookup"><span data-stu-id="0acdb-129">A BizTalk Server deployment account is referenced in this topic for this purpose.</span></span>  
  
 <span data-ttu-id="0acdb-130">這項存取需要網域部署群組的成員**BizTalk Server 系統管理員**和**SSO 分支機構系統管理員**群組。</span><span class="sxs-lookup"><span data-stu-id="0acdb-130">This access requires the domain deployment group to be members of the **BizTalk Server Administrators** and **SSO Affiliate Administrators** groups.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-131">如果用於安裝的帳戶屬於不同伺服器的 Active Directory 樹系，您將無法設定 SSO 元件。</span><span class="sxs-lookup"><span data-stu-id="0acdb-131">You will not be able to configure SSO components if the account used for installation belongs to a different Active Directory forest than the server.</span></span> <span data-ttu-id="0acdb-132">如果您沒有 BizTalk Server 部署帳戶，請使用本機系統管理員帳戶進行 SSO 組態。</span><span class="sxs-lookup"><span data-stu-id="0acdb-132">If you do not have a BizTalk Server deployment account, use a local administrator account for SSO configuration.</span></span> <span data-ttu-id="0acdb-133">這個方法可能會在安裝期間造成其他問題，例如需要使用不同的認證登入資源。</span><span class="sxs-lookup"><span data-stu-id="0acdb-133">This methodology may create other issues during installation, such as the need to log on to resources using different credentials.</span></span>  
  
## <a name="biztalk-server-support-accounts"></a><span data-ttu-id="0acdb-134">BizTalk Server 支援帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-134">BizTalk Server Support Accounts</span></span>  
 <span data-ttu-id="0acdb-135">支援 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式的個人將需要是本機系統上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0acdb-135">Individuals supporting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications will need to be administrators on the local systems.</span></span> <span data-ttu-id="0acdb-136">在本主題中為此目的而參考 BizTalk 支援帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-136">A BizTalk support account is referenced in this topic for this purpose.</span></span>  
  
 <span data-ttu-id="0acdb-137">這項存取需要網域支援群組的成員**BizTalk Server 系統管理員**群組。</span><span class="sxs-lookup"><span data-stu-id="0acdb-137">This access requires the domain support group to be members of the **BizTalk Server Administrators** group.</span></span>  
  
## <a name="sql-server-service-accounts"></a><span data-ttu-id="0acdb-138">SQL Server 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-138">SQL Server Service Accounts</span></span>  
 <span data-ttu-id="0acdb-139">執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 執行個體的服務必須屬於和安裝、開發及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件所使用之帳戶相同的 Active Directory 網域。</span><span class="sxs-lookup"><span data-stu-id="0acdb-139">The service running the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance must belong to the same Active Directory domain as the accounts installing, developing, and deploying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components.</span></span>  
  
-   <span data-ttu-id="0acdb-140">使用**SQLAdmin**系統管理功能 （互動式登入）。</span><span class="sxs-lookup"><span data-stu-id="0acdb-140">Use **SQLAdmin** for administrative functions (interactive logon).</span></span>  
  
-   <span data-ttu-id="0acdb-141">使用**SQLService**管理服務 （無互動式登入）。</span><span class="sxs-lookup"><span data-stu-id="0acdb-141">Use **SQLService** to manage the service (no interactive logon).</span></span>  
  
-   <span data-ttu-id="0acdb-142">使用**SQLAccess**存取外部資料庫。</span><span class="sxs-lookup"><span data-stu-id="0acdb-142">Use **SQLAccess** to access external databases.</span></span>  
  
-   <span data-ttu-id="0acdb-143">SQLAdmin 必須是 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 系統上本機系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="0acdb-143">SQLAdmin must be a member of the local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] system.</span></span>  
  
-   <span data-ttu-id="0acdb-144">SQLService 必須是本機 Administrators 群組的成員上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]系統和必須授與**以服務方式登入**使用者權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-144">SQLService must be a member of the local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] system and needs to be granted the **Log on as a service** user right.</span></span>  
  
-   <span data-ttu-id="0acdb-145">SQLAccess 需要遠端資料庫伺服器上的適當權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-145">SQLAccess needs appropriate rights on the remote database servers.</span></span>  
  
 <span data-ttu-id="0acdb-146">**SQL 帳戶：**</span><span class="sxs-lookup"><span data-stu-id="0acdb-146">**SQL Accounts:**</span></span>  
  
|<span data-ttu-id="0acdb-147">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0acdb-147">**User name**</span></span>|<span data-ttu-id="0acdb-148">**First Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-148">**First Name**</span></span>|<span data-ttu-id="0acdb-149">**Last Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-149">**Last Name**</span></span>|<span data-ttu-id="0acdb-150">**全名**</span><span class="sxs-lookup"><span data-stu-id="0acdb-150">**Full Name**</span></span>|  
|-------------------|--------------------|-------------------|-------------------|  
|<span data-ttu-id="0acdb-151">SQLService</span><span class="sxs-lookup"><span data-stu-id="0acdb-151">SQLService</span></span>|<span data-ttu-id="0acdb-152">SQL</span><span class="sxs-lookup"><span data-stu-id="0acdb-152">SQL</span></span>|<span data-ttu-id="0acdb-153">SQLService</span><span class="sxs-lookup"><span data-stu-id="0acdb-153">SQLService</span></span>|<span data-ttu-id="0acdb-154">SQL 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-154">SQL Service Account</span></span>|  
|<span data-ttu-id="0acdb-155">SQLAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-155">SQLAdmin</span></span>|<span data-ttu-id="0acdb-156">管理</span><span class="sxs-lookup"><span data-stu-id="0acdb-156">Admin</span></span>|<span data-ttu-id="0acdb-157">SQLService</span><span class="sxs-lookup"><span data-stu-id="0acdb-157">SQLService</span></span>|<span data-ttu-id="0acdb-158">SQL 管理帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-158">SQL Admin Account</span></span>|  
|<span data-ttu-id="0acdb-159">SQLAccess</span><span class="sxs-lookup"><span data-stu-id="0acdb-159">SQLAccess</span></span>|<span data-ttu-id="0acdb-160">存取</span><span class="sxs-lookup"><span data-stu-id="0acdb-160">Access</span></span>|<span data-ttu-id="0acdb-161">SQLService</span><span class="sxs-lookup"><span data-stu-id="0acdb-161">SQLService</span></span>|<span data-ttu-id="0acdb-162">SQL 存取帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-162">SQL Access Account</span></span>|  
  
 <span data-ttu-id="0acdb-163">根據公司標準設定帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="0acdb-163">Set account passwords according to company standards.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0acdb-164">在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦上，修改 SQL Server 和 SQLServerAgent 服務的啟動密碼，以使用 SQLService 帳戶和認證。</span><span class="sxs-lookup"><span data-stu-id="0acdb-164">On the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], modify the startup parameters for the SQL Server and SQLServerAgent services to use the SQLService account and credentials.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-165">這個 [使用者名稱] 欄位是範例，您可能需要變更名稱以避免與其他 Active Directory 帳戶發生衝突。</span><span class="sxs-lookup"><span data-stu-id="0acdb-165">The Username fields are samples; you may need to change the names to avoid conflicting with other Active Directory accounts.</span></span>  
  
## <a name="windows-sharepoint-services-account"></a><span data-ttu-id="0acdb-166">Windows SharePoint Services 帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-166">Windows SharePoint Services Account</span></span>  
 <span data-ttu-id="0acdb-167">在安裝 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 之前，必須先建立 Windows SharePoint Services 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-167">The Windows SharePoint Services accounts must be created prior to installing [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0acdb-168">關於 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 帳戶的建議和注意事項：</span><span class="sxs-lookup"><span data-stu-id="0acdb-168">Recommendations and notes on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] account:</span></span>  
  
-   <span data-ttu-id="0acdb-169">請使用 SharePoint 管理帳戶 (SPAdmin) 運用系統管理功能、SharePoint 計時器服務和所有 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 存取。</span><span class="sxs-lookup"><span data-stu-id="0acdb-169">Use the SharePoint Admin Account (SPAdmin) for administrative functions, SharePoint Timer Service and all [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] access.</span></span>  
  
-   <span data-ttu-id="0acdb-170">SPAdmin 是網站擁有者，而且將需要電子郵件別名。</span><span class="sxs-lookup"><span data-stu-id="0acdb-170">SPAdmin is the site owner and will need an e-mail alias.</span></span>  
  
-   <span data-ttu-id="0acdb-171">SPAdmin 必須是本機 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上本機系統管理員群組的成員 (Windows SharePoint Services 安裝會做到這點)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-171">SPAdmin must be a member of the local administrators group on the local [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer (Windows SharePoint Services setup does this).</span></span>  
  
-   <span data-ttu-id="0acdb-172">SPAdmin 必須在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上具有安全性系統管理員和資料庫建立者角色 (Windows SharePoint Services 安裝會做到這點)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-172">SPAdmin must have the security administrator and database creator roles on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer (Windows SharePoint Services setup does this).</span></span>  
  
 <span data-ttu-id="0acdb-173">**Sharepoint 帳戶：**</span><span class="sxs-lookup"><span data-stu-id="0acdb-173">**Sharepoint Accounts:**</span></span>  
  
|<span data-ttu-id="0acdb-174">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0acdb-174">**User name**</span></span>|<span data-ttu-id="0acdb-175">**First Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-175">**First Name**</span></span>|<span data-ttu-id="0acdb-176">**Last Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-176">**Last Name**</span></span>|<span data-ttu-id="0acdb-177">**全名**</span><span class="sxs-lookup"><span data-stu-id="0acdb-177">**Full Name**</span></span>|  
|-------------------|--------------------|-------------------|-------------------|  
|<span data-ttu-id="0acdb-178">SPAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-178">SPAdmin</span></span>|<span data-ttu-id="0acdb-179">管理</span><span class="sxs-lookup"><span data-stu-id="0acdb-179">Admin</span></span>|<span data-ttu-id="0acdb-180">SPService</span><span class="sxs-lookup"><span data-stu-id="0acdb-180">SPService</span></span>|<span data-ttu-id="0acdb-181">SharePoint 管理帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-181">SharePoint Admin Account</span></span>|  
  
 <span data-ttu-id="0acdb-182">根據公司標準設定帳戶密碼，而且能在進行組態步驟的期間擷取這些密碼。</span><span class="sxs-lookup"><span data-stu-id="0acdb-182">Set account passwords according to company standards and be able to retrieve these passwords during the configuration steps.</span></span> <span data-ttu-id="0acdb-183">請參閱**密碼**區段本主題適用於周圍的問題產生密碼。</span><span class="sxs-lookup"><span data-stu-id="0acdb-183">Refer to the **Passwords** section of this topic for issues surrounding generated passwords.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-184">這個 [使用者名稱] 欄位是範例，您可能需要變更名稱以保護其他 AD 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-184">This Username field is a sample; you may need to change this name to protect other AD accounts.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0acdb-185">在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上安裝 Windows SharePoint Services 後，確認 SharePoint 計時器服務的啟動參數有使用 SPAdmin 帳戶和認證。</span><span class="sxs-lookup"><span data-stu-id="0acdb-185">After installing Windows SharePoint Services on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], confirm that the startup parameters for the SharePoint Timer Service is using the SPAdmin account and credentials.</span></span>  
  
## <a name="biztalk-groups-and-users"></a><span data-ttu-id="0acdb-186">BizTalk 群組及使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-186">BizTalk Groups and Users</span></span>  
 <span data-ttu-id="0acdb-187">在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 之前，必須先建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組及使用者。</span><span class="sxs-lookup"><span data-stu-id="0acdb-187">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Groups and Users must be created prior to running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard.</span></span> <span data-ttu-id="0acdb-188">在單一系統安裝中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用在進行組態時所建立的本機群組及帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-188">In a single-system installation, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses local groups and accounts which are created during configuration.</span></span> <span data-ttu-id="0acdb-189">不過，如果部署個別的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主機，或是在兩部不同的電腦上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，您就必須使用網域使用者及群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-189">However, if separate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts are deployed or if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on two different computers you must use domain user and group accounts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-190">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 無法建立網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-190">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard cannot create domain accounts.</span></span>  
  
 <span data-ttu-id="0acdb-191">關於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務及使用者帳戶的建議和注意事項：</span><span class="sxs-lookup"><span data-stu-id="0acdb-191">Recommendations and notes on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service and user accounts:</span></span>  
  
-   <span data-ttu-id="0acdb-192">建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的組織單位 (OU)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-192">Create an Organizational Unit (OU) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="0acdb-193">所有的帳戶及群組都將屬於這個 OU。</span><span class="sxs-lookup"><span data-stu-id="0acdb-193">All accounts and groups will belong to this OU.</span></span>  
  
-   <span data-ttu-id="0acdb-194">請運用完整名稱提供描述，下列清單中的名稱應該讓安裝程式能在進行組態時選取適當的群組/帳戶/使用者。</span><span class="sxs-lookup"><span data-stu-id="0acdb-194">Be descriptive with full names; the names in the following lists should enable the installer to select the proper groups/accounts/users during configuration.</span></span>  
  
-   <span data-ttu-id="0acdb-195">名字和姓氏是選擇性的，只因為一致性而包括。</span><span class="sxs-lookup"><span data-stu-id="0acdb-195">First name and last name are optional; included for consistency only.</span></span>  
  
-   <span data-ttu-id="0acdb-196">區分文字**BTService**和**BTUser**指的是服務帳戶 （自動化） 與一般/共用人員使用者。</span><span class="sxs-lookup"><span data-stu-id="0acdb-196">The differentiator **BTService** and **BTUser** refers to service accounts (automatons) and generic/shared human users.</span></span>  
  
-   <span data-ttu-id="0acdb-197">建立網域帳戶並透過 ADSI 指令碼，為上線路環境建立使用者及群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-197">Create domain accounts and populate them via an ADSI script for user and group account creation for up line environments.</span></span>  
  
 <span data-ttu-id="0acdb-198">**BizTalk 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="0acdb-198">**BizTalk Service Accounts**</span></span>  
  
|<span data-ttu-id="0acdb-199">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0acdb-199">**User name**</span></span>|<span data-ttu-id="0acdb-200">**First Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-200">**First Name**</span></span>|<span data-ttu-id="0acdb-201">**Last Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-201">**Last Name**</span></span>|<span data-ttu-id="0acdb-202">**全名**</span><span class="sxs-lookup"><span data-stu-id="0acdb-202">**Full Name**</span></span>|  
|-------------------|--------------------|-------------------|-------------------|  
|<span data-ttu-id="0acdb-203">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-203">BTService</span></span>|<span data-ttu-id="0acdb-204">BTS</span><span class="sxs-lookup"><span data-stu-id="0acdb-204">BTS</span></span>|<span data-ttu-id="0acdb-205">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-205">BTService</span></span>|<span data-ttu-id="0acdb-206">BizTalk 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-206">BizTalk Service Account</span></span>|  
|<span data-ttu-id="0acdb-207">BTServiceHost</span><span class="sxs-lookup"><span data-stu-id="0acdb-207">BTServiceHost</span></span>|<span data-ttu-id="0acdb-208">Host</span><span class="sxs-lookup"><span data-stu-id="0acdb-208">Host</span></span>|<span data-ttu-id="0acdb-209">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-209">BTService</span></span>|<span data-ttu-id="0acdb-210">BizTalk 主控件執行個體帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-210">BizTalk Host Instance Account</span></span>|  
|<span data-ttu-id="0acdb-211">BTServiceHostIso</span><span class="sxs-lookup"><span data-stu-id="0acdb-211">BTServiceHostIso</span></span>|<span data-ttu-id="0acdb-212">HostIso</span><span class="sxs-lookup"><span data-stu-id="0acdb-212">HostIso</span></span>|<span data-ttu-id="0acdb-213">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-213">BTService</span></span>|<span data-ttu-id="0acdb-214">BizTalk 外掛式主控件執行個體帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-214">BizTalk Isolated Host Instance Account</span></span>|  
|<span data-ttu-id="0acdb-215">SSOService</span><span class="sxs-lookup"><span data-stu-id="0acdb-215">SSOService</span></span>|<span data-ttu-id="0acdb-216">SSO</span><span class="sxs-lookup"><span data-stu-id="0acdb-216">SSO</span></span>|<span data-ttu-id="0acdb-217">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-217">BTService</span></span>|<span data-ttu-id="0acdb-218">企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="0acdb-218">Enterprise Single Sign-On Service</span></span>|  
|<span data-ttu-id="0acdb-219">BTServiceREU</span><span class="sxs-lookup"><span data-stu-id="0acdb-219">BTServiceREU</span></span>|<span data-ttu-id="0acdb-220">REU</span><span class="sxs-lookup"><span data-stu-id="0acdb-220">REU</span></span>|<span data-ttu-id="0acdb-221">BTService</span><span class="sxs-lookup"><span data-stu-id="0acdb-221">BTService</span></span>|<span data-ttu-id="0acdb-222">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="0acdb-222">Rule Engine Update Service</span></span>|  
  
 <span data-ttu-id="0acdb-223">根據公司和環境標準設定使用者名稱 (例如，devBTService、alphaBTService)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-223">Set user names according to company and environmental standards (for example, devBTService, alphaBTService).</span></span> <span data-ttu-id="0acdb-224">根據公司標準設定帳戶密碼，而且能在進行組態步驟時擷取這些密碼。</span><span class="sxs-lookup"><span data-stu-id="0acdb-224">Set account passwords according to company standards and be able to retrieve them for the configuration steps.</span></span> <span data-ttu-id="0acdb-225">請參閱**開發的密碼考量**區段本主題適用於周圍的問題產生密碼。</span><span class="sxs-lookup"><span data-stu-id="0acdb-225">Refer to the **Password Considerations for Development** section of this topic for issues surrounding generated passwords.</span></span>  
  
 <span data-ttu-id="0acdb-226">安裝程式會注意到服務帳戶相當精細，對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所建立的服務，這些幾乎具有一對一的對應。</span><span class="sxs-lookup"><span data-stu-id="0acdb-226">The installer will notice the service accounts are quite granular, with a near one-to-one mapping to the services created by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="0acdb-227">這種粒度讓企業 IT 安全性能夠視需要而追蹤或限制存取。</span><span class="sxs-lookup"><span data-stu-id="0acdb-227">The granularity allows corporate IT security to track or restrict access as needed.</span></span> <span data-ttu-id="0acdb-228">雖然這是建議的粒度，卻必須由系統設計人員和企業安全性人員來決定在企業環境中是否有必要如此。</span><span class="sxs-lookup"><span data-stu-id="0acdb-228">The granularity is recommended, but it is up to the system designer and enterprise security personnel to determine if it is necessary in the enterprise environment.</span></span>  
  
 <span data-ttu-id="0acdb-229">在上一個群組中的服務帳戶，其用途只是要進行自動存取，而非由使用者進行互動式登入。</span><span class="sxs-lookup"><span data-stu-id="0acdb-229">The service accounts in the previous group are intended for automaton access only, not for interactive logon by users.</span></span>  
  
#### <a name="to-set-the-appropriate-account-options"></a><span data-ttu-id="0acdb-230">設定適當的帳戶選項</span><span class="sxs-lookup"><span data-stu-id="0acdb-230">To set the appropriate account options</span></span>  
  
1.  <span data-ttu-id="0acdb-231">在**Active Directory 使用者和電腦**主控台，按一下以展開網域，然後再按一下展開**使用者**容器。</span><span class="sxs-lookup"><span data-stu-id="0acdb-231">In the **Active Directory Users and Computers** console, click to expand the domain, and then click to expand the **Users** container.</span></span>  
  
2.  <span data-ttu-id="0acdb-232">以滑鼠右鍵按一下 帳戶，然後選取**屬性**顯示**屬性**帳戶 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-232">Right-click the account and then select **Properties** to display the **Properties** dialog box for the account.</span></span>  
  
3.  <span data-ttu-id="0acdb-233">按一下**帳戶** 索引標籤**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-233">Click the **Account** tab of the **Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="0acdb-234">按一下以核取下列選項：</span><span class="sxs-lookup"><span data-stu-id="0acdb-234">Click to check the following options:</span></span>  
  
    -   <span data-ttu-id="0acdb-235">**使用者不得變更密碼**(企業安全性會批次處理變更的密碼)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-235">**User cannot change password** (enterprise security will batch change the passwords).</span></span>  
  
    -   <span data-ttu-id="0acdb-236">**密碼永久有效**</span><span class="sxs-lookup"><span data-stu-id="0acdb-236">**Password never expires**</span></span>  
  
5.  <span data-ttu-id="0acdb-237">按一下**登入到** 按鈕以顯示**登入工作站** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-237">Click the **Log On To** button to display the **Logon Workstations** dialog box.</span></span>  
  
6.  <span data-ttu-id="0acdb-238">按一下選項**下列電腦**，新增每台電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-238">Click the option for **The following computers**, add each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="0acdb-239">按一下**遙控器** 索引標籤**屬性**對話方塊，然後按一下以清除選項以**啟用遠端控制**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-239">Click the **Remote Control** tab of the **Properties** dialog box, and then click to clear the option to **Enable remote control**.</span></span>  
  
8.  <span data-ttu-id="0acdb-240">按一下**終端機服務設定檔** 索引標籤**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-240">Click the **Terminal Services Profile** tab of the **Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="0acdb-241">按一下以核取選項**拒絕此使用者的權限登入任何終端機伺服器**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-241">Click to check the option to **Deny this user permissions to log on to any Terminal Server**.</span></span>  
  
10. <span data-ttu-id="0acdb-242">按一下**確定**關閉**屬性**帳戶 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-242">Click **OK** to close the **Properties** dialog box for the account.</span></span>  
  
11. <span data-ttu-id="0acdb-243">針對每個服務帳戶重複步驟 3 到 10。</span><span class="sxs-lookup"><span data-stu-id="0acdb-243">Repeat steps 3 through 10 for each service account.</span></span>  
  
 <span data-ttu-id="0acdb-244">**BizTalk 使用者帳戶**</span><span class="sxs-lookup"><span data-stu-id="0acdb-244">**BizTalk User Accounts**</span></span>  
  
|<span data-ttu-id="0acdb-245">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0acdb-245">**User name**</span></span>|<span data-ttu-id="0acdb-246">**First Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-246">**First Name**</span></span>|<span data-ttu-id="0acdb-247">**Last Name**</span><span class="sxs-lookup"><span data-stu-id="0acdb-247">**Last Name**</span></span>|<span data-ttu-id="0acdb-248">**全名**</span><span class="sxs-lookup"><span data-stu-id="0acdb-248">**Full Name**</span></span>|  
|-------------------|--------------------|-------------------|-------------------|  
|<span data-ttu-id="0acdb-249">BTUserAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-249">BTUserAdmin</span></span>|<span data-ttu-id="0acdb-250">管理</span><span class="sxs-lookup"><span data-stu-id="0acdb-250">Admin</span></span>|<span data-ttu-id="0acdb-251">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-251">BTUser</span></span>|<span data-ttu-id="0acdb-252">BizTalk 系統管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-252">BizTalk Administrative User Account</span></span>|  
|<span data-ttu-id="0acdb-253">BTUserDeploy</span><span class="sxs-lookup"><span data-stu-id="0acdb-253">BTUserDeploy</span></span>|<span data-ttu-id="0acdb-254">部署</span><span class="sxs-lookup"><span data-stu-id="0acdb-254">Deploy</span></span>|<span data-ttu-id="0acdb-255">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-255">BTUser</span></span>|<span data-ttu-id="0acdb-256">BizTalk 部署使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-256">BizTalk Deployment User Account</span></span>|  
|<span data-ttu-id="0acdb-257">BTUserHostInstance</span><span class="sxs-lookup"><span data-stu-id="0acdb-257">BTUserHostInstance</span></span>|<span data-ttu-id="0acdb-258">HostInstance</span><span class="sxs-lookup"><span data-stu-id="0acdb-258">HostInstance</span></span>|<span data-ttu-id="0acdb-259">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-259">BTUser</span></span>|<span data-ttu-id="0acdb-260">BizTalk 主控件執行個體帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-260">BizTalk Host Instance Account</span></span>|  
|<span data-ttu-id="0acdb-261">BTUserHostIsolated</span><span class="sxs-lookup"><span data-stu-id="0acdb-261">BTUserHostIsolated</span></span>|<span data-ttu-id="0acdb-262">IsolatedlHost</span><span class="sxs-lookup"><span data-stu-id="0acdb-262">IsolatedlHost</span></span>|<span data-ttu-id="0acdb-263">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-263">BTUser</span></span>|<span data-ttu-id="0acdb-264">BizTalk 外掛式主控件執行個體帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-264">BizTalk Isolated Host Instance Account</span></span>|  
|<span data-ttu-id="0acdb-265">BTUserInstall</span><span class="sxs-lookup"><span data-stu-id="0acdb-265">BTUserInstall</span></span>|<span data-ttu-id="0acdb-266">Install</span><span class="sxs-lookup"><span data-stu-id="0acdb-266">Install</span></span>|<span data-ttu-id="0acdb-267">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-267">BTUser</span></span>|<span data-ttu-id="0acdb-268">BizTalk 安裝使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-268">BizTalk Installation User Account</span></span>|  
|<span data-ttu-id="0acdb-269">BTUserSupport</span><span class="sxs-lookup"><span data-stu-id="0acdb-269">BTUserSupport</span></span>|<span data-ttu-id="0acdb-270">支援</span><span class="sxs-lookup"><span data-stu-id="0acdb-270">Support</span></span>|<span data-ttu-id="0acdb-271">BTUser</span><span class="sxs-lookup"><span data-stu-id="0acdb-271">BTUser</span></span>|<span data-ttu-id="0acdb-272">BizTalk 支援存取帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-272">BizTalk Support Access Account</span></span>|  
  
#### <a name="to-set-the-appropriate-account-options-follow-these-steps"></a><span data-ttu-id="0acdb-273">遵循以下步驟設定適當的帳戶選項</span><span class="sxs-lookup"><span data-stu-id="0acdb-273">To set the appropriate account options follow these steps</span></span>  
  
1.  <span data-ttu-id="0acdb-274">在**Active Directory 使用者和電腦**主控台中，按一下以展開網域，然後再按一下以展開**使用者**容器。</span><span class="sxs-lookup"><span data-stu-id="0acdb-274">In the **Active Directory Users and Computers** console click to expand the domain, and then click to expand the **Users** container.</span></span>  
  
2.  <span data-ttu-id="0acdb-275">以滑鼠右鍵按一下 帳戶，然後選取**屬性**顯示**屬性**帳戶 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-275">Right-click the account and then select **Properties** to display the **Properties** dialog box for the account.</span></span>  
  
3.  <span data-ttu-id="0acdb-276">按一下**帳戶** 索引標籤**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-276">Click the **Account** tab of the **Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="0acdb-277">按一下以核取下列選項：</span><span class="sxs-lookup"><span data-stu-id="0acdb-277">Click to check the following options:</span></span>  
  
    -   <span data-ttu-id="0acdb-278">**使用者不得變更密碼**(企業安全性會批次處理變更的密碼)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-278">**User cannot change password** (enterprise security will batch change the passwords).</span></span>  
  
    -   <span data-ttu-id="0acdb-279">**密碼永久有效**</span><span class="sxs-lookup"><span data-stu-id="0acdb-279">**Password never expires**</span></span>  
  
5.  <span data-ttu-id="0acdb-280">按一下**登入到** 按鈕以顯示**登入工作站** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-280">Click the **Log On To** button to display the **Logon Workstations** dialog box.</span></span>  
  
6.  <span data-ttu-id="0acdb-281">按一下選項**下列電腦**，新增每台電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-281">Click the option for **The following computers**, add each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="0acdb-282">按一下**遙控器** 索引標籤**屬性**對話方塊，然後按一下以核取選項**啟用遠端控制**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-282">Click the **Remote Control** tab of the **Properties** dialog box, and then click to check the option to **Enable remote control**.</span></span>  
  
8.  <span data-ttu-id="0acdb-283">按一下**終端機服務設定檔** 索引標籤**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-283">Click the **Terminal Services Profile** tab of the **Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="0acdb-284">按一下以清除選項以**拒絕此使用者的權限登入任何終端機伺服器**。</span><span class="sxs-lookup"><span data-stu-id="0acdb-284">Click to clear the option to **Deny this user permissions to log on to any Terminal Server**.</span></span>  
  
10. <span data-ttu-id="0acdb-285">按一下**確定**關閉**屬性**帳戶 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-285">Click **OK** to close the **Properties** dialog box for the account.</span></span>  
  
11. <span data-ttu-id="0acdb-286">針對每個使用者帳戶重複步驟 3 到 10。</span><span class="sxs-lookup"><span data-stu-id="0acdb-286">Repeat steps 3 through 10 for each user account.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0acdb-287">如果這些帳戶所提供的角色都有指派給實際的使用者，便可以停用任何這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-287">Any of these accounts can be disabled if the roles they are to provide are assigned to actual users.</span></span> <span data-ttu-id="0acdb-288">在第一版和第二版的早期階段，都假設會在開發、Alpha 測試和 Beta 測試的環境下使用這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-288">In the early stages of release one and release two, it is assumed that these accounts are used in the development, alpha test, and beta test environments.</span></span>  
  
 <span data-ttu-id="0acdb-289">**BizTalk 群組帳戶**</span><span class="sxs-lookup"><span data-stu-id="0acdb-289">**BizTalk Group Accounts**</span></span>  
  
|<span data-ttu-id="0acdb-290">**群組名稱**</span><span class="sxs-lookup"><span data-stu-id="0acdb-290">**Group Name**</span></span>|<span data-ttu-id="0acdb-291">**群組類型**</span><span class="sxs-lookup"><span data-stu-id="0acdb-291">**Group Type**</span></span>|<span data-ttu-id="0acdb-292">**成員**</span><span class="sxs-lookup"><span data-stu-id="0acdb-292">**Members**</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0acdb-293">BizTalk 應用程式使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-293">BizTalk Application Users</span></span>|<span data-ttu-id="0acdb-294">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-294">Global or Universal</span></span>|<span data-ttu-id="0acdb-295">-BTServiceHost</span><span class="sxs-lookup"><span data-stu-id="0acdb-295">-   BTServiceHost</span></span><br /><span data-ttu-id="0acdb-296">-BTUserHostInstance</span><span class="sxs-lookup"><span data-stu-id="0acdb-296">-   BTUserHostInstance</span></span>|  
|<span data-ttu-id="0acdb-297">BizTalk 開發使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-297">BizTalk Development Users</span></span>|<span data-ttu-id="0acdb-298">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-298">Global or Universal</span></span>|<span data-ttu-id="0acdb-299">（開發使用者的本機網域帳戶）**附註：**最佳做法，請勿啟用 BizTalk 開發使用者群組在上線路環境中的。</span><span class="sxs-lookup"><span data-stu-id="0acdb-299">(local domain accounts of development users) **Note:**  As a best practice, do not enable the BizTalk Development Users group in up-line environments.</span></span>|  
|<span data-ttu-id="0acdb-300">BizTalk 部署使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-300">BizTalk Deployment Users</span></span>|<span data-ttu-id="0acdb-301">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-301">Global or Universal</span></span>|<span data-ttu-id="0acdb-302">(部署使用者的本機網域帳戶)</span><span class="sxs-lookup"><span data-stu-id="0acdb-302">(local domain accounts of deployment users)</span></span>|  
|<span data-ttu-id="0acdb-303">BizTalk 主控件使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-303">BizTalk Host Users</span></span>|<span data-ttu-id="0acdb-304">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-304">Global or Universal</span></span>|<span data-ttu-id="0acdb-305">BTUserHostInstance</span><span class="sxs-lookup"><span data-stu-id="0acdb-305">BTUserHostInstance</span></span>|  
|<span data-ttu-id="0acdb-306">BizTalk 外掛式主控件使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-306">BizTalk Isolated Host Users</span></span>|<span data-ttu-id="0acdb-307">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-307">Global or Universal</span></span>|<span data-ttu-id="0acdb-308">-BTServiceHostIso</span><span class="sxs-lookup"><span data-stu-id="0acdb-308">-   BTServiceHostIso</span></span><br /><span data-ttu-id="0acdb-309">-BTUserHostInstance</span><span class="sxs-lookup"><span data-stu-id="0acdb-309">-   BTUserHostInstance</span></span>|  
|<span data-ttu-id="0acdb-310">BizTalk Server 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-310">BizTalk Server Administrators</span></span>|<span data-ttu-id="0acdb-311">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-311">Global or Universal</span></span>|<span data-ttu-id="0acdb-312">-BTUserAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-312">-   BTUserAdmin</span></span><br /><span data-ttu-id="0acdb-313">-BTUserInstall</span><span class="sxs-lookup"><span data-stu-id="0acdb-313">-   BTUserInstall</span></span><br /><span data-ttu-id="0acdb-314">BizTalk 開發使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-314">-   BizTalk Development Users</span></span><br /><span data-ttu-id="0acdb-315">BizTalk 部署使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-315">-   BizTalk Deployment Users</span></span>|  
|<span data-ttu-id="0acdb-316">BizTalk 支援使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-316">BizTalk Support Users</span></span>|<span data-ttu-id="0acdb-317">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-317">Global or Universal</span></span>|<span data-ttu-id="0acdb-318">BTUserSupport (支援使用者的本機網域帳戶)</span><span class="sxs-lookup"><span data-stu-id="0acdb-318">BTUserSupport (local domain accounts of support users)</span></span>|  
|<span data-ttu-id="0acdb-319">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-319">SSO Administrators</span></span>|<span data-ttu-id="0acdb-320">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-320">Global or Universal</span></span>|<span data-ttu-id="0acdb-321">-SSOService</span><span class="sxs-lookup"><span data-stu-id="0acdb-321">-   SSOService</span></span><br /><span data-ttu-id="0acdb-322">-BTUserInstall</span><span class="sxs-lookup"><span data-stu-id="0acdb-322">-   BTUserInstall</span></span><br /><span data-ttu-id="0acdb-323">本機系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-323">-   Local Administrator</span></span>|  
|<span data-ttu-id="0acdb-324">SSO 分支機構系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-324">SSO Affiliate Administrators</span></span>|<span data-ttu-id="0acdb-325">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-325">Global or Universal</span></span>|<span data-ttu-id="0acdb-326">BizTalk 開發使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-326">-   BizTalk Development Users</span></span><br /><span data-ttu-id="0acdb-327">BizTalk 部署使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-327">-   BizTalk Deployment Users</span></span><br /><span data-ttu-id="0acdb-328">-BTServiceHostIso</span><span class="sxs-lookup"><span data-stu-id="0acdb-328">-   BTServiceHostIso</span></span><br /><span data-ttu-id="0acdb-329">-   \<主控台使用者 ></span><span class="sxs-lookup"><span data-stu-id="0acdb-329">-   \<console user></span></span>|  
|<span data-ttu-id="0acdb-330">Windows SharePoint Services 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-330">Windows SharePoint Services Administrators</span></span>|<span data-ttu-id="0acdb-331">全域或萬用</span><span class="sxs-lookup"><span data-stu-id="0acdb-331">Global or Universal</span></span>|<span data-ttu-id="0acdb-332">-SPAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-332">-   SPAdmin</span></span><br /><span data-ttu-id="0acdb-333">-BTUserInstall</span><span class="sxs-lookup"><span data-stu-id="0acdb-333">-   BTUserInstall</span></span><br /><span data-ttu-id="0acdb-334">-BTUserDeploy</span><span class="sxs-lookup"><span data-stu-id="0acdb-334">-   BTUserDeploy</span></span><br /><span data-ttu-id="0acdb-335">BizTalk 開發使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-335">-   BizTalk Development Users</span></span><br /><span data-ttu-id="0acdb-336">BizTalk 部署使用者</span><span class="sxs-lookup"><span data-stu-id="0acdb-336">-   BizTalk Deployment users</span></span>|  
  
 <span data-ttu-id="0acdb-337">關於網域群組的建議和注意事項：</span><span class="sxs-lookup"><span data-stu-id="0acdb-337">Recommendations and notes on domain groups:</span></span>  
  
-   <span data-ttu-id="0acdb-338">請在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前先建立群組和新增成員。</span><span class="sxs-lookup"><span data-stu-id="0acdb-338">Create the groups and add members prior to installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0acdb-339">網域群組可以是「全域」或「萬用」群組。</span><span class="sxs-lookup"><span data-stu-id="0acdb-339">Domain groups can be Global or Universal groups.</span></span>  
  
-   <span data-ttu-id="0acdb-340">使用 *\<DomainName >\\< 使用者名稱\>*當組態精靈中指定網域帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="0acdb-340">Use *\<DomainName>\\<UserName\>* when specifying domain account information in the Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="0acdb-341">群組與使用者/服務帳戶必須屬於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的所屬網域 ([組態精靈] 會檢查此項，而且不會顯示包含其他網域之帳戶的帳戶或群組)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-341">Groups and user/service accounts must belong to the domain in which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer belongs (the Configuration Wizard checks this and will not display accounts or groups containing accounts from other domains).</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0acdb-342"> 需要在所有叢集案例使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-342"> requires domain accounts for all clustering scenarios.</span></span>  
  
-   <span data-ttu-id="0acdb-343">在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，主控台使用者需要是下列群組的成員：</span><span class="sxs-lookup"><span data-stu-id="0acdb-343">When installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the console user needs to be a member of the following groups:</span></span>  
  
    -   <span data-ttu-id="0acdb-344">BizTalk Server 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-344">BizTalk Server Administrators</span></span>  
  
    -   <span data-ttu-id="0acdb-345">SSO 系統管理員 (僅限設定主要密碼伺服器時)</span><span class="sxs-lookup"><span data-stu-id="0acdb-345">SSO Administrators (only when configuring the master secret server)</span></span>  
  
    -   <span data-ttu-id="0acdb-346">Windows 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-346">Windows administrator</span></span>  
  
    -   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="0acdb-347"> 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-347"> administrator</span></span>  
  
    -   <span data-ttu-id="0acdb-348">OLAP 系統管理員</span><span class="sxs-lookup"><span data-stu-id="0acdb-348">OLAP administrator</span></span>  
  
     <span data-ttu-id="0acdb-349">在進行安裝和組態時都必須使用 BTUserInstall 帳戶，而且在組態完成後，便應該要停用組態。</span><span class="sxs-lookup"><span data-stu-id="0acdb-349">The BTUserInstall account should be used for installation and configuration and should be disabled after configuration is complete.</span></span>  
  
-   <span data-ttu-id="0acdb-350">若要讓訊息事件和服務執行個體追蹤以偵錯工具附加協調流程，開發人員必須屬於 BizTalk Server 系統管理員群組中，如上面所述的區段中**BizTalk 開發帳戶**.</span><span class="sxs-lookup"><span data-stu-id="0acdb-350">To allow message event and service instance tracking to attach orchestrations to the debugger, the developer needs to belong to the BizTalk Server Administrators group, as outlined above in the section **BizTalk Development Accounts**.</span></span>  
  
## <a name="local-administrator-accounts"></a><span data-ttu-id="0acdb-351">本機系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-351">Local Administrator Accounts</span></span>  
 <span data-ttu-id="0acdb-352">確認下列帳戶和群組的存在，或是將其新增到 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上的「本機系統管理員」群組：</span><span class="sxs-lookup"><span data-stu-id="0acdb-352">Confirm or add the following accounts and groups to the Local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer:</span></span>  
  
-   <span data-ttu-id="0acdb-353">Domain\BTUserInstall (在組態完成時停用)</span><span class="sxs-lookup"><span data-stu-id="0acdb-353">Domain\BTUserInstall (disable when configuration is complete)</span></span>  
  
-   <span data-ttu-id="0acdb-354">Domain\BTUserDeploy (當部署完成時便會在實際執行中停用)</span><span class="sxs-lookup"><span data-stu-id="0acdb-354">Domain\BTUserDeploy (disable in production when deployment is complete)</span></span>  
  
-   <span data-ttu-id="0acdb-355">Domain\SPAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-355">Domain\SPAdmin</span></span>  
  
-   <span data-ttu-id="0acdb-356">Domain\SQLAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-356">Domain\SQLAdmin</span></span>  
  
-   <span data-ttu-id="0acdb-357">Domain\SQLService</span><span class="sxs-lookup"><span data-stu-id="0acdb-357">Domain\SQLService</span></span>  
  
-   <span data-ttu-id="0acdb-358">Domain\BizTalk Development Users （在上線路環境省略）</span><span class="sxs-lookup"><span data-stu-id="0acdb-358">Domain\BizTalk Development Users (omit in up line environments)</span></span>  
  
-   <span data-ttu-id="0acdb-359">Domain\BizTalk Deployment Users (在開發環境中省略)</span><span class="sxs-lookup"><span data-stu-id="0acdb-359">Domain\BizTalk Deployment Users (omit in development environments)</span></span>  
  
 <span data-ttu-id="0acdb-360">確認下列帳戶和群組的存在，或是將其新增到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的「本機系統管理員」群組：</span><span class="sxs-lookup"><span data-stu-id="0acdb-360">Confirm or add the following accounts and groups to the Local Administrators group on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer:</span></span>  
  
-   <span data-ttu-id="0acdb-361">Domain\BTUserInstall (在組態完成時停用)</span><span class="sxs-lookup"><span data-stu-id="0acdb-361">Domain\BTUserInstall (disable when configuration is complete)</span></span>  
  
-   <span data-ttu-id="0acdb-362">Domain\BTUserDeploy (當部署完成時便會在實際執行中停用)</span><span class="sxs-lookup"><span data-stu-id="0acdb-362">Domain\BTUserDeploy (disable in production when deployment is complete)</span></span>  
  
-   <span data-ttu-id="0acdb-363">Domain\BTUserSupport</span><span class="sxs-lookup"><span data-stu-id="0acdb-363">Domain\BTUserSupport</span></span>  
  
-   <span data-ttu-id="0acdb-364">Domain\SPAdmin</span><span class="sxs-lookup"><span data-stu-id="0acdb-364">Domain\SPAdmin</span></span>  
  
-   <span data-ttu-id="0acdb-365">Domain\BizTalk Development Users (在上線路環境中省略)</span><span class="sxs-lookup"><span data-stu-id="0acdb-365">Domain\BizTalk Development Users (omit in upline environments)</span></span>  
  
-   <span data-ttu-id="0acdb-366">Domain\BizTalk Deployment Users (在開發環境中省略)</span><span class="sxs-lookup"><span data-stu-id="0acdb-366">Domain\BizTalk Deployment Users (omit in development environments)</span></span>  
  
## <a name="sql-server-administrator-accounts"></a><span data-ttu-id="0acdb-367">SQL Server 系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-367">SQL Server Administrator Accounts</span></span>  
 <span data-ttu-id="0acdb-368">安裝程式 (Setup Program) 會接受安裝程式 (Installer) 的輸入，並將 SQL 角色指派給使用者及群組：</span><span class="sxs-lookup"><span data-stu-id="0acdb-368">Setup programs accept input from the installer and assigns SQL roles to users and groups:</span></span>  
  
-   <span data-ttu-id="0acdb-369">在進行 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 安裝期間，會對 SPAdmin 帳戶授與 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上「安全性系統管理員」和「資料庫建立者」的權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-369">During [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] setup, the SPAdmin account is granted Security Administrator and Database Creator rights on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span> <span data-ttu-id="0acdb-370">如果 SPAdmin 帳戶是「本機系統管理員」群組的成員，便可移除這些權限。</span><span class="sxs-lookup"><span data-stu-id="0acdb-370">These rights can be removed if the SPAdmin account is a member of the Local Administrators group.</span></span>  
  
## <a name="e-mail-account"></a><span data-ttu-id="0acdb-371">電子郵件帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-371">E-Mail Account</span></span>  
 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]<span data-ttu-id="0acdb-372">傳送郵件，根據特定系統事件。</span><span class="sxs-lookup"><span data-stu-id="0acdb-372"> will send mail based on certain system events.</span></span> <span data-ttu-id="0acdb-373">在進行組態程序時，安裝程式會提示您輸入電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0acdb-373">Setup prompts for an e-mail address during the configuration process.</span></span> <span data-ttu-id="0acdb-374">針對此用途建立電子郵件別名，並在安裝和單元測試期間監視的別名。</span><span class="sxs-lookup"><span data-stu-id="0acdb-374">Create e-mail aliases for this purpose and monitor the alias during setup and unit testing.</span></span> <span data-ttu-id="0acdb-375">在實際執行環境中，這個帳戶應該都能由監視系統的系統管理員所存取。</span><span class="sxs-lookup"><span data-stu-id="0acdb-375">In the production environment, this account should be accessible by a system administrator who is monitoring the system.</span></span>  
  
 <span data-ttu-id="0acdb-376">所使用的電子郵件帳戶[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]是**WSS 系統管理員電子郵件**帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-376">The e-mail account used by [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] is the **WSS Administrator E-mail** account.</span></span>  
  
## <a name="password-considerations-for-development"></a><span data-ttu-id="0acdb-377">開發的密碼考量</span><span class="sxs-lookup"><span data-stu-id="0acdb-377">Password Considerations for Development</span></span>  
 <span data-ttu-id="0acdb-378">在開發和測試環境中，都可以用一套標準設定帳戶密碼並加以散發。</span><span class="sxs-lookup"><span data-stu-id="0acdb-378">For development and test environments, account passwords can be set by a standard and be distributable.</span></span> <span data-ttu-id="0acdb-379">安裝程式的標準都不一樣，因此本主題使用首字大寫的字母縮寫服務元件，後面接著小寫的字母縮寫帳戶其餘部分 (服務或使用者) 的範本。</span><span class="sxs-lookup"><span data-stu-id="0acdb-379">Installer standards vary; this topic uses the template of initial capital letters abbreviating the service component followed by a lower-case abbreviation for the rest of the account (service or user).</span></span> <span data-ttu-id="0acdb-380">對於服務帳戶，本主題使用 'Serv'；對於使用者帳戶則使用 'User'。</span><span class="sxs-lookup"><span data-stu-id="0acdb-380">For service accounts, this topic uses 'Serv', for user accounts this topic uses 'User'.</span></span>  
  
 <span data-ttu-id="0acdb-381">例如：</span><span class="sxs-lookup"><span data-stu-id="0acdb-381">For example:</span></span>  
  
-   <span data-ttu-id="0acdb-382">Windows SharePoint Services (SharePoint) 服務和系統管理員帳戶 (SPAdmin) 密碼: 'SPServ'。</span><span class="sxs-lookup"><span data-stu-id="0acdb-382">Windows SharePoint Services (SharePoint) Service and admin account (SPAdmin) passwords: 'SPServ'.</span></span>  
  
-   <span data-ttu-id="0acdb-383">BizTalk 服務帳戶密碼: 'BTServ'。</span><span class="sxs-lookup"><span data-stu-id="0acdb-383">BizTalk Service account passwords: 'BTServ'.</span></span>  
  
-   <span data-ttu-id="0acdb-384">BizTalk 使用者帳戶密碼: 'BTUser'。</span><span class="sxs-lookup"><span data-stu-id="0acdb-384">BizTalk User account passwords: 'BTUser'.</span></span>  
  
 <span data-ttu-id="0acdb-385">某些 IT 環境需要密碼包含非字母和 (或) 數字字元。</span><span class="sxs-lookup"><span data-stu-id="0acdb-385">Some IT environments require passwords to contain non-alpha and/or numeric characters.</span></span> <span data-ttu-id="0acdb-386">在此案例中，您可以用錢幣符號 ($) 取代 "s"，並用 At 符號 (@) 取代 "a"。</span><span class="sxs-lookup"><span data-stu-id="0acdb-386">In this scenario you could substitute a dollar sign ($) for "s", and an 'at' sign (@) for "a".</span></span> <span data-ttu-id="0acdb-387">這些符號只是範例，請發展最能配合自己的模式，以便使用半公開的密碼共用帳戶。</span><span class="sxs-lookup"><span data-stu-id="0acdb-387">The symbols are samples; develop a pattern that works best for you for shared accounts with semi-public passwords.</span></span>  
  
 <span data-ttu-id="0acdb-388">在開發環境中使用的可轉散發密碼範例為：</span><span class="sxs-lookup"><span data-stu-id="0acdb-388">Sample redistributable passwords in use in the development environment are:</span></span>  
  
-   <span data-ttu-id="0acdb-389">BT$erv99           BizTalk 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-389">BT$erv99           BizTalk Service Accounts</span></span>  
  
-   <span data-ttu-id="0acdb-390">BTU$er99          BizTalk 使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-390">BTU$er99          BizTalk User Accounts</span></span>  
  
-   <span data-ttu-id="0acdb-391">SP$erv99           WSS 服務帳戶 (SPAdmin)</span><span class="sxs-lookup"><span data-stu-id="0acdb-391">SP$erv99           WSS Service Account (SPAdmin)</span></span>  
  
-   <span data-ttu-id="0acdb-392">SQL$erv99         SQL 服務/存取/管理帳戶</span><span class="sxs-lookup"><span data-stu-id="0acdb-392">SQL$erv99         SQL Service/Access/Admin Account</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-393">這些建議僅適用於開發和共用的環境，而且既不建議也不反對使用企業密碼原則。</span><span class="sxs-lookup"><span data-stu-id="0acdb-393">These recommendations are for development and shared environments only and do not recommend or discourage the use of corporate password policies.</span></span> <span data-ttu-id="0acdb-394">如需瞭解密碼需求，請洽詢您的網路管理員。</span><span class="sxs-lookup"><span data-stu-id="0acdb-394">See your network administrator for password requirements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acdb-395">如果企業密碼原則包括產生的密碼，請注意一些符號和符號組合在 XML 是具有特殊用途的字元。</span><span class="sxs-lookup"><span data-stu-id="0acdb-395">If corporate password policy includes generated passwords, be advised that some symbols and symbol combinations are special-use characters to XML.</span></span> <span data-ttu-id="0acdb-396">不適當地使用這些字元，將會使組態 XML 檔無法在進行組態程序時開啟。</span><span class="sxs-lookup"><span data-stu-id="0acdb-396">Inappropriate use of these characters will prevent configuration XML files from being opened during the configuration process.</span></span> <span data-ttu-id="0acdb-397">這些符號包括"&"、"\<"，">"、 單一-和雙引號，並且可能包括其他。</span><span class="sxs-lookup"><span data-stu-id="0acdb-397">These symbols include "&", "\<", ">", single- and double-quote, and may include others.</span></span> <span data-ttu-id="0acdb-398">請在執行以檔案為基礎的組態之前，先行測試組態 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0acdb-398">Test the configuration XML file prior to executing file-based configuration.</span></span> <span data-ttu-id="0acdb-399">您只要在 Internet Explorer (或 XML 編輯器) 中開啟其中內嵌產生之密碼的文件，便能可靠地測試適當的 XML 格式設定。</span><span class="sxs-lookup"><span data-stu-id="0acdb-399">You can test this reliably for proper XML formatting by opening the document in Internet Explorer (or an XML editor) with the generated passwords embedded therein.</span></span>  
  
 <span data-ttu-id="0acdb-400">如需有關部署安全密碼在上線路環境中 (包括要測試的方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態檔)，請參閱[BizTalk Server 2013 和 2013 R2 的組態概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。</span><span class="sxs-lookup"><span data-stu-id="0acdb-400">For more information about deployment of secure passwords in up-line environments (including the method to test a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration file), see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acdb-401">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acdb-401">See Also</span></span>  
 [<span data-ttu-id="0acdb-402">疑難排解 BizTalk Server 權限</span><span class="sxs-lookup"><span data-stu-id="0acdb-402">Troubleshooting BizTalk Server Permissions</span></span>](../core/troubleshooting-biztalk-server-permissions.md)