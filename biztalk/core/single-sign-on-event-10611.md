---
title: "單一登入： 事件 10611 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3582ee070b960b7eb17facc8d48e0b3e11dc5b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10611"></a><span data-ttu-id="c82af-102">單一登入： 事件 10611</span><span class="sxs-lookup"><span data-stu-id="c82af-102">Single Sign-On: Event 10611</span></span>
## <a name="details"></a><span data-ttu-id="c82af-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c82af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c82af-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c82af-104">Product Name</span></span>|<span data-ttu-id="c82af-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c82af-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c82af-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c82af-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c82af-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c82af-107">Event ID</span></span>|<span data-ttu-id="c82af-108">10611</span><span class="sxs-lookup"><span data-stu-id="c82af-108">10611</span></span>|  
|<span data-ttu-id="c82af-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c82af-109">Event Source</span></span>|<span data-ttu-id="c82af-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c82af-110">ENTSSO</span></span>|  
|<span data-ttu-id="c82af-111">元件</span><span class="sxs-lookup"><span data-stu-id="c82af-111">Component</span></span>|<span data-ttu-id="c82af-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c82af-112">N/A</span></span>|  
|<span data-ttu-id="c82af-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c82af-113">Symbolic Name</span></span>|<span data-ttu-id="c82af-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span><span class="sxs-lookup"><span data-stu-id="c82af-114">SSO_INFO_SERVICE_STARTING_NO_SSL</span></span>|  
|<span data-ttu-id="c82af-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c82af-115">Message Text</span></span>|<span data-ttu-id="c82af-116">SSO 服務正在 starting.%r</span><span class="sxs-lookup"><span data-stu-id="c82af-116">The SSO service is starting.%r</span></span><br /><br /> <span data-ttu-id="c82af-117">電腦名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="c82af-117">Computer Name: %1%r</span></span><br /><br /> <span data-ttu-id="c82af-118">SQL Server 名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="c82af-118">SQL Server Name: %2%r</span></span><br /><br /> <span data-ttu-id="c82af-119">SSO 資料庫名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="c82af-119">SSO Database Name: %3%r</span></span><br /><br /> <span data-ttu-id="c82af-120">不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="c82af-120">Not using SSL.</span></span> <span data-ttu-id="c82af-121">有關如何保護 SQL Server 連接，請參閱文件以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c82af-121">See documentation for details on how to secure the SQL Server connection.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c82af-122">說明</span><span class="sxs-lookup"><span data-stu-id="c82af-122">Explanation</span></span>  
 <span data-ttu-id="c82af-123">ENTSSO 服務正在啟動而不需要使用安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="c82af-123">The ENTSSO Service is starting without using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="c82af-124">建議您從 SSO 服務保護您的連線，為 SQL。</span><span class="sxs-lookup"><span data-stu-id="c82af-124">It is recommended that you secure your connection from the SSO Service to SQL.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c82af-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c82af-125">User Action</span></span>  
 <span data-ttu-id="c82af-126">請參閱文件，網址[如何針對 SSO 啟用 SSL](../core/how-to-enable-ssl-for-sso.md)</span><span class="sxs-lookup"><span data-stu-id="c82af-126">See the documentation at [How to Enable SSL for SSO](../core/how-to-enable-ssl-for-sso.md)</span></span>  
  
 <span data-ttu-id="c82af-127">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="c82af-127">.</span></span>