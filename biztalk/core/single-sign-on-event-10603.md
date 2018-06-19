---
title: 單一登入： 事件 10603 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 738d2939f4178fdfaa115b8dfcc2273935c37b85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270390"
---
# <a name="single-sign-on-event-10603"></a><span data-ttu-id="8df40-102">單一登入： 事件 10603</span><span class="sxs-lookup"><span data-stu-id="8df40-102">Single Sign-On: Event 10603</span></span>
## <a name="details"></a><span data-ttu-id="8df40-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8df40-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8df40-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8df40-104">Product Name</span></span>|<span data-ttu-id="8df40-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8df40-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8df40-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8df40-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8df40-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8df40-107">Event ID</span></span>|<span data-ttu-id="8df40-108">10603</span><span class="sxs-lookup"><span data-stu-id="8df40-108">10603</span></span>|  
|<span data-ttu-id="8df40-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8df40-109">Event Source</span></span>|<span data-ttu-id="8df40-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8df40-110">ENTSSO</span></span>|  
|<span data-ttu-id="8df40-111">元件</span><span class="sxs-lookup"><span data-stu-id="8df40-111">Component</span></span>|<span data-ttu-id="8df40-112">不適用</span><span class="sxs-lookup"><span data-stu-id="8df40-112">N/A</span></span>|  
|<span data-ttu-id="8df40-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8df40-113">Symbolic Name</span></span>|<span data-ttu-id="8df40-114">SSO_WARN_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="8df40-114">SSO_WARN_DB_ACCESS</span></span>|  
|<span data-ttu-id="8df40-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8df40-115">Message Text</span></span>|<span data-ttu-id="8df40-116">無法存取 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8df40-116">Could not access the SSO database.</span></span> <span data-ttu-id="8df40-117">如果此狀況持續發生，SSO 服務將會移 offline.%r</span><span class="sxs-lookup"><span data-stu-id="8df40-117">If this condition persists, the SSO service will go offline.%r</span></span><br /><br /> <span data-ttu-id="8df40-118">%1.%r</span><span class="sxs-lookup"><span data-stu-id="8df40-118">%1.%r</span></span><br /><br /> <span data-ttu-id="8df40-119">SQL 錯誤代碼： %2</span><span class="sxs-lookup"><span data-stu-id="8df40-119">SQL Error code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8df40-120">說明</span><span class="sxs-lookup"><span data-stu-id="8df40-120">Explanation</span></span>  
 <span data-ttu-id="8df40-121">SSO 資料庫是無法使用。</span><span class="sxs-lookup"><span data-stu-id="8df40-121">The SSO database is unavailable.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8df40-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8df40-122">User Action</span></span>  
 <span data-ttu-id="8df40-123">請檢查警告中包含的 SQL 錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8df40-123">Check the SQL error code contained in the warning.</span></span> <span data-ttu-id="8df40-124">這可能會提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="8df40-124">This may offer some guidance.</span></span> <span data-ttu-id="8df40-125">如果沒有，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="8df40-125">If not, contact Microsoft Product Support Services.</span></span>