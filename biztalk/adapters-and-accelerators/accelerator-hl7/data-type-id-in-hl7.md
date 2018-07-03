---
title: HL7 中的資料類型識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types, data type ID
- data types, messages
- messages, data types
ms.assetid: d1412886-ff0b-4333-b01e-1c3ae45240e2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d7251ce1c041ebfd2f523e3304bd253fec22fb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983007"
---
# <a name="data-type-id-in-hl7"></a><span data-ttu-id="7ad4b-102">HL7 中的資料類型識別碼</span><span class="sxs-lookup"><span data-stu-id="7ad4b-102">Data Type ID in HL7</span></span>
<span data-ttu-id="7ad4b-103">在 HL7 V2.1 的情況下的資料型別 ID 會是未定義的資料類型的預留位置。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-103">In the case of HL7 V2.1, the data type ID is a placeholder for undefined data types.</span></span> <span data-ttu-id="7ad4b-104">其使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-104">The following are examples of its usage:</span></span>  
  
- <span data-ttu-id="7ad4b-105">ST 欄位的表單中的資料類型為 SI (順序 ID)。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-105">The data type in the form of an ST field is SI (Sequence ID).</span></span>  
  
- <span data-ttu-id="7ad4b-106">NM 欄位的表單中的資料類型是複合欄位。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-106">The data type in the form of an NM field is composite fields.</span></span>  
  
  <span data-ttu-id="7ad4b-107">特別定義的複合資料類型的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-107">The following are examples of specifically defined composite data types:</span></span>  
  
- <span data-ttu-id="7ad4b-108">CK： 以檢查數字的複合識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-108">CK: Composite ID with check digit.</span></span> <span data-ttu-id="7ad4b-109">例如：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-109">For example:</span></span>  
  
  ```  
  |128952^6^M11|  
  ```  
  
- <span data-ttu-id="7ad4b-110">CN： 複合的識別碼和名稱。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-110">CN: Composite ID number and name.</span></span> <span data-ttu-id="7ad4b-111">例如：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-111">For example:</span></span>  
  
  ```  
  |12372^RIGGINS^JOHN^""^MD|  
  |12372|  
  |^RIGGINS^JOHN^""^MD|  
  ```  
  
- <span data-ttu-id="7ad4b-112">也是如此： 複合單位數量。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-112">CQ: Composite quantity with units.</span></span> <span data-ttu-id="7ad4b-113">例如：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-113">For example:</span></span>  
  
  ```  
  |123.7^ML|  
  ```  
  
- <span data-ttu-id="7ad4b-114">CE： 自動程式化項目。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-114">CE: Coded element.</span></span> <span data-ttu-id="7ad4b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="7ad4b-115">For example:</span></span>  
  
  ```  
  |54.21^Laparoscopy^I9C^42112^^AS4|  
  ```  
  
  <span data-ttu-id="7ad4b-116">此資料類型會當地語系化，而且網站定義。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-116">This data type is localized and site-defined.</span></span> <span data-ttu-id="7ad4b-117">此外，HL7 V2.1 不提供此 HL7 Access 資料庫中的資料類型的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-117">Additionally, HL7 V2.1 does not provide the coverage for this data type in the HL7 Access database.</span></span> <span data-ttu-id="7ad4b-118">用於產生結構描述，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 假設 HL7 V2.2 資料型別是否有效，然後使用此資訊來建置結構描述。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-118">For generating your schemas, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) assumes that the HL7 V2.2 data types are valid, and uses this information to build the schemas.</span></span> <span data-ttu-id="7ad4b-119">根據結構描述中的使用方式，適當的資料類型必須使用，這表示資料型別必須取代 CK、 也是如此，CE、 ST ^ SI，依此類推。</span><span class="sxs-lookup"><span data-stu-id="7ad4b-119">Depending on the usage in the schema, an appropriate data type must be used, meaning that the data type must be replaced with CK, CQ, CE, ST^SI, and so on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad4b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ad4b-120">See Also</span></span>  
 <span data-ttu-id="7ad4b-121">[資料類型](../../adapters-and-accelerators/accelerator-hl7/data-types.md) </span><span class="sxs-lookup"><span data-stu-id="7ad4b-121">[Data Types](../../adapters-and-accelerators/accelerator-hl7/data-types.md) </span></span>  
 <span data-ttu-id="7ad4b-122">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7ad4b-122">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="7ad4b-123">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="7ad4b-123">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="7ad4b-124">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="7ad4b-124">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)