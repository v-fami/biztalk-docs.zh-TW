---
title: 單一登入： 事件 10603 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5416ae8a2dcfdf5a3da6d8c1d00eb5a556fc3599
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970063"
---
# <a name="single-sign-on-event-10603"></a><span data-ttu-id="cd7a6-102">單一登入： 事件 10603</span><span class="sxs-lookup"><span data-stu-id="cd7a6-102">Single Sign-On: Event 10603</span></span>
## <a name="details"></a><span data-ttu-id="cd7a6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cd7a6-103">Details</span></span>  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="cd7a6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cd7a6-104">Product Name</span></span>   |                                                             <span data-ttu-id="cd7a6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="cd7a6-105">Enterprise Single Sign-On</span></span>                                                              |
| <span data-ttu-id="cd7a6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="cd7a6-106">Product Version</span></span> |                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                             |
|    <span data-ttu-id="cd7a6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cd7a6-107">Event ID</span></span>     |                                                                       <span data-ttu-id="cd7a6-108">10603</span><span class="sxs-lookup"><span data-stu-id="cd7a6-108">10603</span></span>                                                                        |
|  <span data-ttu-id="cd7a6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="cd7a6-109">Event Source</span></span>   |                                                                       <span data-ttu-id="cd7a6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cd7a6-110">ENTSSO</span></span>                                                                       |
|    <span data-ttu-id="cd7a6-111">元件</span><span class="sxs-lookup"><span data-stu-id="cd7a6-111">Component</span></span>    |                                                                        <span data-ttu-id="cd7a6-112">不適用</span><span class="sxs-lookup"><span data-stu-id="cd7a6-112">N/A</span></span>                                                                         |
|  <span data-ttu-id="cd7a6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cd7a6-113">Symbolic Name</span></span>  |                                                                 <span data-ttu-id="cd7a6-114">SSO_WARN_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="cd7a6-114">SSO_WARN_DB_ACCESS</span></span>                                                                 |
|  <span data-ttu-id="cd7a6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cd7a6-115">Message Text</span></span>   | <span data-ttu-id="cd7a6-116">無法存取 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cd7a6-116">Could not access the SSO database.</span></span> <span data-ttu-id="cd7a6-117">如果此狀況持續發生，SSO 服務將會移 offline.%r</span><span class="sxs-lookup"><span data-stu-id="cd7a6-117">If this condition persists, the SSO service will go offline.%r</span></span><br /><br /> <span data-ttu-id="cd7a6-118">%1.%r</span><span class="sxs-lookup"><span data-stu-id="cd7a6-118">%1.%r</span></span><br /><br /> <span data-ttu-id="cd7a6-119">SQL 錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="cd7a6-119">SQL Error code: %2</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="cd7a6-120">說明</span><span class="sxs-lookup"><span data-stu-id="cd7a6-120">Explanation</span></span>  
 <span data-ttu-id="cd7a6-121">無法使用 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cd7a6-121">The SSO database is unavailable.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd7a6-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cd7a6-122">User Action</span></span>  
 <span data-ttu-id="cd7a6-123">請檢查警告中所包含的 SQL 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cd7a6-123">Check the SQL error code contained in the warning.</span></span> <span data-ttu-id="cd7a6-124">這可能會提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="cd7a6-124">This may offer some guidance.</span></span> <span data-ttu-id="cd7a6-125">如果沒有，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="cd7a6-125">If not, contact Microsoft Product Support Services.</span></span>