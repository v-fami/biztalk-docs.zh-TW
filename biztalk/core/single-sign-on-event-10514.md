---
title: 單一登入： 事件 10514 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fff4fbbb9b5c4d32968312b0f585ffbf2f5bb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995303"
---
# <a name="single-sign-on-event-10514"></a><span data-ttu-id="e0e00-102">單一登入： 事件 10514</span><span class="sxs-lookup"><span data-stu-id="e0e00-102">Single Sign-On: Event 10514</span></span>
## <a name="details"></a><span data-ttu-id="e0e00-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e0e00-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="e0e00-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e0e00-104">Product Name</span></span>   |                                                                                    <span data-ttu-id="e0e00-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e0e00-105">Enterprise Single Sign-On</span></span>                                                                                     |
| <span data-ttu-id="e0e00-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e0e00-106">Product Version</span></span> |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                    |
|    <span data-ttu-id="e0e00-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e0e00-107">Event ID</span></span>     |                                                                                              <span data-ttu-id="e0e00-108">10514</span><span class="sxs-lookup"><span data-stu-id="e0e00-108">10514</span></span>                                                                                               |
|  <span data-ttu-id="e0e00-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e0e00-109">Event Source</span></span>   |                                                                                              <span data-ttu-id="e0e00-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e0e00-110">ENTSSO</span></span>                                                                                              |
|    <span data-ttu-id="e0e00-111">元件</span><span class="sxs-lookup"><span data-stu-id="e0e00-111">Component</span></span>    |                                                                                               <span data-ttu-id="e0e00-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e0e00-112">N\A</span></span>                                                                                                |
|  <span data-ttu-id="e0e00-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e0e00-113">Symbolic Name</span></span>  |                                                                                       <span data-ttu-id="e0e00-114">SSO_ERROR_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="e0e00-114">SSO_ERROR_DB_ACCESS</span></span>                                                                                        |
|  <span data-ttu-id="e0e00-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e0e00-115">Message Text</span></span>   | <span data-ttu-id="e0e00-116">嘗試存取 SSO database.%r 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="e0e00-116">An error occurred while attempting to access the SSO database.%r</span></span><br /><br /> <span data-ttu-id="e0e00-117">函式: %1 %r</span><span class="sxs-lookup"><span data-stu-id="e0e00-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="e0e00-118">檔案: %2 %r</span><span class="sxs-lookup"><span data-stu-id="e0e00-118">File: %2%r</span></span><br /><br /> <span data-ttu-id="e0e00-119">%3.%r</span><span class="sxs-lookup"><span data-stu-id="e0e00-119">%3.%r</span></span><br /><br /> <span data-ttu-id="e0e00-120">SQL 錯誤碼: %4 %r</span><span class="sxs-lookup"><span data-stu-id="e0e00-120">SQL Error code: %4%r</span></span><br /><br /> <span data-ttu-id="e0e00-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="e0e00-121">Error code: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e0e00-122">說明</span><span class="sxs-lookup"><span data-stu-id="e0e00-122">Explanation</span></span>  
 <span data-ttu-id="e0e00-123">這個錯誤事件表示當您嘗試存取 SSO 資料庫時，已從 SQL Server 收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0e00-123">This Error event indicates that an error was received from SQL Server when attempting to access the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e0e00-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e0e00-124">User Action</span></span>  
 <span data-ttu-id="e0e00-125">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="e0e00-125">To resolve this error, do one or more of the following:</span></span>  
  
- <span data-ttu-id="e0e00-126">確認 SQL Server (MSSQLSERVER) 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="e0e00-126">Verify that the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
- <span data-ttu-id="e0e00-127">請檢查使用的事件和錯誤訊息中心，在 SQL Server 錯誤碼[ http://go.microsoft.com/fwlink/?LinkID=20869 ](http://go.microsoft.com/fwlink/?LinkID=20869)。</span><span class="sxs-lookup"><span data-stu-id="e0e00-127">Check the SQL Server error code using the Events and Errors Message Center at [http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869).</span></span>  
  
  <span data-ttu-id="e0e00-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="e0e00-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
- [<span data-ttu-id="e0e00-129">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e0e00-129">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
- [<span data-ttu-id="e0e00-130">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="e0e00-130">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
  <span data-ttu-id="e0e00-131">另請參閱 SQL Server 線上叢書。</span><span class="sxs-lookup"><span data-stu-id="e0e00-131">See also SQL Server Books Online.</span></span>