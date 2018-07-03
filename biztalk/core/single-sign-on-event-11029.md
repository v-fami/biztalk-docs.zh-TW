---
title: 單一登入： 事件 11029 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd7cb5b0-532c-4f50-849d-4d1644026463
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2825c8a3563ca9912f176bc3dc45c5350750fbd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992501"
---
# <a name="single-sign-on-event-11029"></a><span data-ttu-id="b9c4d-102">單一登入： 事件 11029</span><span class="sxs-lookup"><span data-stu-id="b9c4d-102">Single Sign-On: Event 11029</span></span>
## <a name="details"></a><span data-ttu-id="b9c4d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9c4d-103">Details</span></span>  
  
|                 |                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="b9c4d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b9c4d-104">Product Name</span></span>   |                                              <span data-ttu-id="b9c4d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b9c4d-105">Enterprise Single Sign-On</span></span>                                               |
| <span data-ttu-id="b9c4d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b9c4d-106">Product Version</span></span> |                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                              |
|    <span data-ttu-id="b9c4d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b9c4d-107">Event ID</span></span>     |                                                        <span data-ttu-id="b9c4d-108">11029</span><span class="sxs-lookup"><span data-stu-id="b9c4d-108">11029</span></span>                                                         |
|  <span data-ttu-id="b9c4d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b9c4d-109">Event Source</span></span>   |                                                        <span data-ttu-id="b9c4d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b9c4d-110">ENTSSO</span></span>                                                        |
|    <span data-ttu-id="b9c4d-111">元件</span><span class="sxs-lookup"><span data-stu-id="b9c4d-111">Component</span></span>    |                                                         <span data-ttu-id="b9c4d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="b9c4d-112">N/A</span></span>                                                          |
|  <span data-ttu-id="b9c4d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b9c4d-113">Symbolic Name</span></span>  |                                               <span data-ttu-id="b9c4d-114">SSO_INFO_CASE_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="b9c4d-114">SSO_INFO_CASE_SENSITIVE</span></span>                                                |
|  <span data-ttu-id="b9c4d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b9c4d-115">Message Text</span></span>   | <span data-ttu-id="b9c4d-116">SSO 資料庫區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-116">The SSO database is case sensitive.</span></span> <span data-ttu-id="b9c4d-117">SSO 伺服器會在區分大小寫的模式中執行。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-117">The SSO server will run in case sensitive mode.</span></span> <span data-ttu-id="b9c4d-118">請參閱 details.%r 文件</span><span class="sxs-lookup"><span data-stu-id="b9c4d-118">See documentation for details.%r</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="b9c4d-119">說明</span><span class="sxs-lookup"><span data-stu-id="b9c4d-119">Explanation</span></span>  
 <span data-ttu-id="b9c4d-120">根據預設 SSO 伺服器不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-120">By default the SSO server is not case-sensitive.</span></span> <span data-ttu-id="b9c4d-121">不過，SQL Server SSO 資料庫具有已設定為區分大小寫，因此 SSO 伺服器也會執行區分大小寫的模式。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-121">However, the SQL Server SSO database has been configured to be case-sensitive, so the SSO Server will also run in case sensitive mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9c4d-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b9c4d-122">User Action</span></span>  
 <span data-ttu-id="b9c4d-123">請注意這個時指定應用程式名稱和外部帳戶名稱，因為它們現在是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-123">Be aware of this when specifying application names and external account names as they are now case-sensitive.</span></span> <span data-ttu-id="b9c4d-124">如需詳細資訊，請參閱 < [SSO 伺服器](../core/sso-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c4d-124">For more information, see [SSO Server](../core/sso-server.md).</span></span>