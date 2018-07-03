---
title: 單一登入： 事件 11026 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e39b252d-2ed0-4006-aac2-4dce6504afb2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 452ccc24174a1e32a133c0ccc6c7a0b5f09c530f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013487"
---
# <a name="single-sign-on-event-11026"></a><span data-ttu-id="b8f42-102">單一登入： 事件 11026</span><span class="sxs-lookup"><span data-stu-id="b8f42-102">Single Sign-On: Event 11026</span></span>
## <a name="details"></a><span data-ttu-id="b8f42-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b8f42-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="b8f42-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b8f42-104">Product Name</span></span>   |                                                                                                                                <span data-ttu-id="b8f42-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b8f42-105">Enterprise Single Sign-On</span></span>                                                                                                                                |
| <span data-ttu-id="b8f42-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b8f42-106">Product Version</span></span> |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    <span data-ttu-id="b8f42-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b8f42-107">Event ID</span></span>     |                                                                                                                                          <span data-ttu-id="b8f42-108">11026</span><span class="sxs-lookup"><span data-stu-id="b8f42-108">11026</span></span>                                                                                                                                          |
|  <span data-ttu-id="b8f42-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b8f42-109">Event Source</span></span>   |                                                                                                                                         <span data-ttu-id="b8f42-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b8f42-110">ENTSSO</span></span>                                                                                                                                          |
|    <span data-ttu-id="b8f42-111">元件</span><span class="sxs-lookup"><span data-stu-id="b8f42-111">Component</span></span>    |                                                                                                                                           <span data-ttu-id="b8f42-112">不適用</span><span class="sxs-lookup"><span data-stu-id="b8f42-112">N/A</span></span>                                                                                                                                           |
|  <span data-ttu-id="b8f42-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b8f42-113">Symbolic Name</span></span>  |                                                                                                                             <span data-ttu-id="b8f42-114">SSO_WARN_EXISTING_GROUP_MAPPING</span><span class="sxs-lookup"><span data-stu-id="b8f42-114">SSO_WARN_EXISTING_GROUP_MAPPING</span></span>                                                                                                                             |
|  <span data-ttu-id="b8f42-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b8f42-115">Message Text</span></span>   | <span data-ttu-id="b8f42-116">無法建立新的群組對應，因為有衝突，以使用現有的對應。</span><span class="sxs-lookup"><span data-stu-id="b8f42-116">A new group mapping could not be created because there is a conflict with an existing mapping.</span></span> <span data-ttu-id="b8f42-117">請刪除現有的對應，然後重試 again.%r</span><span class="sxs-lookup"><span data-stu-id="b8f42-117">Please delete the existing mapping and try again.%r</span></span><br /><br /> <span data-ttu-id="b8f42-118">現有的對應: %1 %r</span><span class="sxs-lookup"><span data-stu-id="b8f42-118">Existing Mapping: %1%r</span></span><br /><br /> <span data-ttu-id="b8f42-119">新的對應: %2 %r</span><span class="sxs-lookup"><span data-stu-id="b8f42-119">New Mapping: %2%r</span></span><br /><br /> <span data-ttu-id="b8f42-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="b8f42-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="b8f42-121">應用程式名稱： %4</span><span class="sxs-lookup"><span data-stu-id="b8f42-121">Application Name: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="b8f42-122">說明</span><span class="sxs-lookup"><span data-stu-id="b8f42-122">Explanation</span></span>  
 <span data-ttu-id="b8f42-123">最可能的原因是您的系統使用企業單一登入，和舊的群組應用程式的舊版本。</span><span class="sxs-lookup"><span data-stu-id="b8f42-123">The most likely cause is that your system is using an old version of Enterprise Single Sign-On, and old group applications.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8f42-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b8f42-124">User Action</span></span>  
 <span data-ttu-id="b8f42-125">刪除並重建為建議警告中的對應。</span><span class="sxs-lookup"><span data-stu-id="b8f42-125">Delete and recreate the mapping as suggested in the warning.</span></span> <span data-ttu-id="b8f42-126">如果失敗，您可能需要升級至較新版本的企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="b8f42-126">If this fails, you may need to upgrade to a more recent version of Enterprise Single Sign-On.</span></span>