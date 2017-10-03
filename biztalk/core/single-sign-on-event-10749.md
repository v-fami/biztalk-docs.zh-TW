---
title: "單一登入： 事件 10749 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 864c887cb6c115a2f766f9c06cbaa292fdbeace2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10749"></a><span data-ttu-id="a8315-102">單一登入： 事件 10749</span><span class="sxs-lookup"><span data-stu-id="a8315-102">Single Sign-On: Event 10749</span></span>
## <a name="details"></a><span data-ttu-id="a8315-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a8315-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8315-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a8315-104">Product Name</span></span>|<span data-ttu-id="a8315-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a8315-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a8315-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a8315-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a8315-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a8315-107">Event ID</span></span>|<span data-ttu-id="a8315-108">10749</span><span class="sxs-lookup"><span data-stu-id="a8315-108">10749</span></span>|  
|<span data-ttu-id="a8315-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a8315-109">Event Source</span></span>|<span data-ttu-id="a8315-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a8315-110">ENTSSO</span></span>|  
|<span data-ttu-id="a8315-111">元件</span><span class="sxs-lookup"><span data-stu-id="a8315-111">Component</span></span>|<span data-ttu-id="a8315-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a8315-112">N\A</span></span>|  
|<span data-ttu-id="a8315-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a8315-113">Symbolic Name</span></span>|<span data-ttu-id="a8315-114">SSO_WARN_PS_CLIENT_PING</span><span class="sxs-lookup"><span data-stu-id="a8315-114">SSO_WARN_PS_CLIENT_PING</span></span>|  
|<span data-ttu-id="a8315-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a8315-115">Message Text</span></span>|<span data-ttu-id="a8315-116">無法連絡目的地 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8315-116">Could not contact the destination SSO server.</span></span><br /><br /> <span data-ttu-id="a8315-117">請檢查 SSO 服務正在該伺服器上，且它可以 contacted.%r</span><span class="sxs-lookup"><span data-stu-id="a8315-117">Check that the SSO service is running on that server and that it can be contacted.%r</span></span><br /><br /> <span data-ttu-id="a8315-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a8315-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a8315-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a8315-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="a8315-120">SSO 伺服器名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="a8315-120">SSO Server Name: %3%r</span></span><br /><br /> <span data-ttu-id="a8315-121">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="a8315-121">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8315-122">說明</span><span class="sxs-lookup"><span data-stu-id="a8315-122">Explanation</span></span>  
 <span data-ttu-id="a8315-123">這個警告事件表示 SSO 密碼同步無法連絡指定的目的地 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8315-123">This Warning event indicates that SSO Password Sync could not contact the specified destination SSO server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8315-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a8315-124">User Action</span></span>  
 <span data-ttu-id="a8315-125">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="a8315-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="a8315-126">使用 ENTSSO 伺服器嵌入式管理單元來檢查的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8315-126">Use the ENTSSO Servers Snap-In to check the server.</span></span>  
  
-   <span data-ttu-id="a8315-127">如果未執行，請啟動 「 企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="a8315-127">Start the Enterprise Single Sign-On Service if it is not running.</span></span>  
  
-   <span data-ttu-id="a8315-128">請檢查目的地 SSO 伺服器的網路連線。</span><span class="sxs-lookup"><span data-stu-id="a8315-128">Check the network connection to the destination SSO server.</span></span>  
  
-   <span data-ttu-id="a8315-129">請檢查目的地 SSO 伺服器上的防火牆。</span><span class="sxs-lookup"><span data-stu-id="a8315-129">Check firewall on the destination SSO Server.</span></span>  
  
 <span data-ttu-id="a8315-130">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="a8315-130">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="a8315-131">如何使用伺服器嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="a8315-131">How to Use the Servers Snap-in</span></span>](../core/how-to-use-the-servers-snap-in.md)