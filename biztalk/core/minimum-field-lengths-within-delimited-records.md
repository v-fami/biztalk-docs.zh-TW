---
title: 分隔記錄中的最小欄位長度 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 992ffbc6a2e0568bc000413bf90b3c92012d4d59
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983311"
---
# <a name="minimum-field-lengths-within-delimited-records"></a><span data-ttu-id="5e4a1-102">分隔記錄中的最小欄位長度</span><span class="sxs-lookup"><span data-stu-id="5e4a1-102">Minimum Field Lengths Within Delimited Records</span></span>
<span data-ttu-id="5e4a1-103">依照定義，序數記錄中的欄位都定義為具有指定的長度。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-103">By definition, the fields in positional records are all defined to have specific exact lengths.</span></span> <span data-ttu-id="5e4a1-104">分隔記錄中的欄位也可以定義為具有最小長度。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-104">Fields in delimited records can also be defined to have a minimum length.</span></span> <span data-ttu-id="5e4a1-105">這項特性由定義 **[Minimum Length with Pad Character**屬性**欄位項目**並**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-105">This characteristic is defined by the **[Minimum Length with Pad Character** property of **Field Element** and **Field Attribute** nodes.</span></span>  

 <span data-ttu-id="5e4a1-106">當您提供非零的值給**Minimum Length with Pad Character**屬性，一般檔案組合器會判斷與欄位相關聯的資料字元數目是否小於設定**Minimum Length with Pad Character**屬性相關的填補字元會用來補足差距。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-106">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file assembler will determine whether the number of data characters associated with the field is smaller than the setting of the **Minimum Length with Pad Character** property, the relevant pad character will be used to make up the difference.</span></span>  

 <span data-ttu-id="5e4a1-107">之前或之後的資料字元為基礎的設定，將會加入填補字元**理由**欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-107">The pad characters will be added before or after the data characters based on the setting of the **Justification** property for the field.</span></span> <span data-ttu-id="5e4a1-108">當**理由**屬性設定為**左**，符合的最小長度所需的任何填補字元將會新增在資料字元之後。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-108">When the **Justification** property is set to **Left**, any pad characters required to meet the minimum length will be added after the data characters.</span></span> <span data-ttu-id="5e4a1-109">當**理由**屬性設定為**右**，符合的最小長度所需的任何填補字元會在資料字元之前新增。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-109">When the **Justification** property is set to **Right**, any pad characters required to meet the minimum length will be added before the data characters.</span></span>  

 <span data-ttu-id="5e4a1-110">當您提供非零的值給**Minimum Length with Pad Character**屬性，一般檔案解譯器會檢查的開頭或結尾 (根據設定的**理由**屬性) 的欄位值存在相關填補字元，以及如果有的話，填補字元都會被捨棄，不會出現在對等所建構的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="5e4a1-110">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file disassembler will examine the beginning or end (based on the setting of the **Justification** property) of the field value for the presence of the relevant pad character, and if present, the pad characters will be discarded and not appear in the equivalent XML message being constructed.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5e4a1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e4a1-111">See Also</span></span>  
- [<span data-ttu-id="5e4a1-112">欄位考量</span><span class="sxs-lookup"><span data-stu-id="5e4a1-112">Field Considerations</span></span>](../core/field-considerations.md)   
- <span data-ttu-id="5e4a1-113">**（一般檔案結構描述中的節點屬性） 的理由**和**Minimum Length with Pad Character （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4a1-113">**Justification (Node Property of Flat File Schemas)** and **Minimum Length with Pad Character (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
