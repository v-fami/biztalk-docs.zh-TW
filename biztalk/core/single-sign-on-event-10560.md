---
title: "單一登入： 事件 10560 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8677a807-2973-4753-8816-c93c45697d92
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d630dccdd21aaade843d4aa8fd7026d05fd71da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10560"></a><span data-ttu-id="2db7f-102">單一登入： 事件 10560</span><span class="sxs-lookup"><span data-stu-id="2db7f-102">Single Sign-On: Event 10560</span></span>
## <a name="details"></a><span data-ttu-id="2db7f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2db7f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2db7f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2db7f-104">Product Name</span></span>|<span data-ttu-id="2db7f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2db7f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2db7f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2db7f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2db7f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2db7f-107">Event ID</span></span>|<span data-ttu-id="2db7f-108">10560</span><span class="sxs-lookup"><span data-stu-id="2db7f-108">10560</span></span>|  
|<span data-ttu-id="2db7f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2db7f-109">Event Source</span></span>|<span data-ttu-id="2db7f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2db7f-110">ENTSSO</span></span>|  
|<span data-ttu-id="2db7f-111">元件</span><span class="sxs-lookup"><span data-stu-id="2db7f-111">Component</span></span>|<span data-ttu-id="2db7f-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2db7f-112">N/A</span></span>|  
|<span data-ttu-id="2db7f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2db7f-113">Symbolic Name</span></span>|<span data-ttu-id="2db7f-114">SSO_ERROR_BACKUP_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="2db7f-114">SSO_ERROR_BACKUP_SECRET_FAILED</span></span>|  
|<span data-ttu-id="2db7f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2db7f-115">Message Text</span></span>|<span data-ttu-id="2db7f-116">無法備份主要 secrets.%r</span><span class="sxs-lookup"><span data-stu-id="2db7f-116">Failed to back up the master secrets.%r</span></span><br /><br /> <span data-ttu-id="2db7f-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2db7f-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="2db7f-118">目前的 MSID: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2db7f-118">Current MSID: %2%r</span></span><br /><br /> <span data-ttu-id="2db7f-119">之前的 MSID: %3 %r</span><span class="sxs-lookup"><span data-stu-id="2db7f-119">Previous MSID: %3%r</span></span><br /><br /> <span data-ttu-id="2db7f-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="2db7f-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="2db7f-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="2db7f-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2db7f-122">說明</span><span class="sxs-lookup"><span data-stu-id="2db7f-122">Explanation</span></span>  
 <span data-ttu-id="2db7f-123">嘗試備份主要密碼失敗。</span><span class="sxs-lookup"><span data-stu-id="2db7f-123">An attempt to back up the master secret has failed.</span></span> <span data-ttu-id="2db7f-124">使用者嘗試此備份可能已經不正確的權限、 路徑或目錄。</span><span class="sxs-lookup"><span data-stu-id="2db7f-124">The user attempting this backup may have had the wrong permissions, path, or directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2db7f-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2db7f-125">User Action</span></span>  
 <span data-ttu-id="2db7f-126">如需備份主要密碼資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="2db7f-126">For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>