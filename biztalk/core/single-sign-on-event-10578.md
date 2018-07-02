---
title: 單一登入： 事件 10578 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4693bc25-d4d5-4cc7-b9bd-42d3471b2b0c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6ffb086106f8aa73c268cf3938be28e46b49354
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982639"
---
# <a name="single-sign-on-event-10578"></a><span data-ttu-id="2d5f7-102">單一登入： 事件 10578</span><span class="sxs-lookup"><span data-stu-id="2d5f7-102">Single Sign-On: Event 10578</span></span>
## <a name="details"></a><span data-ttu-id="2d5f7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d5f7-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2d5f7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2d5f7-104">Product Name</span></span>   |                                                                                             <span data-ttu-id="2d5f7-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2d5f7-105">Enterprise Single Sign-On</span></span>                                                                                             |
| <span data-ttu-id="2d5f7-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2d5f7-106">Product Version</span></span> |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    <span data-ttu-id="2d5f7-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2d5f7-107">Event ID</span></span>     |                                                                                                       <span data-ttu-id="2d5f7-108">10578</span><span class="sxs-lookup"><span data-stu-id="2d5f7-108">10578</span></span>                                                                                                       |
|  <span data-ttu-id="2d5f7-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2d5f7-109">Event Source</span></span>   |                                                                                                      <span data-ttu-id="2d5f7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2d5f7-110">ENTSSO</span></span>                                                                                                       |
|    <span data-ttu-id="2d5f7-111">元件</span><span class="sxs-lookup"><span data-stu-id="2d5f7-111">Component</span></span>    |                                                                                                        <span data-ttu-id="2d5f7-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2d5f7-112">N/A</span></span>                                                                                                        |
|  <span data-ttu-id="2d5f7-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2d5f7-113">Symbolic Name</span></span>  |                                                                                          <span data-ttu-id="2d5f7-114">SSO_INFO_CHANGED_APP_USER_GROUP</span><span class="sxs-lookup"><span data-stu-id="2d5f7-114">SSO_INFO_CHANGED_APP_USER_GROUP</span></span>                                                                                          |
|  <span data-ttu-id="2d5f7-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2d5f7-115">Message Text</span></span>   | <span data-ttu-id="2d5f7-116">更新應用程式使用者 account.%r</span><span class="sxs-lookup"><span data-stu-id="2d5f7-116">Updated Application Users account.%r</span></span><br /><br /> <span data-ttu-id="2d5f7-117">新的應用程式使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2d5f7-117">New Application Users: %1%r</span></span><br /><br /> <span data-ttu-id="2d5f7-118">舊的應用程式使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2d5f7-118">Old Application Users: %2%r</span></span><br /><br /> <span data-ttu-id="2d5f7-119">追蹤識別碼: %3 %r</span><span class="sxs-lookup"><span data-stu-id="2d5f7-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="2d5f7-120">用戶端使用者: %4 %r</span><span class="sxs-lookup"><span data-stu-id="2d5f7-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="2d5f7-121">應用程式名稱： %5</span><span class="sxs-lookup"><span data-stu-id="2d5f7-121">Application Name: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="2d5f7-122">說明</span><span class="sxs-lookup"><span data-stu-id="2d5f7-122">Explanation</span></span>  
 <span data-ttu-id="2d5f7-123">這是參考用訊息，而且可用於追蹤重要的安全性相關事件，會進行 SSO 系統中。</span><span class="sxs-lookup"><span data-stu-id="2d5f7-123">This is an informational message and can be useful for tracking significant security-related events that occurr within the SSO system.</span></span> <span data-ttu-id="2d5f7-124">此訊息表示已更新的更新的應用程式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2d5f7-124">This message states that the Updated Application Users account has been updated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d5f7-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2d5f7-125">User Action</span></span>  
 <span data-ttu-id="2d5f7-126">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="2d5f7-126">No user action is required.</span></span>