---
title: 宣告自訂項目 |Microsoft Docs
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
ms.openlocfilehash: 091612d1ad15f7ea841b5936beba1fcf7fc26ddf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988263"
---
# <a name="declared-customizations"></a><span data-ttu-id="b8a0c-102">宣告的自訂項目</span><span class="sxs-lookup"><span data-stu-id="b8a0c-102">Declared Customizations</span></span>
<span data-ttu-id="b8a0c-103">宣告的自訂設定，您可以修改或加入 HL7 訊息的彈性。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-103">With declared customizations, you have the flexibility of modifying or adding to HL7 messages.</span></span> <span data-ttu-id="b8a0c-104">您甚至可以定義新類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-104">You can even define a new type of message.</span></span> <span data-ttu-id="b8a0c-105">您可以在下列任一方式來這麼做：</span><span class="sxs-lookup"><span data-stu-id="b8a0c-105">You can do this in any of the following ways:</span></span>  
  
- <span data-ttu-id="b8a0c-106">變更訊息的定義，藉由定義新的訊息類型或觸發程序事件</span><span class="sxs-lookup"><span data-stu-id="b8a0c-106">Changing the definition of a message by defining a new message type or trigger event</span></span>  
  
- <span data-ttu-id="b8a0c-107">將新的區段新增至現有的訊息類型</span><span class="sxs-lookup"><span data-stu-id="b8a0c-107">Adding a new segment to an existing message type</span></span>  
  
- <span data-ttu-id="b8a0c-108">變更現有的訊息部分 （區段、 欄位、 元件或子元件） 的資料類型</span><span class="sxs-lookup"><span data-stu-id="b8a0c-108">Changing the data type of an existing message part (segment, field, component, or subcomponent)</span></span>  
  
- <span data-ttu-id="b8a0c-109">變更可能的值，您可以使用現有的訊息組件中</span><span class="sxs-lookup"><span data-stu-id="b8a0c-109">Changing the potential values that you can use in an existing message part</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="b8a0c-110">您可以變更用於宣告的 Z 物件或標準 HL7 結構描述中的物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-110">You can change the enumeration values used in declared Z objects or the standard objects in HL7 schemas.</span></span> <span data-ttu-id="b8a0c-111">若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-111">To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).</span></span>  
  
  <span data-ttu-id="b8a0c-112">您可以修改或加入 HL7 訊息，藉由新增、 維護及建立自訂的物件，在目前定義的訊息類型的關聯。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-112">You modify or add to HL7 messages by adding, maintaining, and associating custom objects within the currently defined message types.</span></span> <span data-ttu-id="b8a0c-113">HL7 標準呼叫這些自訂物件 「 Z 物件 」 以便區別 HL7 標準符合的現有物件。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-113">The HL7 standards call these custom objects "Z objects" to distinguish them from existing objects that conform to the HL7 standard.</span></span> <span data-ttu-id="b8a0c-114">您可以使用 BizTalk 編輯器來定義 Z 物件。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-114">You use BizTalk Editor to define Z objects.</span></span> <span data-ttu-id="b8a0c-115">您也可以使用 BizTalk 編輯器來處理將更新傳播到 Z 物件在所有觸發程序事件的功能和包含它的抽象訊息。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-115">You also use BizTalk Editor to work with features that propagate updates to a Z object across all the trigger events and abstract messages that include it.</span></span> <span data-ttu-id="b8a0c-116">如需建立 Z 物件的詳細資訊，請參閱 <<c0> [ 使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-116">For more information about creating Z objects, see [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md).</span></span>  
  
  <span data-ttu-id="b8a0c-117">您可以使用 Z 物件提供給本機的定義，以您使用方式不 HL7 標準中所指定的區段。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-117">You can use Z objects to give local definitions to segments that you use in ways not specified in the HL7 standard.</span></span> <span data-ttu-id="b8a0c-118">您進行這些變更的結構描述，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝精靈安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-118">You make these changes to the schemas that the BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Setup Wizard installed on your computer.</span></span> <span data-ttu-id="b8a0c-119">您接著可以共用這些修改過的結構描述與其他[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝與您交換訊息。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-119">You can then share these modified schemas with other [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] installations with which you exchange messages.</span></span>  
  
## <a name="types-of-z-objects"></a><span data-ttu-id="b8a0c-120">Z 物件的類型</span><span class="sxs-lookup"><span data-stu-id="b8a0c-120">Types of Z Objects</span></span>  
 <span data-ttu-id="b8a0c-121">HL7 標準 (2.X) 目前支援下列形式進行自訂：</span><span class="sxs-lookup"><span data-stu-id="b8a0c-121">The HL7 standard (2.X) currently supports the following forms of customization:</span></span>  
  
-   <span data-ttu-id="b8a0c-122">**自訂觸發程序事件。**</span><span class="sxs-lookup"><span data-stu-id="b8a0c-122">**Custom trigger events.**</span></span> <span data-ttu-id="b8a0c-123">如果您在本機區域和需要新的訊息結構，或想要支援不包含在標準的觸發程序事件，您可以建立新的觸發程序事件使用 Z 的前置詞，例如 Z05。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-123">If you are at a local area and need a new message structure, or want to support a trigger event that is not included within the standard, you can create a new trigger event using a Z prefix, for example, Z05.</span></span> <span data-ttu-id="b8a0c-124">在此情況下，您必須建立新的本機訊息結構描述定義的抽象訊息和包含區段的模式。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-124">In this case, you must create a new local message schema by defining the abstract message and the pattern of included segments.</span></span>  
  
-   <span data-ttu-id="b8a0c-125">**自訂的使用者分佈。**</span><span class="sxs-lookup"><span data-stu-id="b8a0c-125">**Custom segments.**</span></span> <span data-ttu-id="b8a0c-126">如果您是在本機的區域中，在內容中，已經支援的觸發程序事件，以及需要額外的資料，您可以建立新的區段，並包含需的資料區段中項目。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-126">If you are at a local area, in the context of an already supported trigger event, and in need of additional data, you can create a new segment or segments and include the wanted data elements within the segment.</span></span> <span data-ttu-id="b8a0c-127">您必須指定使用現有的 HL7 資料型別區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-127">You must specify the elements within the segment using existing HL7 data types.</span></span> <span data-ttu-id="b8a0c-128">您可以建立自訂的 Z 區段在 「 BizTalk 編輯器 」 中，結構描述中建立新的記錄。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-128">You can create custom Z segments in BizTalk Editor, by creating a new record in the schema.</span></span> <span data-ttu-id="b8a0c-129">如需詳細資訊，請參閱 <<c0> [ 建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-129">For more information, see [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md).</span></span> <span data-ttu-id="b8a0c-130">或者，您可以新增透過存取資料庫，然後再將該 Z 區段加入訊息結構的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-130">Alternatively, you can add a Z segment through the Access database, and then adding that Z segment to the message structure.</span></span> <span data-ttu-id="b8a0c-131">如需詳細資訊，請參閱 <<c0> [ 解決資料庫錯誤](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-131">For more information, see [Resolving Database Errors](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).</span></span>  
  
-   <span data-ttu-id="b8a0c-132">**自訂資料子型別。**</span><span class="sxs-lookup"><span data-stu-id="b8a0c-132">**Custom data subtypes.**</span></span> <span data-ttu-id="b8a0c-133">HL7 提供一份支援的資料類型，例如，格式化文字時，掃描影像、 音訊資料。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-133">HL7 provides a list of supported data types, for example, formatted text, scanned image, audio data.</span></span> <span data-ttu-id="b8a0c-134">不過，如果您想要定義其他資料類型，您可以執行前面加上"Z"搭配使用的助憶鍵，藉此建立 Z 資料輸入。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-134">However, if you want to define additional data types, you can do so by prefixing the mnemonic used with a "Z", thereby creating a Z data type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8a0c-135">不允許的標準，以建立新的資料類型，或將項目新增至現有的區段範圍內。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-135">It is not permissible, within the confines of the standard, to create new data types or to add elements to an existing segment.</span></span> <span data-ttu-id="b8a0c-136">仍少就是它允許接受目前未使用的項目，並重新定義它以符合某些其他用途。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-136">Still less is it permissible to take an element that is not currently used and to redefine it to meet some additional purpose.</span></span> <span data-ttu-id="b8a0c-137">相反地，支援舊版介面的組織可能需要配合這種做法。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-137">On the other hand, organizations that support legacy interfaces may need to accommodate such practices.</span></span>  
  
-   <span data-ttu-id="b8a0c-138">**自訂的資料表。**</span><span class="sxs-lookup"><span data-stu-id="b8a0c-138">**Custom tables.**</span></span> <span data-ttu-id="b8a0c-139">在訊息中的許多現有物件具有有限的特定值，列舉 HL7 通用結構描述所定義的資料表中所定義。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-139">Many existing objects within messages have a limited range of specific values, as defined by enumerations in tables defined by HL7 common schemas.</span></span> <span data-ttu-id="b8a0c-140">您可以修改這些列舉，可透過建立 Z 資料表的其他值。</span><span class="sxs-lookup"><span data-stu-id="b8a0c-140">You can modify these enumerations to enable additional values by creating Z tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a0c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8a0c-141">See Also</span></span>  
 <span data-ttu-id="b8a0c-142">[未宣告的自訂項目](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md) </span><span class="sxs-lookup"><span data-stu-id="b8a0c-142">[Undeclared Customizations](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md) </span></span>  
 <span data-ttu-id="b8a0c-143">[使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="b8a0c-143">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="b8a0c-144">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b8a0c-144">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="b8a0c-145">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="b8a0c-145">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="b8a0c-146">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="b8a0c-146">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)