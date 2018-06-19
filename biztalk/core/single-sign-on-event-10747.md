---
title: 單一登入： 事件 10747 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63ae1ab4-0f4e-45a7-83c1-31b8037e4dd7
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e26960bcba1ff3c640c88cd3fb6f5e4bd7dfceb6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270894"
---
# <a name="single-sign-on-event-10747"></a><span data-ttu-id="8a2a0-102">單一登入： 事件 10747</span><span class="sxs-lookup"><span data-stu-id="8a2a0-102">Single Sign-On: Event 10747</span></span>
## <a name="details"></a><span data-ttu-id="8a2a0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a2a0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a2a0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8a2a0-104">Product Name</span></span>|<span data-ttu-id="8a2a0-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8a2a0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8a2a0-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8a2a0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8a2a0-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8a2a0-107">Event ID</span></span>|<span data-ttu-id="8a2a0-108">10747</span><span class="sxs-lookup"><span data-stu-id="8a2a0-108">10747</span></span>|  
|<span data-ttu-id="8a2a0-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8a2a0-109">Event Source</span></span>|<span data-ttu-id="8a2a0-110">N\A</span><span class="sxs-lookup"><span data-stu-id="8a2a0-110">N\A</span></span>|  
|<span data-ttu-id="8a2a0-111">元件</span><span class="sxs-lookup"><span data-stu-id="8a2a0-111">Component</span></span>|<span data-ttu-id="8a2a0-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8a2a0-112">N\A</span></span>|  
|<span data-ttu-id="8a2a0-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8a2a0-113">Symbolic Name</span></span>|<span data-ttu-id="8a2a0-114">SSO_ERROR_UNKNOWN_NOTIFICATION</span><span class="sxs-lookup"><span data-stu-id="8a2a0-114">SSO_ERROR_UNKNOWN_NOTIFICATION</span></span>|  
|<span data-ttu-id="8a2a0-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8a2a0-115">Message Text</span></span>|<span data-ttu-id="8a2a0-116">收到未知的通知類型。 received.%r</span><span class="sxs-lookup"><span data-stu-id="8a2a0-116">An unknown notification type was received.%r</span></span><br /><br /> <span data-ttu-id="8a2a0-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8a2a0-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="8a2a0-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8a2a0-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="8a2a0-119">通知類型： %3</span><span class="sxs-lookup"><span data-stu-id="8a2a0-119">Notification Type: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a2a0-120">說明</span><span class="sxs-lookup"><span data-stu-id="8a2a0-120">Explanation</span></span>  
 <span data-ttu-id="8a2a0-121">這個錯誤事件表示 SSO 服務偵測到無效的通知類型發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a2a0-121">This Error event indicates that an internal error with an invalid notification type was detected by the SSO service.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a2a0-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8a2a0-122">User Action</span></span>  
 <span data-ttu-id="8a2a0-123">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8a2a0-123">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="8a2a0-124">檢查系統和應用程式事件記錄檔相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="8a2a0-124">Check the system and application event logs for associated events.</span></span>  
  
 <span data-ttu-id="8a2a0-125">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="8a2a0-125">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="8a2a0-126">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="8a2a0-126">Using SSO</span></span>](../core/using-sso.md)