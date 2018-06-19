---
title: 宣告自訂 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declared customizations
- Z objects, declared customizations
- customizing, Z objects
- customizing, declared customizations
ms.assetid: 484655e9-8bfa-4643-bbe6-4ef69cbd83ad
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 767fdd543b1cb5d87bf3ec1c1943ac81d91c6ea4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204782"
---
# <a name="declared-customizations"></a><span data-ttu-id="8211d-102">宣告的自訂項目</span><span class="sxs-lookup"><span data-stu-id="8211d-102">Declared Customizations</span></span>
<span data-ttu-id="8211d-103">宣告的自訂設定，您必須修改或加入 HL7 訊息的彈性。</span><span class="sxs-lookup"><span data-stu-id="8211d-103">With declared customizations, you have the flexibility of modifying or adding to HL7 messages.</span></span> <span data-ttu-id="8211d-104">您甚至可以定義新類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="8211d-104">You can even define a new type of message.</span></span> <span data-ttu-id="8211d-105">您可以下列方式：</span><span class="sxs-lookup"><span data-stu-id="8211d-105">You can do this in any of the following ways:</span></span>  
  
-   <span data-ttu-id="8211d-106">變更訊息的定義，藉由定義新的訊息類型或觸發程序事件</span><span class="sxs-lookup"><span data-stu-id="8211d-106">Changing the definition of a message by defining a new message type or trigger event</span></span>  
  
-   <span data-ttu-id="8211d-107">將新的區段新增至現有的訊息類型</span><span class="sxs-lookup"><span data-stu-id="8211d-107">Adding a new segment to an existing message type</span></span>  
  
-   <span data-ttu-id="8211d-108">變更 （區段、 欄位、 元件或子元件） 的現有訊息部分的資料類型</span><span class="sxs-lookup"><span data-stu-id="8211d-108">Changing the data type of an existing message part (segment, field, component, or subcomponent)</span></span>  
  
-   <span data-ttu-id="8211d-109">您可以使用現有的訊息組件中的可能值的變更</span><span class="sxs-lookup"><span data-stu-id="8211d-109">Changing the potential values that you can use in an existing message part</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8211d-110">您可以變更用於宣告的 Z 物件或標準 HL7 結構描述中的物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8211d-110">You can change the enumeration values used in declared Z objects or the standard objects in HL7 schemas.</span></span> <span data-ttu-id="8211d-111">若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="8211d-111">To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).</span></span>  
  
 <span data-ttu-id="8211d-112">您可以修改或加入 HL7 訊息由加入、 維護和關聯的目前定義的訊息類型的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="8211d-112">You modify or add to HL7 messages by adding, maintaining, and associating custom objects within the currently defined message types.</span></span> <span data-ttu-id="8211d-113">HL7 標準呼叫這些自訂物件 「 Z 物件 」 以便區別 HL7 標準符合的現有物件。</span><span class="sxs-lookup"><span data-stu-id="8211d-113">The HL7 standards call these custom objects "Z objects" to distinguish them from existing objects that conform to the HL7 standard.</span></span> <span data-ttu-id="8211d-114">您可以使用 BizTalk 編輯器來定義 Z 物件。</span><span class="sxs-lookup"><span data-stu-id="8211d-114">You use BizTalk Editor to define Z objects.</span></span> <span data-ttu-id="8211d-115">您也可以使用 BizTalk 編輯器 中使用 Z 物件的更新可直接傳播到所有的觸發程序事件的功能和包含它的抽象訊息。</span><span class="sxs-lookup"><span data-stu-id="8211d-115">You also use BizTalk Editor to work with features that propagate updates to a Z object across all the trigger events and abstract messages that include it.</span></span> <span data-ttu-id="8211d-116">如需建立 Z 物件的詳細資訊，請參閱[擴充 HL7 2.X 結構描述具有 Z 物件](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8211d-116">For more information about creating Z objects, see [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md).</span></span>  
  
 <span data-ttu-id="8211d-117">您可以使用 Z 物件，讓您使用方式不 HL7 標準中所指定的區段的本機定義。</span><span class="sxs-lookup"><span data-stu-id="8211d-117">You can use Z objects to give local definitions to segments that you use in ways not specified in the HL7 standard.</span></span> <span data-ttu-id="8211d-118">進行這些變更結構描述，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝精靈安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="8211d-118">You make these changes to the schemas that the BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Setup Wizard installed on your computer.</span></span> <span data-ttu-id="8211d-119">您接著可以共用這些修改過的結構描述與其他[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝與您交換訊息。</span><span class="sxs-lookup"><span data-stu-id="8211d-119">You can then share these modified schemas with other [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] installations with which you exchange messages.</span></span>  
  
## <a name="types-of-z-objects"></a><span data-ttu-id="8211d-120">Z 物件類型</span><span class="sxs-lookup"><span data-stu-id="8211d-120">Types of Z Objects</span></span>  
 <span data-ttu-id="8211d-121">HL7 標準 (2.X) 目前支援下列形式的自訂：</span><span class="sxs-lookup"><span data-stu-id="8211d-121">The HL7 standard (2.X) currently supports the following forms of customization:</span></span>  
  
-   <span data-ttu-id="8211d-122">**自訂觸發程序事件。**</span><span class="sxs-lookup"><span data-stu-id="8211d-122">**Custom trigger events.**</span></span> <span data-ttu-id="8211d-123">如果您在區域和需要新的訊息結構，或想要支援的觸發程序事件，就不會包含在標準中，您可以建立新的觸發程序事件使用 Z 的前置詞，例如 Z05。</span><span class="sxs-lookup"><span data-stu-id="8211d-123">If you are at a local area and need a new message structure, or want to support a trigger event that is not included within the standard, you can create a new trigger event using a Z prefix, for example, Z05.</span></span> <span data-ttu-id="8211d-124">在此情況下，您必須建立新的本機訊息結構描述，藉由定義抽象的訊息包含區段的模式。</span><span class="sxs-lookup"><span data-stu-id="8211d-124">In this case, you must create a new local message schema by defining the abstract message and the pattern of included segments.</span></span>  
  
-   <span data-ttu-id="8211d-125">**自訂區段。**</span><span class="sxs-lookup"><span data-stu-id="8211d-125">**Custom segments.**</span></span> <span data-ttu-id="8211d-126">如果您是在本機的區域中，在內容中，已經支援的觸發程序事件，並需要額外的資料，您可以建立新的區段，並包含區段內需要的資料元素。</span><span class="sxs-lookup"><span data-stu-id="8211d-126">If you are at a local area, in the context of an already supported trigger event, and in need of additional data, you can create a new segment or segments and include the wanted data elements within the segment.</span></span> <span data-ttu-id="8211d-127">您必須指定使用現有的 HL7 資料類型的區段內的項目。</span><span class="sxs-lookup"><span data-stu-id="8211d-127">You must specify the elements within the segment using existing HL7 data types.</span></span> <span data-ttu-id="8211d-128">您可以建立自訂 Z 區段中 [BizTalk 編輯器] 中，結構描述中建立新的記錄。</span><span class="sxs-lookup"><span data-stu-id="8211d-128">You can create custom Z segments in BizTalk Editor, by creating a new record in the schema.</span></span> <span data-ttu-id="8211d-129">如需詳細資訊，請參閱[建立宣告 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)。</span><span class="sxs-lookup"><span data-stu-id="8211d-129">For more information, see [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md).</span></span> <span data-ttu-id="8211d-130">或者，您可以加入透過存取資料庫，然後再將該 Z 區段加入訊息結構的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="8211d-130">Alternatively, you can add a Z segment through the Access database, and then adding that Z segment to the message structure.</span></span> <span data-ttu-id="8211d-131">如需詳細資訊，請參閱[解決資料庫錯誤](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="8211d-131">For more information, see [Resolving Database Errors](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).</span></span>  
  
-   <span data-ttu-id="8211d-132">**自訂資料子型別。**</span><span class="sxs-lookup"><span data-stu-id="8211d-132">**Custom data subtypes.**</span></span> <span data-ttu-id="8211d-133">HL7 提供一份支援的資料類型，例如，格式化的文字，掃描影像、 音訊資料。</span><span class="sxs-lookup"><span data-stu-id="8211d-133">HL7 provides a list of supported data types, for example, formatted text, scanned image, audio data.</span></span> <span data-ttu-id="8211d-134">不過，如果您想要定義其他資料類型，您可以執行前面加上"Z"搭配使用的助憶鍵，藉此建立 Z 資料輸入。</span><span class="sxs-lookup"><span data-stu-id="8211d-134">However, if you want to define additional data types, you can do so by prefixing the mnemonic used with a "Z", thereby creating a Z data type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8211d-135">不允許標準，來建立新的資料類型，或將項目新增至現有區段的範圍內。</span><span class="sxs-lookup"><span data-stu-id="8211d-135">It is not permissible, within the confines of the standard, to create new data types or to add elements to an existing segment.</span></span> <span data-ttu-id="8211d-136">小於仍然是它允許來取得目前未使用的項目，並重新定義它以符合某些其他用途。</span><span class="sxs-lookup"><span data-stu-id="8211d-136">Still less is it permissible to take an element that is not currently used and to redefine it to meet some additional purpose.</span></span> <span data-ttu-id="8211d-137">相反地，支援傳統介面的組織可能必須配合這種作法。</span><span class="sxs-lookup"><span data-stu-id="8211d-137">On the other hand, organizations that support legacy interfaces may need to accommodate such practices.</span></span>  
  
-   <span data-ttu-id="8211d-138">**自訂資料表。**</span><span class="sxs-lookup"><span data-stu-id="8211d-138">**Custom tables.**</span></span> <span data-ttu-id="8211d-139">在訊息中的許多現有物件具有有限的範圍內的特定值，HL7 常見的結構描述所定義的資料表中的列舉所定義。</span><span class="sxs-lookup"><span data-stu-id="8211d-139">Many existing objects within messages have a limited range of specific values, as defined by enumerations in tables defined by HL7 common schemas.</span></span> <span data-ttu-id="8211d-140">您可以修改這些列舉型別來建立 Z 資料表，以啟用額外的值。</span><span class="sxs-lookup"><span data-stu-id="8211d-140">You can modify these enumerations to enable additional values by creating Z tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8211d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8211d-141">See Also</span></span>  
 <span data-ttu-id="8211d-142">[未宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md) </span><span class="sxs-lookup"><span data-stu-id="8211d-142">[Undeclared Customizations](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md) </span></span>  
 <span data-ttu-id="8211d-143">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="8211d-143">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="8211d-144">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8211d-144">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="8211d-145">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="8211d-145">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="8211d-146">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="8211d-146">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)