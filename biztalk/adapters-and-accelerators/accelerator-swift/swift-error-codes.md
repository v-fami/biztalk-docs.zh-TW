---
title: 在 BizTalk Server 中的 SWIFT 錯誤碼 |Microsoft 文件
description: SWIFT 加速器，BizTalk Server 中的檢視類別和驗證類型
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03699986-965b-4a28-ab2e-09f110fb4db6
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d8e027eb9cce1cf66342484070310141e10b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215022"
---
# <a name="swift-error-codes"></a><span data-ttu-id="502b3-103">SWIFT 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="502b3-103">SWIFT Error Codes</span></span>
<span data-ttu-id="502b3-104">SWIFT 定義許多網路造成的驗證，針對財務 (FIN) 訊息組。</span><span class="sxs-lookup"><span data-stu-id="502b3-104">SWIFT defines many network-imposed validations against the set of financial (FIN) messages.</span></span> <span data-ttu-id="502b3-105">每個驗證與檢查訊息的內容類型，然後傳回三個字元的錯誤碼與相關聯。</span><span class="sxs-lookup"><span data-stu-id="502b3-105">Each validation relates to a type of check against the contents of the message, and is associated with a three-character error code.</span></span> <span data-ttu-id="502b3-106">錯誤的程式碼的第一個字元隱含偵測到問題的類別，而值為字母。</span><span class="sxs-lookup"><span data-stu-id="502b3-106">The first character of the error code implies the class of the problem detected, and is a letter.</span></span> <span data-ttu-id="502b3-107">其餘的兩個字元代表的 （結合類別） 時的錯誤詳細資料，並且一律會顯示為兩位數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="502b3-107">The remaining two characters denote the detail of the error (when combined with the class) and always appear as a two-digit code.</span></span>  

## <a name="class-of-errors"></a><span data-ttu-id="502b3-108">類別的錯誤</span><span class="sxs-lookup"><span data-stu-id="502b3-108">Class of errors</span></span>  
 <span data-ttu-id="502b3-109">下表列出的字母指定、 驗證類型，與每個錯誤，類別相關聯的規則變更和錯誤的類別是否支援。</span><span class="sxs-lookup"><span data-stu-id="502b3-109">The following table lists the letter designations, validation type, rule change associated with each class of error, and whether or not the class of error is supported.</span></span>  
  
|<span data-ttu-id="502b3-110">類別</span><span class="sxs-lookup"><span data-stu-id="502b3-110">Class</span></span>|<span data-ttu-id="502b3-111">驗證類型和規則的變更</span><span class="sxs-lookup"><span data-stu-id="502b3-111">Validation type and rule change</span></span>|<span data-ttu-id="502b3-112">支援？</span><span class="sxs-lookup"><span data-stu-id="502b3-112">Supported?</span></span>|  
|-----------|-------------------------------------|----------------|  
|<span data-ttu-id="502b3-113">**C，D，E**</span><span class="sxs-lookup"><span data-stu-id="502b3-113">**C, D, E**</span></span>|<span data-ttu-id="502b3-114">語意驗證規則 0 299</span><span class="sxs-lookup"><span data-stu-id="502b3-114">Semantic validation rules 0-299</span></span>|<span data-ttu-id="502b3-115">支援</span><span class="sxs-lookup"><span data-stu-id="502b3-115">Supported</span></span>|  
|<span data-ttu-id="502b3-116">**Knn**</span><span class="sxs-lookup"><span data-stu-id="502b3-116">**Knn**</span></span>|<span data-ttu-id="502b3-117">無效的程式碼文字欄位中*nn*</span><span class="sxs-lookup"><span data-stu-id="502b3-117">Invalid code word in field *nn*</span></span>|<span data-ttu-id="502b3-118">支援</span><span class="sxs-lookup"><span data-stu-id="502b3-118">Supported</span></span>|  
|<span data-ttu-id="502b3-119">**M50**</span><span class="sxs-lookup"><span data-stu-id="502b3-119">**M50**</span></span>|<span data-ttu-id="502b3-120">訊息長度超過</span><span class="sxs-lookup"><span data-stu-id="502b3-120">Message length exceeded</span></span>|<span data-ttu-id="502b3-121">不支援</span><span class="sxs-lookup"><span data-stu-id="502b3-121">Unsupported</span></span>|  
|<span data-ttu-id="502b3-122">**M60**</span><span class="sxs-lookup"><span data-stu-id="502b3-122">**M60**</span></span>|<span data-ttu-id="502b3-123">遇到非 SWIFT 字元</span><span class="sxs-lookup"><span data-stu-id="502b3-123">Non-SWIFT character encountered</span></span>|<span data-ttu-id="502b3-124">支援</span><span class="sxs-lookup"><span data-stu-id="502b3-124">Supported</span></span>|  
|<span data-ttu-id="502b3-125">**T**</span><span class="sxs-lookup"><span data-stu-id="502b3-125">**T**</span></span>|<span data-ttu-id="502b3-126">文字驗證錯誤代碼</span><span class="sxs-lookup"><span data-stu-id="502b3-126">Text validation error codes</span></span>|<span data-ttu-id="502b3-127">支援</span><span class="sxs-lookup"><span data-stu-id="502b3-127">Supported</span></span>|  
|<span data-ttu-id="502b3-128">**G**</span><span class="sxs-lookup"><span data-stu-id="502b3-128">**G**</span></span>|<span data-ttu-id="502b3-129">訊息的使用者群組 （咖啡杯） Textval 規則的特定錯誤代碼</span><span class="sxs-lookup"><span data-stu-id="502b3-129">Specific error codes for message user group (MUG) Textval rules</span></span>|<span data-ttu-id="502b3-130">不支援</span><span class="sxs-lookup"><span data-stu-id="502b3-130">Unsupported</span></span>|  
|<span data-ttu-id="502b3-131">**B**</span><span class="sxs-lookup"><span data-stu-id="502b3-131">**B**</span></span>|<span data-ttu-id="502b3-132">加值型服務的特殊的錯誤代碼</span><span class="sxs-lookup"><span data-stu-id="502b3-132">Special error codes for value-added services</span></span>|<span data-ttu-id="502b3-133">不支援</span><span class="sxs-lookup"><span data-stu-id="502b3-133">Unsupported</span></span>|  
  
 <span data-ttu-id="502b3-134">中應參考所有 SWIFT 錯誤*SWIFT 使用者手冊*。</span><span class="sxs-lookup"><span data-stu-id="502b3-134">All SWIFT errors should be referenced in the *SWIFT User Handbook*.</span></span> <span data-ttu-id="502b3-135">如需詳細資訊以及 SWIFT 錯誤碼的完整清單，請參閱*訊息格式的驗證規則*數量*SWIFT 使用者手冊*。</span><span class="sxs-lookup"><span data-stu-id="502b3-135">For more information and for a complete list of SWIFT error codes, refer to the *Message Format Validation Rules* volume of the *SWIFT User Handbook*.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="502b3-136">此發行集的 2003 年 9 月版本中實作的規則。</span><span class="sxs-lookup"><span data-stu-id="502b3-136"> implements the rules in the September 2003 edition of this publication.</span></span> <span data-ttu-id="502b3-137">您可以存取位於 SWIFT 網站[http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885)。</span><span class="sxs-lookup"><span data-stu-id="502b3-137">You can access the SWIFT Web site at [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).</span></span>  

## <a name="validation-errors"></a><span data-ttu-id="502b3-138">驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="502b3-138">Validation errors</span></span>  
 <span data-ttu-id="502b3-139">有一些定義 A4SWIFT 的代碼。</span><span class="sxs-lookup"><span data-stu-id="502b3-139">There are some codes which are defined by A4SWIFT.</span></span> <span data-ttu-id="502b3-140">這些錯誤碼會用於建立和實作 A4SWIFT，因此沒有對應的錯誤程式碼為這類規則 SWIFT 所定義的驗證/網路規則。</span><span class="sxs-lookup"><span data-stu-id="502b3-140">These error codes are used in the validation/network rules created and implemented by A4SWIFT, so there is no corresponding error code defined by SWIFT for such rules.</span></span> <span data-ttu-id="502b3-141">下表顯示的錯誤碼和錯誤會擲回對應的大小寫。</span><span class="sxs-lookup"><span data-stu-id="502b3-141">Below table shows the error code and corresponding case in which the error is thrown.</span></span> <span data-ttu-id="502b3-142">是的特定欄位，會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="502b3-142">is the particular field which throws the error.</span></span>  
  
|<span data-ttu-id="502b3-143">錯誤碼</span><span class="sxs-lookup"><span data-stu-id="502b3-143">Error Code</span></span>|<span data-ttu-id="502b3-144">Description</span><span class="sxs-lookup"><span data-stu-id="502b3-144">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="502b3-145">A4SWIFT001</span><span class="sxs-lookup"><span data-stu-id="502b3-145">A4SWIFT001</span></span>|<span data-ttu-id="502b3-146">多行欄位的第一個字元不可為 ':' 或 '-' 字元的第二個和後續的行。</span><span class="sxs-lookup"><span data-stu-id="502b3-146">The first character of multiline field cannot be ':' or '-' character for second and  subsequent lines.</span></span>|  
|<span data-ttu-id="502b3-147">A4SWIFT002</span><span class="sxs-lookup"><span data-stu-id="502b3-147">A4SWIFT002</span></span>|<span data-ttu-id="502b3-148">欄位包含無效的值。</span><span class="sxs-lookup"><span data-stu-id="502b3-148">Field contains invalid value.</span></span>|  
  
> [!NOTE]
>  [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]<span data-ttu-id="502b3-149">包含支援某些舊版的訊息，因為內部應用程式可能會使用這些訊息。</span><span class="sxs-lookup"><span data-stu-id="502b3-149"> includes support for some legacy messages, because internal applications might use these messages.</span></span> <span data-ttu-id="502b3-150">因此，A4SWIFT 維護相關聯的 SWIFT 規則和錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="502b3-150">Therefore, A4SWIFT maintains the associated SWIFT rules and error codes.</span></span>

## <a name="more-good-info"></a><span data-ttu-id="502b3-151">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="502b3-151">More good info</span></span>
[<span data-ttu-id="502b3-152">疑難排解： 問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="502b3-152">Troubleshooting: Issues and Resolutions</span></span>](troubleshooting-issues-and-resolutions1.md)  
[<span data-ttu-id="502b3-153">已知問題</span><span class="sxs-lookup"><span data-stu-id="502b3-153">Known Issues</span></span>](known-issues5.md)  
[<span data-ttu-id="502b3-154">一般詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="502b3-154">Common terms and definitions</span></span>](glossary6.md)