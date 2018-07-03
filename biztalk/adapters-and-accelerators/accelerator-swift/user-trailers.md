---
title: 使用者結尾 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10bc0d4d0fcdb36311e0590d9ae04239db168ed7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010215"
---
# <a name="user-trailers"></a><span data-ttu-id="d5d15-102">使用者結尾</span><span class="sxs-lookup"><span data-stu-id="d5d15-102">User Trailers</span></span>
<span data-ttu-id="d5d15-103">使用者結尾，除了 CHK 結尾是選擇性的存在時，會發生順序如下：</span><span class="sxs-lookup"><span data-stu-id="d5d15-103">User trailers, except for the CHK trailer, are optional and when present, occur in the following order:</span></span>  
  
|<span data-ttu-id="d5d15-104">結尾程式碼</span><span class="sxs-lookup"><span data-stu-id="d5d15-104">Trailer code</span></span>|<span data-ttu-id="d5d15-105">[屬性]</span><span class="sxs-lookup"><span data-stu-id="d5d15-105">Name</span></span>|  
|------------------|----------|  
|<span data-ttu-id="d5d15-106">MAC</span><span class="sxs-lookup"><span data-stu-id="d5d15-106">MAC</span></span>|<span data-ttu-id="d5d15-107">訊息驗證碼</span><span class="sxs-lookup"><span data-stu-id="d5d15-107">Message Authentication Code</span></span>|  
|<span data-ttu-id="d5d15-108">PAC</span><span class="sxs-lookup"><span data-stu-id="d5d15-108">PAC</span></span>|<span data-ttu-id="d5d15-109">專屬的驗證碼</span><span class="sxs-lookup"><span data-stu-id="d5d15-109">Proprietary Authentication Code</span></span>|  
|<span data-ttu-id="d5d15-110">CHK</span><span class="sxs-lookup"><span data-stu-id="d5d15-110">CHK</span></span>|<span data-ttu-id="d5d15-111">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="d5d15-111">Checksum</span></span>|  
|<span data-ttu-id="d5d15-112">TNG</span><span class="sxs-lookup"><span data-stu-id="d5d15-112">TNG</span></span>|<span data-ttu-id="d5d15-113">訓練</span><span class="sxs-lookup"><span data-stu-id="d5d15-113">Training</span></span>|  
|<span data-ttu-id="d5d15-114">PDE</span><span class="sxs-lookup"><span data-stu-id="d5d15-114">PDE</span></span>|<span data-ttu-id="d5d15-115">可能的重複發出</span><span class="sxs-lookup"><span data-stu-id="d5d15-115">Possible Duplicate Emission</span></span>|  
  
- <span data-ttu-id="d5d15-116">**訊息驗證碼 (MAC) 結尾。**</span><span class="sxs-lookup"><span data-stu-id="d5d15-116">**Message Authentication Code (MAC) Trailer.**</span></span> <span data-ttu-id="d5d15-117">允許接收使用者的驗證。</span><span class="sxs-lookup"><span data-stu-id="d5d15-117">Allows authentication by the receiving user.</span></span> <span data-ttu-id="d5d15-118">MAC 結尾後面的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="d5d15-118">The MAC trailer is followed by an authentication result.</span></span> <span data-ttu-id="d5d15-119">此結尾是 FIN 應用程式中的大多數使用者的使用者訊息分類的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="d5d15-119">This trailer is mandatory for most user-to-user message categories within the FIN application.</span></span>  
  
   <span data-ttu-id="d5d15-120">使用 「 FIN 複製 」 服務時，PAC 結尾 （如果有的話） 會遵循 MAC 結尾。</span><span class="sxs-lookup"><span data-stu-id="d5d15-120">When the FIN Copy Service is used, a PAC trailer (if present) follows the MAC trailer.</span></span> <span data-ttu-id="d5d15-121">下列程式碼是 MAC 結尾的範例：</span><span class="sxs-lookup"><span data-stu-id="d5d15-121">The following code is an example of a MAC trailer:</span></span>  
  
  ```  
  {MAC:<authentication-result>}  
  where <authentication-result> = 8!h  
  ```  
  
- <span data-ttu-id="d5d15-122">**專屬的驗證程式碼 (PAC) 結尾。**</span><span class="sxs-lookup"><span data-stu-id="d5d15-122">**Proprietary Authentication Code (PAC) Trailer.**</span></span> <span data-ttu-id="d5d15-123">使用雙重驗證選項時，才 FIN 複製服務使用 PAC 結尾。</span><span class="sxs-lookup"><span data-stu-id="d5d15-123">The PAC trailer is used within the FIN Copy service only when using the double authentication option.</span></span> <span data-ttu-id="d5d15-124">如果有的話，區塊 5 FIN 使用者對使用者訊息會包含 PAC 結尾後面 MAC 結尾。</span><span class="sxs-lookup"><span data-stu-id="d5d15-124">Block 5 of FIN user-to-user messages include the PAC trailer immediately after the MAC trailer, if present.</span></span> <span data-ttu-id="d5d15-125">此結果計算的訊息，也就是 115，欄位的值的區塊 4 擷取的欄位，如果有的話，而\<驗證結果\>的雙重驗證 MAC 結尾複製服務。</span><span class="sxs-lookup"><span data-stu-id="d5d15-125">This result is calculated on the extracted fields of Block 4 of the message, the value of field 115, if present, and the \<authentication-result\> of the MAC trailer for Copy Services with double authentication.</span></span>  
  
   <span data-ttu-id="d5d15-126">如此一來，PAC 計算中包含結尾區塊的指標 （CrLf-） 和欄位的定義，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5d15-126">As a result, the end-of-block indicator (CrLf-) is included in the PAC calculation and the fields are defined as follows:</span></span>  
  
  - <span data-ttu-id="d5d15-127">前四個字元是 CrLf:</span><span class="sxs-lookup"><span data-stu-id="d5d15-127">The first four characters are CrLf:</span></span>  
  
  - <span data-ttu-id="d5d15-128">欄位和分隔符號都存在，也就是 32A: 20，:，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d5d15-128">The field and the delimiter are present, that is, 32A:, 20:, and so on.</span></span>  
  
  - <span data-ttu-id="d5d15-129">所有的子欄位和分隔符號會出現。</span><span class="sxs-lookup"><span data-stu-id="d5d15-129">All subfields and their delimiters are present.</span></span>  
  
    <span data-ttu-id="d5d15-130">下列程式碼是 PAC 結尾格式範例：</span><span class="sxs-lookup"><span data-stu-id="d5d15-130">The following code is an example of the PAC trailer format:</span></span>  
  
  ```  
  {PAC:[<authentication-result>]}  
  where <authentication-result> is mandatory on input messages only and  
  <authentication-result> = 8!h  
  ```  
  
- <span data-ttu-id="d5d15-131">**CHK （總和檢查碼） 結尾 （針對所有 FIN 訊息的必要項）**</span><span class="sxs-lookup"><span data-stu-id="d5d15-131">**CHK (Checksum) Trailer (mandatory for all FIN messages)**</span></span>  
  
   <span data-ttu-id="d5d15-132">CHK 結尾是所有 FIN 訊息的必要步驟，並計算根據收件者位址 (12 個字元，第九個字元取代*X*再加上文字區塊)。</span><span class="sxs-lookup"><span data-stu-id="d5d15-132">The CHK trailer is mandatory for all FIN messages and is computed based upon the receiver's address (12 characters with the ninth character replaced by *X* plus the text block).</span></span> <span data-ttu-id="d5d15-133">這個後端項目可讓系統，並檢查訊息不會因為系統故障或未偵測到的傳輸錯誤而損毀 CBT。</span><span class="sxs-lookup"><span data-stu-id="d5d15-133">This trailer allows the system and the CBT to check that messages are not corrupted due to a system malfunction or an undetected transmission error.</span></span>  
  
   <span data-ttu-id="d5d15-134">下列程式碼是 CHK 結尾格式範例：</span><span class="sxs-lookup"><span data-stu-id="d5d15-134">The following code is an example of the CHK trailer format:</span></span>  
  
  ```  
  {CHK:<checksum-result>}  
  where <checksum-result> = 12!h  
  ```  
  
## <a name="see-also"></a><span data-ttu-id="d5d15-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d15-135">See Also</span></span>  
 [<span data-ttu-id="d5d15-136">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="d5d15-136">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)