---
title: "EDI 交換結構元素 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f47ae2-fa0f-4d88-a700-85f3d515d2d0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc07ae40a3665b47b446b61e24954ca9c588a6a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-interchange-structural-element"></a><span data-ttu-id="3abd7-102">EDI 交換結構元素</span><span class="sxs-lookup"><span data-stu-id="3abd7-102">EDI Interchange Structural Element</span></span>
<span data-ttu-id="3abd7-103">此交換是 EDI 訊息的最高層結構元素。</span><span class="sxs-lookup"><span data-stu-id="3abd7-103">The interchange is the highest-level structural element of an EDI message.</span></span> <span data-ttu-id="3abd7-104">它包含由兩個夥伴交換之一或多個群組的集合。</span><span class="sxs-lookup"><span data-stu-id="3abd7-104">It contains a collection of one or more groups exchanged by two partners.</span></span> <span data-ttu-id="3abd7-105">交換的目的地必須是單一交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="3abd7-105">The destination of an interchange must be a single trading partner.</span></span> <span data-ttu-id="3abd7-106">交換可能會包含一或多種類型的交易集/訊息。</span><span class="sxs-lookup"><span data-stu-id="3abd7-106">Interchanges may contain transaction sets/message of one or more than one type.</span></span>  
  
 <span data-ttu-id="3abd7-107">進行交換時，交換本身以及其中的群組和交易集/訊息是由標頭定義。</span><span class="sxs-lookup"><span data-stu-id="3abd7-107">With an interchange, the interchange itself and the groups and transaction sets/messages within it are defined by headers.</span></span> <span data-ttu-id="3abd7-108">區段、資料元素和子元素以分隔符號來區隔。</span><span class="sxs-lookup"><span data-stu-id="3abd7-108">Segments, data elements, and sub-elements are delimited by separators.</span></span> <span data-ttu-id="3abd7-109">雖然每個分隔符號都具有預設值，但是可能會針對合作對象定義成不同的字元。</span><span class="sxs-lookup"><span data-stu-id="3abd7-109">Each separator has a default value, but may be defined as a different character for the party.</span></span> <span data-ttu-id="3abd7-110">在 EDIFACT 交換中，選取做為交換中之分隔符號的字元是在單獨的 UNA 交換標頭中定義。</span><span class="sxs-lookup"><span data-stu-id="3abd7-110">In EDIFACT interchanges, the characters selected for use as separators in the interchange are defined in a separate UNA Interchange Header.</span></span> <span data-ttu-id="3abd7-111">在 X12 交換中，分隔符號是在 ISA 交換標頭中定義。</span><span class="sxs-lookup"><span data-stu-id="3abd7-111">In X12 interchanges, separators are defined in the ISA Interchange Header.</span></span> <span data-ttu-id="3abd7-112">請注意，在 X12 中，資料元素分隔符號是位於第四個字元位置的字元，而資料區段結束字元是位於最後一個字元位置的字元。</span><span class="sxs-lookup"><span data-stu-id="3abd7-112">Note that in X12, the data element separator is the character in the fourth character position, and the data segment terminator is the character in the last character position.</span></span> <span data-ttu-id="3abd7-113">其他 X12 分隔符號和所有的 EDIFACT 分隔符號由所定義的欄位，例如 X12 ISA16 欄位，EDIFACT 資料項目分隔符號 UNA2 欄位的元件分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3abd7-113">The other X12 separators and all the EDIFACT separators are defined by fields, such as the X12 component separator by the ISA16 field and the EDIFACT data element separator by the UNA2 field.</span></span>  
  
 <span data-ttu-id="3abd7-114">此交換包含定義 EDI 訊息的信封。</span><span class="sxs-lookup"><span data-stu-id="3abd7-114">The interchange includes an envelope that defines the EDI message.</span></span> <span data-ttu-id="3abd7-115">此信封必須以交換標頭 (X12 中的 ISA 或 EDIFACT 中的 UNA/UNB) 為開頭，而且它必須以交換結尾 (IEA/UNZ) 為結尾。</span><span class="sxs-lookup"><span data-stu-id="3abd7-115">The envelope must start with an Interchange Header (ISA in X12 or UNA/UNB in EDIFACT), and it must end with an Interchange Trailer (IEA/UNZ).</span></span> <span data-ttu-id="3abd7-116">交換標頭包含定義傳送者和接收者的元素、日期與時間、版本號碼、與標頭和結尾相符的控制編號，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3abd7-116">The Interchange Header includes elements defining the sender and receiver, a date and time, a version number, a control number that matches the header and the trailer, and other information.</span></span>  
  
 <span data-ttu-id="3abd7-117">ISA12 和 GS8 欄位 (適用於 X12 交換) 以及 UNH2 欄位 (適用於 EDIFACT 交換) 包含結構描述探索所需的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="3abd7-117">The ISA12 and GS8 fields (for X12 interchanges) and the UNH2 field (for EDIFACT interchanges) contain version information that is required for schema discovery.</span></span>  
  
 <span data-ttu-id="3abd7-118">交換結尾具有指出交換內部群組數目的元素。</span><span class="sxs-lookup"><span data-stu-id="3abd7-118">The Interchange Trailer has an element that indicates the number of groups within the interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3abd7-119">功能安全性標頭、功能確保標頭、功能安全性值區段和功能安全性結尾區段已超出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 的範圍。</span><span class="sxs-lookup"><span data-stu-id="3abd7-119">The functional security header, functional assurance header, functional security value segment, and functional security trailer segments are beyond the scope of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2.</span></span> <span data-ttu-id="3abd7-120">如果您收到含有這些區段的交換，系統就會擱置此作業並顯示錯誤記錄，表示這些是無法識別的區段。</span><span class="sxs-lookup"><span data-stu-id="3abd7-120">If an interchange with these segments is received, it will be suspended with an error log indicating that these are unidentified segments.</span></span>