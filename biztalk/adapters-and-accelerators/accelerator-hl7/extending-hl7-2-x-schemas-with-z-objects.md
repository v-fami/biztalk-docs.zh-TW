---
title: "擴充 HL7 2.X Z 物件結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, Z objects
- Z objects, extending 2.X schemas
ms.assetid: 0980d919-eb81-4c65-b0f7-f17f7cfef6b3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27ef2bea3e13904f04449a5b77d05672c2b2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extending-hl7-2x-schemas-with-z-objects"></a><span data-ttu-id="2a54e-102">擴充 HL7 2.X Z 物件結構描述</span><span class="sxs-lookup"><span data-stu-id="2a54e-102">Extending HL7 2.X Schemas with Z Objects</span></span>
<span data-ttu-id="2a54e-103">HL7 組織定義 HL7 2.X 結構描述，並預期所有寄件者和接收者辨識並使用這些結構描述，因為組織定義它們。</span><span class="sxs-lookup"><span data-stu-id="2a54e-103">The HL7 organization defines HL7 2.X schemas, and expects all senders and receivers to recognize and use these schemas as the organization defines them.</span></span> <span data-ttu-id="2a54e-104">互通性可確保符合結構描述。</span><span class="sxs-lookup"><span data-stu-id="2a54e-104">Conforming to the schemas ensures for interoperability.</span></span> <span data-ttu-id="2a54e-105">不過，HL7 標準可讓您自訂現有 HL7 2.X 特定的本機目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2a54e-105">However, the HL7 standard enables you to customize existing HL7 2.X schemas for your specific local purposes.</span></span> <span data-ttu-id="2a54e-106">您也可以定義完全新的結構描述和物件。</span><span class="sxs-lookup"><span data-stu-id="2a54e-106">You can also define entirely new schemas and objects.</span></span> <span data-ttu-id="2a54e-107">您可以使用哪些 HL7 標準呼叫 Z 物件。</span><span class="sxs-lookup"><span data-stu-id="2a54e-107">You do so with what the HL7 standard calls Z objects.</span></span>  
  
 <span data-ttu-id="2a54e-108">標準 HL7 並未定義 Z 物件的值。</span><span class="sxs-lookup"><span data-stu-id="2a54e-108">The HL7 standard does not define the value of Z objects.</span></span> <span data-ttu-id="2a54e-109">已發行的 HL7 結構描述不包含它們。</span><span class="sxs-lookup"><span data-stu-id="2a54e-109">The published HL7 schemas do not include them.</span></span> <span data-ttu-id="2a54e-110">在本機，定義它們，並與所有本機的合作對象的協議來使用它們。</span><span class="sxs-lookup"><span data-stu-id="2a54e-110">You define them locally, and use them by agreement with all local parties.</span></span> <span data-ttu-id="2a54e-111">HL7 組織會保留所有訊息類型、 觸發程序事件、 區段、 資料類型，以及這個在本機使用開頭為"Z"的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="2a54e-111">The HL7 organization reserves all message type, trigger event, segment, data type, and table names beginning with "Z" for this local use.</span></span> <span data-ttu-id="2a54e-112">前置詞，因為 HL7 標準呼叫這些站台定義物件 Z 物件。</span><span class="sxs-lookup"><span data-stu-id="2a54e-112">Because of the prefix, the HL7 standard calls these site-defined objects Z objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a54e-113">當您將 Z 物件加入至現有的自訂 HL7 結構描述時，最後可能使用該結構描述的多個版本。</span><span class="sxs-lookup"><span data-stu-id="2a54e-113">When you add a Z object to an existing HL7-defined schema, you may end up with multiple versions of that schema.</span></span> <span data-ttu-id="2a54e-114">若要處理這些多個版本，最好是使用中的命名空間功能[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a54e-114">The best way to handle these multiple versions is to use the Namespace feature in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="2a54e-115">您可以在找到這項功能**驗證**索引標籤中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 （在合作對象層級）。</span><span class="sxs-lookup"><span data-stu-id="2a54e-115">You can find this feature on the **Validation** tab in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (at the party level).</span></span> <span data-ttu-id="2a54e-116">您也必須變更您部署該專案的結構描述中的命名空間屬性。</span><span class="sxs-lookup"><span data-stu-id="2a54e-116">You will also need to change the namespace property within the schema that you deploy for that project.</span></span>  
  
 <span data-ttu-id="2a54e-117">在建立或處理 Z 物件中，您應該遵循 HL7 組織已建立 Z 物件的規則...</span><span class="sxs-lookup"><span data-stu-id="2a54e-117">In creating or processing Z objects, you should follow the rules that the HL7 organization has established for Z objects..</span></span>  
  
 <span data-ttu-id="2a54e-118">當您將 Z 物件加入至現有的結構描述，或建立新的 Z 訊息結構描述，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會使用具有 Z 物件的結構描述來處理 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="2a54e-118">When you add a Z object to an existing schema or create a new Z message schema, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use the schema with the Z object(s) to process the HL7-encoded message.</span></span> <span data-ttu-id="2a54e-119">這種類型的 Z 物件是宣告的 Z 物件。</span><span class="sxs-lookup"><span data-stu-id="2a54e-119">This type of Z object is a declared Z object.</span></span> <span data-ttu-id="2a54e-120">您也可以使用整合引擎不會處理依據訊息結構描述宣告的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="2a54e-120">You can also use an undeclared Z segment, which the integration engine will not process according to the message schema.</span></span> <span data-ttu-id="2a54e-121">如需這種類型的 Z 區段的詳細資訊，請參閱[處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)。</span><span class="sxs-lookup"><span data-stu-id="2a54e-121">For more information about this type of Z segment, see [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a54e-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="2a54e-122">In This Section</span></span>  
  
-   [<span data-ttu-id="2a54e-123">建立宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="2a54e-123">Creating Declared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)  
  
-   [<span data-ttu-id="2a54e-124">在結構描述中建立自訂資料型別</span><span class="sxs-lookup"><span data-stu-id="2a54e-124">Creating Custom Data Types in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)  
  
-   [<span data-ttu-id="2a54e-125">在結構描述中建立自訂的資料表</span><span class="sxs-lookup"><span data-stu-id="2a54e-125">Creating Custom Tables in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)  
  
-   [<span data-ttu-id="2a54e-126">擴充列舉型別</span><span class="sxs-lookup"><span data-stu-id="2a54e-126">Extending Enumerations</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)  
  
-   [<span data-ttu-id="2a54e-127">自訂訊息透過 Z 物件</span><span class="sxs-lookup"><span data-stu-id="2a54e-127">Customizing Messages through Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)