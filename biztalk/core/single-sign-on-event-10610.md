---
title: "單一登入： 事件 10610 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e4edc579c18147ad34234fbf268ec8d867c60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10610"></a><span data-ttu-id="2b988-102">單一登入： 事件 10610</span><span class="sxs-lookup"><span data-stu-id="2b988-102">Single Sign-On: Event 10610</span></span>
## <a name="details"></a><span data-ttu-id="2b988-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b988-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b988-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2b988-104">Product Name</span></span>|<span data-ttu-id="2b988-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2b988-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2b988-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2b988-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2b988-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2b988-107">Event ID</span></span>|<span data-ttu-id="2b988-108">10610</span><span class="sxs-lookup"><span data-stu-id="2b988-108">10610</span></span>|  
|<span data-ttu-id="2b988-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2b988-109">Event Source</span></span>|<span data-ttu-id="2b988-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2b988-110">ENTSSO</span></span>|  
|<span data-ttu-id="2b988-111">元件</span><span class="sxs-lookup"><span data-stu-id="2b988-111">Component</span></span>|<span data-ttu-id="2b988-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2b988-112">N/A</span></span>|  
|<span data-ttu-id="2b988-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2b988-113">Symbolic Name</span></span>|<span data-ttu-id="2b988-114">SSO_WARN_CRED_CACHE_FAILED</span><span class="sxs-lookup"><span data-stu-id="2b988-114">SSO_WARN_CRED_CACHE_FAILED</span></span>|  
|<span data-ttu-id="2b988-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2b988-115">Message Text</span></span>|<span data-ttu-id="2b988-116">認證快取發生未預期的錯誤，並且已關閉。</span><span class="sxs-lookup"><span data-stu-id="2b988-116">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="2b988-117">這可能會影響 performance.%r</span><span class="sxs-lookup"><span data-stu-id="2b988-117">This may affect performance.%r</span></span><br /><br /> <span data-ttu-id="2b988-118">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="2b988-118">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2b988-119">說明</span><span class="sxs-lookup"><span data-stu-id="2b988-119">Explanation</span></span>  
 <span data-ttu-id="2b988-120">認證快取發生未預期的錯誤，並且已關閉。</span><span class="sxs-lookup"><span data-stu-id="2b988-120">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="2b988-121">雖然這可能會影響效能，它不會影響功能。</span><span class="sxs-lookup"><span data-stu-id="2b988-121">While this may affect performance, it will not affect functionality.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2b988-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2b988-122">User Action</span></span>  
 <span data-ttu-id="2b988-123">重新啟動 SSO 服務時方便。</span><span class="sxs-lookup"><span data-stu-id="2b988-123">Restart the SSO service when convenient.</span></span>