---
title: "單一登入： 事件 10679 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 645f2b74-2cbe-4c6a-b0f5-7e31f93f88c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f612f3cf6540340124a3f11ed99fe736df65296b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10679"></a><span data-ttu-id="ed554-102">單一登入： 事件 10679</span><span class="sxs-lookup"><span data-stu-id="ed554-102">Single Sign-On: Event 10679</span></span>
## <a name="details"></a><span data-ttu-id="ed554-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ed554-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed554-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ed554-104">Product Name</span></span>|<span data-ttu-id="ed554-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ed554-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ed554-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ed554-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ed554-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ed554-107">Event ID</span></span>|<span data-ttu-id="ed554-108">10679</span><span class="sxs-lookup"><span data-stu-id="ed554-108">10679</span></span>|  
|<span data-ttu-id="ed554-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ed554-109">Event Source</span></span>|<span data-ttu-id="ed554-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ed554-110">ENTSSO</span></span>|  
|<span data-ttu-id="ed554-111">元件</span><span class="sxs-lookup"><span data-stu-id="ed554-111">Component</span></span>|<span data-ttu-id="ed554-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ed554-112">N\A</span></span>|  
|<span data-ttu-id="ed554-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ed554-113">Symbolic Name</span></span>|<span data-ttu-id="ed554-114">SSO_WARN_PS_MAPPING_DISABLED</span><span class="sxs-lookup"><span data-stu-id="ed554-114">SSO_WARN_PS_MAPPING_DISABLED</span></span>|  
|<span data-ttu-id="ed554-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ed554-115">Message Text</span></span>|<span data-ttu-id="ed554-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="ed554-116">External password change.</span></span> <span data-ttu-id="ed554-117">因為對應 disabled.%r 密碼未變更外部帳戶</span><span class="sxs-lookup"><span data-stu-id="ed554-117">The password was not changed for the external account because the mapping is disabled.%r</span></span><br /><br /> <span data-ttu-id="ed554-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ed554-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="ed554-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ed554-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="ed554-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="ed554-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="ed554-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="ed554-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ed554-122">說明</span><span class="sxs-lookup"><span data-stu-id="ed554-122">Explanation</span></span>  
 <span data-ttu-id="ed554-123">這個警告事件表示，密碼未變更外部帳戶因為已停用對應。</span><span class="sxs-lookup"><span data-stu-id="ed554-123">This Warning event indicates that the password was not changed for the external account because the mapping is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ed554-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ed554-124">User Action</span></span>  
 <span data-ttu-id="ed554-125">若要解決這個警告，請執行下列：</span><span class="sxs-lookup"><span data-stu-id="ed554-125">To resolve this warning do the following:</span></span>  
  
-   <span data-ttu-id="ed554-126">若要啟用對應，此配接器使用 SSO 管理工具。</span><span class="sxs-lookup"><span data-stu-id="ed554-126">Use the SSO administration tools to enable mapping for this adapter.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="ed554-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="ed554-127">More info</span></span>
  
-   [<span data-ttu-id="ed554-128">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="ed554-128">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="ed554-129">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="ed554-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>