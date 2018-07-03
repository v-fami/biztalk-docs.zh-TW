---
title: 單一登入： 事件 10596 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a1e565ca3b96663e0ece5a2cf68c02d3258ac5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008791"
---
# <a name="single-sign-on-event-10596"></a><span data-ttu-id="fba69-102">單一登入： 事件 10596</span><span class="sxs-lookup"><span data-stu-id="fba69-102">Single Sign-On: Event 10596</span></span>
## <a name="details"></a><span data-ttu-id="fba69-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fba69-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="fba69-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fba69-104">Product Name</span></span>   |                                                                                                         <span data-ttu-id="fba69-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fba69-105">Enterprise Single Sign-On</span></span>                                                                                                          |
| <span data-ttu-id="fba69-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fba69-106">Product Version</span></span> |                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    <span data-ttu-id="fba69-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fba69-107">Event ID</span></span>     |                                                                                                                   <span data-ttu-id="fba69-108">10596</span><span class="sxs-lookup"><span data-stu-id="fba69-108">10596</span></span>                                                                                                                    |
|  <span data-ttu-id="fba69-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fba69-109">Event Source</span></span>   |                                                                                                                   <span data-ttu-id="fba69-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fba69-110">ENTSSO</span></span>                                                                                                                   |
|    <span data-ttu-id="fba69-111">元件</span><span class="sxs-lookup"><span data-stu-id="fba69-111">Component</span></span>    |                                                                                                                    <span data-ttu-id="fba69-112">不適用</span><span class="sxs-lookup"><span data-stu-id="fba69-112">N/A</span></span>                                                                                                                     |
|  <span data-ttu-id="fba69-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fba69-113">Symbolic Name</span></span>  |                                                                                                     <span data-ttu-id="fba69-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="fba69-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span></span>                                                                                                      |
|  <span data-ttu-id="fba69-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fba69-115">Message Text</span></span>   | <span data-ttu-id="fba69-116">無法贖回票證，因為的使用者票證的核發對象不是應用程式使用者 account.%r 的成員</span><span class="sxs-lookup"><span data-stu-id="fba69-116">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="fba69-117">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fba69-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="fba69-118">票證核發對: %2 %r</span><span class="sxs-lookup"><span data-stu-id="fba69-118">Ticket Issued For: %2%r</span></span><br /><br /> <span data-ttu-id="fba69-119">應用程式使用者： %3</span><span class="sxs-lookup"><span data-stu-id="fba69-119">Application Users: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="fba69-120">說明</span><span class="sxs-lookup"><span data-stu-id="fba69-120">Explanation</span></span>  
 <span data-ttu-id="fba69-121">因為票證的核發對象的使用者不是應用程式使用者帳戶的成員，就無法贖回票證。</span><span class="sxs-lookup"><span data-stu-id="fba69-121">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fba69-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fba69-122">User Action</span></span>  
 <span data-ttu-id="fba69-123">請重新發出的票證應用程式使用者帳戶隸屬的使用者。</span><span class="sxs-lookup"><span data-stu-id="fba69-123">Reissue the ticket to a user who is a member of the Application Users account.</span></span>