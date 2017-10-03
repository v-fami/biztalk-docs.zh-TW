---
title: "欄位左右對齊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04380208-9bfd-43cf-a279-104daea2b978
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da9209040e64380b3a7a167dd013a15232543a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-justification"></a><span data-ttu-id="a993a-102">欄位左右對齊</span><span class="sxs-lookup"><span data-stu-id="a993a-102">Field Justification</span></span>

## <a name="overview"></a><span data-ttu-id="a993a-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a993a-103">Overview</span></span>
<span data-ttu-id="a993a-104">欄位左右對齊關係著欄位中的資料字元是在附加填補字元的前面 (靠左對齊) 或後面 (靠右對齊)。</span><span class="sxs-lookup"><span data-stu-id="a993a-104">Field justification concerns whether the data characters in a field occur before (left-aligned) or after (right-aligned) any accompanying pad characters.</span></span>  
  
 <span data-ttu-id="a993a-105">有時欄位中所包含的資料字元在該欄位中不需要所有的空格。</span><span class="sxs-lookup"><span data-stu-id="a993a-105">Sometimes the data characters contained within a field do not require all of the space dedicated to that field.</span></span> <span data-ttu-id="a993a-106">這是最常在位置記錄，其中固定的位元組數或欄位的字元，則為 true，由**Positional Length**和**Positional Offset**屬性。</span><span class="sxs-lookup"><span data-stu-id="a993a-106">This is true most frequently in positional records, where the number of bytes or characters dedicated to a field is fixed, as determined by the **Positional Length** and **Positional Offset** properties.</span></span> <span data-ttu-id="a993a-107">這在資料項目小於欄位長度的實例中是很常見的，會在欄位未使用的部分填入填補字元。</span><span class="sxs-lookup"><span data-stu-id="a993a-107">It is common in such scenarios that the item of data is smaller than the field length, with the unused portion of the field being filled with pad characters.</span></span>  
  
 <span data-ttu-id="a993a-108">分隔記錄中，這類填補也會發生時的值**Minimum Length with Pad Character**屬性超過儲存相關資料項目所需的空間。</span><span class="sxs-lookup"><span data-stu-id="a993a-108">Such padding can also occur in delimited records when the value of the **Minimum Length with Pad Character** property exceeds the space required to store the relevant item of data.</span></span>  
  
 <span data-ttu-id="a993a-109">在這兩個這類情況下，值**理由**屬性 (**左**或**右邊**) 之相關**欄位項目**或**欄位屬性**節點判斷是否填補字元會遵循 （靠左對齊） 的資料字元或填補字元會在前面 （靠右對齊） 的資料字元。</span><span class="sxs-lookup"><span data-stu-id="a993a-109">In both such cases, the value of the **Justification** property (**Left** or **Right**) of the relevant **Field Element** or **Field Attribute** node determines whether the pad characters will follow the data characters (left-aligned) or whether the pad characters will precede the data characters (right-aligned).</span></span>  
  
 <span data-ttu-id="a993a-110">當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息，**理由**屬性可在剖析對應的欄位。</span><span class="sxs-lookup"><span data-stu-id="a993a-110">When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the **Justification** property is used when parsing the corresponding field.</span></span> <span data-ttu-id="a993a-111">當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息中，**理由**屬性用來判斷當填補字元相關聯的特定欄位中，如果有的話，應加入至資料流： 之前或之後的對應資料字元。</span><span class="sxs-lookup"><span data-stu-id="a993a-111">When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the **Justification** property is used to determine when the pad characters associated with a particular field, if any, should be added to the data stream: either before or after the corresponding data characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a993a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a993a-112">See Also</span></span>  
- [<span data-ttu-id="a993a-113">欄位考量</span><span class="sxs-lookup"><span data-stu-id="a993a-113">Field Considerations</span></span>](../core/field-considerations.md)   
- <span data-ttu-id="a993a-114">下列屬性的詳細資訊[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="a993a-114">More info on the following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    - <span data-ttu-id="a993a-115">對齊方式 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="a993a-115">Justification (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="a993a-116">Positional Offset （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="a993a-116">Positional Offset (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="a993a-117">Positional Length （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="a993a-117">Positional Length (Node Property of Flat File Schemas)</span></span>