---
title: "單一登入： 事件 11031 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aec5ae3a128da8a13379c574ddd2dba3c1065f79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11031"></a><span data-ttu-id="46af1-102">單一登入： 事件 11031</span><span class="sxs-lookup"><span data-stu-id="46af1-102">Single Sign-On: Event 11031</span></span>
## <a name="details"></a><span data-ttu-id="46af1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46af1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46af1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="46af1-104">Product Name</span></span>|<span data-ttu-id="46af1-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="46af1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="46af1-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="46af1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="46af1-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="46af1-107">Event ID</span></span>|<span data-ttu-id="46af1-108">11031</span><span class="sxs-lookup"><span data-stu-id="46af1-108">11031</span></span>|  
|<span data-ttu-id="46af1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="46af1-109">Event Source</span></span>|<span data-ttu-id="46af1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="46af1-110">ENTSSO</span></span>|  
|<span data-ttu-id="46af1-111">元件</span><span class="sxs-lookup"><span data-stu-id="46af1-111">Component</span></span>|<span data-ttu-id="46af1-112">不適用</span><span class="sxs-lookup"><span data-stu-id="46af1-112">N/A</span></span>|  
|<span data-ttu-id="46af1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="46af1-113">Symbolic Name</span></span>|<span data-ttu-id="46af1-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span><span class="sxs-lookup"><span data-stu-id="46af1-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span></span>|  
|<span data-ttu-id="46af1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="46af1-115">Message Text</span></span>|<span data-ttu-id="46af1-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="46af1-116">Windows password change.</span></span> <span data-ttu-id="46af1-117">已偵測到此 Windows 帳戶的對應，但忽略，因為它已經 valid.%r</span><span class="sxs-lookup"><span data-stu-id="46af1-117">A mapping for this Windows account has been detected but ignored because it is no longer valid.%r</span></span><br /><br /> <span data-ttu-id="46af1-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="46af1-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="46af1-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="46af1-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="46af1-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="46af1-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="46af1-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="46af1-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="46af1-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="46af1-122">Client User: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46af1-123">說明</span><span class="sxs-lookup"><span data-stu-id="46af1-123">Explanation</span></span>  
 <span data-ttu-id="46af1-124">它可能是 Windows 帳戶存在且有效，但並非在應用程式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="46af1-124">It may be that the Windows account exists and is valid, but is not in the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46af1-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="46af1-125">User Action</span></span>  
 <span data-ttu-id="46af1-126">刪除對應，然後嘗試重新建立它。</span><span class="sxs-lookup"><span data-stu-id="46af1-126">Delete the mapping and try to recreate it.</span></span>