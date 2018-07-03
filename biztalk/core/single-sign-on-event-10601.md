---
title: 單一登入： 事件 10601 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2624025e-b7a8-43b9-aa7e-6811a2fc3278
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ea1dfbcc36cc83498aa316cedeab8fc46a2f4dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987735"
---
# <a name="single-sign-on-event-10601"></a><span data-ttu-id="f0b7a-102">單一登入： 事件 10601</span><span class="sxs-lookup"><span data-stu-id="f0b7a-102">Single Sign-On: Event 10601</span></span>
## <a name="details"></a><span data-ttu-id="f0b7a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0b7a-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f0b7a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f0b7a-104">Product Name</span></span>   |                                                                                                                  <span data-ttu-id="f0b7a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f0b7a-105">Enterprise Single Sign-On</span></span>                                                                                                                   |
| <span data-ttu-id="f0b7a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f0b7a-106">Product Version</span></span> |                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                  |
|    <span data-ttu-id="f0b7a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f0b7a-107">Event ID</span></span>     |                                                                                                                            <span data-ttu-id="f0b7a-108">10601</span><span class="sxs-lookup"><span data-stu-id="f0b7a-108">10601</span></span>                                                                                                                             |
|  <span data-ttu-id="f0b7a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f0b7a-109">Event Source</span></span>   |                                                                                                                            <span data-ttu-id="f0b7a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f0b7a-110">ENTSSO</span></span>                                                                                                                            |
|    <span data-ttu-id="f0b7a-111">元件</span><span class="sxs-lookup"><span data-stu-id="f0b7a-111">Component</span></span>    |                                                                                                                             <span data-ttu-id="f0b7a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f0b7a-112">N/A</span></span>                                                                                                                              |
|  <span data-ttu-id="f0b7a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f0b7a-113">Symbolic Name</span></span>  |                                                                                                                    <span data-ttu-id="f0b7a-114">SSO_WARN_INVALID_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f0b7a-114">SSO_WARN_INVALID_FLAGS</span></span>                                                                                                                    |
|  <span data-ttu-id="f0b7a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f0b7a-115">Message Text</span></span>   | <span data-ttu-id="f0b7a-116">指定的旗標不適用於建立這個類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0b7a-116">The specified flags are not valid for creating this type of application.</span></span><br /><br /> <span data-ttu-id="f0b7a-117">請參閱 details.%r 文件</span><span class="sxs-lookup"><span data-stu-id="f0b7a-117">See documentation for details.%r</span></span><br /><br /> <span data-ttu-id="f0b7a-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f0b7a-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="f0b7a-119">指定的旗標: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f0b7a-119">Specified Flags: %2%r</span></span><br /><br /> <span data-ttu-id="f0b7a-120">允許的旗標: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f0b7a-120">Allowed Flags: %3%r</span></span><br /><br /> <span data-ttu-id="f0b7a-121">不允許的旗標： %4</span><span class="sxs-lookup"><span data-stu-id="f0b7a-121">Not Allowed Flags: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="f0b7a-122">說明</span><span class="sxs-lookup"><span data-stu-id="f0b7a-122">Explanation</span></span>  
 <span data-ttu-id="f0b7a-123">指定的旗標不適用於建立這個類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0b7a-123">The specified flags are not valid for creating this type of application.</span></span> <span data-ttu-id="f0b7a-124">警告列出而言，應用程式，以及允許的旗標和不可。</span><span class="sxs-lookup"><span data-stu-id="f0b7a-124">The warning lists the application concerned, as well as the flags that are allowed and those that are not.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0b7a-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f0b7a-125">User Action</span></span>  
 <span data-ttu-id="f0b7a-126">重新建立應用程式的警告訊息中所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="f0b7a-126">Recreate the application following the guidelines outlined in the warning message.</span></span>