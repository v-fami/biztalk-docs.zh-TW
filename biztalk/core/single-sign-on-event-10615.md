---
title: 單一登入： 事件 10615 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5dd0041-2dfd-4fd1-97ec-f9fc719a6fcc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9570290f82821a80d22826f41d4ed669e29f5b4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271494"
---
# <a name="single-sign-on-event-10615"></a><span data-ttu-id="3d5f7-102">單一登入： 事件 10615</span><span class="sxs-lookup"><span data-stu-id="3d5f7-102">Single Sign-On: Event 10615</span></span>
## <a name="details"></a><span data-ttu-id="3d5f7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3d5f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d5f7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3d5f7-104">Product Name</span></span>|<span data-ttu-id="3d5f7-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3d5f7-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3d5f7-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3d5f7-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3d5f7-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3d5f7-107">Event ID</span></span>|<span data-ttu-id="3d5f7-108">10615</span><span class="sxs-lookup"><span data-stu-id="3d5f7-108">10615</span></span>|  
|<span data-ttu-id="3d5f7-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3d5f7-109">Event Source</span></span>|<span data-ttu-id="3d5f7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3d5f7-110">ENTSSO</span></span>|  
|<span data-ttu-id="3d5f7-111">元件</span><span class="sxs-lookup"><span data-stu-id="3d5f7-111">Component</span></span>|<span data-ttu-id="3d5f7-112">不適用</span><span class="sxs-lookup"><span data-stu-id="3d5f7-112">N/A</span></span>|  
|<span data-ttu-id="3d5f7-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3d5f7-113">Symbolic Name</span></span>|<span data-ttu-id="3d5f7-114">SSO_WARN_NO_UPDATE_TICKET_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d5f7-114">SSO_WARN_NO_UPDATE_TICKET_TIMEOUT</span></span>|  
|<span data-ttu-id="3d5f7-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3d5f7-115">Message Text</span></span>|<span data-ttu-id="3d5f7-116">用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能變更 application.%r 票證逾時</span><span class="sxs-lookup"><span data-stu-id="3d5f7-116">The client user must be a member of the SSO Administrators account to change the ticket time-out for an application.%r</span></span><br /><br /> <span data-ttu-id="3d5f7-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="3d5f7-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="3d5f7-118">SSO 系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="3d5f7-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="3d5f7-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="3d5f7-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="3d5f7-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="3d5f7-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3d5f7-121">說明</span><span class="sxs-lookup"><span data-stu-id="3d5f7-121">Explanation</span></span>  
 <span data-ttu-id="3d5f7-122">用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能變更應用程式的票證逾時。</span><span class="sxs-lookup"><span data-stu-id="3d5f7-122">The client user must be a member of the SSO Administrators account to change the ticket time-out for an application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3d5f7-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3d5f7-123">User Action</span></span>  
 <span data-ttu-id="3d5f7-124">請要求系統管理員協助您找出 SSO 系統管理員帳戶的成員，才能進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="3d5f7-124">Have your system administrator help you find a member of the SSO Administrators account to make this change.</span></span>