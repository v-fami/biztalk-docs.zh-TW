---
title: 單一登入： 事件 10728 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5052d03713808754abf04e8c2ba1590800e6cf9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270750"
---
# <a name="single-sign-on-event-10728"></a><span data-ttu-id="fe952-102">單一登入： 事件 10728</span><span class="sxs-lookup"><span data-stu-id="fe952-102">Single Sign-On: Event 10728</span></span>
## <a name="details"></a><span data-ttu-id="fe952-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe952-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe952-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fe952-104">Product Name</span></span>|<span data-ttu-id="fe952-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fe952-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fe952-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fe952-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fe952-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fe952-107">Event ID</span></span>|<span data-ttu-id="fe952-108">10728</span><span class="sxs-lookup"><span data-stu-id="fe952-108">10728</span></span>|  
|<span data-ttu-id="fe952-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fe952-109">Event Source</span></span>|<span data-ttu-id="fe952-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fe952-110">ENTSSO</span></span>|  
|<span data-ttu-id="fe952-111">元件</span><span class="sxs-lookup"><span data-stu-id="fe952-111">Component</span></span>|<span data-ttu-id="fe952-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fe952-112">N\A</span></span>|  
|<span data-ttu-id="fe952-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fe952-113">Symbolic Name</span></span>|<span data-ttu-id="fe952-114">SSO_ERROR_VERSION</span><span class="sxs-lookup"><span data-stu-id="fe952-114">SSO_ERROR_VERSION</span></span>|  
|<span data-ttu-id="fe952-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fe952-115">Message Text</span></span>|<span data-ttu-id="fe952-116">這個版本的 SSO 伺服器與不相容的 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe952-116">This version of the SSO server is not compatible with the SSO database.</span></span> <span data-ttu-id="fe952-117">請升級您的主要密碼 server.%r</span><span class="sxs-lookup"><span data-stu-id="fe952-117">Please upgrade your master secret server.%r</span></span><br /><br /> <span data-ttu-id="fe952-118">SQL Server 名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fe952-118">SQL Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="fe952-119">SSO 資料庫名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="fe952-119">SSO Database Name: %2%r</span></span><br /><br /> <span data-ttu-id="fe952-120">SSO 資料庫版本: %3 %r</span><span class="sxs-lookup"><span data-stu-id="fe952-120">SSO Database Version: %3%r</span></span><br /><br /> <span data-ttu-id="fe952-121">必要版本： %4</span><span class="sxs-lookup"><span data-stu-id="fe952-121">Required Version: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe952-122">說明</span><span class="sxs-lookup"><span data-stu-id="fe952-122">Explanation</span></span>  
 <span data-ttu-id="fe952-123">這個錯誤事件表示 SSO 伺服器版本會比 （原先建立版） 還新的 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe952-123">This Error event indicates that the SSO server version is more recent than (the version that originally created) the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe952-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fe952-124">User Action</span></span>  
 <span data-ttu-id="fe952-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fe952-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="fe952-126">升級 SSO 主要密碼伺服器以符合此 SSO 伺服器目前的版本。</span><span class="sxs-lookup"><span data-stu-id="fe952-126">Upgrade the SSO master secret server to match the current version of this SSO server.</span></span> <span data-ttu-id="fe952-127">這將會升級 SSO 資料庫目前的版本。</span><span class="sxs-lookup"><span data-stu-id="fe952-127">This will upgrade the SSO database to the current version.</span></span>  
  
 <span data-ttu-id="fe952-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="fe952-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="fe952-129">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="fe952-129">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)