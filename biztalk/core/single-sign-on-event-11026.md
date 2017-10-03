---
title: "單一登入： 事件 11026 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e39b252d-2ed0-4006-aac2-4dce6504afb2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecee6d3c3e6dcf01b8489c4041f4aab717eba585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11026"></a><span data-ttu-id="0cbd6-102">單一登入： 事件 11026</span><span class="sxs-lookup"><span data-stu-id="0cbd6-102">Single Sign-On: Event 11026</span></span>
## <a name="details"></a><span data-ttu-id="0cbd6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cbd6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0cbd6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0cbd6-104">Product Name</span></span>|<span data-ttu-id="0cbd6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0cbd6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="0cbd6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0cbd6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="0cbd6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0cbd6-107">Event ID</span></span>|<span data-ttu-id="0cbd6-108">11026</span><span class="sxs-lookup"><span data-stu-id="0cbd6-108">11026</span></span>|  
|<span data-ttu-id="0cbd6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0cbd6-109">Event Source</span></span>|<span data-ttu-id="0cbd6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0cbd6-110">ENTSSO</span></span>|  
|<span data-ttu-id="0cbd6-111">元件</span><span class="sxs-lookup"><span data-stu-id="0cbd6-111">Component</span></span>|<span data-ttu-id="0cbd6-112">不適用</span><span class="sxs-lookup"><span data-stu-id="0cbd6-112">N/A</span></span>|  
|<span data-ttu-id="0cbd6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0cbd6-113">Symbolic Name</span></span>|<span data-ttu-id="0cbd6-114">SSO_WARN_EXISTING_GROUP_MAPPING</span><span class="sxs-lookup"><span data-stu-id="0cbd6-114">SSO_WARN_EXISTING_GROUP_MAPPING</span></span>|  
|<span data-ttu-id="0cbd6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0cbd6-115">Message Text</span></span>|<span data-ttu-id="0cbd6-116">無法建立新群組對應，因為與現有的對應相衝突。</span><span class="sxs-lookup"><span data-stu-id="0cbd6-116">A new group mapping could not be created because there is a conflict with an existing mapping.</span></span> <span data-ttu-id="0cbd6-117">請刪除現有的對應，然後再試一次 again.%r</span><span class="sxs-lookup"><span data-stu-id="0cbd6-117">Please delete the existing mapping and try again.%r</span></span><br /><br /> <span data-ttu-id="0cbd6-118">現有的對應: %1 %r</span><span class="sxs-lookup"><span data-stu-id="0cbd6-118">Existing Mapping: %1%r</span></span><br /><br /> <span data-ttu-id="0cbd6-119">新的對應: %2 %r</span><span class="sxs-lookup"><span data-stu-id="0cbd6-119">New Mapping: %2%r</span></span><br /><br /> <span data-ttu-id="0cbd6-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="0cbd6-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="0cbd6-121">應用程式名稱： %4</span><span class="sxs-lookup"><span data-stu-id="0cbd6-121">Application Name: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0cbd6-122">說明</span><span class="sxs-lookup"><span data-stu-id="0cbd6-122">Explanation</span></span>  
 <span data-ttu-id="0cbd6-123">最可能的原因是您的系統使用較舊版本的企業單一登入，與舊群組應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cbd6-123">The most likely cause is that your system is using an old version of Enterprise Single Sign-On, and old group applications.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0cbd6-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0cbd6-124">User Action</span></span>  
 <span data-ttu-id="0cbd6-125">刪除並重新建立警告中建議的對應。</span><span class="sxs-lookup"><span data-stu-id="0cbd6-125">Delete and recreate the mapping as suggested in the warning.</span></span> <span data-ttu-id="0cbd6-126">如果這個作業失敗，您可能需要升級至較新版本的企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="0cbd6-126">If this fails, you may need to upgrade to a more recent version of Enterprise Single Sign-On.</span></span>