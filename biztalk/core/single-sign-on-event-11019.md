---
title: 單一登入： 事件 11019 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec07b00-d567-4518-89eb-340e4f92429b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4b2d2494a404566c7350a9e9988d429a3e335c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276374"
---
# <a name="single-sign-on-event-11019"></a><span data-ttu-id="47e11-102">單一登入： 事件 11019</span><span class="sxs-lookup"><span data-stu-id="47e11-102">Single Sign-On: Event 11019</span></span>
## <a name="details"></a><span data-ttu-id="47e11-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47e11-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47e11-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="47e11-104">Product Name</span></span>|<span data-ttu-id="47e11-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="47e11-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="47e11-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="47e11-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="47e11-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="47e11-107">Event ID</span></span>|<span data-ttu-id="47e11-108">11019</span><span class="sxs-lookup"><span data-stu-id="47e11-108">11019</span></span>|  
|<span data-ttu-id="47e11-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="47e11-109">Event Source</span></span>|<span data-ttu-id="47e11-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="47e11-110">ENTSSO</span></span>|  
|<span data-ttu-id="47e11-111">元件</span><span class="sxs-lookup"><span data-stu-id="47e11-111">Component</span></span>|<span data-ttu-id="47e11-112">不適用</span><span class="sxs-lookup"><span data-stu-id="47e11-112">N/A</span></span>|  
|<span data-ttu-id="47e11-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="47e11-113">Symbolic Name</span></span>|<span data-ttu-id="47e11-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED</span><span class="sxs-lookup"><span data-stu-id="47e11-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED</span></span>|  
|<span data-ttu-id="47e11-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="47e11-115">Message Text</span></span>|<span data-ttu-id="47e11-116">對應無效，因為 Windows 帳戶不是應用程式的應用程式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="47e11-116">The mapping is not valid because the Windows account is not in the Application Users account for the application.</span></span> <span data-ttu-id="47e11-117">無法刪除對應。</span><span class="sxs-lookup"><span data-stu-id="47e11-117">Failed to delete the mapping.</span></span> <span data-ttu-id="47e11-118">將 ignored.%r 對應。</span><span class="sxs-lookup"><span data-stu-id="47e11-118">The mapping will be ignored.%r</span></span><br /><br /> <span data-ttu-id="47e11-119">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="47e11-119">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="47e11-120">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="47e11-120">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="47e11-121">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="47e11-121">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="47e11-122">應用程式使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="47e11-122">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="47e11-123">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="47e11-123">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="47e11-124">說明</span><span class="sxs-lookup"><span data-stu-id="47e11-124">Explanation</span></span>  
 <span data-ttu-id="47e11-125">請指定的 Windows 帳戶向來是不屬於此應用程式的應用程式使用者帳戶，或它是一次，但已變更或移除。</span><span class="sxs-lookup"><span data-stu-id="47e11-125">Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed.</span></span> <span data-ttu-id="47e11-126">尚未刪除對應。</span><span class="sxs-lookup"><span data-stu-id="47e11-126">The mapping has not been deleted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="47e11-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="47e11-127">User Action</span></span>  
 <span data-ttu-id="47e11-128">請檢查您的系統密碼同步處理帳戶資訊，請確定您的資訊有效。</span><span class="sxs-lookup"><span data-stu-id="47e11-128">Check the password sync account information for your system, and make sure your information is valid.</span></span> <span data-ttu-id="47e11-129">然後重新建立對應。</span><span class="sxs-lookup"><span data-stu-id="47e11-129">Then recreate the mapping.</span></span> <span data-ttu-id="47e11-130">請注意，使用 建立對應精靈可降低無效的對應資訊的風險。</span><span class="sxs-lookup"><span data-stu-id="47e11-130">Note that using the Create Mapping Wizard reduces the risk of invalid mapping information.</span></span> <span data-ttu-id="47e11-131">您可以刪除失敗的對應。</span><span class="sxs-lookup"><span data-stu-id="47e11-131">You can delete the failed mapping.</span></span> <span data-ttu-id="47e11-132">如果您沒有刪除，將會忽略它。</span><span class="sxs-lookup"><span data-stu-id="47e11-132">If you do not delete it, it will be ignored.</span></span>