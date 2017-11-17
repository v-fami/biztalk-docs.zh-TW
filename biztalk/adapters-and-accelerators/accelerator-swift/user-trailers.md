---
title: "使用者結尾 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc2d7f2a3dd21d35bb33fa625f59aa27c04e656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="user-trailers"></a><span data-ttu-id="8ad63-102">使用者結尾</span><span class="sxs-lookup"><span data-stu-id="8ad63-102">User Trailers</span></span>
<span data-ttu-id="8ad63-103">使用者的結尾，除了 CHK 結尾是選擇性的存在時，依下列順序發生：</span><span class="sxs-lookup"><span data-stu-id="8ad63-103">User trailers, except for the CHK trailer, are optional and when present, occur in the following order:</span></span>  
  
|<span data-ttu-id="8ad63-104">結尾程式碼</span><span class="sxs-lookup"><span data-stu-id="8ad63-104">Trailer code</span></span>|<span data-ttu-id="8ad63-105">名稱</span><span class="sxs-lookup"><span data-stu-id="8ad63-105">Name</span></span>|  
|------------------|----------|  
|<span data-ttu-id="8ad63-106">MAC</span><span class="sxs-lookup"><span data-stu-id="8ad63-106">MAC</span></span>|<span data-ttu-id="8ad63-107">訊息驗證碼</span><span class="sxs-lookup"><span data-stu-id="8ad63-107">Message Authentication Code</span></span>|  
|<span data-ttu-id="8ad63-108">PAC</span><span class="sxs-lookup"><span data-stu-id="8ad63-108">PAC</span></span>|<span data-ttu-id="8ad63-109">專屬的驗證碼</span><span class="sxs-lookup"><span data-stu-id="8ad63-109">Proprietary Authentication Code</span></span>|  
|<span data-ttu-id="8ad63-110">CHK</span><span class="sxs-lookup"><span data-stu-id="8ad63-110">CHK</span></span>|<span data-ttu-id="8ad63-111">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="8ad63-111">Checksum</span></span>|  
|<span data-ttu-id="8ad63-112">TNG</span><span class="sxs-lookup"><span data-stu-id="8ad63-112">TNG</span></span>|<span data-ttu-id="8ad63-113">訓練</span><span class="sxs-lookup"><span data-stu-id="8ad63-113">Training</span></span>|  
|<span data-ttu-id="8ad63-114">PDE</span><span class="sxs-lookup"><span data-stu-id="8ad63-114">PDE</span></span>|<span data-ttu-id="8ad63-115">可能的重複發出</span><span class="sxs-lookup"><span data-stu-id="8ad63-115">Possible Duplicate Emission</span></span>|  
  
-   <span data-ttu-id="8ad63-116">**訊息驗證碼 (MAC) 結尾。**</span><span class="sxs-lookup"><span data-stu-id="8ad63-116">**Message Authentication Code (MAC) Trailer.**</span></span> <span data-ttu-id="8ad63-117">可讓接收的使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="8ad63-117">Allows authentication by the receiving user.</span></span> <span data-ttu-id="8ad63-118">MAC 結尾後面驗證結果。</span><span class="sxs-lookup"><span data-stu-id="8ad63-118">The MAC trailer is followed by an authentication result.</span></span> <span data-ttu-id="8ad63-119">這個結尾會強制 FIN 應用程式中的大部分使用者的訊息分類。</span><span class="sxs-lookup"><span data-stu-id="8ad63-119">This trailer is mandatory for most user-to-user message categories within the FIN application.</span></span>  
  
     <span data-ttu-id="8ad63-120">使用 FIN 複製服務時，PAC 結尾 （如果有的話） 會遵循 MAC 結尾。</span><span class="sxs-lookup"><span data-stu-id="8ad63-120">When the FIN Copy Service is used, a PAC trailer (if present) follows the MAC trailer.</span></span> <span data-ttu-id="8ad63-121">下列程式碼是 MAC 結尾的範例：</span><span class="sxs-lookup"><span data-stu-id="8ad63-121">The following code is an example of a MAC trailer:</span></span>  
  
    ```  
    {MAC:<authentication-result>}  
    where <authentication-result> = 8!h  
    ```  
  
-   <span data-ttu-id="8ad63-122">**專屬的驗證程式碼 (PAC) 尾端。**</span><span class="sxs-lookup"><span data-stu-id="8ad63-122">**Proprietary Authentication Code (PAC) Trailer.**</span></span> <span data-ttu-id="8ad63-123">PAC 結尾被使用雙重驗證選項時，才使用 FIN 複製服務。</span><span class="sxs-lookup"><span data-stu-id="8ad63-123">The PAC trailer is used within the FIN Copy service only when using the double authentication option.</span></span> <span data-ttu-id="8ad63-124">區塊 5 FIN 使用者的訊息包含 MAC 結尾之後立即 PAC 結尾，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="8ad63-124">Block 5 of FIN user-to-user messages include the PAC trailer immediately after the MAC trailer, if present.</span></span> <span data-ttu-id="8ad63-125">如果有的話，此結果計算上擷取的區塊 4 115，欄位的值，訊息的欄位和\<驗證結果 > MAC 結尾複製服務使用雙重驗證。</span><span class="sxs-lookup"><span data-stu-id="8ad63-125">This result is calculated on the extracted fields of Block 4 of the message, the value of field 115, if present, and the \<authentication-result> of the MAC trailer for Copy Services with double authentication.</span></span>  
  
     <span data-ttu-id="8ad63-126">如此一來，end 區塊的指標 （CrLf-） 納入 PAC 計算，且在定義欄位，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8ad63-126">As a result, the end-of-block indicator (CrLf-) is included in the PAC calculation and the fields are defined as follows:</span></span>  
  
    -   <span data-ttu-id="8ad63-127">前四個字元都是 CrLf:</span><span class="sxs-lookup"><span data-stu-id="8ad63-127">The first four characters are CrLf:</span></span>  
  
    -   <span data-ttu-id="8ad63-128">欄位和分隔符號都存在，也就是 32A: 20，:，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8ad63-128">The field and the delimiter are present, that is, 32A:, 20:, and so on.</span></span>  
  
    -   <span data-ttu-id="8ad63-129">所有的子欄位和分隔符號會呈現。</span><span class="sxs-lookup"><span data-stu-id="8ad63-129">All subfields and their delimiters are present.</span></span>  
  
     <span data-ttu-id="8ad63-130">下列程式碼是 PAC 結尾格式的範例：</span><span class="sxs-lookup"><span data-stu-id="8ad63-130">The following code is an example of the PAC trailer format:</span></span>  
  
    ```  
    {PAC:[<authentication-result>]}  
    where <authentication-result> is mandatory on input messages only and  
    <authentication-result> = 8!h  
    ```  
  
-   <span data-ttu-id="8ad63-131">**CHK （總和檢查碼） 結尾的所有 FIN 訊息 （必要項）**</span><span class="sxs-lookup"><span data-stu-id="8ad63-131">**CHK (Checksum) Trailer (mandatory for all FIN messages)**</span></span>  
  
     <span data-ttu-id="8ad63-132">CHK 結尾會強制所有 FIN 訊息，並計算根據收件者位址 (12 個字元的第九個字元取代*X*再加上文字區塊)。</span><span class="sxs-lookup"><span data-stu-id="8ad63-132">The CHK trailer is mandatory for all FIN messages and is computed based upon the receiver's address (12 characters with the ninth character replaced by *X* plus the text block).</span></span> <span data-ttu-id="8ad63-133">系統中，並檢查訊息不會因系統發生問題或未偵測到的傳輸錯誤而損毀 CBT，可讓此結尾。</span><span class="sxs-lookup"><span data-stu-id="8ad63-133">This trailer allows the system and the CBT to check that messages are not corrupted due to a system malfunction or an undetected transmission error.</span></span>  
  
     <span data-ttu-id="8ad63-134">下列程式碼是 CHK 結尾格式的範例：</span><span class="sxs-lookup"><span data-stu-id="8ad63-134">The following code is an example of the CHK trailer format:</span></span>  
  
    ```  
    {CHK:<checksum-result>}  
    where <checksum-result> = 12!h  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8ad63-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad63-135">See Also</span></span>  
 [<span data-ttu-id="8ad63-136">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="8ad63-136">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)