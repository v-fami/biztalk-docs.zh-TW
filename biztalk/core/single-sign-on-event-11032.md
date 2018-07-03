---
title: 單一登入： 事件 11032 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d58cf9d-6806-4580-8014-7eff88d5cc5f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc69ecf447f0917f843a0f80a0a25b1ed0b6e0a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022044"
---
# <a name="single-sign-on-event-11032"></a><span data-ttu-id="50ef2-102">單一登入： 事件 11032</span><span class="sxs-lookup"><span data-stu-id="50ef2-102">Single Sign-On: Event 11032</span></span>
## <a name="details"></a><span data-ttu-id="50ef2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="50ef2-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="50ef2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="50ef2-104">Product Name</span></span>   |                                                                                                                            <span data-ttu-id="50ef2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="50ef2-105">Enterprise Single Sign-On</span></span>                                                                                                                             |
| <span data-ttu-id="50ef2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="50ef2-106">Product Version</span></span> |                                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                            |
|    <span data-ttu-id="50ef2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="50ef2-107">Event ID</span></span>     |                                                                                                                                      <span data-ttu-id="50ef2-108">11032</span><span class="sxs-lookup"><span data-stu-id="50ef2-108">11032</span></span>                                                                                                                                       |
|  <span data-ttu-id="50ef2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="50ef2-109">Event Source</span></span>   |                                                                                                                                      <span data-ttu-id="50ef2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="50ef2-110">ENTSSO</span></span>                                                                                                                                      |
|    <span data-ttu-id="50ef2-111">元件</span><span class="sxs-lookup"><span data-stu-id="50ef2-111">Component</span></span>    |                                                                                                                                       <span data-ttu-id="50ef2-112">不適用</span><span class="sxs-lookup"><span data-stu-id="50ef2-112">N/A</span></span>                                                                                                                                        |
|  <span data-ttu-id="50ef2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="50ef2-113">Symbolic Name</span></span>  |                                                                                                                     <span data-ttu-id="50ef2-114">SSO_INFO_PS_WIN_CHANGE_MAPPING_DISABLED</span><span class="sxs-lookup"><span data-stu-id="50ef2-114">SSO_INFO_PS_WIN_CHANGE_MAPPING_DISABLED</span></span>                                                                                                                      |
|  <span data-ttu-id="50ef2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="50ef2-115">Message Text</span></span>   | <span data-ttu-id="50ef2-116">Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="50ef2-116">Windows password change.</span></span> <span data-ttu-id="50ef2-117">已偵測到此 Windows 帳戶的對應，但忽略，因為它是 disabled.%r</span><span class="sxs-lookup"><span data-stu-id="50ef2-117">A mapping for this Windows account has been detected but ignored because it is disabled.%r</span></span><br /><br /> <span data-ttu-id="50ef2-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="50ef2-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="50ef2-119">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="50ef2-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="50ef2-120">應用程式: %3 %r</span><span class="sxs-lookup"><span data-stu-id="50ef2-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="50ef2-121">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="50ef2-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="50ef2-122">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="50ef2-122">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="50ef2-123">說明</span><span class="sxs-lookup"><span data-stu-id="50ef2-123">Explanation</span></span>  
 <span data-ttu-id="50ef2-124">已偵測到此 Windows 帳戶的對應，但忽略，因為它已停用。</span><span class="sxs-lookup"><span data-stu-id="50ef2-124">A mapping for this Windows account has been detected but ignored because it is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="50ef2-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="50ef2-125">User Action</span></span>  
  
-   <span data-ttu-id="50ef2-126">若要啟用對應，請參閱[如何啟用使用者對應](../core/how-to-enable-a-user-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="50ef2-126">To enable the mapping, see [How to Enable a User Mapping](../core/how-to-enable-a-user-mapping.md).</span></span>