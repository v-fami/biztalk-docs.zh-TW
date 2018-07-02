---
title: 單一登入： 事件 10575 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a691812-433c-42ba-a225-873ad1bfee99
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93ae664da9f4f9a36c82cdec2dea0edeeac6bdeb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968559"
---
# <a name="single-sign-on-event-10575"></a><span data-ttu-id="7b5b1-102">單一登入： 事件 10575</span><span class="sxs-lookup"><span data-stu-id="7b5b1-102">Single Sign-On: Event 10575</span></span>
## <a name="details"></a><span data-ttu-id="7b5b1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b5b1-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="7b5b1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7b5b1-104">Product Name</span></span>   |                                                                                     <span data-ttu-id="7b5b1-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="7b5b1-105">Enterprise Single Sign-On</span></span>                                                                                     |
| <span data-ttu-id="7b5b1-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="7b5b1-106">Product Version</span></span> |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    <span data-ttu-id="7b5b1-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7b5b1-107">Event ID</span></span>     |                                                                                               <span data-ttu-id="7b5b1-108">10575</span><span class="sxs-lookup"><span data-stu-id="7b5b1-108">10575</span></span>                                                                                               |
|  <span data-ttu-id="7b5b1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7b5b1-109">Event Source</span></span>   |                                                                                              <span data-ttu-id="7b5b1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7b5b1-110">ENTSSO</span></span>                                                                                               |
|    <span data-ttu-id="7b5b1-111">元件</span><span class="sxs-lookup"><span data-stu-id="7b5b1-111">Component</span></span>    |                                                                                                <span data-ttu-id="7b5b1-112">不適用</span><span class="sxs-lookup"><span data-stu-id="7b5b1-112">N/A</span></span>                                                                                                |
|  <span data-ttu-id="7b5b1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7b5b1-113">Symbolic Name</span></span>  |                                                                                  <span data-ttu-id="7b5b1-114">SSO_INFO_CHANGED_SECRET_SERVER</span><span class="sxs-lookup"><span data-stu-id="7b5b1-114">SSO_INFO_CHANGED_SECRET_SERVER</span></span>                                                                                   |
|  <span data-ttu-id="7b5b1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7b5b1-115">Message Text</span></span>   | <span data-ttu-id="7b5b1-116">更新祕密伺服器 name.%r</span><span class="sxs-lookup"><span data-stu-id="7b5b1-116">Updated secret server name.%r</span></span><br /><br /> <span data-ttu-id="7b5b1-117">新的祕密伺服器: %1 %r</span><span class="sxs-lookup"><span data-stu-id="7b5b1-117">New Secret Server: %1%r</span></span><br /><br /> <span data-ttu-id="7b5b1-118">舊的祕密伺服器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="7b5b1-118">Old Secret Server: %2%r</span></span><br /><br /> <span data-ttu-id="7b5b1-119">追蹤識別碼: %3 %r</span><span class="sxs-lookup"><span data-stu-id="7b5b1-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="7b5b1-120">用戶端電腦: %4 %r</span><span class="sxs-lookup"><span data-stu-id="7b5b1-120">Client Computer: %4%r</span></span><br /><br /> <span data-ttu-id="7b5b1-121">用戶端使用者： %5</span><span class="sxs-lookup"><span data-stu-id="7b5b1-121">Client User: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="7b5b1-122">說明</span><span class="sxs-lookup"><span data-stu-id="7b5b1-122">Explanation</span></span>  
 <span data-ttu-id="7b5b1-123">這是參考用訊息，而且可用於追蹤重要的安全性相關事件，會進行 SSO 系統中。</span><span class="sxs-lookup"><span data-stu-id="7b5b1-123">This is an informational message and can be useful for tracking significant security-related events that occurr within the SSO system.</span></span> <span data-ttu-id="7b5b1-124">此訊息表示已更新的祕密伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="7b5b1-124">This message states that the secret server name has been updated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b5b1-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7b5b1-125">User Action</span></span>  
 <span data-ttu-id="7b5b1-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7b5b1-126">No user action is required.</span></span>