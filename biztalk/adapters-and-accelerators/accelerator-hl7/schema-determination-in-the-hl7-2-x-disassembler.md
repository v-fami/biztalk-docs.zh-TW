---
title: HL7 2.X 反組譯工具中的結構描述判斷 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- header segments [2.X]
- 2.X messages, header segments
- messages, parsing messages
- MSH
- disassembler, parsing messages
- 2.X messages, MSH
ms.assetid: afd45c4c-2feb-44eb-b3bd-49fe114eb893
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fcdd3b0ba6565aff4d401c8e43ae2f86fc37384
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010255"
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a><span data-ttu-id="b59ad-102">HL7 2.X 反組譯工具中的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="b59ad-102">Schema Determination in the HL7 2.X Disassembler</span></span>
<span data-ttu-id="b59ad-103">HL7 2.X 訊息包含標頭區段 (MSH)，後面接著的主體區段的數目和選擇性的 Z 區段的數目。</span><span class="sxs-lookup"><span data-stu-id="b59ad-103">HL7 2.X messages contain a header segment (MSH), followed by a number of body segments and an optional number of Z segments.</span></span> <span data-ttu-id="b59ad-104">MSH 包含 21 的欄位。</span><span class="sxs-lookup"><span data-stu-id="b59ad-104">MSH contains 21 fields.</span></span>  
  
 <span data-ttu-id="b59ad-105">當訊息抵達時，2.X 引擎讀取來判斷要用來剖析訊息內文結構描述的標頭。</span><span class="sxs-lookup"><span data-stu-id="b59ad-105">When a message arrives, the 2.X engine reads the header to determine the schema to use to parse the message body.</span></span> <span data-ttu-id="b59ad-106">就會發生以下一連串事件：</span><span class="sxs-lookup"><span data-stu-id="b59ad-106">The following sequence of events occurs:</span></span>  
  
1. <span data-ttu-id="b59ad-107">解譯器會讀取 MSH3 的值 （來源合作對象） 可判斷下列的驗證選項：</span><span class="sxs-lookup"><span data-stu-id="b59ad-107">The disassembler reads the value of MSH3 (source party) to determine the following validation options:</span></span>  
  
   1.  <span data-ttu-id="b59ad-108">是否要執行 XML 驗證的主體</span><span class="sxs-lookup"><span data-stu-id="b59ad-108">Whether to perform XML validation for the body</span></span>  
  
   2.  <span data-ttu-id="b59ad-109">是否要驗證自訂資料類型之主體資料的欄位</span><span class="sxs-lookup"><span data-stu-id="b59ad-109">Whether to validate custom data type fields in the body data</span></span>  
  
   3.  <span data-ttu-id="b59ad-110">是否允許尾端分隔符號，在主體中</span><span class="sxs-lookup"><span data-stu-id="b59ad-110">Whether to allow trailing delimiters in the body</span></span>  
  
   4.  <span data-ttu-id="b59ad-111">本文結構描述的目標命名空間的功能 (**Targetns-xdrt.xml**)</span><span class="sxs-lookup"><span data-stu-id="b59ad-111">What the target namespace of the body schema is (**TargetNS**)</span></span>  
  
2. <span data-ttu-id="b59ad-112">反組譯工具接著會讀取 MSH9 並 MSH12 判斷主體的根節點名稱。</span><span class="sxs-lookup"><span data-stu-id="b59ad-112">The disassembler then reads MSH9 and MSH12 to determine the root node name of the body.</span></span> <span data-ttu-id="b59ad-113">此演算法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b59ad-113">The algorithm is as follows:</span></span>  
  
   ```  
   Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
   ```  
  
    <span data-ttu-id="b59ad-114">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 永遠可以在尾端加入訊息標頭中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b59ad-114">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) always allows trailing delimiters in a message header.</span></span> <span data-ttu-id="b59ad-115">引擎會檢查每一行的第三個字元的區段識別碼。</span><span class="sxs-lookup"><span data-stu-id="b59ad-115">The engine examines the segment identifier that is the first three characters of each line.</span></span> <span data-ttu-id="b59ad-116">它會保留產生 XML 內文結構描述所定義的所有區段。</span><span class="sxs-lookup"><span data-stu-id="b59ad-116">It keeps on generating XML for all segments that the body schema defines.</span></span> <span data-ttu-id="b59ad-117">發生未定義的區段，它會將該區段為 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="b59ad-117">When it encounters an undefined segment, it treats that segment as a Z segment.</span></span> <span data-ttu-id="b59ad-118">從那時起，所有未定義的區段構成 Z 訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="b59ad-118">From that point on, all undefined segments constitute the Z part of the message.</span></span> <span data-ttu-id="b59ad-119">下一步 的 MSH 標示此訊息的結束。</span><span class="sxs-lookup"><span data-stu-id="b59ad-119">The next MSH marks the end of this message.</span></span> <span data-ttu-id="b59ad-120">批次訊息的 BTS （批次結尾區段標記） 的下一步 的 MSH 結束標記訊息。</span><span class="sxs-lookup"><span data-stu-id="b59ad-120">For batch messages, the next MSH or BTS (the batch trailer segment tag) marks the end of a message.</span></span> <span data-ttu-id="b59ad-121">Z 區段只能包含結構描述中未宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="b59ad-121">A Z segment can only contain segments that are undeclared in a schema.</span></span> <span data-ttu-id="b59ad-122">就會遇到的宣告的區段中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b59ad-122">It is an error to encounter a declared segment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59ad-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b59ad-123">See Also</span></span>  
 <span data-ttu-id="b59ad-124">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="b59ad-124">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="b59ad-125">BTAHL72X 一般檔案處理</span><span class="sxs-lookup"><span data-stu-id="b59ad-125">BTAHL72X Flat File Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)