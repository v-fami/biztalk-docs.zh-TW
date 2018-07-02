---
title: 單一登入： 事件 10515 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41edc008-b6d3-401d-97af-80b36ab0ba55
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1c3d7498bcd6a045936103d682d3643761a182c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980815"
---
# <a name="single-sign-on-event-10515"></a><span data-ttu-id="b1c55-102">單一登入： 事件 10515</span><span class="sxs-lookup"><span data-stu-id="b1c55-102">Single Sign-On: Event 10515</span></span>
## <a name="details"></a><span data-ttu-id="b1c55-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b1c55-103">Details</span></span>  
  
|                 |                                                                               |
|-----------------|-------------------------------------------------------------------------------|
|  <span data-ttu-id="b1c55-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b1c55-104">Product Name</span></span>   |                           <span data-ttu-id="b1c55-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b1c55-105">Enterprise Single Sign-On</span></span>                           |
| <span data-ttu-id="b1c55-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b1c55-106">Product Version</span></span> |          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]           |
|    <span data-ttu-id="b1c55-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b1c55-107">Event ID</span></span>     |                                     <span data-ttu-id="b1c55-108">10515</span><span class="sxs-lookup"><span data-stu-id="b1c55-108">10515</span></span>                                     |
|  <span data-ttu-id="b1c55-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b1c55-109">Event Source</span></span>   |                                    <span data-ttu-id="b1c55-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b1c55-110">ENTSSO</span></span>                                     |
|    <span data-ttu-id="b1c55-111">元件</span><span class="sxs-lookup"><span data-stu-id="b1c55-111">Component</span></span>    |                                      <span data-ttu-id="b1c55-112">N\A</span><span class="sxs-lookup"><span data-stu-id="b1c55-112">N\A</span></span>                                      |
|  <span data-ttu-id="b1c55-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b1c55-113">Symbolic Name</span></span>  |                            <span data-ttu-id="b1c55-114">SSO_ERROR_POLL_DATABASE</span><span class="sxs-lookup"><span data-stu-id="b1c55-114">SSO_ERROR_POLL_DATABASE</span></span>                            |
|  <span data-ttu-id="b1c55-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b1c55-115">Message Text</span></span>   | <span data-ttu-id="b1c55-116">失去與 SSO 資料庫的連絡。</span><span class="sxs-lookup"><span data-stu-id="b1c55-116">Lost contact with the SSO database.</span></span> <span data-ttu-id="b1c55-117">請檢查 SSO 資料庫是否可用。</span><span class="sxs-lookup"><span data-stu-id="b1c55-117">Check that the SSO database is available.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="b1c55-118">說明</span><span class="sxs-lookup"><span data-stu-id="b1c55-118">Explanation</span></span>  
 <span data-ttu-id="b1c55-119">這個錯誤事件表示 SSO 服務已失去與 SSO 資料庫的聯繫。</span><span class="sxs-lookup"><span data-stu-id="b1c55-119">This Error event indicates that the SSO Service has lost contact with the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b1c55-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b1c55-120">User Action</span></span>  
 <span data-ttu-id="b1c55-121">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="b1c55-121">To resolve this error, do one or more of the following:</span></span>  
  
- <span data-ttu-id="b1c55-122">確認 SQL Server (MSSQLSERVER) 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="b1c55-122">Verify that the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
- <span data-ttu-id="b1c55-123">請確認網路連線到 SQL Server 的遠端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b1c55-123">Verify network connectivity to SQL Server if on a remote server.</span></span>  
  
  <span data-ttu-id="b1c55-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="b1c55-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
- [<span data-ttu-id="b1c55-125">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b1c55-125">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
- [<span data-ttu-id="b1c55-126">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="b1c55-126">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
- [<span data-ttu-id="b1c55-127">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="b1c55-127">Configuring SSO</span></span>](../core/configuring-sso.md)  
  
  <span data-ttu-id="b1c55-128">另請參閱 SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="b1c55-128">See also SQL Server Books Online</span></span>