---
title: 單一登入： 事件 10674 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad0c0d9e-1e6d-4c3e-86e0-9e336a18f3d6
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f67258bb1ee9118c6f462d0eded4b8f238707b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996127"
---
# <a name="single-sign-on-event-10674"></a><span data-ttu-id="3ac0d-102">單一登入： 事件 10674</span><span class="sxs-lookup"><span data-stu-id="3ac0d-102">Single Sign-On: Event 10674</span></span>
## <a name="details"></a><span data-ttu-id="3ac0d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3ac0d-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="3ac0d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3ac0d-104">Product Name</span></span>   |                                                                                                                                                                                  <span data-ttu-id="3ac0d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3ac0d-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                                  |
| <span data-ttu-id="3ac0d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3ac0d-106">Product Version</span></span> |                                                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                  |
|    <span data-ttu-id="3ac0d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3ac0d-107">Event ID</span></span>     |                                                                                                                                                                                            <span data-ttu-id="3ac0d-108">10674</span><span class="sxs-lookup"><span data-stu-id="3ac0d-108">10674</span></span>                                                                                                                                                                                            |
|  <span data-ttu-id="3ac0d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3ac0d-109">Event Source</span></span>   |                                                                                                                                                                                           <span data-ttu-id="3ac0d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3ac0d-110">ENTSSO</span></span>                                                                                                                                                                                            |
|    <span data-ttu-id="3ac0d-111">元件</span><span class="sxs-lookup"><span data-stu-id="3ac0d-111">Component</span></span>    |                                                                                                                                                                                             <span data-ttu-id="3ac0d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="3ac0d-112">N\A</span></span>                                                                                                                                                                                             |
|  <span data-ttu-id="3ac0d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3ac0d-113">Symbolic Name</span></span>  |                                                                                                                                                                        <span data-ttu-id="3ac0d-114">SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="3ac0d-114">SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED</span></span>                                                                                                                                                                        |
|  <span data-ttu-id="3ac0d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3ac0d-115">Message Text</span></span>   | <span data-ttu-id="3ac0d-116">外部密碼變更可能造成對多個 Windows 帳戶進行變更。%r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-116">An external password change would have caused changes to more than one Windows account.%r</span></span><br /><br /> <span data-ttu-id="3ac0d-117">這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="3ac0d-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="3ac0d-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="3ac0d-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="3ac0d-121">Windows 帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="3ac0d-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="3ac0d-122">Windows 帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="3ac0d-122">Windows Account 2: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="3ac0d-123">說明</span><span class="sxs-lookup"><span data-stu-id="3ac0d-123">Explanation</span></span>  
 <span data-ttu-id="3ac0d-124">這個警告事件表示外部密碼變更可能已造成一個以上的 Windows 帳戶的變更。</span><span class="sxs-lookup"><span data-stu-id="3ac0d-124">This Warning event indicates that an external password change would have caused changes to more than one Windows account.</span></span> <span data-ttu-id="3ac0d-125">因為配接器組態不會讓它，因此已防止這項變更。</span><span class="sxs-lookup"><span data-stu-id="3ac0d-125">This change was prevented because the adapter configuration would not allow it.</span></span>  

## <a name="user-action"></a><span data-ttu-id="3ac0d-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3ac0d-126">User Action</span></span>  
 <span data-ttu-id="3ac0d-127">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3ac0d-127">To resolve this error, do the following:</span></span>  

-   <span data-ttu-id="3ac0d-128">如果預期及允許對應衝突，會使用 SSO 管理工具來設定**允許對應衝突**密碼同步配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="3ac0d-128">If mapping conflicts are expected and allowed, use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.</span></span>  

## <a name="more-info"></a><span data-ttu-id="3ac0d-129">其他資訊</span><span class="sxs-lookup"><span data-stu-id="3ac0d-129">More info</span></span>

- <span data-ttu-id="3ac0d-130">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="3ac0d-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="3ac0d-131">密碼同步</span><span class="sxs-lookup"><span data-stu-id="3ac0d-131">Password Synchronization</span></span>](../core/password-synchronization2.md)
