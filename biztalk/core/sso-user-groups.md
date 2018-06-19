---
title: SSO 使用者群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- groups, SSO
- user accounts, administrators
- service accounts, SSO
- SSO, user groups
- SSO, service accounts
- SSO, administrator accounts
ms.assetid: e279001e-c724-4a2d-8939-0ba9dd08a19c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 949f3aa72771982321abf6904c43352b8821fc0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277622"
---
# <a name="sso-user-groups"></a><span data-ttu-id="a483c-102">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="a483c-102">SSO User Groups</span></span>
<span data-ttu-id="a483c-103">若要設定及管理「企業單一登入」(SSO) 系統，您必須為其中每個角色建立 Windows 群組與帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-103">To configure and manage the Enterprise Single Sign-On (SSO) system, you must create certain Windows groups and accounts for each of these roles.</span></span> <span data-ttu-id="a483c-104">設定企業 SSO 中的存取帳戶時，您可以為其中每個角色指定多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-104">When configuring the access accounts in Enterprise SSO, you can specify more than one account for each of these roles.</span></span> <span data-ttu-id="a483c-105">本節描述這些角色。</span><span class="sxs-lookup"><span data-stu-id="a483c-105">This section describes these roles.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a483c-106">強烈建議您在設定 SSO 時使用網域群組。</span><span class="sxs-lookup"><span data-stu-id="a483c-106">It is strongly recommended that you use domain groups when configuring SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a483c-107">基於安全起見，SSO 系統不允許使用內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-107">For security purposes, the SSO system does not allow built-in accounts.</span></span>  
  
## <a name="single-sign-on-administrators"></a><span data-ttu-id="a483c-108">單一登入系統管理員</span><span class="sxs-lookup"><span data-stu-id="a483c-108">Single Sign-On Administrators</span></span>  
 <span data-ttu-id="a483c-109">SSO 系統管理員擁有 SSO 系統中最高層級的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="a483c-109">SSO administrators have the highest level user rights in the SSO system.</span></span> <span data-ttu-id="a483c-110">他們可以：</span><span class="sxs-lookup"><span data-stu-id="a483c-110">They can:</span></span>  
  
-   <span data-ttu-id="a483c-111">建立及管理 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="a483c-111">Create and manage the SSO database</span></span>  
  
-   <span data-ttu-id="a483c-112">建立及管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="a483c-112">Create and manage the master secret</span></span>  
  
-   <span data-ttu-id="a483c-113">啟用及停用 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="a483c-113">Enable and disable the SSO system</span></span>  
  
-   <span data-ttu-id="a483c-114">建立密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="a483c-114">Create password synchronization adapters</span></span>  
  
-   <span data-ttu-id="a483c-115">啟用及停用 SSO 系統中的密碼同步</span><span class="sxs-lookup"><span data-stu-id="a483c-115">Enable and disable password synchronization in the SSO system</span></span>  
  
-   <span data-ttu-id="a483c-116">啟用及停用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="a483c-116">Enable and disable host initiated SSO</span></span>  
  
-   <span data-ttu-id="a483c-117">執行所有管理工作</span><span class="sxs-lookup"><span data-stu-id="a483c-117">Perform all administration tasks</span></span>  
  
 <span data-ttu-id="a483c-118">SSO 系統管理員帳戶可以是 Windows 群組或個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-118">The SSO administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="a483c-119">SSO 系統管理員帳戶也可以是網域或本機群組，或是個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-119">The SSO administrators account can also be either a domain or local group or individual account.</span></span> <span data-ttu-id="a483c-120">若使用個人帳戶，您無法將此帳戶改為另一個個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-120">When using an individual account, you cannot change this account to another individual account.</span></span> <span data-ttu-id="a483c-121">因此，建議您不要使用個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-121">Therefore, it is recommended that you do not use an individual account.</span></span> <span data-ttu-id="a483c-122">只要原始帳戶是新帳戶的成員，您就可以將此帳戶改為群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-122">You can change this account to a group account as long as the original account is a member of the new account.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a483c-123">執行「企業單一登入」服務的服務帳戶需為此帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="a483c-123">The service account running the Enterprise Single Sign-On service must be a member of this account.</span></span> <span data-ttu-id="a483c-124">為保護環境的安全，請確定沒有其他服務正在使用同一個服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-124">To secure your environment, ensure that no other service is using the same service account.</span></span>  
  
## <a name="single-sign-on-affiliate-administrators"></a><span data-ttu-id="a483c-125">單一登入分支機構管理員</span><span class="sxs-lookup"><span data-stu-id="a483c-125">Single Sign-On Affiliate Administrators</span></span>  
 <span data-ttu-id="a483c-126">SSO 分支機構系統管理員定義 SSO 系統所包含的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="a483c-126">The SSO affiliate administrator defines the affiliate applications that the SSO system contains.</span></span> <span data-ttu-id="a483c-127">分支機構應用程式是一種邏輯實體，其代表您使用 SSO 連線的後端系統。</span><span class="sxs-lookup"><span data-stu-id="a483c-127">Affiliate applications are a logical entity that represents the back-end system to which you are connecting using SSO.</span></span> <span data-ttu-id="a483c-128">SSO 分支機構系統管理員可以：</span><span class="sxs-lookup"><span data-stu-id="a483c-128">SSO affiliate administrators can:</span></span>  
  
-   <span data-ttu-id="a483c-129">建立、管理及刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="a483c-129">Create, manage, and delete affiliate applications</span></span>  
  
-   <span data-ttu-id="a483c-130">指定每個分支機構應用程式的應用程式系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="a483c-130">Specify the application administrators account for each affiliate application</span></span>  
  
-   <span data-ttu-id="a483c-131">執行應用程式系統管理員與應用程式使用者可執行的所有管理工作</span><span class="sxs-lookup"><span data-stu-id="a483c-131">Perform all the administration tasks that the application administrators and application users can</span></span>  
  
 <span data-ttu-id="a483c-132">SSO 分支機構應用程式帳戶可以是 Windows 群組或個人帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-132">The SSO Affiliate Administrator account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="a483c-133">SSO 分支機構系統管理員帳戶也可以是網域或本機群組或帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-133">The SSO Affiliate Administrator account can also be either a domain or local group or account.</span></span>  
  
## <a name="application-administrators"></a><span data-ttu-id="a483c-134">應用程式系統管理員</span><span class="sxs-lookup"><span data-stu-id="a483c-134">Application Administrators</span></span>  
 <span data-ttu-id="a483c-135">每個分支機構應用程式都有一個應用程式系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="a483c-135">There is one application administrators group per affiliate application.</span></span>  
  
 <span data-ttu-id="a483c-136">此群組的成員可以：</span><span class="sxs-lookup"><span data-stu-id="a483c-136">Members of this group can:</span></span>  
  
-   <span data-ttu-id="a483c-137">變更應用程式使用者群組帳戶</span><span class="sxs-lookup"><span data-stu-id="a483c-137">Change the application users group account</span></span>  
  
-   <span data-ttu-id="a483c-138">建立、刪除及管理特定分支機構應用程式所有使用者的認證對應</span><span class="sxs-lookup"><span data-stu-id="a483c-138">Create, delete, and manage credential mappings for all users of the specific affiliate application</span></span>  
  
-   <span data-ttu-id="a483c-139">為特定分支機構應用程式使用者群組帳戶中的任何使用者設定認證</span><span class="sxs-lookup"><span data-stu-id="a483c-139">Set credentials for any user in that specific affiliate application users group account</span></span>  
  
-   <span data-ttu-id="a483c-140">執行應用程式使用者可執行的所有管理工作</span><span class="sxs-lookup"><span data-stu-id="a483c-140">Perform all the administration tasks that the application users can</span></span>  
  
## <a name="application-users"></a><span data-ttu-id="a483c-141">應用程式使用者</span><span class="sxs-lookup"><span data-stu-id="a483c-141">Application Users</span></span>  
 <span data-ttu-id="a483c-142">每個分支機構應用程式都有一個應用程式使用者群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="a483c-142">There is one application users group account for each affiliate application.</span></span> <span data-ttu-id="a483c-143">此帳戶包含「企業單一登入」環境中一般使用者的清單。</span><span class="sxs-lookup"><span data-stu-id="a483c-143">This account contains the list of end users in an Enterprise Single Sign-On environment.</span></span> <span data-ttu-id="a483c-144">此帳戶的成員可以：</span><span class="sxs-lookup"><span data-stu-id="a483c-144">Members of this account can:</span></span>  
  
-   <span data-ttu-id="a483c-145">在分支機構應用程式中尋查自己的認證</span><span class="sxs-lookup"><span data-stu-id="a483c-145">Look up their credentials in the affiliate application</span></span>  
  
-   <span data-ttu-id="a483c-146">在分支機構應用程式中管理自己的認證對應</span><span class="sxs-lookup"><span data-stu-id="a483c-146">Manage their credential mappings in the affiliate application</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a483c-147">指派群組時記得保持警戒。</span><span class="sxs-lookup"><span data-stu-id="a483c-147">Remember to be vigilant when assigning groups.</span></span> <span data-ttu-id="a483c-148">例如，可以在 SSO 應用程式使用者群組中使用 BizTalk Server 安全性使用者群組。</span><span class="sxs-lookup"><span data-stu-id="a483c-148">It is possible, for example, to use a BizTalk Server security user group for the SSO application users group.</span></span> <span data-ttu-id="a483c-149">在這麼做之前，請確定是否所有使用者都需要他們即將可用的所有存取權。</span><span class="sxs-lookup"><span data-stu-id="a483c-149">Before you do this, be certain that all users need all access that will then be available to them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a483c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a483c-150">See Also</span></span>  
 <span data-ttu-id="a483c-151">[如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="a483c-151">[How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="a483c-152">[如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="a483c-152">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 <span data-ttu-id="a483c-153">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="a483c-153">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="a483c-154">瞭解 SSO</span><span class="sxs-lookup"><span data-stu-id="a483c-154">Understanding SSO</span></span>](../core/understanding-sso.md)