---
title: 單一登入： 事件 10817 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1668b81-e7f4-46d2-aebe-47007f70372b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e42873f0b56c43a7c997a2476ba2b15148d4639
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979191"
---
# <a name="single-sign-on-event-10817"></a><span data-ttu-id="554a5-102">單一登入： 事件 10817</span><span class="sxs-lookup"><span data-stu-id="554a5-102">Single Sign-On: Event 10817</span></span>
## <a name="details"></a><span data-ttu-id="554a5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="554a5-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="554a5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="554a5-104">Product Name</span></span>   |                 <span data-ttu-id="554a5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="554a5-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="554a5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="554a5-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="554a5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="554a5-107">Event ID</span></span>     |                           <span data-ttu-id="554a5-108">10817</span><span class="sxs-lookup"><span data-stu-id="554a5-108">10817</span></span>                            |
|  <span data-ttu-id="554a5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="554a5-109">Event Source</span></span>   |                           <span data-ttu-id="554a5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="554a5-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="554a5-111">元件</span><span class="sxs-lookup"><span data-stu-id="554a5-111">Component</span></span>    |                            <span data-ttu-id="554a5-112">不適用</span><span class="sxs-lookup"><span data-stu-id="554a5-112">N/A</span></span>                             |
|  <span data-ttu-id="554a5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="554a5-113">Symbolic Name</span></span>  |              <span data-ttu-id="554a5-114">ENTSSO_E_NOTIFICATION_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="554a5-114">ENTSSO_E_NOTIFICATION_NOT_FOUND</span></span>               |
|  <span data-ttu-id="554a5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="554a5-115">Message Text</span></span>   |         <span data-ttu-id="554a5-116">找不到指定的通知。</span><span class="sxs-lookup"><span data-stu-id="554a5-116">The specified notification was not found.</span></span>          |
  
## <a name="explanation"></a><span data-ttu-id="554a5-117">說明</span><span class="sxs-lookup"><span data-stu-id="554a5-117">Explanation</span></span>  
 <span data-ttu-id="554a5-118">密碼變更指定找不到 GUID 的通知。</span><span class="sxs-lookup"><span data-stu-id="554a5-118">The password change specified a notification GUID which cannot be found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="554a5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="554a5-119">User Action</span></span>  
 <span data-ttu-id="554a5-120">請參閱此密碼同步配接器，來判斷通知的適當 GUID 的組態。</span><span class="sxs-lookup"><span data-stu-id="554a5-120">See the configuration for this password sync adapter to determine the proper GUID of the notification.</span></span>