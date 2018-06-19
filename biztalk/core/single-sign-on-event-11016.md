---
title: 單一登入： 事件 11016 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3963b706-168d-438d-a068-637f8a6b7b0c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f84bfef5dcef8e28bb3616ce30f1addc77f240c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276526"
---
# <a name="single-sign-on-event-11016"></a><span data-ttu-id="a878d-102">單一登入： 事件 11016</span><span class="sxs-lookup"><span data-stu-id="a878d-102">Single Sign-On: Event 11016</span></span>
## <a name="details"></a><span data-ttu-id="a878d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a878d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a878d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a878d-104">Product Name</span></span>|<span data-ttu-id="a878d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a878d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a878d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a878d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a878d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a878d-107">Event ID</span></span>|<span data-ttu-id="a878d-108">11016</span><span class="sxs-lookup"><span data-stu-id="a878d-108">11016</span></span>|  
|<span data-ttu-id="a878d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a878d-109">Event Source</span></span>|<span data-ttu-id="a878d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a878d-110">ENTSSO</span></span>|  
|<span data-ttu-id="a878d-111">元件</span><span class="sxs-lookup"><span data-stu-id="a878d-111">Component</span></span>|<span data-ttu-id="a878d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a878d-112">N/A</span></span>|  
|<span data-ttu-id="a878d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a878d-113">Symbolic Name</span></span>|<span data-ttu-id="a878d-114">RPC 擴充錯誤資訊 %r</span><span class="sxs-lookup"><span data-stu-id="a878d-114">RPC EXTENDED ERROR INFORMATION%r</span></span>|  
|<span data-ttu-id="a878d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a878d-115">Message Text</span></span>|<span data-ttu-id="a878d-116">%1 %r</span><span class="sxs-lookup"><span data-stu-id="a878d-116">%1%r</span></span><br /><br /> <span data-ttu-id="a878d-117">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="a878d-117">Error Code: %2</span></span><br /><br /> <span data-ttu-id="a878d-118">AuthzInitializeContextFromSid 函式失敗，ERROR_ACCESS_DENIED。</span><span class="sxs-lookup"><span data-stu-id="a878d-118">The AuthzInitializeContextFromSid function failed with ERROR_ACCESS_DENIED.</span></span> <span data-ttu-id="a878d-119">這表示執行 SSO server 的服務帳戶沒有足夠的權限可檢查 Active Directory 中的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="a878d-119">This means that the service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory.</span></span> <span data-ttu-id="a878d-120">請檢查您的文件，如需如何修正此 problem.%r 詳細資料</span><span class="sxs-lookup"><span data-stu-id="a878d-120">Please check your documentation for details on how to fix this problem.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a878d-121">說明</span><span class="sxs-lookup"><span data-stu-id="a878d-121">Explanation</span></span>  
 <span data-ttu-id="a878d-122">SSO 伺服器下執行的服務帳戶沒有足夠的權限可檢查 Active Directory 中的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="a878d-122">The service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a878d-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a878d-123">User Action</span></span>  
 <span data-ttu-id="a878d-124">請參閱[SSO 伺服器](../core/sso-server.md)SSO 文件中。</span><span class="sxs-lookup"><span data-stu-id="a878d-124">See [SSO Server](../core/sso-server.md) in the SSO documentation.</span></span>