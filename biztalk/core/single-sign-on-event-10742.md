---
title: "單一登入： 事件 10742 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abb3acb03e60d1d7a7e705ac8b36aa5157616f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10742"></a><span data-ttu-id="94772-102">單一登入： 事件 10742</span><span class="sxs-lookup"><span data-stu-id="94772-102">Single Sign-On: Event 10742</span></span>
## <a name="details"></a><span data-ttu-id="94772-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="94772-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94772-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="94772-104">Product Name</span></span>|<span data-ttu-id="94772-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="94772-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="94772-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="94772-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="94772-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="94772-107">Event ID</span></span>|<span data-ttu-id="94772-108">10742</span><span class="sxs-lookup"><span data-stu-id="94772-108">10742</span></span>|  
|<span data-ttu-id="94772-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="94772-109">Event Source</span></span>|<span data-ttu-id="94772-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="94772-110">ENTSSO</span></span>|  
|<span data-ttu-id="94772-111">元件</span><span class="sxs-lookup"><span data-stu-id="94772-111">Component</span></span>|<span data-ttu-id="94772-112">N\A</span><span class="sxs-lookup"><span data-stu-id="94772-112">N\A</span></span>|  
|<span data-ttu-id="94772-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="94772-113">Symbolic Name</span></span>|<span data-ttu-id="94772-114">SSO_WARN_NO_UPDATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="94772-114">SSO_WARN_NO_UPDATE_ADAPTER</span></span>|  
|<span data-ttu-id="94772-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="94772-115">Message Text</span></span>|<span data-ttu-id="94772-116">用戶端使用者必須是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員，才能更新 adapter.%r</span><span class="sxs-lookup"><span data-stu-id="94772-116">The client user must be a member of the SSO Administrators account or the Application Administrators account to update the adapter.%r</span></span><br /><br /> <span data-ttu-id="94772-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="94772-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="94772-118">SSO 系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="94772-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="94772-119">應用程式系統管理員: %3 %r</span><span class="sxs-lookup"><span data-stu-id="94772-119">Application Administrators: %3%r</span></span><br /><br /> <span data-ttu-id="94772-120">配接器: %4 %r</span><span class="sxs-lookup"><span data-stu-id="94772-120">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="94772-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="94772-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94772-122">說明</span><span class="sxs-lookup"><span data-stu-id="94772-122">Explanation</span></span>  
 <span data-ttu-id="94772-123">這個警告事件表示，嘗試更新指定的配接器，但無法完成，因為使用的使用者帳戶不是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="94772-123">This Warning event indicates that an attempt to update the specified adapter was made, but could not be completed because the user account used is not a member of the SSO Administrators account or the Application Administrators account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94772-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="94772-124">User Action</span></span>  
 <span data-ttu-id="94772-125">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="94772-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="94772-126">將使用者帳戶新增至 SSO 系統管理員帳戶或應用程式系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="94772-126">Add user account to the SSO Administrators account or the Application Administrators account.</span></span>  
  
-   <span data-ttu-id="94772-127">重試更新。</span><span class="sxs-lookup"><span data-stu-id="94772-127">Retry update.</span></span>  
  
 <span data-ttu-id="94772-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="94772-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="94772-129">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="94772-129">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)