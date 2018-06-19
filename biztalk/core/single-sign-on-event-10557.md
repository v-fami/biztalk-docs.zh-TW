---
title: 單一登入： 事件 10557 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f29bc394-4c56-4ded-93a1-004afb3a054a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afc65dba8760c85ad9eb6552e56e52cc6b7dd3ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269766"
---
# <a name="single-sign-on-event-10557"></a><span data-ttu-id="fa36f-102">單一登入： 事件 10557</span><span class="sxs-lookup"><span data-stu-id="fa36f-102">Single Sign-On: Event 10557</span></span>
## <a name="details"></a><span data-ttu-id="fa36f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa36f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa36f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fa36f-104">Product Name</span></span>|<span data-ttu-id="fa36f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fa36f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fa36f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fa36f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fa36f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fa36f-107">Event ID</span></span>|<span data-ttu-id="fa36f-108">10557</span><span class="sxs-lookup"><span data-stu-id="fa36f-108">10557</span></span>|  
|<span data-ttu-id="fa36f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fa36f-109">Event Source</span></span>|<span data-ttu-id="fa36f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fa36f-110">ENTSSO</span></span>|  
|<span data-ttu-id="fa36f-111">元件</span><span class="sxs-lookup"><span data-stu-id="fa36f-111">Component</span></span>|<span data-ttu-id="fa36f-112">不適用</span><span class="sxs-lookup"><span data-stu-id="fa36f-112">N/A</span></span>|  
|<span data-ttu-id="fa36f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fa36f-113">Symbolic Name</span></span>|<span data-ttu-id="fa36f-114">SSO_WARN_USER_NOT_ALLOWED_FOR_GROUPS</span><span class="sxs-lookup"><span data-stu-id="fa36f-114">SSO_WARN_USER_NOT_ALLOWED_FOR_GROUPS</span></span>|  
|<span data-ttu-id="fa36f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fa36f-115">Message Text</span></span>|<span data-ttu-id="fa36f-116">不允許應用程式使用者控制群組 applications.%r 對應</span><span class="sxs-lookup"><span data-stu-id="fa36f-116">Application Users are not allowed to control mappings for Group applications.%r</span></span><br /><br /> <span data-ttu-id="fa36f-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fa36f-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="fa36f-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="fa36f-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="fa36f-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="fa36f-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="fa36f-120">用戶端使用者： %4</span><span class="sxs-lookup"><span data-stu-id="fa36f-120">Client User: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa36f-121">說明</span><span class="sxs-lookup"><span data-stu-id="fa36f-121">Explanation</span></span>  
 <span data-ttu-id="fa36f-122">應用程式使用者沒有足夠的權限，才能建立或控制群組應用程式的對應。</span><span class="sxs-lookup"><span data-stu-id="fa36f-122">An Application User does not have sufficient privileges to create or control mappings for Group applications.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa36f-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fa36f-123">User Action</span></span>  
 <span data-ttu-id="fa36f-124">必須由應用程式系統管理員身分執行此活動。</span><span class="sxs-lookup"><span data-stu-id="fa36f-124">This activity must be performed by an Application Administrator.</span></span>