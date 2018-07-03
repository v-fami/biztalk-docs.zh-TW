---
title: 單一登入： 事件 10673 |Microsoft Docs
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
ms.openlocfilehash: 3fb923d1e137a00eed4ba87e65df71b226287aa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975135"
---
# <a name="single-sign-on-event-10673"></a><span data-ttu-id="d6762-102">單一登入： 事件 10673</span><span class="sxs-lookup"><span data-stu-id="d6762-102">Single Sign-On: Event 10673</span></span>
## <a name="details"></a><span data-ttu-id="d6762-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d6762-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d6762-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d6762-104">Product Name</span></span>   |                                                                                                                                                                        <span data-ttu-id="d6762-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d6762-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                         |
| <span data-ttu-id="d6762-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d6762-106">Product Version</span></span> |                                                                                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                        |
|    <span data-ttu-id="d6762-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d6762-107">Event ID</span></span>     |                                                                                                                                                                                  <span data-ttu-id="d6762-108">10673</span><span class="sxs-lookup"><span data-stu-id="d6762-108">10673</span></span>                                                                                                                                                                                   |
|  <span data-ttu-id="d6762-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d6762-109">Event Source</span></span>   |                                                                                                                                                                                  <span data-ttu-id="d6762-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d6762-110">ENTSSO</span></span>                                                                                                                                                                                  |
|    <span data-ttu-id="d6762-111">元件</span><span class="sxs-lookup"><span data-stu-id="d6762-111">Component</span></span>    |                                                                                                                                                                                   <span data-ttu-id="d6762-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d6762-112">N\A</span></span>                                                                                                                                                                                    |
|  <span data-ttu-id="d6762-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d6762-113">Symbolic Name</span></span>  |                                                                                                                                                                <span data-ttu-id="d6762-114">SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="d6762-114">SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span></span>                                                                                                                                                                 |
|  <span data-ttu-id="d6762-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d6762-115">Message Text</span></span>   | <span data-ttu-id="d6762-116">外部密碼變更將造成一個以上的 Windows account.%r 變更</span><span class="sxs-lookup"><span data-stu-id="d6762-116">An external password change will cause changes to more than one Windows account.%r</span></span><br /><br /> <span data-ttu-id="d6762-117">這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="d6762-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="d6762-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="d6762-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="d6762-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="d6762-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="d6762-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="d6762-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="d6762-121">Windows 帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="d6762-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="d6762-122">Windows 帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="d6762-122">Windows Account 2: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="d6762-123">說明</span><span class="sxs-lookup"><span data-stu-id="d6762-123">Explanation</span></span>  
 <span data-ttu-id="d6762-124">這個資訊事件表示外部密碼變更會導致多個 Windows 帳戶的變更。</span><span class="sxs-lookup"><span data-stu-id="d6762-124">This Information event indicates that an external password change will cause changes to more than one Windows account.</span></span>  

## <a name="user-action"></a><span data-ttu-id="d6762-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d6762-125">User Action</span></span>  

-   <span data-ttu-id="d6762-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d6762-126">No user action is necessary.</span></span>  

## <a name="more-info"></a><span data-ttu-id="d6762-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="d6762-127">More info</span></span>

- [<span data-ttu-id="d6762-128">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="d6762-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  

- <span data-ttu-id="d6762-129">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d6762-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="d6762-130">密碼同步</span><span class="sxs-lookup"><span data-stu-id="d6762-130">Password Synchronization</span></span>](../core/password-synchronization2.md)
