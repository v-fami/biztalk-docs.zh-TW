---
title: 單一登入： 事件 10610 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c90855c1f136dc8204afe718ea4456c834ab667
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024404"
---
# <a name="single-sign-on-event-10610"></a><span data-ttu-id="6e945-102">單一登入： 事件 10610</span><span class="sxs-lookup"><span data-stu-id="6e945-102">Single Sign-On: Event 10610</span></span>
## <a name="details"></a><span data-ttu-id="6e945-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6e945-103">Details</span></span>  
  
|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="6e945-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6e945-104">Product Name</span></span>   |                                                       <span data-ttu-id="6e945-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6e945-105">Enterprise Single Sign-On</span></span>                                                       |
| <span data-ttu-id="6e945-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="6e945-106">Product Version</span></span> |                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    <span data-ttu-id="6e945-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6e945-107">Event ID</span></span>     |                                                                 <span data-ttu-id="6e945-108">10610</span><span class="sxs-lookup"><span data-stu-id="6e945-108">10610</span></span>                                                                 |
|  <span data-ttu-id="6e945-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6e945-109">Event Source</span></span>   |                                                                <span data-ttu-id="6e945-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6e945-110">ENTSSO</span></span>                                                                 |
|    <span data-ttu-id="6e945-111">元件</span><span class="sxs-lookup"><span data-stu-id="6e945-111">Component</span></span>    |                                                                  <span data-ttu-id="6e945-112">不適用</span><span class="sxs-lookup"><span data-stu-id="6e945-112">N/A</span></span>                                                                  |
|  <span data-ttu-id="6e945-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6e945-113">Symbolic Name</span></span>  |                                                      <span data-ttu-id="6e945-114">SSO_WARN_CRED_CACHE_FAILED</span><span class="sxs-lookup"><span data-stu-id="6e945-114">SSO_WARN_CRED_CACHE_FAILED</span></span>                                                       |
|  <span data-ttu-id="6e945-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6e945-115">Message Text</span></span>   | <span data-ttu-id="6e945-116">認證快取發生未預期的錯誤，並且已關閉。</span><span class="sxs-lookup"><span data-stu-id="6e945-116">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="6e945-117">這可能會影響 performance.%r</span><span class="sxs-lookup"><span data-stu-id="6e945-117">This may affect performance.%r</span></span><br /><br /> <span data-ttu-id="6e945-118">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="6e945-118">Error Code: %1</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="6e945-119">說明</span><span class="sxs-lookup"><span data-stu-id="6e945-119">Explanation</span></span>  
 <span data-ttu-id="6e945-120">認證快取發生未預期的錯誤，並且已關閉。</span><span class="sxs-lookup"><span data-stu-id="6e945-120">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="6e945-121">雖然這可能會影響效能，它不會影響功能。</span><span class="sxs-lookup"><span data-stu-id="6e945-121">While this may affect performance, it will not affect functionality.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e945-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6e945-122">User Action</span></span>  
 <span data-ttu-id="6e945-123">重新啟動 SSO 服務時很方便。</span><span class="sxs-lookup"><span data-stu-id="6e945-123">Restart the SSO service when convenient.</span></span>