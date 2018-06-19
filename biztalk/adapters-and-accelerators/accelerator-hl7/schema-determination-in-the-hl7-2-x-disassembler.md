---
title: HL7 2.X 解譯器中的結構描述判斷 |Microsoft 文件
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
ms.openlocfilehash: 6314f9651d09dbb041d2e8851565e904366c9efe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206086"
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a><span data-ttu-id="d8e45-102">HL7 2.X 解譯器中的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="d8e45-102">Schema Determination in the HL7 2.X Disassembler</span></span>
<span data-ttu-id="d8e45-103">HL7 2.X 訊息包含標頭區段 (MSH)，後面接著的主體區段的數目和選擇性的 Z 區段數目。</span><span class="sxs-lookup"><span data-stu-id="d8e45-103">HL7 2.X messages contain a header segment (MSH), followed by a number of body segments and an optional number of Z segments.</span></span> <span data-ttu-id="d8e45-104">MSH 包含 21 的欄位。</span><span class="sxs-lookup"><span data-stu-id="d8e45-104">MSH contains 21 fields.</span></span>  
  
 <span data-ttu-id="d8e45-105">當訊息抵達時，2.X 引擎會讀取標頭來判斷要用來剖析訊息內文結構描述。</span><span class="sxs-lookup"><span data-stu-id="d8e45-105">When a message arrives, the 2.X engine reads the header to determine the schema to use to parse the message body.</span></span> <span data-ttu-id="d8e45-106">就會發生以下一連串事件：</span><span class="sxs-lookup"><span data-stu-id="d8e45-106">The following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="d8e45-107">解譯器會讀取 MSH3 值 （來源合作對象） 可判斷下列的驗證選項：</span><span class="sxs-lookup"><span data-stu-id="d8e45-107">The disassembler reads the value of MSH3 (source party) to determine the following validation options:</span></span>  
  
    1.  <span data-ttu-id="d8e45-108">是否要為主體執行 XML 驗證</span><span class="sxs-lookup"><span data-stu-id="d8e45-108">Whether to perform XML validation for the body</span></span>  
  
    2.  <span data-ttu-id="d8e45-109">是否要驗證自訂資料欄位在本文資料</span><span class="sxs-lookup"><span data-stu-id="d8e45-109">Whether to validate custom data type fields in the body data</span></span>  
  
    3.  <span data-ttu-id="d8e45-110">是否允許尾端分隔符號，在主體中</span><span class="sxs-lookup"><span data-stu-id="d8e45-110">Whether to allow trailing delimiters in the body</span></span>  
  
    4.  <span data-ttu-id="d8e45-111">內文結構描述的目標命名空間是什麼 (**Targetns-xdrt.xml**)</span><span class="sxs-lookup"><span data-stu-id="d8e45-111">What the target namespace of the body schema is (**TargetNS**)</span></span>  
  
2.  <span data-ttu-id="d8e45-112">解譯器接著會讀取 MSH9 和 MSH12 判斷主體的根節點名稱。</span><span class="sxs-lookup"><span data-stu-id="d8e45-112">The disassembler then reads MSH9 and MSH12 to determine the root node name of the body.</span></span> <span data-ttu-id="d8e45-113">此演算法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d8e45-113">The algorithm is as follows:</span></span>  
  
    ```  
    Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
    ```  
  
     [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="d8e45-114">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 永遠可以在尾端加入訊息標頭中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d8e45-114"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) always allows trailing delimiters in a message header.</span></span> <span data-ttu-id="d8e45-115">引擎會檢查每一行的第一次三個字元的區段識別項。</span><span class="sxs-lookup"><span data-stu-id="d8e45-115">The engine examines the segment identifier that is the first three characters of each line.</span></span> <span data-ttu-id="d8e45-116">它會保存產生 XML 的內文結構描述定義的所有區段。</span><span class="sxs-lookup"><span data-stu-id="d8e45-116">It keeps on generating XML for all segments that the body schema defines.</span></span> <span data-ttu-id="d8e45-117">當它遇到未定義的區段時，它會將該區段為 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="d8e45-117">When it encounters an undefined segment, it treats that segment as a Z segment.</span></span> <span data-ttu-id="d8e45-118">從該點上，所有未定義的區段會構成 Z 訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="d8e45-118">From that point on, all undefined segments constitute the Z part of the message.</span></span> <span data-ttu-id="d8e45-119">下一步的 MSH 標記本訊息結尾。</span><span class="sxs-lookup"><span data-stu-id="d8e45-119">The next MSH marks the end of this message.</span></span> <span data-ttu-id="d8e45-120">對於批次的訊息下, 一步的 MSH 或 BTS （批次結尾區段已標記） 結束標記的訊息。</span><span class="sxs-lookup"><span data-stu-id="d8e45-120">For batch messages, the next MSH or BTS (the batch trailer segment tag) marks the end of a message.</span></span> <span data-ttu-id="d8e45-121">Z 區段只能包含結構描述中未宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="d8e45-121">A Z segment can only contain segments that are undeclared in a schema.</span></span> <span data-ttu-id="d8e45-122">就會發生宣告的區段的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8e45-122">It is an error to encounter a declared segment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e45-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8e45-123">See Also</span></span>  
 <span data-ttu-id="d8e45-124">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="d8e45-124">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="d8e45-125">BTAHL72X 一般檔案處理</span><span class="sxs-lookup"><span data-stu-id="d8e45-125">BTAHL72X Flat File Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)