---
title: "單一登入： 事件 10550 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9772885746f2c0519cba84db9ad1bee612607117
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10550"></a><span data-ttu-id="c4941-102">單一登入： 事件 10550</span><span class="sxs-lookup"><span data-stu-id="c4941-102">Single Sign-On: Event 10550</span></span>
## <a name="details"></a><span data-ttu-id="c4941-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4941-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4941-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c4941-104">Product Name</span></span>|<span data-ttu-id="c4941-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c4941-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c4941-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c4941-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c4941-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c4941-107">Event ID</span></span>|<span data-ttu-id="c4941-108">10550</span><span class="sxs-lookup"><span data-stu-id="c4941-108">10550</span></span>|  
|<span data-ttu-id="c4941-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c4941-109">Event Source</span></span>|<span data-ttu-id="c4941-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c4941-110">ENTSSO</span></span>|  
|<span data-ttu-id="c4941-111">元件</span><span class="sxs-lookup"><span data-stu-id="c4941-111">Component</span></span>|<span data-ttu-id="c4941-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c4941-112">N/A</span></span>|  
|<span data-ttu-id="c4941-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c4941-113">Symbolic Name</span></span>|<span data-ttu-id="c4941-114">SSO_ERROR_SERVICE_NOT_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="c4941-114">SSO_ERROR_SERVICE_NOT_SSO_ADMIN</span></span>|  
|<span data-ttu-id="c4941-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c4941-115">Message Text</span></span>|<span data-ttu-id="c4941-116">SSO 服務無法啟動，因為它執行的服務帳戶不是 SSO 系統管理員 account.%r 的成員</span><span class="sxs-lookup"><span data-stu-id="c4941-116">The SSO service could not start because the service account it is running under is not a member of the SSO Administrators account.%r</span></span><br /><br /> <span data-ttu-id="c4941-117">SSO 系統管理員: %1 %r</span><span class="sxs-lookup"><span data-stu-id="c4941-117">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="c4941-118">SSO 服務帳戶： %2</span><span class="sxs-lookup"><span data-stu-id="c4941-118">SSO Service Account: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c4941-119">說明</span><span class="sxs-lookup"><span data-stu-id="c4941-119">Explanation</span></span>  
 <span data-ttu-id="c4941-120">SSO 服務必須是 SSO 系統管理員帳戶的成員的服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c4941-120">The SSO service must be running under a service account that is a member of the SSO Administrators account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c4941-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c4941-121">User Action</span></span>  
 <span data-ttu-id="c4941-122">如需詳細資訊，請參閱[如何指定 SSO 系統管理員和分支機構系統管理員帳戶](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)。</span><span class="sxs-lookup"><span data-stu-id="c4941-122">For more information, see [How to Specify SSO Administrators and Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md).</span></span>