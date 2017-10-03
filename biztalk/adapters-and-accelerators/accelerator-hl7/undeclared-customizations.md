---
title: "未宣告的自訂項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeclared customizations
- Z objects, undeclared customizations
- customizing, Z objects
- customizing, undeclared customizations
ms.assetid: f062dbb7-2c78-47ea-a927-99e1fba4854b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77f688e4cf6a4bbb55243d9f5f6f60e144bad862
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="undeclared-customizations"></a><span data-ttu-id="be1a1-102">未宣告的自訂項目</span><span class="sxs-lookup"><span data-stu-id="be1a1-102">Undeclared Customizations</span></span>
<span data-ttu-id="be1a1-103">您可以新增至訊息的資料，但未定義的格式或資料的本質。</span><span class="sxs-lookup"><span data-stu-id="be1a1-103">You can add data to a message without defining the format or nature of the data.</span></span> <span data-ttu-id="be1a1-104">您使用未宣告的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="be1a1-104">You do so by using undeclared Z segments.</span></span> <span data-ttu-id="be1a1-105">未宣告的 Z 區段是未預期的執行個體訊息結尾處。</span><span class="sxs-lookup"><span data-stu-id="be1a1-105">Undeclared Z segments are unexpected instances at the end of a message.</span></span> <span data-ttu-id="be1a1-106">XML 剖析器/驗證程式不會驗證區段。</span><span class="sxs-lookup"><span data-stu-id="be1a1-106">The parser/XML validator does not validate the segment.</span></span> <span data-ttu-id="be1a1-107">未定義任何結構描述。</span><span class="sxs-lookup"><span data-stu-id="be1a1-107">It is not defined by any schema.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="be1a1-108">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 視為二進位大型物件 (BLOB) 的區段。</span><span class="sxs-lookup"><span data-stu-id="be1a1-108"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) treats the segment as a binary large object (BLOB).</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="be1a1-109">將未宣告的 Z 區段資料，透過傳遞做為三部分訊息的第三個部分。</span><span class="sxs-lookup"><span data-stu-id="be1a1-109"> passes undeclared Z segment data through as the third part of a three-part message.</span></span> <span data-ttu-id="be1a1-110">三個部分是標頭、 內文和未宣告的 Z 區段，也稱為 Z 組件。</span><span class="sxs-lookup"><span data-stu-id="be1a1-110">The three parts are the header, the body, and the undeclared Z segment, also called the Z part.</span></span> <span data-ttu-id="be1a1-111">區段識別碼開頭為字母"Z"，比方說，「 ZPD 「 自訂病患的人口統計資訊，識別 Z 組件。</span><span class="sxs-lookup"><span data-stu-id="be1a1-111">A segment ID beginning with the letter "Z", for instance, "ZPD" for custom patient demographics information, identifies the Z part.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1a1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1a1-112">See Also</span></span>  
 <span data-ttu-id="be1a1-113">[宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md) </span><span class="sxs-lookup"><span data-stu-id="be1a1-113">[Declared Customizations](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md) </span></span>  
 <span data-ttu-id="be1a1-114">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="be1a1-114">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="be1a1-115">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="be1a1-115">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="be1a1-116">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="be1a1-116">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="be1a1-117">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="be1a1-117">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)