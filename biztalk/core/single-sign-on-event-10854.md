---
title: "單一登入： 事件 10854 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f9e9e761689b2ed21ec37acdbb8a63f1f88070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10854"></a><span data-ttu-id="c69f2-102">單一登入： 事件 10854</span><span class="sxs-lookup"><span data-stu-id="c69f2-102">Single Sign-On: Event 10854</span></span>
## <a name="details"></a><span data-ttu-id="c69f2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c69f2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c69f2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c69f2-104">Product Name</span></span>|<span data-ttu-id="c69f2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c69f2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c69f2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c69f2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c69f2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c69f2-107">Event ID</span></span>|<span data-ttu-id="c69f2-108">10854</span><span class="sxs-lookup"><span data-stu-id="c69f2-108">10854</span></span>|  
|<span data-ttu-id="c69f2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c69f2-109">Event Source</span></span>|<span data-ttu-id="c69f2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c69f2-110">ENTSSO</span></span>|  
|<span data-ttu-id="c69f2-111">元件</span><span class="sxs-lookup"><span data-stu-id="c69f2-111">Component</span></span>|<span data-ttu-id="c69f2-112">不適用</span><span class="sxs-lookup"><span data-stu-id="c69f2-112">N/A</span></span>|  
|<span data-ttu-id="c69f2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c69f2-113">Symbolic Name</span></span>|<span data-ttu-id="c69f2-114">ENTSSO_E_INVALID_STRING_FORMAT</span><span class="sxs-lookup"><span data-stu-id="c69f2-114">ENTSSO_E_INVALID_STRING_FORMAT</span></span>|  
|<span data-ttu-id="c69f2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c69f2-115">Message Text</span></span>|<span data-ttu-id="c69f2-116">字串格式不正確。 這個函式。</span><span class="sxs-lookup"><span data-stu-id="c69f2-116">The string format is incorrect for this function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c69f2-117">說明</span><span class="sxs-lookup"><span data-stu-id="c69f2-117">Explanation</span></span>  
 <span data-ttu-id="c69f2-118">字串格式不正確。 這個函式。</span><span class="sxs-lookup"><span data-stu-id="c69f2-118">The string format is incorrect for this function.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c69f2-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c69f2-119">User Action</span></span>  
 <span data-ttu-id="c69f2-120">正確的密碼字串的格式如下所述。</span><span class="sxs-lookup"><span data-stu-id="c69f2-120">Proper formatting for password strings is described below:</span></span>  
  
 <span data-ttu-id="c69f2-121">VT_BSTR 類型的屬性</span><span class="sxs-lookup"><span data-stu-id="c69f2-121">VT_BSTR type property</span></span>  
  
 <span data-ttu-id="c69f2-122">分隔符號是/（斜線）</span><span class="sxs-lookup"><span data-stu-id="c69f2-122">The delimiter is / (slash)</span></span>  
  
 <span data-ttu-id="c69f2-123">dc = 預設案例中 (沒有作業-不執行任何動作)</span><span class="sxs-lookup"><span data-stu-id="c69f2-123">dc = default case (no operation - do nothing)</span></span>  
  
 <span data-ttu-id="c69f2-124">範例： dc /</span><span class="sxs-lookup"><span data-stu-id="c69f2-124">Example: dc/</span></span>  
  
 <span data-ttu-id="c69f2-125">（無變化-'Cat' 至 'Cat'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-125">(no change - 'Cat' to 'Cat')</span></span>  
  
 <span data-ttu-id="c69f2-126">uc = 大寫</span><span class="sxs-lookup"><span data-stu-id="c69f2-126">uc = upper case</span></span>  
  
 <span data-ttu-id="c69f2-127">範例： uc /</span><span class="sxs-lookup"><span data-stu-id="c69f2-127">Example: uc/</span></span>  
  
 <span data-ttu-id="c69f2-128">（將密碼變更為大寫-'Cat' 至 'CAT'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-128">(change password to upper case - 'Cat' to 'CAT')</span></span>  
  
 <span data-ttu-id="c69f2-129">lc = 小寫</span><span class="sxs-lookup"><span data-stu-id="c69f2-129">lc = lower case</span></span>  
  
 <span data-ttu-id="c69f2-130">範例： lc /</span><span class="sxs-lookup"><span data-stu-id="c69f2-130">Example: lc/</span></span>  
  
 <span data-ttu-id="c69f2-131">（將密碼變更為小寫的 'Cat' 至 'cat'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-131">(change password to lower case - 'Cat' to 'cat')</span></span>  
  
 <span data-ttu-id="c69f2-132">rc = 移除字元-後面接著後面接著字元的計數</span><span class="sxs-lookup"><span data-stu-id="c69f2-132">rc = remove chars - followed by count followed by chars</span></span>  
  
 <span data-ttu-id="c69f2-133">範例： rc/2 / #@/</span><span class="sxs-lookup"><span data-stu-id="c69f2-133">Example: rc/2/#@/</span></span>  
  
 <span data-ttu-id="c69f2-134">(移除字元 '#' 和 '@' 從密碼-'C@t#' 至 'Ct')</span><span class="sxs-lookup"><span data-stu-id="c69f2-134">(remove the characters '#' and '@' from the password - 'C@t#' to 'Ct')</span></span>  
  
 <span data-ttu-id="c69f2-135">sc = 的替代的替代字元後面接著字元-後面接著後面接著要取代的字元計數</span><span class="sxs-lookup"><span data-stu-id="c69f2-135">sc = substitute chars - followed by count followed by chars to replace followed by substitute chars</span></span>  
  
 <span data-ttu-id="c69f2-136">範例： sc/3/abc/def /</span><span class="sxs-lookup"><span data-stu-id="c69f2-136">Example: sc/3/abc/def/</span></span>  
  
 <span data-ttu-id="c69f2-137">(移除的字元 'a'、 'b' 和 'c' 取代密碼與使用具有 '、 'e' 和 'f' 分別)</span><span class="sxs-lookup"><span data-stu-id="c69f2-137">(remove the characters 'a', 'b' and 'c' from the password and replace with 'd', 'e' and 'f' respectively)</span></span>  
  
 <span data-ttu-id="c69f2-138">（' 數據機用作 ' 'Cdt'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-138">('Cat' to 'Cdt')</span></span>  
  
 <span data-ttu-id="c69f2-139">ps = 從開始時間-後面接著計數 （最小密碼長度），後面接著單一填補字元板</span><span class="sxs-lookup"><span data-stu-id="c69f2-139">ps = pad from start - followed by count (min password length) followed by single pad char</span></span>  
  
 <span data-ttu-id="c69f2-140">範例： ps/8 / #/</span><span class="sxs-lookup"><span data-stu-id="c69f2-140">Example: ps/8/#/</span></span>  
  
 <span data-ttu-id="c69f2-141">（如果密碼不是在至少 8 字元長度，然後從直到 '#' 字元開頭的填補都是總 8 個字元）</span><span class="sxs-lookup"><span data-stu-id="c69f2-141">(if the password is not at least 8 chars in length then pad from the start with the character '#' until there are 8 chars total)</span></span>  
  
 <span data-ttu-id="c69f2-142">（' 數據機用作 ' '###Cat'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-142">('Cat' to '#####Cat')</span></span>  
  
 <span data-ttu-id="c69f2-143">pe = 從端-後面接著計數 （最小密碼長度），後面接著單一填補字元板</span><span class="sxs-lookup"><span data-stu-id="c69f2-143">pe = pad from end - followed by count (min password length) followed by single pad char</span></span>  
  
 <span data-ttu-id="c69f2-144">範例： pe/10 / $/</span><span class="sxs-lookup"><span data-stu-id="c69f2-144">Example: pe/10/$/</span></span>  
  
 <span data-ttu-id="c69f2-145">（如果密碼不是在至少 10 個字元長度，則以字元 '$' 直到結尾處的填補都是總 10 個字元）</span><span class="sxs-lookup"><span data-stu-id="c69f2-145">(if the password is not at least 10 chars in length then pad to the end with the character '$' until there are 10 chars total)</span></span>  
  
 <span data-ttu-id="c69f2-146">（' 數據機用作 ' 'Cat$ $$'）</span><span class="sxs-lookup"><span data-stu-id="c69f2-146">('Cat' to 'Cat$$$$$$$')</span></span>  
  
 <span data-ttu-id="c69f2-147">tr = 截斷-後面計數-字串長度限制</span><span class="sxs-lookup"><span data-stu-id="c69f2-147">tr = truncate - limit length of string - followed by count</span></span>  
  
 <span data-ttu-id="c69f2-148">範例： tr/11 /</span><span class="sxs-lookup"><span data-stu-id="c69f2-148">Example: tr/11/</span></span>  
  
 <span data-ttu-id="c69f2-149">('Cat123456789' 至 'Cat12345678');</span><span class="sxs-lookup"><span data-stu-id="c69f2-149">('Cat123456789' to 'Cat12345678');</span></span>  
  
 <span data-ttu-id="c69f2-150">語彙基元字串的順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="c69f2-150">The tokens are processed in their order in the string.</span></span>  
  
 <span data-ttu-id="c69f2-151">範例：</span><span class="sxs-lookup"><span data-stu-id="c69f2-151">Example:</span></span>  
  
 <span data-ttu-id="c69f2-152">uc/rc/1/（& s) / sc/2 / #$/-/ ps/8/&/tr/32 /</span><span class="sxs-lookup"><span data-stu-id="c69f2-152">uc/rc/1/&/sc/2/#$/--/ps/8/&/tr/32/</span></span>