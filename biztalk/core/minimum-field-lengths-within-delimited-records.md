---
title: "分隔記錄中的最小欄位長度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d803eb311bda7c27db5a05830f7a84f9b9857e8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="minimum-field-lengths-within-delimited-records"></a><span data-ttu-id="20e83-102">分隔記錄中的最小欄位長度</span><span class="sxs-lookup"><span data-stu-id="20e83-102">Minimum Field Lengths Within Delimited Records</span></span>
<span data-ttu-id="20e83-103">依照定義，序數記錄中的欄位都定義為具有指定的長度。</span><span class="sxs-lookup"><span data-stu-id="20e83-103">By definition, the fields in positional records are all defined to have specific exact lengths.</span></span> <span data-ttu-id="20e83-104">分隔記錄中的欄位也可以定義為具有最小長度。</span><span class="sxs-lookup"><span data-stu-id="20e83-104">Fields in delimited records can also be defined to have a minimum length.</span></span> <span data-ttu-id="20e83-105">這項特性由定義**[Minimum Length with Pad Character**屬性**欄位項目**和**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="20e83-105">This characteristic is defined by the **[Minimum Length with Pad Character** property of **Field Element** and **Field Attribute** nodes.</span></span>  
  
 <span data-ttu-id="20e83-106">當您提供非零值給**Minimum Length with Pad Character**屬性，一般檔案組合器將會決定欄位相關聯的資料字元數目是否小於設定**Minimum Length with Pad Character**屬性相關的填補字元會用來補足差距。</span><span class="sxs-lookup"><span data-stu-id="20e83-106">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file assembler will determine whether the number of data characters associated with the field is smaller than the setting of the **Minimum Length with Pad Character** property, the relevant pad character will be used to make up the difference.</span></span>  
  
 <span data-ttu-id="20e83-107">之前或之後的資料字元為基礎的設定，將會加入填補字元**理由**欄位的屬性。</span><span class="sxs-lookup"><span data-stu-id="20e83-107">The pad characters will be added before or after the data characters based on the setting of the **Justification** property for the field.</span></span> <span data-ttu-id="20e83-108">當**理由**屬性設定為**左**，在資料字元之後，就會新增為滿足最小長度所需的任何填補字元。</span><span class="sxs-lookup"><span data-stu-id="20e83-108">When the **Justification** property is set to **Left**, any pad characters required to meet the minimum length will be added after the data characters.</span></span> <span data-ttu-id="20e83-109">當**理由**屬性設定為**右邊**，為滿足最小長度所需的任何填補字元將會加入在資料字元之前。</span><span class="sxs-lookup"><span data-stu-id="20e83-109">When the **Justification** property is set to **Right**, any pad characters required to meet the minimum length will be added before the data characters.</span></span>  
  
 <span data-ttu-id="20e83-110">當您提供非零值給**Minimum Length with Pad Character**屬性，一般檔案解譯器會檢查的開頭或結尾 (根據設定的**理由**屬性) 的欄位值的相關填補字元，存在，如果有的話，填補字元會被捨棄，並且不會出現在要建構的對等 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="20e83-110">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file disassembler will examine the beginning or end (based on the setting of the **Justification** property) of the field value for the presence of the relevant pad character, and if present, the pad characters will be discarded and not appear in the equivalent XML message being constructed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e83-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20e83-111">See Also</span></span>  
-  [<span data-ttu-id="20e83-112">欄位考量</span><span class="sxs-lookup"><span data-stu-id="20e83-112">Field Considerations</span></span>](../core/field-considerations.md)   
-  <span data-ttu-id="20e83-113">**對齊方式 （一般檔案結構描述中的節點屬性）**和**Minimum Length with Pad Character （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="20e83-113">**Justification (Node Property of Flat File Schemas)** and **Minimum Length with Pad Character (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>