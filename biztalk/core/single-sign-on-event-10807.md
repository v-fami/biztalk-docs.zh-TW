---
title: 單一登入： 事件 10807 |Microsoft Docs
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
ms.openlocfilehash: d9e23aefbb950160f29b6145e64bfaa1784dc3f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985407"
---
# <a name="single-sign-on-event-10807"></a><span data-ttu-id="ee767-102">單一登入： 事件 10807</span><span class="sxs-lookup"><span data-stu-id="ee767-102">Single Sign-On: Event 10807</span></span>
## <a name="details"></a><span data-ttu-id="ee767-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee767-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="ee767-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee767-104">Product Name</span></span>   |                 <span data-ttu-id="ee767-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ee767-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="ee767-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ee767-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="ee767-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee767-107">Event ID</span></span>     |                           <span data-ttu-id="ee767-108">10807</span><span class="sxs-lookup"><span data-stu-id="ee767-108">10807</span></span>                            |
|  <span data-ttu-id="ee767-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee767-109">Event Source</span></span>   |                           <span data-ttu-id="ee767-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ee767-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="ee767-111">元件</span><span class="sxs-lookup"><span data-stu-id="ee767-111">Component</span></span>    |                            <span data-ttu-id="ee767-112">不適用</span><span class="sxs-lookup"><span data-stu-id="ee767-112">N/A</span></span>                             |
|  <span data-ttu-id="ee767-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ee767-113">Symbolic Name</span></span>  |        <span data-ttu-id="ee767-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="ee767-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span></span>         |
|  <span data-ttu-id="ee767-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee767-115">Message Text</span></span>   |            <span data-ttu-id="ee767-116">太多未確認的通知。</span><span class="sxs-lookup"><span data-stu-id="ee767-116">Too many unconfirmed notifications.</span></span>             |
  
## <a name="explanation"></a><span data-ttu-id="ee767-117">說明</span><span class="sxs-lookup"><span data-stu-id="ee767-117">Explanation</span></span>  
 <span data-ttu-id="ee767-118">傳送密碼變更通知每次，但在收到確認訊息。</span><span class="sxs-lookup"><span data-stu-id="ee767-118">Each time a password change notification is sent, a confirmation message is received.</span></span> <span data-ttu-id="ee767-119">在此情況下，已超過此限制，而不需要確認的通知。</span><span class="sxs-lookup"><span data-stu-id="ee767-119">In this case, the limit for notifications without confirmation has been exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee767-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee767-120">User Action</span></span>  
 <span data-ttu-id="ee767-121">檢查 「 密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="ee767-121">Check the password sync adapter.</span></span>