---
title: "設定位移量驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, validating
- validating, amounts
- amounts, offsets
- offsets
ms.assetid: 39d5510c-52e6-4fd9-9632-582b508f04d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cfae474407daa7dd3c0b95db3fed076a581cf1c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="setting-offsets-for-amount-validation"></a><span data-ttu-id="0f314-102">設定位移量驗證</span><span class="sxs-lookup"><span data-stu-id="0f314-102">Setting Offsets for Amount Validation</span></span>
<span data-ttu-id="0f314-103">在訊息類型 MT102，MT103，以及 MT103PLUS 量欄位的使用方式規則會驗證其各自的驗證原則中的規則。</span><span class="sxs-lookup"><span data-stu-id="0f314-103">The usage rules for Amount fields in message types MT102, MT103, and MT103PLUS are validated by rules in their respective validation policies.</span></span> <span data-ttu-id="0f314-104">數量欄位可以完全相符，或是可驗證的金額的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0f314-104">The Amount fields can be matched exactly or can be validated to be within a range of amounts.</span></span>  
  
 <span data-ttu-id="0f314-105">若要啟用驗證的範圍內，您可以指定位移的百分比在相關的驗證原則中的方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="0f314-105">To enable validation within a range, you specify an offset percentage in the method call in the relevant validation policy.</span></span> <span data-ttu-id="0f314-106">例如，如果您設定欄位的金額為 100，位移的百分比為 10%，有效的金額會 110 （含) 到 90 的任何值。</span><span class="sxs-lookup"><span data-stu-id="0f314-106">For example, if the amount that you set for the field is 100, and the offset percentage is 10 percent, a valid amount would be any value from 90 to 110, inclusive.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="0f314-107">提供這項支援 MT102、 MT102PLUS 和 MT103 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="0f314-107"> provides this support for the MT102, MT102PLUS, and MT103 message types.</span></span>  
  
 <span data-ttu-id="0f314-108">在指定位移的百分比**IsValidSettlementAmount**或**IsValidInterbankSettledAmount**驗證原則中的方法。</span><span class="sxs-lookup"><span data-stu-id="0f314-108">The offset percentage is specified in either the **IsValidSettlementAmount** or **IsValidInterbankSettledAmount** method in the validation policy.</span></span> <span data-ttu-id="0f314-109">**IsValidSettlementAmount**方法會實作 MT102 和 MT102PLUS 訊息量欄位的使用方式規則。</span><span class="sxs-lookup"><span data-stu-id="0f314-109">The **IsValidSettlementAmount** method implements the usage rule for Amount fields of MT102 and MT102PLUS messages.</span></span> <span data-ttu-id="0f314-110">**IsValidInterbankSettledAmount**方法會實作 MT103 訊息量欄位的使用方式規則。</span><span class="sxs-lookup"><span data-stu-id="0f314-110">The **IsValidInterbankSettledAmount** method implements the usage rule for Amount fields of MT103 messages.</span></span> <span data-ttu-id="0f314-111">您 OffsetPercent 引數，也就是其中一個這些方法的第十個引數中指定位移的百分比。</span><span class="sxs-lookup"><span data-stu-id="0f314-111">You specify the offset percentage in the OffsetPercent argument, which is the tenth argument of either of those methods.</span></span>  
  
 <span data-ttu-id="0f314-112">百分比位移設定時，套用至下列欄位：</span><span class="sxs-lookup"><span data-stu-id="0f314-112">When set, the percentage offset applies to the following fields:</span></span>  
  
|<span data-ttu-id="0f314-113">訊息類型</span><span class="sxs-lookup"><span data-stu-id="0f314-113">Message type</span></span>|<span data-ttu-id="0f314-114">位移通過驗證的欄位</span><span class="sxs-lookup"><span data-stu-id="0f314-114">Fields validated with offsets</span></span>|  
|------------------|-----------------------------------|  
|<span data-ttu-id="0f314-115">MT102 或 MT102PLUS</span><span class="sxs-lookup"><span data-stu-id="0f314-115">MT102 or MT102PLUS</span></span>|<span data-ttu-id="0f314-116">32</span><span class="sxs-lookup"><span data-stu-id="0f314-116">32</span></span><br /><br /> <span data-ttu-id="0f314-117">33B</span><span class="sxs-lookup"><span data-stu-id="0f314-117">33B</span></span>|  
|<span data-ttu-id="0f314-118">MT103</span><span class="sxs-lookup"><span data-stu-id="0f314-118">MT103</span></span>|<span data-ttu-id="0f314-119">19，順序 C</span><span class="sxs-lookup"><span data-stu-id="0f314-119">19, Sequence C</span></span><br /><br /> <span data-ttu-id="0f314-120">31A，順序 C</span><span class="sxs-lookup"><span data-stu-id="0f314-120">31A, Sequence C</span></span><br /><br /> <span data-ttu-id="0f314-121">72 G</span><span class="sxs-lookup"><span data-stu-id="0f314-121">72G</span></span>|  
  
### <a name="to-set-an-offset-percentage"></a><span data-ttu-id="0f314-122">若要設定位移的百分比</span><span class="sxs-lookup"><span data-stu-id="0f314-122">To set an offset percentage</span></span>  
  
1.  <span data-ttu-id="0f314-123">開啟文字編輯器，例如 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="0f314-123">Open a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="0f314-124">在編輯器中，瀏覽至您要設定位移的百分比的訊息驗證原則的位置。</span><span class="sxs-lookup"><span data-stu-id="0f314-124">In the editor, browse to the location of the message validation policy in which you want to set an offset percentage.</span></span> <span data-ttu-id="0f314-125">例如，您可以找到訊息驗證原則 MT103 訊息類型，MT103_Validation_Policy.xml，在*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT \<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103。</span><span class="sxs-lookup"><span data-stu-id="0f314-125">For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.</span></span> <span data-ttu-id="0f314-126">開啟 驗證原則。</span><span class="sxs-lookup"><span data-stu-id="0f314-126">Open the validation policy.</span></span>  
  
3.  <span data-ttu-id="0f314-127">在原則中，搜尋上 IsValidSettlementAmount MT102 和 MT102PLUS 訊息或 IsValidInterbankSettledAmount MT103 訊息。</span><span class="sxs-lookup"><span data-stu-id="0f314-127">In the policy, search on IsValidSettlementAmount for MT102 and MT102PLUS messages or IsValidInterbankSettledAmount for MT103 messages.</span></span>  
  
4.  <span data-ttu-id="0f314-128">向下計數的第十個引數。</span><span class="sxs-lookup"><span data-stu-id="0f314-128">Count down to the tenth argument.</span></span> <span data-ttu-id="0f314-129">輸入引數中的位移的百分比。</span><span class="sxs-lookup"><span data-stu-id="0f314-129">Enter the percentage of the offset in the argument.</span></span>  
  
5.  <span data-ttu-id="0f314-130">儲存檔案，然後關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="0f314-130">Save the file, and then close the editor.</span></span>