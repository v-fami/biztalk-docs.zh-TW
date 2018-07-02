---
title: 單一登入： 事件 10558 |Microsoft Docs
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
ms.openlocfilehash: 1d9a281d6a6ca20a274db4b3ffe5b2697ff812c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974864"
---
# <a name="single-sign-on-event-10558"></a><span data-ttu-id="cafbe-102">單一登入： 事件 10558</span><span class="sxs-lookup"><span data-stu-id="cafbe-102">Single Sign-On: Event 10558</span></span>
## <a name="details"></a><span data-ttu-id="cafbe-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cafbe-103">Details</span></span>  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="cafbe-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cafbe-104">Product Name</span></span>   |                                                                                  <span data-ttu-id="cafbe-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="cafbe-105">Enterprise Single Sign-On</span></span>                                                                                   |
| <span data-ttu-id="cafbe-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="cafbe-106">Product Version</span></span> |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    <span data-ttu-id="cafbe-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cafbe-107">Event ID</span></span>     |                                                                                            <span data-ttu-id="cafbe-108">10558</span><span class="sxs-lookup"><span data-stu-id="cafbe-108">10558</span></span>                                                                                             |
|  <span data-ttu-id="cafbe-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="cafbe-109">Event Source</span></span>   |                                                                                            <span data-ttu-id="cafbe-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cafbe-110">ENTSSO</span></span>                                                                                            |
|    <span data-ttu-id="cafbe-111">元件</span><span class="sxs-lookup"><span data-stu-id="cafbe-111">Component</span></span>    |                                                                                             <span data-ttu-id="cafbe-112">不適用</span><span class="sxs-lookup"><span data-stu-id="cafbe-112">N/A</span></span>                                                                                              |
|  <span data-ttu-id="cafbe-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cafbe-113">Symbolic Name</span></span>  |                                                                                  <span data-ttu-id="cafbe-114">SSO_WARN_USER_OWN_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="cafbe-114">SSO_WARN_USER_OWN_MAPPINGS</span></span>                                                                                  |
|  <span data-ttu-id="cafbe-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cafbe-115">Message Text</span></span>   | <span data-ttu-id="cafbe-116">只允許應用程式使用者控制自己的 mappings.%r</span><span class="sxs-lookup"><span data-stu-id="cafbe-116">Application Users are only allowed to control their own mappings.%r</span></span><br /><br /> <span data-ttu-id="cafbe-117">網域名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="cafbe-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="cafbe-118">使用者名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="cafbe-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="cafbe-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="cafbe-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="cafbe-120">用戶端使用者： %4</span><span class="sxs-lookup"><span data-stu-id="cafbe-120">Client User: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="cafbe-121">說明</span><span class="sxs-lookup"><span data-stu-id="cafbe-121">Explanation</span></span>  
 <span data-ttu-id="cafbe-122">嘗試透過應用程式使用者控制不同使用者的對應。</span><span class="sxs-lookup"><span data-stu-id="cafbe-122">An attempt was made by an Application User to control the mappings of a different user.</span></span> <span data-ttu-id="cafbe-123">但這種作法並不合法。</span><span class="sxs-lookup"><span data-stu-id="cafbe-123">This is not allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cafbe-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cafbe-124">User Action</span></span>  
 <span data-ttu-id="cafbe-125">只針對這些特定的對應應用程式使用者可以控制對應。</span><span class="sxs-lookup"><span data-stu-id="cafbe-125">Mappings can only be controlled by the Application Users for those specific mappings.</span></span>