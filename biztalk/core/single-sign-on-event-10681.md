---
title: 單一登入： 事件 10681 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd0f1b6c27f3e77220d4615da1c0b5bb343344de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22272038"
---
# <a name="single-sign-on-event-10681"></a><span data-ttu-id="dc3b0-102">單一登入： 事件 10681</span><span class="sxs-lookup"><span data-stu-id="dc3b0-102">Single Sign-On: Event 10681</span></span>
## <a name="details"></a><span data-ttu-id="dc3b0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dc3b0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc3b0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dc3b0-104">Product Name</span></span>|<span data-ttu-id="dc3b0-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="dc3b0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="dc3b0-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="dc3b0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="dc3b0-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dc3b0-107">Event ID</span></span>|<span data-ttu-id="dc3b0-108">10681</span><span class="sxs-lookup"><span data-stu-id="dc3b0-108">10681</span></span>|  
|<span data-ttu-id="dc3b0-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="dc3b0-109">Event Source</span></span>|<span data-ttu-id="dc3b0-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dc3b0-110">ENTSSO</span></span>|  
|<span data-ttu-id="dc3b0-111">元件</span><span class="sxs-lookup"><span data-stu-id="dc3b0-111">Component</span></span>|<span data-ttu-id="dc3b0-112">N\A</span><span class="sxs-lookup"><span data-stu-id="dc3b0-112">N\A</span></span>|  
|<span data-ttu-id="dc3b0-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dc3b0-113">Symbolic Name</span></span>|<span data-ttu-id="dc3b0-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span><span class="sxs-lookup"><span data-stu-id="dc3b0-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span></span>|  
|<span data-ttu-id="dc3b0-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dc3b0-115">Message Text</span></span>|<span data-ttu-id="dc3b0-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="dc3b0-116">External password change.</span></span> <span data-ttu-id="dc3b0-117">未變更 Windows 密碼，因為一或多個外部帳戶變更 failed.%r</span><span class="sxs-lookup"><span data-stu-id="dc3b0-117">The Windows password was not changed because one or more of the external account changes failed.%r</span></span><br /><br /> <span data-ttu-id="dc3b0-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="dc3b0-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="dc3b0-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="dc3b0-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="dc3b0-120">Windows 帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="dc3b0-120">Windows Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dc3b0-121">說明</span><span class="sxs-lookup"><span data-stu-id="dc3b0-121">Explanation</span></span>  
 <span data-ttu-id="dc3b0-122">這個警告事件表示，Windows 密碼未變更，因為一個或多個外部帳戶變更失敗。</span><span class="sxs-lookup"><span data-stu-id="dc3b0-122">This Warning event indicates that the Windows password was not changed because one or more of the external account changes failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dc3b0-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dc3b0-123">User Action</span></span>  
 <span data-ttu-id="dc3b0-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="dc3b0-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="dc3b0-125">請檢查系統及應用程式事件記錄檔的相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="dc3b0-125">Check the System and Application Event logs for associated events.</span></span>  
  
-   <span data-ttu-id="dc3b0-126">請確認介面卡設定使用 SSO 管理工具。</span><span class="sxs-lookup"><span data-stu-id="dc3b0-126">Verify adapter configuration using the SSO administration tools.</span></span>  
  
-   <span data-ttu-id="dc3b0-127">確認外部系統。</span><span class="sxs-lookup"><span data-stu-id="dc3b0-127">Verify external systems.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="dc3b0-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="dc3b0-128">More info</span></span>
  
-   [<span data-ttu-id="dc3b0-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="dc3b0-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="dc3b0-130">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="dc3b0-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>