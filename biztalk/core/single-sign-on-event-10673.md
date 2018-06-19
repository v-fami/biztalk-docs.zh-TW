---
title: 單一登入： 事件 10673 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa1d572a-1e9f-496e-a219-852e7d9228d5
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8068d7ec43cc07dfd76b21dc749ca062226e49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271390"
---
# <a name="single-sign-on-event-10673"></a><span data-ttu-id="601c6-102">單一登入： 事件 10673</span><span class="sxs-lookup"><span data-stu-id="601c6-102">Single Sign-On: Event 10673</span></span>
## <a name="details"></a><span data-ttu-id="601c6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="601c6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="601c6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="601c6-104">Product Name</span></span>|<span data-ttu-id="601c6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="601c6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="601c6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="601c6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="601c6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="601c6-107">Event ID</span></span>|<span data-ttu-id="601c6-108">10673</span><span class="sxs-lookup"><span data-stu-id="601c6-108">10673</span></span>|  
|<span data-ttu-id="601c6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="601c6-109">Event Source</span></span>|<span data-ttu-id="601c6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="601c6-110">ENTSSO</span></span>|  
|<span data-ttu-id="601c6-111">元件</span><span class="sxs-lookup"><span data-stu-id="601c6-111">Component</span></span>|<span data-ttu-id="601c6-112">N\A</span><span class="sxs-lookup"><span data-stu-id="601c6-112">N\A</span></span>|  
|<span data-ttu-id="601c6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="601c6-113">Symbolic Name</span></span>|<span data-ttu-id="601c6-114">SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="601c6-114">SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="601c6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="601c6-115">Message Text</span></span>|<span data-ttu-id="601c6-116">外部密碼變更將造成一個以上的 Windows account.%r 變更</span><span class="sxs-lookup"><span data-stu-id="601c6-116">An external password change will cause changes to more than one Windows account.%r</span></span><br /><br /> <span data-ttu-id="601c6-117">這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="601c6-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="601c6-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="601c6-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="601c6-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="601c6-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="601c6-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="601c6-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="601c6-121">Windows 帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="601c6-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="601c6-122">Windows 帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="601c6-122">Windows Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="601c6-123">說明</span><span class="sxs-lookup"><span data-stu-id="601c6-123">Explanation</span></span>  
 <span data-ttu-id="601c6-124">這個資訊事件表示外部密碼變更將會導致一個以上的 Windows 帳戶的變更。</span><span class="sxs-lookup"><span data-stu-id="601c6-124">This Information event indicates that an external password change will cause changes to more than one Windows account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="601c6-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="601c6-125">User Action</span></span>  
  
-   <span data-ttu-id="601c6-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="601c6-126">No user action is necessary.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="601c6-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="601c6-127">More info</span></span>
  
-   [<span data-ttu-id="601c6-128">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="601c6-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   <span data-ttu-id="601c6-129">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="601c6-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="601c6-130">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="601c6-130">Password Synchronization</span></span>](../core/password-synchronization2.md)