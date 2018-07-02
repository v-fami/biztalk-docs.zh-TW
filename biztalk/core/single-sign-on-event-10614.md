---
title: 單一登入： 事件 10614 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1f9cd21-3f4b-446f-a4c7-15266973adf1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba6cae7c64b5eeff339499f279aa85917211cbba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968167"
---
# <a name="single-sign-on-event-10614"></a><span data-ttu-id="97348-102">單一登入： 事件 10614</span><span class="sxs-lookup"><span data-stu-id="97348-102">Single Sign-On: Event 10614</span></span>
## <a name="details"></a><span data-ttu-id="97348-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="97348-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="97348-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="97348-104">Product Name</span></span>   |                                                                                                        <span data-ttu-id="97348-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="97348-105">Enterprise Single Sign-On</span></span>                                                                                                        |
| <span data-ttu-id="97348-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="97348-106">Product Version</span></span> |                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                        |
|    <span data-ttu-id="97348-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="97348-107">Event ID</span></span>     |                                                                                                                  <span data-ttu-id="97348-108">10614</span><span class="sxs-lookup"><span data-stu-id="97348-108">10614</span></span>                                                                                                                  |
|  <span data-ttu-id="97348-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="97348-109">Event Source</span></span>   |                                                                                                                 <span data-ttu-id="97348-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="97348-110">ENTSSO</span></span>                                                                                                                  |
|    <span data-ttu-id="97348-111">元件</span><span class="sxs-lookup"><span data-stu-id="97348-111">Component</span></span>    |                                                                                                                   <span data-ttu-id="97348-112">不適用</span><span class="sxs-lookup"><span data-stu-id="97348-112">N/A</span></span>                                                                                                                   |
|  <span data-ttu-id="97348-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="97348-113">Symbolic Name</span></span>  |                                                                                                     <span data-ttu-id="97348-114">SSO_WARN_INVALID_TICKET_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97348-114">SSO_WARN_INVALID_TICKET_TIMEOUT</span></span>                                                                                                     |
|  <span data-ttu-id="97348-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="97348-115">Message Text</span></span>   | <span data-ttu-id="97348-116">票證逾時值對於全域資訊更新無效。%r</span><span class="sxs-lookup"><span data-stu-id="97348-116">The ticket time-out value is not valid for global info update.%r</span></span><br /><br /> <span data-ttu-id="97348-117">票證逾時： %1 分鐘 %r</span><span class="sxs-lookup"><span data-stu-id="97348-117">Ticket time-out: %1 minutes%r</span></span><br /><br /> <span data-ttu-id="97348-118">最小票證逾時： 1 分鐘 %r</span><span class="sxs-lookup"><span data-stu-id="97348-118">Minimum ticket time-out: 1 minute%r</span></span><br /><br /> <span data-ttu-id="97348-119">最大票證逾時： %2 分鐘 %r</span><span class="sxs-lookup"><span data-stu-id="97348-119">Maximum ticket time-out: %2 minutes%r</span></span><br /><br /> <span data-ttu-id="97348-120">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="97348-120">Error Code: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="97348-121">說明</span><span class="sxs-lookup"><span data-stu-id="97348-121">Explanation</span></span>  
 <span data-ttu-id="97348-122">指定票證逾時值無效。</span><span class="sxs-lookup"><span data-stu-id="97348-122">The ticket time-out value specified is not valid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="97348-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="97348-123">User Action</span></span>  
 <span data-ttu-id="97348-124">您可以使用所提供的警告訊息中的資訊來修正值。</span><span class="sxs-lookup"><span data-stu-id="97348-124">Use the information supplied in the warning message to fix the value.</span></span>