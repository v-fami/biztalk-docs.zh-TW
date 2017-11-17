---
title: "單一登入： 事件 10514 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40077ead4157b4cc6c91a2c44b4a19569d76ebc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10514"></a><span data-ttu-id="a1dc4-102">單一登入： 事件 10514</span><span class="sxs-lookup"><span data-stu-id="a1dc4-102">Single Sign-On: Event 10514</span></span>
## <a name="details"></a><span data-ttu-id="a1dc4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1dc4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1dc4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a1dc4-104">Product Name</span></span>|<span data-ttu-id="a1dc4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a1dc4-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a1dc4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a1dc4-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a1dc4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a1dc4-107">Event ID</span></span>|<span data-ttu-id="a1dc4-108">10514</span><span class="sxs-lookup"><span data-stu-id="a1dc4-108">10514</span></span>|  
|<span data-ttu-id="a1dc4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a1dc4-109">Event Source</span></span>|<span data-ttu-id="a1dc4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a1dc4-110">ENTSSO</span></span>|  
|<span data-ttu-id="a1dc4-111">元件</span><span class="sxs-lookup"><span data-stu-id="a1dc4-111">Component</span></span>|<span data-ttu-id="a1dc4-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a1dc4-112">N\A</span></span>|  
|<span data-ttu-id="a1dc4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a1dc4-113">Symbolic Name</span></span>|<span data-ttu-id="a1dc4-114">SSO_ERROR_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="a1dc4-114">SSO_ERROR_DB_ACCESS</span></span>|  
|<span data-ttu-id="a1dc4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a1dc4-115">Message Text</span></span>|<span data-ttu-id="a1dc4-116">嘗試存取 SSO database.%r 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="a1dc4-116">An error occurred while attempting to access the SSO database.%r</span></span><br /><br /> <span data-ttu-id="a1dc4-117">函式: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a1dc4-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="a1dc4-118">檔案: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a1dc4-118">File: %2%r</span></span><br /><br /> <span data-ttu-id="a1dc4-119">%3.%r</span><span class="sxs-lookup"><span data-stu-id="a1dc4-119">%3.%r</span></span><br /><br /> <span data-ttu-id="a1dc4-120">SQL 錯誤碼: %4 %r</span><span class="sxs-lookup"><span data-stu-id="a1dc4-120">SQL Error code: %4%r</span></span><br /><br /> <span data-ttu-id="a1dc4-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="a1dc4-121">Error code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a1dc4-122">說明</span><span class="sxs-lookup"><span data-stu-id="a1dc4-122">Explanation</span></span>  
 <span data-ttu-id="a1dc4-123">這個錯誤事件表示當您嘗試存取 SSO 資料庫時，已從 SQL Server 收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1dc4-123">This Error event indicates that an error was received from SQL Server when attempting to access the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1dc4-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a1dc4-124">User Action</span></span>  
 <span data-ttu-id="a1dc4-125">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="a1dc4-125">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="a1dc4-126">確認 SQL Server (MSSQLSERVER) 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="a1dc4-126">Verify that the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="a1dc4-127">檢查 SQL Server 錯誤程式碼使用事件和錯誤訊息中心在[http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869)。</span><span class="sxs-lookup"><span data-stu-id="a1dc4-127">Check the SQL Server error code using the Events and Errors Message Center at [http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869).</span></span>  
  
 <span data-ttu-id="a1dc4-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="a1dc4-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="a1dc4-129">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a1dc4-129">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="a1dc4-130">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="a1dc4-130">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
 <span data-ttu-id="a1dc4-131">另請參閱 SQL Server 線上叢書。</span><span class="sxs-lookup"><span data-stu-id="a1dc4-131">See also SQL Server Books Online.</span></span>