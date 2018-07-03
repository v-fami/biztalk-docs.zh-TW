---
title: 單一登入： 事件 10590 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd8c3804-5c84-403f-881b-e4b101c2323a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc2ac48ecf1279c1a8347e8f1ab3bcd1367854ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006767"
---
# <a name="single-sign-on-event-10590"></a><span data-ttu-id="3a70f-102">單一登入： 事件 10590</span><span class="sxs-lookup"><span data-stu-id="3a70f-102">Single Sign-On: Event 10590</span></span>
## <a name="details"></a><span data-ttu-id="3a70f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a70f-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="3a70f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a70f-104">Product Name</span></span>   |                 <span data-ttu-id="3a70f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3a70f-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="3a70f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3a70f-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="3a70f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a70f-107">Event ID</span></span>     |                           <span data-ttu-id="3a70f-108">10590</span><span class="sxs-lookup"><span data-stu-id="3a70f-108">10590</span></span>                            |
|  <span data-ttu-id="3a70f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a70f-109">Event Source</span></span>   |                           <span data-ttu-id="3a70f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3a70f-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="3a70f-111">元件</span><span class="sxs-lookup"><span data-stu-id="3a70f-111">Component</span></span>    |                            <span data-ttu-id="3a70f-112">不適用</span><span class="sxs-lookup"><span data-stu-id="3a70f-112">N/A</span></span>                             |
|  <span data-ttu-id="3a70f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a70f-113">Symbolic Name</span></span>  |                  <span data-ttu-id="3a70f-114">SSO_ERROR_OUT_OF_SERVICE</span><span class="sxs-lookup"><span data-stu-id="3a70f-114">SSO_ERROR_OUT_OF_SERVICE</span></span>                  |
|  <span data-ttu-id="3a70f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a70f-115">Message Text</span></span>   |        <span data-ttu-id="3a70f-116">企業單一登入 」 即將離線。</span><span class="sxs-lookup"><span data-stu-id="3a70f-116">Enterprise Single Sign-On is going offline.</span></span>         |
  
## <a name="explanation"></a><span data-ttu-id="3a70f-117">說明</span><span class="sxs-lookup"><span data-stu-id="3a70f-117">Explanation</span></span>  
 <span data-ttu-id="3a70f-118">ENTSSO 系統通常會檢查 ENTSSO 資料庫的更新每隔 30 秒。</span><span class="sxs-lookup"><span data-stu-id="3a70f-118">The ENTSSO system usually checks for updates on the ENTSSO database every 30 seconds.</span></span> <span data-ttu-id="3a70f-119">如果資料庫無法使用指定的時間 （通常為 5 分鐘），系統本身會離線。</span><span class="sxs-lookup"><span data-stu-id="3a70f-119">If the database is unavailable for a specified time (usually five minutes), the system itself goes offline.</span></span> <span data-ttu-id="3a70f-120">處於此狀態，系統不會回應要求的認證。</span><span class="sxs-lookup"><span data-stu-id="3a70f-120">In this state the system will not respond to requests for credentials.</span></span> <span data-ttu-id="3a70f-121">仍可能會有一些離線和系統管理活動。</span><span class="sxs-lookup"><span data-stu-id="3a70f-121">Some offline and administrative activities are still possible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a70f-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a70f-122">User Action</span></span>  
 <span data-ttu-id="3a70f-123">此錯誤表示 ENTSSO 資料庫已離線。</span><span class="sxs-lookup"><span data-stu-id="3a70f-123">This error indicates that the ENTSSO database is offline.</span></span> <span data-ttu-id="3a70f-124">您應該立即調查。</span><span class="sxs-lookup"><span data-stu-id="3a70f-124">You should investigate immediately.</span></span>