---
title: 單一登入： 事件 10671 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06c5564f-6412-4e83-9bec-03264e992ebe
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f321a971f89c535da26604c3e03a2b62ebf060e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000071"
---
# <a name="single-sign-on-event-10671"></a><span data-ttu-id="57508-102">單一登入： 事件 10671</span><span class="sxs-lookup"><span data-stu-id="57508-102">Single Sign-On: Event 10671</span></span>
## <a name="details"></a><span data-ttu-id="57508-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="57508-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="57508-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="57508-104">Product Name</span></span>   |                                                                                                                                                                                  <span data-ttu-id="57508-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="57508-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                                  |
| <span data-ttu-id="57508-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="57508-106">Product Version</span></span> |                                                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                  |
|    <span data-ttu-id="57508-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="57508-107">Event ID</span></span>     |                                                                                                                                                                                            <span data-ttu-id="57508-108">10671</span><span class="sxs-lookup"><span data-stu-id="57508-108">10671</span></span>                                                                                                                                                                                            |
|  <span data-ttu-id="57508-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="57508-109">Event Source</span></span>   |                                                                                                                                                                                           <span data-ttu-id="57508-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="57508-110">ENTSSO</span></span>                                                                                                                                                                                            |
|    <span data-ttu-id="57508-111">元件</span><span class="sxs-lookup"><span data-stu-id="57508-111">Component</span></span>    |                                                                                                                                                                                             <span data-ttu-id="57508-112">N\A</span><span class="sxs-lookup"><span data-stu-id="57508-112">N\A</span></span>                                                                                                                                                                                             |
|  <span data-ttu-id="57508-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="57508-113">Symbolic Name</span></span>  |                                                                                                                                                                         <span data-ttu-id="57508-114">SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="57508-114">SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span></span>                                                                                                                                                                          |
|  <span data-ttu-id="57508-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="57508-115">Message Text</span></span>   | <span data-ttu-id="57508-116">Windows 密碼變更將造成相同外部 system.%r 上的多個帳戶變更</span><span class="sxs-lookup"><span data-stu-id="57508-116">A Windows password change will cause changes to more than one account on the same external system.%r</span></span><br /><br /> <span data-ttu-id="57508-117">這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="57508-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="57508-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="57508-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="57508-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="57508-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="57508-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="57508-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="57508-121">外部帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="57508-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="57508-122">外部帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="57508-122">External Account 2: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="57508-123">說明</span><span class="sxs-lookup"><span data-stu-id="57508-123">Explanation</span></span>  
 <span data-ttu-id="57508-124">這個資訊事件表示 Windows 密碼變更會導致相同的外部系統上的多個帳戶的變更。</span><span class="sxs-lookup"><span data-stu-id="57508-124">This Information event indicates that a Windows password change will cause changes to more than one account on the same external system.</span></span>  

## <a name="user-action"></a><span data-ttu-id="57508-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="57508-125">User Action</span></span>  

-   <span data-ttu-id="57508-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="57508-126">No user action is necessary.</span></span>  

## <a name="more-info"></a><span data-ttu-id="57508-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="57508-127">More info</span></span>

- <span data-ttu-id="57508-128">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="57508-128">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="57508-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="57508-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
