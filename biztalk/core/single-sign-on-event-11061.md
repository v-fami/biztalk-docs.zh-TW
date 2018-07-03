---
title: 單一登入： 事件 11061 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52fb18e2-4482-4cdb-b8ed-d579a95acd7c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1733e444ecdfdaf54b20beb2de6894ade3466f4c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011327"
---
# <a name="single-sign-on-event-11061"></a><span data-ttu-id="ad263-102">單一登入： 事件 11061</span><span class="sxs-lookup"><span data-stu-id="ad263-102">Single Sign-On: Event 11061</span></span>
## <a name="details"></a><span data-ttu-id="ad263-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ad263-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ad263-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ad263-104">Product Name</span></span>   |                                                                                                                     <span data-ttu-id="ad263-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ad263-105">Enterprise Single Sign-On</span></span>                                                                                                                     |
| <span data-ttu-id="ad263-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ad263-106">Product Version</span></span> |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    <span data-ttu-id="ad263-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ad263-107">Event ID</span></span>     |                                                                                                                               <span data-ttu-id="ad263-108">11061</span><span class="sxs-lookup"><span data-stu-id="ad263-108">11061</span></span>                                                                                                                               |
|  <span data-ttu-id="ad263-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ad263-109">Event Source</span></span>   |                                                                                                                              <span data-ttu-id="ad263-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ad263-110">ENTSSO</span></span>                                                                                                                               |
|    <span data-ttu-id="ad263-111">元件</span><span class="sxs-lookup"><span data-stu-id="ad263-111">Component</span></span>    |                                                                                                                                <span data-ttu-id="ad263-112">不適用</span><span class="sxs-lookup"><span data-stu-id="ad263-112">N/A</span></span>                                                                                                                                |
|  <span data-ttu-id="ad263-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ad263-113">Symbolic Name</span></span>  |                                                                                                                   <span data-ttu-id="ad263-114">SSO_WARN_BAD_PASSWORD_FILTER</span><span class="sxs-lookup"><span data-stu-id="ad263-114">SSO_WARN_BAD_PASSWORD_FILTER</span></span>                                                                                                                    |
|  <span data-ttu-id="ad263-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ad263-115">Message Text</span></span>   | <span data-ttu-id="ad263-116">密碼篩選字串無效。</span><span class="sxs-lookup"><span data-stu-id="ad263-116">The password filter string is not valid.</span></span> <span data-ttu-id="ad263-117">任何密碼篩選將不會 used.%r</span><span class="sxs-lookup"><span data-stu-id="ad263-117">No password filter will be used.%r</span></span><br /><br /> <span data-ttu-id="ad263-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ad263-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="ad263-119">密碼篩選字串: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ad263-119">Password Filter String: %2%r</span></span><br /><br /> <span data-ttu-id="ad263-120">處理的 Token 數目: %3 %r</span><span class="sxs-lookup"><span data-stu-id="ad263-120">Number Of Tokens Processed: %3%r</span></span><br /><br /> <span data-ttu-id="ad263-121">其他資料: %4 %r</span><span class="sxs-lookup"><span data-stu-id="ad263-121">Additional Data: %4%r</span></span><br /><br /> <span data-ttu-id="ad263-122">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="ad263-122">Error Code: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="ad263-123">說明</span><span class="sxs-lookup"><span data-stu-id="ad263-123">Explanation</span></span>  
 <span data-ttu-id="ad263-124">已手動建立的無效密碼篩選器。</span><span class="sxs-lookup"><span data-stu-id="ad263-124">An invalid password filter has been created manually.</span></span> <span data-ttu-id="ad263-125">在此程序中的某個時間點引進錯誤 （請參閱錯誤位置的警告文字中的 「 密碼篩選字串 」）。</span><span class="sxs-lookup"><span data-stu-id="ad263-125">At some point in this process an error was introduced (see Password Filter String in the warning text for the location of the error).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad263-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ad263-126">User Action</span></span>  
 <span data-ttu-id="ad263-127">若要建立密碼篩選器使用 建立密碼篩選器精靈，請參閱[如何使用密碼篩選](../core/how-to-use-password-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="ad263-127">To create the Password Filter using the Create Password Filter Wizard, see [How to Use Password Filters](../core/how-to-use-password-filters.md).</span></span>