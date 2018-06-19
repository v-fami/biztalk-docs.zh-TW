---
title: 單一登入： 事件 10596 |Microsoft 文件
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
ms.openlocfilehash: 051fdf627edc3f560a8d02026207dc2fe5bb3533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270142"
---
# <a name="single-sign-on-event-10596"></a><span data-ttu-id="b4689-102">單一登入： 事件 10596</span><span class="sxs-lookup"><span data-stu-id="b4689-102">Single Sign-On: Event 10596</span></span>
## <a name="details"></a><span data-ttu-id="b4689-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b4689-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4689-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b4689-104">Product Name</span></span>|<span data-ttu-id="b4689-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b4689-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b4689-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b4689-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b4689-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b4689-107">Event ID</span></span>|<span data-ttu-id="b4689-108">10596</span><span class="sxs-lookup"><span data-stu-id="b4689-108">10596</span></span>|  
|<span data-ttu-id="b4689-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b4689-109">Event Source</span></span>|<span data-ttu-id="b4689-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b4689-110">ENTSSO</span></span>|  
|<span data-ttu-id="b4689-111">元件</span><span class="sxs-lookup"><span data-stu-id="b4689-111">Component</span></span>|<span data-ttu-id="b4689-112">不適用</span><span class="sxs-lookup"><span data-stu-id="b4689-112">N/A</span></span>|  
|<span data-ttu-id="b4689-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b4689-113">Symbolic Name</span></span>|<span data-ttu-id="b4689-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="b4689-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span></span>|  
|<span data-ttu-id="b4689-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b4689-115">Message Text</span></span>|<span data-ttu-id="b4689-116">因為票證的核發對象的使用者不是應用程式使用者 account.%r 的成員，就無法贖回票證</span><span class="sxs-lookup"><span data-stu-id="b4689-116">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="b4689-117">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="b4689-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="b4689-118">票證核發對: %2 %r</span><span class="sxs-lookup"><span data-stu-id="b4689-118">Ticket Issued For: %2%r</span></span><br /><br /> <span data-ttu-id="b4689-119">應用程式使用者： %3</span><span class="sxs-lookup"><span data-stu-id="b4689-119">Application Users: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4689-120">說明</span><span class="sxs-lookup"><span data-stu-id="b4689-120">Explanation</span></span>  
 <span data-ttu-id="b4689-121">因為票證的核發對象的使用者不是應用程式使用者帳戶的成員，就無法贖回票證。</span><span class="sxs-lookup"><span data-stu-id="b4689-121">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4689-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b4689-122">User Action</span></span>  
 <span data-ttu-id="b4689-123">請重新發出票證的使用者可以是應用程式使用者帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="b4689-123">Reissue the ticket to a user who is a member of the Application Users account.</span></span>