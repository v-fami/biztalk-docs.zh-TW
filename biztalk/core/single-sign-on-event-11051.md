---
title: 單一登入： 事件 11051 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe767818-f74e-415c-9287-5b7cc46e358a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26a58ee5a4fd842dd292179cea0f7461a5ab0517
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277566"
---
# <a name="single-sign-on-event-11051"></a><span data-ttu-id="92669-102">單一登入： 事件 11051</span><span class="sxs-lookup"><span data-stu-id="92669-102">Single Sign-On: Event 11051</span></span>
## <a name="details"></a><span data-ttu-id="92669-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="92669-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92669-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="92669-104">Product Name</span></span>|<span data-ttu-id="92669-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="92669-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="92669-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="92669-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="92669-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="92669-107">Event ID</span></span>|<span data-ttu-id="92669-108">11051</span><span class="sxs-lookup"><span data-stu-id="92669-108">11051</span></span>|  
|<span data-ttu-id="92669-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="92669-109">Event Source</span></span>|<span data-ttu-id="92669-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="92669-110">ENTSSO</span></span>|  
|<span data-ttu-id="92669-111">元件</span><span class="sxs-lookup"><span data-stu-id="92669-111">Component</span></span>|<span data-ttu-id="92669-112">不適用</span><span class="sxs-lookup"><span data-stu-id="92669-112">N/A</span></span>|  
|<span data-ttu-id="92669-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="92669-113">Symbolic Name</span></span>|<span data-ttu-id="92669-114">SSO_WARN_SSO_ADMIN_NOT_GROUP</span><span class="sxs-lookup"><span data-stu-id="92669-114">SSO_WARN_SSO_ADMIN_NOT_GROUP</span></span>|  
|<span data-ttu-id="92669-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="92669-115">Message Text</span></span>|<span data-ttu-id="92669-116">SSO 系統管理員帳戶包含一或多個個別 （非群組） 帳戶。</span><span class="sxs-lookup"><span data-stu-id="92669-116">The SSO Administrators account contains one or more individual (not group) accounts.</span></span> <span data-ttu-id="92669-117">如果從 Active Directory 或本機電腦中刪除這些個別帳戶立即將它們必須移除從 SSO 系統，或可能會成為安全性的 risk.%r</span><span class="sxs-lookup"><span data-stu-id="92669-117">If these individual accounts are deleted from Active Directory or the local computer they must be promptly removed from the SSO system or they could become a security risk.%r</span></span><br /><br /> <span data-ttu-id="92669-118">SSO 系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="92669-118">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="92669-119">個別帳戶： %2</span><span class="sxs-lookup"><span data-stu-id="92669-119">Individual accounts: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92669-120">說明</span><span class="sxs-lookup"><span data-stu-id="92669-120">Explanation</span></span>  
 <span data-ttu-id="92669-121">從 Active Directory 或本機電腦中刪除個別的帳戶不會自動刪除該帳戶從 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="92669-121">Deleting an individual account from the Active Directory or local computer does not automatically delete that account from the SSO System.</span></span> <span data-ttu-id="92669-122">這表示，如果 USER1 已在本機刪除的帳戶，然後以不同的使用者 （例如，新的員工） 已加入系統使用該相同的名稱，SSO 系統會將授與新 USER1 所有原始 USER1 所擁有的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="92669-122">This means that if the account USER1 was deleted locally, and then a different user (for instance, a new employee) joined the system using that same name, the SSO System would grant the new USER1 all security rights possessed by the original USER1.</span></span> <span data-ttu-id="92669-123">這會造成安全性風險。</span><span class="sxs-lookup"><span data-stu-id="92669-123">This poses a security risk.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92669-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="92669-124">User Action</span></span>  
 <span data-ttu-id="92669-125">從 Active Directory 或本機電腦刪除個別的帳戶之前，不不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="92669-125">No action is necessary until an individual account is deleted from Active Directory or the local computer.</span></span> <span data-ttu-id="92669-126">此時，您必須刪除 [個別] 帳戶從 SSO 系統儘速。</span><span class="sxs-lookup"><span data-stu-id="92669-126">At that point, you must delete the individual account from the SSO System as soon as possible.</span></span>