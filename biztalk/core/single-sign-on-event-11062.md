---
title: 單一登入： 事件 11062 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55c7c2ea-c671-4853-ac64-8cb80bba98b0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50df4834f92eff7cc679c051f529f4dbaefc4335
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970136"
---
# <a name="single-sign-on-event-11062"></a><span data-ttu-id="763e4-102">單一登入： 事件 11062</span><span class="sxs-lookup"><span data-stu-id="763e4-102">Single Sign-On: Event 11062</span></span>
## <a name="details"></a><span data-ttu-id="763e4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="763e4-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="763e4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="763e4-104">Product Name</span></span>   |                                                                                       <span data-ttu-id="763e4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="763e4-105">Enterprise Single Sign-On</span></span>                                                                                        |
| <span data-ttu-id="763e4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="763e4-106">Product Version</span></span> |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                       |
|    <span data-ttu-id="763e4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="763e4-107">Event ID</span></span>     |                                                                                                 <span data-ttu-id="763e4-108">11062</span><span class="sxs-lookup"><span data-stu-id="763e4-108">11062</span></span>                                                                                                  |
|  <span data-ttu-id="763e4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="763e4-109">Event Source</span></span>   |                                                                                                 <span data-ttu-id="763e4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="763e4-110">ENTSSO</span></span>                                                                                                 |
|    <span data-ttu-id="763e4-111">元件</span><span class="sxs-lookup"><span data-stu-id="763e4-111">Component</span></span>    |                                                                                                  <span data-ttu-id="763e4-112">不適用</span><span class="sxs-lookup"><span data-stu-id="763e4-112">N/A</span></span>                                                                                                   |
|  <span data-ttu-id="763e4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="763e4-113">Symbolic Name</span></span>  |                                                                                    <span data-ttu-id="763e4-114">SSO_WARN_PASSWORD_FILTER_FAILED</span><span class="sxs-lookup"><span data-stu-id="763e4-114">SSO_WARN_PASSWORD_FILTER_FAILED</span></span>                                                                                     |
|  <span data-ttu-id="763e4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="763e4-115">Message Text</span></span>   | <span data-ttu-id="763e4-116">密碼篩選失敗。</span><span class="sxs-lookup"><span data-stu-id="763e4-116">Password filtering failed.</span></span> <span data-ttu-id="763e4-117">任何密碼篩選將不會 used.%r</span><span class="sxs-lookup"><span data-stu-id="763e4-117">No password filter will be used.%r</span></span><br /><br /> <span data-ttu-id="763e4-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="763e4-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="763e4-119">密碼篩選字串: %2 %r</span><span class="sxs-lookup"><span data-stu-id="763e4-119">Password Filter String: %2%r</span></span><br /><br /> <span data-ttu-id="763e4-120">其他資料: %3 %r</span><span class="sxs-lookup"><span data-stu-id="763e4-120">Additional Data: %3%r</span></span><br /><br /> <span data-ttu-id="763e4-121">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="763e4-121">Error Code: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="763e4-122">說明</span><span class="sxs-lookup"><span data-stu-id="763e4-122">Explanation</span></span>  
 <span data-ttu-id="763e4-123">建立密碼篩選條件時發生錯誤，無法建立篩選條件。</span><span class="sxs-lookup"><span data-stu-id="763e4-123">An error occurred while creating a password filter, and the filter was not created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="763e4-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="763e4-124">User Action</span></span>  
 <span data-ttu-id="763e4-125">若要建立密碼篩選器使用 建立密碼篩選器精靈，請參閱[如何使用密碼篩選](../core/how-to-use-password-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="763e4-125">To create the Password Filter using the Create Password Filter Wizard, see [How to Use Password Filters](../core/how-to-use-password-filters.md).</span></span>