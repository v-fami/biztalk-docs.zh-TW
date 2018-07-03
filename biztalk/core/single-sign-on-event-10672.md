---
title: 單一登入： 事件 10672 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2422c7d-51bc-4f12-8830-193d71d2bce9
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39a8dd5e65b513ceabf2c654dcb5cf083d6f1295
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000759"
---
# <a name="single-sign-on-event-10672"></a><span data-ttu-id="bec7e-102">單一登入： 事件 10672</span><span class="sxs-lookup"><span data-stu-id="bec7e-102">Single Sign-On: Event 10672</span></span>
## <a name="details"></a><span data-ttu-id="bec7e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bec7e-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="bec7e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bec7e-104">Product Name</span></span>   |                                                                                                                                                                                           <span data-ttu-id="bec7e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="bec7e-105">Enterprise Single Sign-On</span></span>                                                                                                                                                                                            |
| <span data-ttu-id="bec7e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="bec7e-106">Product Version</span></span> |                                                                                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                           |
|    <span data-ttu-id="bec7e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bec7e-107">Event ID</span></span>     |                                                                                                                                                                                                     <span data-ttu-id="bec7e-108">10672</span><span class="sxs-lookup"><span data-stu-id="bec7e-108">10672</span></span>                                                                                                                                                                                                      |
|  <span data-ttu-id="bec7e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="bec7e-109">Event Source</span></span>   |                                                                                                                                                                                                     <span data-ttu-id="bec7e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="bec7e-110">ENTSSO</span></span>                                                                                                                                                                                                     |
|    <span data-ttu-id="bec7e-111">元件</span><span class="sxs-lookup"><span data-stu-id="bec7e-111">Component</span></span>    |                                                                                                                                                                                                      <span data-ttu-id="bec7e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="bec7e-112">N\A</span></span>                                                                                                                                                                                                       |
|  <span data-ttu-id="bec7e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bec7e-113">Symbolic Name</span></span>  |                                                                                                                                                                                 <span data-ttu-id="bec7e-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="bec7e-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span></span>                                                                                                                                                                                 |
|  <span data-ttu-id="bec7e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bec7e-115">Message Text</span></span>   | <span data-ttu-id="bec7e-116">Windows 密碼變更可能已造成一個以上的帳戶的變更上相同的外部 system.%r</span><span class="sxs-lookup"><span data-stu-id="bec7e-116">A Windows password change would have caused changes to more than one account on the same external system.%r</span></span><br /><br /> <span data-ttu-id="bec7e-117">這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r</span><span class="sxs-lookup"><span data-stu-id="bec7e-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="bec7e-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="bec7e-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="bec7e-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="bec7e-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="bec7e-120">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="bec7e-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="bec7e-121">外部帳戶 1: %4 %r</span><span class="sxs-lookup"><span data-stu-id="bec7e-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="bec7e-122">外部帳戶 2: %5</span><span class="sxs-lookup"><span data-stu-id="bec7e-122">External Account 2: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="bec7e-123">說明</span><span class="sxs-lookup"><span data-stu-id="bec7e-123">Explanation</span></span>  
 <span data-ttu-id="bec7e-124">這個警告事件表示，Windows 密碼變更可能已造成一個以上的帳戶的變更相同的外部系統上。</span><span class="sxs-lookup"><span data-stu-id="bec7e-124">This Warning event indicates that a Windows password change would have caused changes to more than one account on the same external system.</span></span> <span data-ttu-id="bec7e-125">因為配接器組態不會讓它，因此已防止這項變更。</span><span class="sxs-lookup"><span data-stu-id="bec7e-125">This change was prevented because the adapter configuration would not allow it.</span></span>  

## <a name="user-action"></a><span data-ttu-id="bec7e-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bec7e-126">User Action</span></span>  

-   <span data-ttu-id="bec7e-127">使用 SSO 管理工具來設定**允許對應衝突**密碼同步配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="bec7e-127">Use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.</span></span>  

## <a name="more-info"></a><span data-ttu-id="bec7e-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="bec7e-128">More info</span></span>

- <span data-ttu-id="bec7e-129">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="bec7e-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>

- [<span data-ttu-id="bec7e-130">密碼同步</span><span class="sxs-lookup"><span data-stu-id="bec7e-130">Password Synchronization</span></span>](../core/password-synchronization2.md)
