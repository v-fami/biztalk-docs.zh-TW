---
title: 單一登入： 事件 10807 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 882c01c6-70db-4986-9f4b-f08335424250
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e269b22bc8ea2fec013123d515ac04bd3f60d46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277694"
---
# <a name="single-sign-on-event-10807"></a><span data-ttu-id="f635a-102">單一登入： 事件 10807</span><span class="sxs-lookup"><span data-stu-id="f635a-102">Single Sign-On: Event 10807</span></span>
## <a name="details"></a><span data-ttu-id="f635a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f635a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f635a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f635a-104">Product Name</span></span>|<span data-ttu-id="f635a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f635a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f635a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f635a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f635a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f635a-107">Event ID</span></span>|<span data-ttu-id="f635a-108">10807</span><span class="sxs-lookup"><span data-stu-id="f635a-108">10807</span></span>|  
|<span data-ttu-id="f635a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f635a-109">Event Source</span></span>|<span data-ttu-id="f635a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f635a-110">ENTSSO</span></span>|  
|<span data-ttu-id="f635a-111">元件</span><span class="sxs-lookup"><span data-stu-id="f635a-111">Component</span></span>|<span data-ttu-id="f635a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f635a-112">N/A</span></span>|  
|<span data-ttu-id="f635a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f635a-113">Symbolic Name</span></span>|<span data-ttu-id="f635a-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="f635a-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span></span>|  
|<span data-ttu-id="f635a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f635a-115">Message Text</span></span>|<span data-ttu-id="f635a-116">太多未確認的通知。</span><span class="sxs-lookup"><span data-stu-id="f635a-116">Too many unconfirmed notifications.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f635a-117">說明</span><span class="sxs-lookup"><span data-stu-id="f635a-117">Explanation</span></span>  
 <span data-ttu-id="f635a-118">每次密碼變更通知會傳送，會收到確認訊息。</span><span class="sxs-lookup"><span data-stu-id="f635a-118">Each time a password change notification is sent, a confirmation message is received.</span></span> <span data-ttu-id="f635a-119">在此情況下，已超過此限制，但不用確認的通知。</span><span class="sxs-lookup"><span data-stu-id="f635a-119">In this case, the limit for notifications without confirmation has been exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f635a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f635a-120">User Action</span></span>  
 <span data-ttu-id="f635a-121">請檢查密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="f635a-121">Check the password sync adapter.</span></span>