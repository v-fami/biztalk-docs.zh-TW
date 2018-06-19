---
title: 單一登入： 事件 10558 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84637b67-09df-4c1e-b9f2-85a738ba0d7a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2ee5c21bdf90e6aedcdbe2ac83e0e51a7f48f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270798"
---
# <a name="single-sign-on-event-10558"></a><span data-ttu-id="cf85a-102">單一登入： 事件 10558</span><span class="sxs-lookup"><span data-stu-id="cf85a-102">Single Sign-On: Event 10558</span></span>
## <a name="details"></a><span data-ttu-id="cf85a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf85a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf85a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cf85a-104">Product Name</span></span>|<span data-ttu-id="cf85a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="cf85a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cf85a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="cf85a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cf85a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cf85a-107">Event ID</span></span>|<span data-ttu-id="cf85a-108">10558</span><span class="sxs-lookup"><span data-stu-id="cf85a-108">10558</span></span>|  
|<span data-ttu-id="cf85a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="cf85a-109">Event Source</span></span>|<span data-ttu-id="cf85a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cf85a-110">ENTSSO</span></span>|  
|<span data-ttu-id="cf85a-111">元件</span><span class="sxs-lookup"><span data-stu-id="cf85a-111">Component</span></span>|<span data-ttu-id="cf85a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="cf85a-112">N/A</span></span>|  
|<span data-ttu-id="cf85a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cf85a-113">Symbolic Name</span></span>|<span data-ttu-id="cf85a-114">SSO_WARN_USER_OWN_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="cf85a-114">SSO_WARN_USER_OWN_MAPPINGS</span></span>|  
|<span data-ttu-id="cf85a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cf85a-115">Message Text</span></span>|<span data-ttu-id="cf85a-116">只允許應用程式使用者控制自己的 mappings.%r</span><span class="sxs-lookup"><span data-stu-id="cf85a-116">Application Users are only allowed to control their own mappings.%r</span></span><br /><br /> <span data-ttu-id="cf85a-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="cf85a-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="cf85a-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="cf85a-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="cf85a-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="cf85a-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="cf85a-120">用戶端使用者： %4</span><span class="sxs-lookup"><span data-stu-id="cf85a-120">Client User: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf85a-121">說明</span><span class="sxs-lookup"><span data-stu-id="cf85a-121">Explanation</span></span>  
 <span data-ttu-id="cf85a-122">嘗試由應用程式使用者控制不同的使用者的對應。</span><span class="sxs-lookup"><span data-stu-id="cf85a-122">An attempt was made by an Application User to control the mappings of a different user.</span></span> <span data-ttu-id="cf85a-123">但這種作法並不合法。</span><span class="sxs-lookup"><span data-stu-id="cf85a-123">This is not allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf85a-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cf85a-124">User Action</span></span>  
 <span data-ttu-id="cf85a-125">只針對這些特定的對應應用程式使用者可以控制對應。</span><span class="sxs-lookup"><span data-stu-id="cf85a-125">Mappings can only be controlled by the Application Users for those specific mappings.</span></span>