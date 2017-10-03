---
title: "單一登入： 事件 10672 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2422c7d-51bc-4f12-8830-193d71d2bce9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03eb6a72be53f928c8c173ac84556f709df0723c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10672"></a><span data-ttu-id="548e2-102">單一登入： 事件 10672</span><span class="sxs-lookup"><span data-stu-id="548e2-102">Single Sign-On: Event 10672</span></span>
## <a name="details"></a><span data-ttu-id="548e2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="548e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="548e2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="548e2-104">Product Name</span></span>|<span data-ttu-id="548e2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="548e2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="548e2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="548e2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="548e2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="548e2-107">Event ID</span></span>|<span data-ttu-id="548e2-108">10672</span><span class="sxs-lookup"><span data-stu-id="548e2-108">10672</span></span>|  
|<span data-ttu-id="548e2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="548e2-109">Event Source</span></span>|<span data-ttu-id="548e2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="548e2-110">ENTSSO</span></span>|  
|<span data-ttu-id="548e2-111">元件</span><span class="sxs-lookup"><span data-stu-id="548e2-111">Component</span></span>|<span data-ttu-id="548e2-112">N\A</span><span class="sxs-lookup"><span data-stu-id="548e2-112">N\A</span></span>|  
|<span data-ttu-id="548e2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="548e2-113">Symbolic Name</span></span>|<span data-ttu-id="548e2-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="548e2-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="548e2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="548e2-115">Message Text</span></span>|<span data-ttu-id="548e2-116">Windows 密碼變更可能已造成一個以上的帳戶的變更上相同的外部 system.%r</span><span class="sxs-lookup"><span data-stu-id="548e2-116">A Windows password change would have caused changes to more than one account on the same external system.%r</span></span><br /><br /> <span data-ttu-id="548e2-117">這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="548e2-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="548e2-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="548e2-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="548e2-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="548e2-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="548e2-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="548e2-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="548e2-121">外部帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="548e2-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="548e2-122">外部帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="548e2-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="548e2-123">說明</span><span class="sxs-lookup"><span data-stu-id="548e2-123">Explanation</span></span>  
 <span data-ttu-id="548e2-124">這個警告事件表示，Windows 密碼變更可能已造成一個以上的帳戶的變更相同外部系統上。</span><span class="sxs-lookup"><span data-stu-id="548e2-124">This Warning event indicates that a Windows password change would have caused changes to more than one account on the same external system.</span></span> <span data-ttu-id="548e2-125">因為配接器組態不會讓它無法的這項變更。</span><span class="sxs-lookup"><span data-stu-id="548e2-125">This change was prevented because the adapter configuration would not allow it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="548e2-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="548e2-126">User Action</span></span>  
  
-   <span data-ttu-id="548e2-127">使用 SSO 管理工具來設定**允許對應衝突**密碼同步配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="548e2-127">Use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="548e2-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="548e2-128">More info</span></span>
  
-   <span data-ttu-id="548e2-129">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="548e2-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="548e2-130">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="548e2-130">Password Synchronization</span></span>](../core/password-synchronization2.md)