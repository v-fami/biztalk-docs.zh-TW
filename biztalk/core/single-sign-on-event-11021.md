---
title: 單一登入： 事件 11021 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70b987aa-8097-4243-a25b-f1cc12c5bc6a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e246ac3d0bbab4e991b17c091567b4b59131b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278070"
---
# <a name="single-sign-on-event-11021"></a><span data-ttu-id="e3565-102">單一登入： 事件 11021</span><span class="sxs-lookup"><span data-stu-id="e3565-102">Single Sign-On: Event 11021</span></span>
## <a name="details"></a><span data-ttu-id="e3565-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e3565-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3565-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e3565-104">Product Name</span></span>|<span data-ttu-id="e3565-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e3565-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e3565-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e3565-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e3565-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e3565-107">Event ID</span></span>|<span data-ttu-id="e3565-108">11021</span><span class="sxs-lookup"><span data-stu-id="e3565-108">11021</span></span>|  
|<span data-ttu-id="e3565-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e3565-109">Event Source</span></span>|<span data-ttu-id="e3565-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e3565-110">ENTSSO</span></span>|  
|<span data-ttu-id="e3565-111">元件</span><span class="sxs-lookup"><span data-stu-id="e3565-111">Component</span></span>|<span data-ttu-id="e3565-112">不適用</span><span class="sxs-lookup"><span data-stu-id="e3565-112">N/A</span></span>|  
|<span data-ttu-id="e3565-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e3565-113">Symbolic Name</span></span>|<span data-ttu-id="e3565-114">SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="e3565-114">SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="e3565-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e3565-115">Message Text</span></span>|<span data-ttu-id="e3565-116">外部密碼變更將造成不同的外部帳戶 changed.%r</span><span class="sxs-lookup"><span data-stu-id="e3565-116">An external password change will cause a different external account to be changed.%r</span></span><br /><br /> <span data-ttu-id="e3565-117">這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="e3565-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="e3565-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="e3565-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="e3565-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="e3565-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="e3565-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="e3565-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="e3565-121">外部帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="e3565-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="e3565-122">外部帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="e3565-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3565-123">說明</span><span class="sxs-lookup"><span data-stu-id="e3565-123">Explanation</span></span>  
 <span data-ttu-id="e3565-124">這是資訊訊息，指出外部密碼變更將造成不同的外部帳戶變更。</span><span class="sxs-lookup"><span data-stu-id="e3565-124">This is an informational message stating that an external password change will cause a different external account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3565-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e3565-125">User Action</span></span>  
 <span data-ttu-id="e3565-126">您應該立即確認這項變更為了與您的知識和授權。</span><span class="sxs-lookup"><span data-stu-id="e3565-126">You should confirm immediately that this change was made with your knowledge and authorization.</span></span> <span data-ttu-id="e3565-127">如果是的話，不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="e3565-127">If so, no action is required.</span></span> <span data-ttu-id="e3565-128">如果沒有，找出變更其中起始，並確認它安全地在系統中的位置。</span><span class="sxs-lookup"><span data-stu-id="e3565-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>