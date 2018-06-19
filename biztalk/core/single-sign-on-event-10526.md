---
title: 單一登入： 事件 10526 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69a78b337cfdf90ea35367bd8fb20569e56717b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270606"
---
# <a name="single-sign-on-event-10526"></a><span data-ttu-id="9ad61-102">單一登入： 事件 10526</span><span class="sxs-lookup"><span data-stu-id="9ad61-102">Single Sign-On: Event 10526</span></span>
## <a name="details"></a><span data-ttu-id="9ad61-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9ad61-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ad61-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9ad61-104">Product Name</span></span>|<span data-ttu-id="9ad61-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9ad61-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9ad61-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="9ad61-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9ad61-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9ad61-107">Event ID</span></span>|<span data-ttu-id="9ad61-108">10526</span><span class="sxs-lookup"><span data-stu-id="9ad61-108">10526</span></span>|  
|<span data-ttu-id="9ad61-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9ad61-109">Event Source</span></span>|<span data-ttu-id="9ad61-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9ad61-110">ENTSSO</span></span>|  
|<span data-ttu-id="9ad61-111">元件</span><span class="sxs-lookup"><span data-stu-id="9ad61-111">Component</span></span>|<span data-ttu-id="9ad61-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9ad61-112">N\A</span></span>|  
|<span data-ttu-id="9ad61-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9ad61-113">Symbolic Name</span></span>|<span data-ttu-id="9ad61-114">SSO_ERROR_GENERATE_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="9ad61-114">SSO_ERROR_GENERATE_SECRET_FAILED</span></span>|  
|<span data-ttu-id="9ad61-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9ad61-115">Message Text</span></span>|<span data-ttu-id="9ad61-116">無法產生新的主要密碼。%r</span><span class="sxs-lookup"><span data-stu-id="9ad61-116">Failed to generate a new master secret.%r</span></span><br /><br /> <span data-ttu-id="9ad61-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="9ad61-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="9ad61-118">用戶端電腦：%2%r</span><span class="sxs-lookup"><span data-stu-id="9ad61-118">Client Computer:%2%r</span></span><br /><br /> <span data-ttu-id="9ad61-119">追蹤識別碼: %3 %r</span><span class="sxs-lookup"><span data-stu-id="9ad61-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="9ad61-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="9ad61-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ad61-121">說明</span><span class="sxs-lookup"><span data-stu-id="9ad61-121">Explanation</span></span>  
 <span data-ttu-id="9ad61-122">這個錯誤事件表示，產生新的主要密碼的使用者嘗試已經失敗。</span><span class="sxs-lookup"><span data-stu-id="9ad61-122">This Error event indicates that a user attempt to generate a new master secret has failed.</span></span> <span data-ttu-id="9ad61-123">這可能是因為權限 （您必須是 SSO 系統管理員，以產生主要密碼） 的問題，或可能有問題的主要密碼寫入備份檔案。</span><span class="sxs-lookup"><span data-stu-id="9ad61-123">This might be due to permissions issues (you must be an SSO Administrator to generate the master secret) or possibly there were problems writing the master secret to the backup file.</span></span> <span data-ttu-id="9ad61-124">在這些情況下應該會有相關的郵件應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="9ad61-124">In these cases there should be related messages in the Application event log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ad61-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9ad61-125">User Action</span></span>  
 <span data-ttu-id="9ad61-126">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="9ad61-126">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="9ad61-127">請檢查應用程式事件記錄檔，取得相關聯的事件或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9ad61-127">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="9ad61-128">檢查您有適當的 SSO 系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="9ad61-128">Check that you have the appropriate SSO Administrator permissions.</span></span>  
  
 <span data-ttu-id="9ad61-129">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="9ad61-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9ad61-130">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="9ad61-130">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="9ad61-131">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="9ad61-131">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)