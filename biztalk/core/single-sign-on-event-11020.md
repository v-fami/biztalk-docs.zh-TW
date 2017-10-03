---
title: "單一登入： 事件 11020 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a0d72-ece6-4094-9263-dbf69bb068c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444a61beec74a9d7141df79d05d8863cc10d6dc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11020"></a><span data-ttu-id="f8314-102">單一登入： 事件 11020</span><span class="sxs-lookup"><span data-stu-id="f8314-102">Single Sign-On: Event 11020</span></span>
## <a name="details"></a><span data-ttu-id="f8314-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f8314-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8314-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f8314-104">Product Name</span></span>|<span data-ttu-id="f8314-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f8314-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f8314-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f8314-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f8314-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f8314-107">Event ID</span></span>|<span data-ttu-id="f8314-108">11020</span><span class="sxs-lookup"><span data-stu-id="f8314-108">11020</span></span>|  
|<span data-ttu-id="f8314-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f8314-109">Event Source</span></span>|<span data-ttu-id="f8314-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f8314-110">ENTSSO</span></span>|  
|<span data-ttu-id="f8314-111">元件</span><span class="sxs-lookup"><span data-stu-id="f8314-111">Component</span></span>|<span data-ttu-id="f8314-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f8314-112">N/A</span></span>|  
|<span data-ttu-id="f8314-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f8314-113">Symbolic Name</span></span>|<span data-ttu-id="f8314-114">SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="f8314-114">SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="f8314-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f8314-115">Message Text</span></span>|<span data-ttu-id="f8314-116">Windows 密碼變更將造成不同的 Windows 帳戶 changed.%r</span><span class="sxs-lookup"><span data-stu-id="f8314-116">A Windows password change will cause a different Windows account to be changed.%r</span></span><br /><br /> <span data-ttu-id="f8314-117">這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="f8314-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="f8314-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f8314-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="f8314-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f8314-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="f8314-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f8314-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="f8314-121">Windows 帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="f8314-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="f8314-122">Windows 帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="f8314-122">Windows Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f8314-123">說明</span><span class="sxs-lookup"><span data-stu-id="f8314-123">Explanation</span></span>  
 <span data-ttu-id="f8314-124">這是資訊訊息，指出 Windows 密碼變更將造成不同 Windows 帳戶變更。</span><span class="sxs-lookup"><span data-stu-id="f8314-124">This is an informational message stating that a Windows password change will cause a different Windows account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f8314-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f8314-125">User Action</span></span>  
 <span data-ttu-id="f8314-126">您應該立即確認這項變更為了與您的知識和授權。</span><span class="sxs-lookup"><span data-stu-id="f8314-126">You should confirm immediately that this change was made with your knowledge and authorization.</span></span> <span data-ttu-id="f8314-127">如果是的話，不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="f8314-127">If so, no action is required.</span></span> <span data-ttu-id="f8314-128">如果沒有，找出變更其中起始，並確認它安全地在系統中的位置。</span><span class="sxs-lookup"><span data-stu-id="f8314-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>