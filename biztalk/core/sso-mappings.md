---
title: SSO 對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO]
- maps [SSO], creating
- SSO, maps
ms.assetid: b44f7a0c-595c-49dc-9d75-2e76f29dca88
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98b44a1a9e8be3b275a4dd328c70323d79eb8a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277238"
---
# <a name="sso-mappings"></a><span data-ttu-id="b8f92-102">SSO 對應</span><span class="sxs-lookup"><span data-stu-id="b8f92-102">SSO Mappings</span></span>
<span data-ttu-id="b8f92-103">當「企業單一登入」(SSO) 系統管理員或 SSO 分支機構系統管理員定義分支機構應用程式時，系統管理員可以將它定義為具有個別對應的應用程式，或具有群組對應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8f92-103">When an Enterprise Single Sign-On (SSO) administrator or an SSO affiliate administrator defines an affiliate application, the administrator can define it either as an application with individual mappings, or as an application with a group mapping.</span></span>  
  
## <a name="individual-mappings"></a><span data-ttu-id="b8f92-104">個別對應</span><span class="sxs-lookup"><span data-stu-id="b8f92-104">Individual Mappings</span></span>  
 <span data-ttu-id="b8f92-105">SSO 個別對應可以讓系統管理員和使用者在 Windows 使用者與其對應的非 Windows 認證之間建立一對一的對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-105">SSO individual mappings enable administrators and users to create a one-to-one mapping between Windows users and their corresponding non-Windows credentials.</span></span> <span data-ttu-id="b8f92-106">使用個別對應時，使用者可以管理自己的對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-106">When using individual mappings, users can manage their own mappings.</span></span> <span data-ttu-id="b8f92-107">SSO 系統為使用者的 Windows 帳戶與使用者的非 Windows 帳戶維護一對一的關係。</span><span class="sxs-lookup"><span data-stu-id="b8f92-107">The SSO system maintains the one-to-one relation for the user's Windows account and the user's non-Windows account.</span></span>  
  
 <span data-ttu-id="b8f92-108">Windows 一般使用者可以為個別類型應用程式建立與管理他們自己的對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-108">Windows End-users can create and manage their own mappings for individual type applications.</span></span> <span data-ttu-id="b8f92-109">相同的分支機構應用程式可以當做 Windows 初始化的 SSO 與主控件初始化的 SSO 類型應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8f92-109">The same affiliate application can act as a Windows Initiated SSO and a Host Initiated SSO type application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8f92-110">只能為 Windows 網域帳戶建立對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-110">Mappings can be created only for Windows domain accounts.</span></span> <span data-ttu-id="b8f92-111">無法對應本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="b8f92-111">Local accounts cannot be mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8f92-112">只有個別使用者可以在使用個別對應時取得其個別帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="b8f92-112">Only individual users can obtain the credentials to their individual accounts when using individual mappings.</span></span>  
  
## <a name="group-mapping"></a><span data-ttu-id="b8f92-113">群組對應</span><span class="sxs-lookup"><span data-stu-id="b8f92-113">Group Mapping</span></span>  
 <span data-ttu-id="b8f92-114">SSO 群組對應是由 Windows 群組 (包含多個 Windows 使用者) 對應到分支機構應用程式中的單一帳戶所組成。</span><span class="sxs-lookup"><span data-stu-id="b8f92-114">SSO group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.</span></span>  
  
 <span data-ttu-id="b8f92-115">您也可以為「SSO 應用程式使用者」角色指定多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="b8f92-115">You can also specify multiple accounts for the SSO Application Users role.</span></span> <span data-ttu-id="b8f92-116">您指定的每個帳戶都可以與一個外部帳戶關聯。</span><span class="sxs-lookup"><span data-stu-id="b8f92-116">Each account you specify can be associated with an external account.</span></span> <span data-ttu-id="b8f92-117">例如，您可以將網域群組對應到 EXTERNALUSER1，並將個別網域帳戶對應到 EXTERNALUSER2。</span><span class="sxs-lookup"><span data-stu-id="b8f92-117">For example, you can map a domain group account to EXTERNALUSER1 and an individual domain account to EXTERNALUSER2.</span></span> <span data-ttu-id="b8f92-118">若相同使用者有多個對應，會使用「SSO 應用程式使用者」順序中的第一個對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-118">If the same user has more than one mapping, the first mapping in the order of SSO Application Users is used.</span></span>  
  
 <span data-ttu-id="b8f92-119">只有應用程式系統管理員、SSO 分支機構系統管理員或 SSO 系統管理員可以建立或管理群組對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-119">Only an application administrator, SSO affiliate administrator, or SSO administrator can create or manage a group mapping.</span></span>  
  
 <span data-ttu-id="b8f92-120">您無法為 Windows 初始化的 SSO 與主控件初始化的 SSO 指定相同的群組應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8f92-120">You cannot specify the same group application for Windows initiated SSO and Host Initiated SSO.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8f92-121">只能為 Windows 網域帳戶建立對應。</span><span class="sxs-lookup"><span data-stu-id="b8f92-121">Mappings can be created only for Windows domain accounts.</span></span> <span data-ttu-id="b8f92-122">無法對應本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="b8f92-122">Local accounts cannot be mapped.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8f92-123">當您使用群組對應時，群組的成員可以取得群組對應的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="b8f92-123">When you use group mappings, the members of the group can obtain the credential information for the group mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f92-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8f92-124">See Also</span></span>  
 <span data-ttu-id="b8f92-125">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="b8f92-125">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="b8f92-126">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b8f92-126">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)