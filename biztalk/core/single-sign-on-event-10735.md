---
title: 單一登入： 事件 10735 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31c791c6-1901-4441-b329-ed75833cb83e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94417860296cf01c2266a678832f8b02b9b51055
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271902"
---
# <a name="single-sign-on-event-10735"></a><span data-ttu-id="1714f-102">單一登入： 事件 10735</span><span class="sxs-lookup"><span data-stu-id="1714f-102">Single Sign-On: Event 10735</span></span>
## <a name="details"></a><span data-ttu-id="1714f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1714f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1714f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1714f-104">Product Name</span></span>|<span data-ttu-id="1714f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1714f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1714f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1714f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1714f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1714f-107">Event ID</span></span>|<span data-ttu-id="1714f-108">10735</span><span class="sxs-lookup"><span data-stu-id="1714f-108">10735</span></span>|  
|<span data-ttu-id="1714f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1714f-109">Event Source</span></span>|<span data-ttu-id="1714f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1714f-110">ENTSSO</span></span>|  
|<span data-ttu-id="1714f-111">元件</span><span class="sxs-lookup"><span data-stu-id="1714f-111">Component</span></span>|<span data-ttu-id="1714f-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1714f-112">N\A</span></span>|  
|<span data-ttu-id="1714f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1714f-113">Symbolic Name</span></span>|<span data-ttu-id="1714f-114">SSO_WARN_PS_APP_DISABLED</span><span class="sxs-lookup"><span data-stu-id="1714f-114">SSO_WARN_PS_APP_DISABLED</span></span>|  
|<span data-ttu-id="1714f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1714f-115">Message Text</span></span>|<span data-ttu-id="1714f-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="1714f-116">External password change.</span></span> <span data-ttu-id="1714f-117">因為應用程式 disabled.%r 密碼未變更外部帳戶</span><span class="sxs-lookup"><span data-stu-id="1714f-117">The password was not changed for the external account because the application is disabled.%r</span></span><br /><br /> <span data-ttu-id="1714f-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="1714f-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="1714f-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="1714f-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="1714f-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="1714f-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="1714f-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="1714f-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1714f-122">說明</span><span class="sxs-lookup"><span data-stu-id="1714f-122">Explanation</span></span>  
 <span data-ttu-id="1714f-123">這個警告事件表示，密碼未變更外部帳戶因為應用程式已停用。</span><span class="sxs-lookup"><span data-stu-id="1714f-123">This Warning event indicates that a password was not changed for the external account because the application is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1714f-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1714f-124">User Action</span></span>  
 <span data-ttu-id="1714f-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1714f-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="1714f-126">啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="1714f-126">Enable the affiliate application</span></span>  
  
 <span data-ttu-id="1714f-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="1714f-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="1714f-128">如何啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="1714f-128">How to Enable an Affiliate Application</span></span>](../core/how-to-enable-an-affiliate-application.md)  
  
-   [<span data-ttu-id="1714f-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="1714f-129">Password Synchronization</span></span>](../core/password-synchronization2.md)