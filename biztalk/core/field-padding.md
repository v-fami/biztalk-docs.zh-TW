---
title: 欄位填補 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47017036-7d64-4222-b574-d2913bf69358
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56aa8490bd9e72677c9c8eefa73e7f6bd8438dfd
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "22246222"
---
# <a name="field-padding"></a><span data-ttu-id="a989b-102">欄位填補</span><span class="sxs-lookup"><span data-stu-id="a989b-102">Field Padding</span></span>

## <a name="overview"></a><span data-ttu-id="a989b-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a989b-103">Overview</span></span>

<span data-ttu-id="a989b-104">當欄位中包含的資料小於欄位的保留字元數目或位元組數目時，就會在分隔和序數記錄中的欄位使用填補字元。</span><span class="sxs-lookup"><span data-stu-id="a989b-104">Pad characters are used in fields within both delimited and positional records when the data contained within the field smaller than the number of characters or bytes reserved for the field.</span></span> <span data-ttu-id="a989b-105">這些字元佔用資料不需要的欄位部分 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="a989b-105">These characters occupy the portion of the field not required by the data, if any.</span></span> <span data-ttu-id="a989b-106">指定欄位的欄位使用填補字元**填補字元**和**Pad Character Type**屬性對應**欄位項目**和**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="a989b-106">Pad characters are specified on a field-by-field basis using the  **Pad Character** and **Pad Character Type** properties of the corresponding **Field Element** and **Field Attribute** nodes.</span></span> <span data-ttu-id="a989b-107">若特定欄位沒有指定的填補字元，則該欄位會使用預設的填補字元，即空格 (" ")。</span><span class="sxs-lookup"><span data-stu-id="a989b-107">If no pad character is specified for a particular field, the default pad character, space (" "), is used for that field.</span></span>  
  
## <a name="inbound-instances"></a><span data-ttu-id="a989b-108">輸入執行個體</span><span class="sxs-lookup"><span data-stu-id="a989b-108">Inbound instances</span></span>
 <span data-ttu-id="a989b-109">若是輸入的執行個體訊息，因為要將執行個體訊息轉譯為其對等的 XML 格式，所以無論特定記錄是序數記錄或分隔記錄，一般檔案解譯器都會捨棄特定欄位的指定或預設填補字元之前置或尾端執行個體。</span><span class="sxs-lookup"><span data-stu-id="a989b-109">For inbound instance messages, regardless of whether a particular record is positional or delimited, the flat file disassembler discards leading or trailing instances for the specified or default pad character for a particular field as the instance message is translated into its equivalent XML form.</span></span> <span data-ttu-id="a989b-110">它是否前置或尾端會捨棄相關填補字元的執行個體取決於是否**理由**屬性對應**欄位項目**和**欄位屬性**節點設定為**右邊**或**左**分別。</span><span class="sxs-lookup"><span data-stu-id="a989b-110">Whether it is leading or trailing instances of the relevant pad character that are discarded depends on whether the **Justification** property of corresponding **Field Element** and **Field Attribute** node is set to **Right** or **Left**, respectively.</span></span>  

## <a name="outbound-instances"></a><span data-ttu-id="a989b-111">輸出執行個體</span><span class="sxs-lookup"><span data-stu-id="a989b-111">Outbound instances</span></span>  
 <span data-ttu-id="a989b-112">若是輸出的執行個體訊息，一般檔案解譯器會將適當數目的指定或預設填補字元插入欄位，使欄位的長度正確。</span><span class="sxs-lookup"><span data-stu-id="a989b-112">For outbound instance messages, the flat file assembler will insert the appropriate number of the specified or default pad character into fields so that the length of the field is correct.</span></span> <span data-ttu-id="a989b-113">之前或之後的資料字元根據是否會插入填補字元 **理由** 對應 **欄位項目** 和 **欄位屬性** 節點設定為 **右邊** 或 **左**, 分別。</span><span class="sxs-lookup"><span data-stu-id="a989b-113">The pad characters will be inserted before or after the data characters based on whether the **Justification** property of the corresponding **Field Element** and **Field Attribute** node is set to **Right** or **Left**, respectively.</span></span>  
  
 <span data-ttu-id="a989b-114">當輸出執行個體訊息中被填補的欄位是否包含在位置記錄， **Positional Offset**和**Positional Length**屬性對應**欄位項目**或**欄位屬性**結合的欄位必須包含的資料字元數 節點，判斷是否有任何填補字元是必要的而且如果是，多少。</span><span class="sxs-lookup"><span data-stu-id="a989b-114">When the field to be padded in an outbound instance message is contained within a positional record, the **Positional Offset** and **Positional Length** properties of the corresponding **Field Element** or **Field Attribute** node, combined with the number of data characters that the field must contain, determine whether any pad characters are required, and if so, how many.</span></span> <span data-ttu-id="a989b-115">當輸出執行個體訊息中被填補的欄位包含在分隔記錄中時，只會填補字元插入時的值**Minimum Length with Pad Character**對應**欄位項目**或**欄位屬性**節點超過資料字元數。</span><span class="sxs-lookup"><span data-stu-id="a989b-115">When the field to be padded in an outbound instance message is contained within a delimited record, pad characters are only inserted when the value of the **Minimum Length with Pad Character** property of the corresponding **Field Element** or **Field Attribute** node exceeds the number of data characters.</span></span>  

## 
<span data-ttu-id="a989b-116">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a989b-116">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="a989b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a989b-117">See Also</span></span>  
 <span data-ttu-id="a989b-118">[欄位考量](../core/field-considerations.md) </span><span class="sxs-lookup"><span data-stu-id="a989b-118">[Field Considerations](../core/field-considerations.md) </span></span>  
 <span data-ttu-id="a989b-119">[欄位左右對齊](../core/field-justification.md) </span><span class="sxs-lookup"><span data-stu-id="a989b-119">[Field Justification](../core/field-justification.md) </span></span>  
 [<span data-ttu-id="a989b-120">位置記錄中欄位位置的規格</span><span class="sxs-lookup"><span data-stu-id="a989b-120">Specification of Field Positions within Positional Records</span></span>](../core/specification-of-field-positions-within-positional-records.md)  