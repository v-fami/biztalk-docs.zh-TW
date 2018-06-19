---
title: 單一登入： 事件 10513 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3306223-111f-4abf-ae65-be839b355216
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1be7ae463dbb1ee9651f69f231614cc11db5f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270342"
---
# <a name="single-sign-on-event-10513"></a><span data-ttu-id="8385d-102">單一登入： 事件 10513</span><span class="sxs-lookup"><span data-stu-id="8385d-102">Single Sign-On: Event 10513</span></span>
## <a name="details"></a><span data-ttu-id="8385d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8385d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8385d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8385d-104">Product Name</span></span>|<span data-ttu-id="8385d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8385d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8385d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8385d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8385d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8385d-107">Event ID</span></span>|<span data-ttu-id="8385d-108">10513</span><span class="sxs-lookup"><span data-stu-id="8385d-108">10513</span></span>|  
|<span data-ttu-id="8385d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8385d-109">Event Source</span></span>|<span data-ttu-id="8385d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8385d-110">ENTSSO</span></span>|  
|<span data-ttu-id="8385d-111">元件</span><span class="sxs-lookup"><span data-stu-id="8385d-111">Component</span></span>|<span data-ttu-id="8385d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8385d-112">N\A</span></span>|  
|<span data-ttu-id="8385d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8385d-113">Symbolic Name</span></span>|<span data-ttu-id="8385d-114">SSO_ERROR_DB_FIRST_ACCESS</span><span class="sxs-lookup"><span data-stu-id="8385d-114">SSO_ERROR_DB_FIRST_ACCESS</span></span>|  
|<span data-ttu-id="8385d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8385d-115">Message Text</span></span>|<span data-ttu-id="8385d-116">無法聯繫 SSO 資料庫: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8385d-116">Failed to contact the SSO database: %1%r</span></span><br /><br /> <span data-ttu-id="8385d-117">%2 %r</span><span class="sxs-lookup"><span data-stu-id="8385d-117">%2%r</span></span><br /><br /> <span data-ttu-id="8385d-118">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="8385d-118">Error code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8385d-119">說明</span><span class="sxs-lookup"><span data-stu-id="8385d-119">Explanation</span></span>  
 <span data-ttu-id="8385d-120">這個錯誤事件表示 SSO 服務無法在啟動時連絡 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8385d-120">This Error event indicates that the SSO Service cannot connect to the SSO database when it starts.</span></span> <span data-ttu-id="8385d-121">事件訊息包含資料來源名稱 (DSN) 字串，指出指定的 SQL Server 和資料庫名稱，以及 SQL 連接程式庫傳回的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8385d-121">The event message contains the Data Source Name (DSN) string indicating the specified SQL Server and database names as well as the error message that was returned from the SQL connection libraries.</span></span>  
  
 <span data-ttu-id="8385d-122">SSO 服務啟動時，它會嘗試連接到 SSO 資料庫使用登錄中指定的 SQL Server 與 SSO 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8385d-122">When the SSO Service starts, it will attempt to connect to the SSO database using the SQL Server and SSO database names specified in the registry.</span></span> <span data-ttu-id="8385d-123">SSO 服務會嘗試連線 12 倍，等候 5 秒，每個失敗的嘗試，總共有 1 分鐘之間。</span><span class="sxs-lookup"><span data-stu-id="8385d-123">The SSO Service will attempt to connect 12 times, waiting 5 seconds between each failed attempt, for a total of 1 minute.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8385d-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8385d-124">User Action</span></span>  
 <span data-ttu-id="8385d-125">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="8385d-125">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="8385d-126">確認 SQL Server (MSSQLSERVER) 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="8385d-126">Verify the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="8385d-127">確認錯誤訊息中指出的資料來源名稱 (DSN) 字串正確，且包含正確的 SQL Server 和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8385d-127">Verify the Data Source Name (DSN) string indicated in the error message is correct and contains the correct SQL Server and database names.</span></span>  
  
 <span data-ttu-id="8385d-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="8385d-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8385d-129">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8385d-129">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="8385d-130">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="8385d-130">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="8385d-131">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="8385d-131">Configuring SSO</span></span>](../core/configuring-sso.md)  
  
-   <span data-ttu-id="8385d-132">SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="8385d-132">SQL Server Books Online</span></span>