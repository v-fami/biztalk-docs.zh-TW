---
title: 單一登入： 事件 11017 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4f7264-18aa-4eca-97c9-d5fd7e90e2cc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25ef3f3be84e775fe522b508f7726f3e4e88870b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276774"
---
# <a name="single-sign-on-event-11017"></a><span data-ttu-id="8c109-102">單一登入： 事件 11017</span><span class="sxs-lookup"><span data-stu-id="8c109-102">Single Sign-On: Event 11017</span></span>
## <a name="details"></a><span data-ttu-id="8c109-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c109-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c109-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8c109-104">Product Name</span></span>|<span data-ttu-id="8c109-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8c109-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8c109-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8c109-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8c109-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8c109-107">Event ID</span></span>|<span data-ttu-id="8c109-108">11017</span><span class="sxs-lookup"><span data-stu-id="8c109-108">11017</span></span>|  
|<span data-ttu-id="8c109-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8c109-109">Event Source</span></span>|<span data-ttu-id="8c109-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8c109-110">ENTSSO</span></span>|  
|<span data-ttu-id="8c109-111">元件</span><span class="sxs-lookup"><span data-stu-id="8c109-111">Component</span></span>|<span data-ttu-id="8c109-112">不適用</span><span class="sxs-lookup"><span data-stu-id="8c109-112">N/A</span></span>|  
|<span data-ttu-id="8c109-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8c109-113">Symbolic Name</span></span>|<span data-ttu-id="8c109-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK</span><span class="sxs-lookup"><span data-stu-id="8c109-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK</span></span>|  
|<span data-ttu-id="8c109-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8c109-115">Message Text</span></span>|<span data-ttu-id="8c109-116">對應無效，因為 Windows 帳戶不是應用程式的應用程式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c109-116">The mapping is not valid because the Windows account is not in the Application Users account for the application.</span></span> <span data-ttu-id="8c109-117">對應已 deleted.%r</span><span class="sxs-lookup"><span data-stu-id="8c109-117">The mapping has been deleted.%r</span></span><br /><br /> <span data-ttu-id="8c109-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8c109-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="8c109-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8c109-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="8c109-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="8c109-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="8c109-121">應用程式使用者： %4</span><span class="sxs-lookup"><span data-stu-id="8c109-121">Application Users: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8c109-122">說明</span><span class="sxs-lookup"><span data-stu-id="8c109-122">Explanation</span></span>  
 <span data-ttu-id="8c109-123">請指定的 Windows 帳戶向來是不屬於此應用程式的應用程式使用者帳戶，或它是一次，但已變更或移除。</span><span class="sxs-lookup"><span data-stu-id="8c109-123">Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed.</span></span> <span data-ttu-id="8c109-124">對應已被刪除。</span><span class="sxs-lookup"><span data-stu-id="8c109-124">The mapping has been deleted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c109-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8c109-125">User Action</span></span>  
 <span data-ttu-id="8c109-126">請檢查您的系統密碼同步處理帳戶資訊，請確定您的資訊有效。</span><span class="sxs-lookup"><span data-stu-id="8c109-126">Check the password sync account information for your system, and make sure your information is valid.</span></span> <span data-ttu-id="8c109-127">然後重新建立對應。</span><span class="sxs-lookup"><span data-stu-id="8c109-127">Then recreate the mapping.</span></span> <span data-ttu-id="8c109-128">請注意，使用 建立對應精靈可降低無效的對應資訊的風險。</span><span class="sxs-lookup"><span data-stu-id="8c109-128">Note that using the Create Mapping Wizard reduces the risk of invalid mapping information.</span></span>