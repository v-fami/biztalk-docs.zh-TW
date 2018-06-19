---
title: 單一登入： 事件 11022 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccae36e9beef672e6c5fb7917c88341ce4bb3c08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276990"
---
# <a name="single-sign-on-event-11022"></a><span data-ttu-id="a0b7d-102">單一登入： 事件 11022</span><span class="sxs-lookup"><span data-stu-id="a0b7d-102">Single Sign-On: Event 11022</span></span>
## <a name="details"></a><span data-ttu-id="a0b7d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0b7d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0b7d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a0b7d-104">Product Name</span></span>|<span data-ttu-id="a0b7d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a0b7d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a0b7d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a0b7d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a0b7d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a0b7d-107">Event ID</span></span>|<span data-ttu-id="a0b7d-108">11022</span><span class="sxs-lookup"><span data-stu-id="a0b7d-108">11022</span></span>|  
|<span data-ttu-id="a0b7d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a0b7d-109">Event Source</span></span>|<span data-ttu-id="a0b7d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a0b7d-110">ENTSSO</span></span>|  
|<span data-ttu-id="a0b7d-111">元件</span><span class="sxs-lookup"><span data-stu-id="a0b7d-111">Component</span></span>|<span data-ttu-id="a0b7d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a0b7d-112">N/A</span></span>|  
|<span data-ttu-id="a0b7d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a0b7d-113">Symbolic Name</span></span>|<span data-ttu-id="a0b7d-114">SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="a0b7d-114">SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="a0b7d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a0b7d-115">Message Text</span></span>|<span data-ttu-id="a0b7d-116">外部密碼變更可能已造成不同的外部帳戶 changed.%r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-116">An external password change would have caused a different external account to be changed.%r</span></span><br /><br /> <span data-ttu-id="a0b7d-117">這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="a0b7d-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a0b7d-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="a0b7d-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="a0b7d-121">外部帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="a0b7d-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="a0b7d-122">外部帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="a0b7d-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a0b7d-123">說明</span><span class="sxs-lookup"><span data-stu-id="a0b7d-123">Explanation</span></span>  
 <span data-ttu-id="a0b7d-124">這是參考用訊息報告的外部密碼變更可能已造成不同的外部帳戶變更失敗。</span><span class="sxs-lookup"><span data-stu-id="a0b7d-124">This is an informational message reporting the failure of an external password change which would have caused a different external account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0b7d-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a0b7d-125">User Action</span></span>  
 <span data-ttu-id="a0b7d-126">雖然沒有任何變更 （因為此系統設定為不允許對應衝突），您應該確認立即，此嘗試與您的知識和授權。</span><span class="sxs-lookup"><span data-stu-id="a0b7d-126">Although no change was made (because this system is configured to not allow mapping conflicts) you should confirm immediately that this attempt was made with your knowledge and authorization.</span></span> <span data-ttu-id="a0b7d-127">如果是的話，不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="a0b7d-127">If so, no action is required.</span></span> <span data-ttu-id="a0b7d-128">如果沒有，找出變更其中起始，並確認它安全地在系統中的位置。</span><span class="sxs-lookup"><span data-stu-id="a0b7d-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>