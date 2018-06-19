---
title: 單一登入： 事件 10538 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1211ac33-9149-4dd3-85a2-d46eb24d1060
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac7e027c240091e6a1a67ff53a41a00afeef7288
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270182"
---
# <a name="single-sign-on-event-10538"></a><span data-ttu-id="54f4b-102">單一登入： 事件 10538</span><span class="sxs-lookup"><span data-stu-id="54f4b-102">Single Sign-On: Event 10538</span></span>
## <a name="details"></a><span data-ttu-id="54f4b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="54f4b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54f4b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="54f4b-104">Product Name</span></span>|<span data-ttu-id="54f4b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="54f4b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="54f4b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="54f4b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="54f4b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="54f4b-107">Event ID</span></span>|<span data-ttu-id="54f4b-108">10538</span><span class="sxs-lookup"><span data-stu-id="54f4b-108">10538</span></span>|  
|<span data-ttu-id="54f4b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="54f4b-109">Event Source</span></span>|<span data-ttu-id="54f4b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="54f4b-110">ENTSSO</span></span>|  
|<span data-ttu-id="54f4b-111">元件</span><span class="sxs-lookup"><span data-stu-id="54f4b-111">Component</span></span>|<span data-ttu-id="54f4b-112">CO</span><span class="sxs-lookup"><span data-stu-id="54f4b-112">CO</span></span>|  
|<span data-ttu-id="54f4b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="54f4b-113">Symbolic Name</span></span>|<span data-ttu-id="54f4b-114">SSO_WARN_APP_DISABLED</span><span class="sxs-lookup"><span data-stu-id="54f4b-114">SSO_WARN_APP_DISABLED</span></span>|  
|<span data-ttu-id="54f4b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="54f4b-115">Message Text</span></span>|<span data-ttu-id="54f4b-116">正在 disabled.%r 應用程式。</span><span class="sxs-lookup"><span data-stu-id="54f4b-116">The application is currently disabled.%r</span></span><br /><br /> <span data-ttu-id="54f4b-117">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="54f4b-117">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="54f4b-118">說明</span><span class="sxs-lookup"><span data-stu-id="54f4b-118">Explanation</span></span>  
 <span data-ttu-id="54f4b-119">這個警告事件表示，SSO 分支機構應用程式已停用的應用程式系統管理員。</span><span class="sxs-lookup"><span data-stu-id="54f4b-119">This Warning event indicates that the SSO affiliate application has been disabled by an Application Administrator.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="54f4b-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="54f4b-120">User Action</span></span>  
 <span data-ttu-id="54f4b-121">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="54f4b-121">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="54f4b-122">請連絡您的應用程式系統管理員，以便將 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="54f4b-122">Contact your Application Administrator to enable the SSO affiliate application.</span></span> <span data-ttu-id="54f4b-123">這可以使用 SSO 管理工具 （GUI 或命令列）。</span><span class="sxs-lookup"><span data-stu-id="54f4b-123">This can be done using the SSO administration tools (GUI or command line).</span></span>  
  
 <span data-ttu-id="54f4b-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="54f4b-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="54f4b-125">如何啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="54f4b-125">How to Enable an Affiliate Application</span></span>](../core/how-to-enable-an-affiliate-application.md)  
  
-   [<span data-ttu-id="54f4b-126">如何停用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="54f4b-126">How to Disable an Affiliate Application</span></span>](../core/how-to-disable-an-affiliate-application.md)