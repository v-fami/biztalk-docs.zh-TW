---
title: "單一登入： 事件 10524 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55e26da3-f67f-4f87-92e5-2f8765b19989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c79da37aaa54f44daaa39048fcdf58e67064f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10524"></a><span data-ttu-id="186ec-102">單一登入： 事件 10524</span><span class="sxs-lookup"><span data-stu-id="186ec-102">Single Sign-On: Event 10524</span></span>
## <a name="details"></a><span data-ttu-id="186ec-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="186ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="186ec-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="186ec-104">Product Name</span></span>|<span data-ttu-id="186ec-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="186ec-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="186ec-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="186ec-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="186ec-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="186ec-107">Event ID</span></span>|<span data-ttu-id="186ec-108">10524</span><span class="sxs-lookup"><span data-stu-id="186ec-108">10524</span></span>|  
|<span data-ttu-id="186ec-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="186ec-109">Event Source</span></span>|<span data-ttu-id="186ec-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="186ec-110">ENTSSO</span></span>|  
|<span data-ttu-id="186ec-111">元件</span><span class="sxs-lookup"><span data-stu-id="186ec-111">Component</span></span>|<span data-ttu-id="186ec-112">N\A</span><span class="sxs-lookup"><span data-stu-id="186ec-112">N\A</span></span>|  
|<span data-ttu-id="186ec-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="186ec-113">Symbolic Name</span></span>|<span data-ttu-id="186ec-114">SSO_ERROR_RESTORE_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="186ec-114">SSO_ERROR_RESTORE_SECRET_FAILED</span></span>|  
|<span data-ttu-id="186ec-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="186ec-115">Message Text</span></span>|<span data-ttu-id="186ec-116">還原主要密碼失敗。%r</span><span class="sxs-lookup"><span data-stu-id="186ec-116">Failed to restore the master secrets.%r</span></span><br /><br /> <span data-ttu-id="186ec-117">檔案名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="186ec-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="186ec-118">目前的 MSID: %2 %r</span><span class="sxs-lookup"><span data-stu-id="186ec-118">Current MSID: %2%r</span></span><br /><br /> <span data-ttu-id="186ec-119">之前的 MSID: %3 %r</span><span class="sxs-lookup"><span data-stu-id="186ec-119">Previous MSID: %3%r</span></span><br /><br /> <span data-ttu-id="186ec-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="186ec-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="186ec-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="186ec-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="186ec-122">說明</span><span class="sxs-lookup"><span data-stu-id="186ec-122">Explanation</span></span>  
 <span data-ttu-id="186ec-123">這個錯誤事件表示從備份檔案還原主要密碼的使用者嘗試失敗。</span><span class="sxs-lookup"><span data-stu-id="186ec-123">This Error event indicates that a user attempt to restore the master secrets from a backup file failed.</span></span> <span data-ttu-id="186ec-124">這可能是因為權限 （您必須是 SSO 系統管理員還原主要密碼） 的問題或可能是因為備份檔案的檔案損毀。</span><span class="sxs-lookup"><span data-stu-id="186ec-124">This might be due to permissions issues (you must be an SSO Administrator to restore the master secret) or possibly due to file corruption of the backup file.</span></span> <span data-ttu-id="186ec-125">在這些情況下應該會有相關的郵件應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="186ec-125">In these cases there should be related messages in the Application event log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="186ec-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="186ec-126">User Action</span></span>  
 <span data-ttu-id="186ec-127">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="186ec-127">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="186ec-128">請檢查應用程式事件記錄檔，取得相關聯的事件或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="186ec-128">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="186ec-129">檢查您有適當的 SSO 系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="186ec-129">Check that you have the appropriate SSO Administrator permissions.</span></span>  
  
 <span data-ttu-id="186ec-130">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="186ec-130">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="186ec-131">如何還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="186ec-131">How to Restore the Master Secret</span></span>](../core/how-to-restore-the-master-secret.md)  
  
-   [<span data-ttu-id="186ec-132">如何備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="186ec-132">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="186ec-133">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="186ec-133">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)