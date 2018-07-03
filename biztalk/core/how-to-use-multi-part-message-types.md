---
title: 如何使用多部分訊息類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multi-part message types, parts
- multi-part message types, creating
- multi-part message types, type modifiers
- messages
- multi-part message types, deleting
- orchestrations, messages
- deleting, multi-part messages
- multi-part message types, about multi-part message types
- orchestrations, type modifier
- messages, multi-parts
- creating, multi-part messages
- messages, about messages
ms.assetid: 009a39bd-cfc4-42d9-918c-88ac24bfc370
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 083746c38a175db840f4554297e86d26b5fcb366
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013943"
---
# <a name="how-to-use-multi-part-message-types"></a><span data-ttu-id="abc0f-102">如何使用多部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="abc0f-102">How to Use Multi-part Message Types</span></span>
<span data-ttu-id="abc0f-103">每個訊息都有多部分訊息類型，即是由零或多個訊息部分所組成的訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="abc0f-103">Each message has a multi-part message type, a description of the message structure that consists of zero or more message parts.</span></span> <span data-ttu-id="abc0f-104">這些部分是由 XML 結構描述定義 (XSD) 語言結構描述或 .NET 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="abc0f-104">The parts are defined by XML Schema Definition (XSD) language schemas or .NET classes.</span></span> <span data-ttu-id="abc0f-105">您可以定義自己的多部分訊息類型，也可以使用現有的 .NET 類別和結構描述。</span><span class="sxs-lookup"><span data-stu-id="abc0f-105">You can define your own multi-part message types, or you can use existing .NET classes and schemas.</span></span>  

 <span data-ttu-id="abc0f-106">您可以直接在協調流程內存取或指派訊息部分，也可以使用公開為辨別欄位或屬性欄位的個別訊息部分項目。</span><span class="sxs-lookup"><span data-stu-id="abc0f-106">You can access or assign message parts directly within your orchestration, or you can use individual elements of message parts that are exposed as distinguished fields or property fields.</span></span> <span data-ttu-id="abc0f-107">如需詳細資訊，請參閱 <<c0> [ 使用辨別欄位和訊息屬性](../core/using-distinguished-fields-and-property-fields.md)。</span><span class="sxs-lookup"><span data-stu-id="abc0f-107">For more information, see [Using Distinguished Fields and Message Properties](../core/using-distinguished-fields-and-property-fields.md).</span></span>  

> [!NOTE]
>  <span data-ttu-id="abc0f-108">多部分訊息類型不一定要包含多個部分。</span><span class="sxs-lookup"><span data-stu-id="abc0f-108">A multi-part message type does not necessarily contain multiple parts.</span></span>  

> [!NOTE]
>  <span data-ttu-id="abc0f-109">可由.NET 型別定義的訊息部分**XmlDocument**、 可用來包含任意的 XML 文件、 XML 序列化，任何.NET 型別或任何.NET 類型支援的自訂序列化。</span><span class="sxs-lookup"><span data-stu-id="abc0f-109">A message part can be defined by the .NET type **XmlDocument**, which can be used to contain an arbitrary XML document, by any .NET type that is XML-serializable, or by any .NET type supporting custom serialization.</span></span>  

## <a name="add-a-multi-part-message-type"></a><span data-ttu-id="abc0f-110">新增多部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="abc0f-110">Add a multi-part message type</span></span>  

1.  <span data-ttu-id="abc0f-111">在 [**協調流程檢視**] 視窗中，展開**型別**節點。</span><span class="sxs-lookup"><span data-stu-id="abc0f-111">In the **Orchestration View** window, expand the **Types** node.</span></span>  

2.  <span data-ttu-id="abc0f-112">以滑鼠右鍵按一下**多部分訊息類型**，然後按一下**新的多部分訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="abc0f-112">Right-click **Multi-part Message Types** and then click **New Multi-part Message Type**.</span></span>  

     <span data-ttu-id="abc0f-113">**多部分訊息類型**資料夾，則會展開摺疊，並使用一個預設訊息部分加入新的多部分訊息類型。</span><span class="sxs-lookup"><span data-stu-id="abc0f-113">The **Multi-part Message Types** folder expands, if collapsed, and a new multi-part message type is added with one default message part.</span></span>  

3.  <span data-ttu-id="abc0f-114">命名多部分訊息類型和提供的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="abc0f-114">Name the multi-part message type and the provided message part.</span></span>  

     <span data-ttu-id="abc0f-115">如果您的多部分訊息類型需要一個以上的訊息部分，您可以新增其他部分指派名稱給\<新增\>訊息部分。</span><span class="sxs-lookup"><span data-stu-id="abc0f-115">If your multi-part message type requires more than one message part, you can add additional parts by assigning a name to the \<New\> message part.</span></span>  

4.  <span data-ttu-id="abc0f-116">將每個訊息部分與類型 (例如，.NET 類別或結構描述) 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="abc0f-116">Associate each message part with a type, such as a .NET class or schema.</span></span>  

## <a name="remove-a-multi-part-message-type"></a><span data-ttu-id="abc0f-117">移除多部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="abc0f-117">Remove a multi-part message type</span></span>  

-   <span data-ttu-id="abc0f-118">在 **協調流程檢視**視窗中，以滑鼠右鍵按一下的多部分訊息的類型，您想要移除，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="abc0f-118">In the **Orchestration View** window, right-click the multi-part message type you want to remove and then click **Delete**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="abc0f-119">從協調流程移除多部分訊息類型，也會從用到它的訊息中移除類型資訊。</span><span class="sxs-lookup"><span data-stu-id="abc0f-119">Removing a multi-part message type from your orchestration will also remove the type information from messages that use it.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="abc0f-120">顯示為唯讀的項目定義在另一個協調流程中。</span><span class="sxs-lookup"><span data-stu-id="abc0f-120">Items that appear as read-only are defined in another orchestration.</span></span>  

## <a name="remove-a-part-from-a-multi-part-message-type"></a><span data-ttu-id="abc0f-121">移除多部分訊息類型的組件</span><span class="sxs-lookup"><span data-stu-id="abc0f-121">Remove a part from a multi-part message type</span></span>  

-   <span data-ttu-id="abc0f-122">在 [**協調流程檢視**] 視窗中，以滑鼠右鍵按一下您想要移除，然後按一下組的件**刪除**。</span><span class="sxs-lookup"><span data-stu-id="abc0f-122">In the **Orchestration View** window, right-click the part you want to remove and click **Delete**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="abc0f-123">如果您無法刪除訊息類型的訊息部分**訊息內文部分**屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="abc0f-123">You cannot delete a message type's message part if the **Message Body Part** property is set to true.</span></span> <span data-ttu-id="abc0f-124">您必須先設定**訊息內文部分**屬性設為 True 的另一個訊息類型的組件。</span><span class="sxs-lookup"><span data-stu-id="abc0f-124">You must first set the **Message Body Part** property to True for another of the message type's parts.</span></span>  

## <a name="set-the-type-modifier-for-a-multi-part-message-type"></a><span data-ttu-id="abc0f-125">設定多部分訊息類型的類型修飾詞</span><span class="sxs-lookup"><span data-stu-id="abc0f-125">Set the type modifier for a multi-part message type</span></span>  

- <span data-ttu-id="abc0f-126">在 [**屬性**] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="abc0f-126">In the **Properties** window, set the following property:</span></span>  


  |     <span data-ttu-id="abc0f-127">屬性</span><span class="sxs-lookup"><span data-stu-id="abc0f-127">Property</span></span>      |                                                                                                                                                                                        <span data-ttu-id="abc0f-128">描述</span><span class="sxs-lookup"><span data-stu-id="abc0f-128">Description</span></span>                                                                                                                                                                                         |
  |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | <span data-ttu-id="abc0f-129">**類型修飾詞**</span><span class="sxs-lookup"><span data-stu-id="abc0f-129">**Type Modifier**</span></span> | <span data-ttu-id="abc0f-130">決定多部分訊息類型的範圍：</span><span class="sxs-lookup"><span data-stu-id="abc0f-130">Determines the scope of the multi-part message type:</span></span><br /><br /> <span data-ttu-id="abc0f-131">-   <strong>私用 —</strong>此多部分訊息類型的存取限於包含的模組。</span><span class="sxs-lookup"><span data-stu-id="abc0f-131">-   <strong>Private—</strong>Access to this multi-part message type is limited to the containing module.</span></span><br /><span data-ttu-id="abc0f-132">-   <strong>公用 —</strong>存取此多部分訊息類型不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="abc0f-132">-   <strong>Public—</strong>Access to this multi-part message type is not limited.</span></span><br /><span data-ttu-id="abc0f-133">-   <strong>內部 —</strong>存取此多部分訊息類型僅限於相同專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="abc0f-133">-   <strong>Internal—</strong>Access to this multi-part message type is limited to modules within the same project.</span></span> |

## <a name="add-parts-to-an-existing-multi-part-message"></a><span data-ttu-id="abc0f-134">將組件加入至現有的多部分訊息</span><span class="sxs-lookup"><span data-stu-id="abc0f-134">Add parts to an existing multi-part message</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="abc0f-135"> 可讓您將部分新增至多部分 XLANG 訊息，並且透過大於原始宣告的部分數目的索引來參考訊息部分 (如果有該部分存在的話)。</span><span class="sxs-lookup"><span data-stu-id="abc0f-135"> provides the ability to add parts to a multi part XLANG message and also to refer to a message part by an index greater than the originally declared number of parts if the part exists.</span></span> <span data-ttu-id="abc0f-136">傳送或接收夾帶數目不定之附件的 SMTP 訊息時，此功能可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="abc0f-136">This functionality may be useful for sending or receiving SMTP messages with a variable number of attachments.</span></span> <span data-ttu-id="abc0f-137">實作此功能的方法如下：</span><span class="sxs-lookup"><span data-stu-id="abc0f-137">This functionality is implemented as follows:</span></span>  

- <span data-ttu-id="abc0f-138">從您的專案，將參考加入**Microsoft.XLANGs.BaseTypes**。</span><span class="sxs-lookup"><span data-stu-id="abc0f-138">From your project, add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  

- <span data-ttu-id="abc0f-139">建立的變數 (例如*xlangPart*) 的型別**Microsoft.XLANGs.BaseTypes.XLANGMessage**。</span><span class="sxs-lookup"><span data-stu-id="abc0f-139">Create a variable (for example *xlangPart*) of type **Microsoft.XLANGs.BaseTypes.XLANGMessage**.</span></span>  

- <span data-ttu-id="abc0f-140">呼叫<em>xlangPart</em>**。AddPart(...)** 使用適當的引數，從 「 運算式 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="abc0f-140">Call <em>xlangPart</em>**.AddPart(…)** using the appropriate arguments from an Expression shape.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="abc0f-141">新增的部分為型別的**XmlDocument**因此您無法加入自訂格式化的訊息部分使用**addpart （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="abc0f-141">The added parts are of type **XmlDocument** so you cannot add a custom formatted message part using the **AddPart()** method.</span></span>  

> [!NOTE]
>  <span data-ttu-id="abc0f-142">如果收到包含大於宣告的部分數目的多部分訊息時，有多少部分是在訊息中，協調流程引擎讀取接著會建構適當的部分類型的組件相符的部分宣告的訊息數目類型，然後建構**XmlDocument**組件的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="abc0f-142">If a multi part message that contains greater than the number of declared parts is received, the orchestration engine reads how many parts there are in the message, then constructs the proper part types for the parts that match the number of parts in the declared message type and then constructs **XmlDocument** parts for the remaining parts.</span></span>  

## <a name="see-also"></a><span data-ttu-id="abc0f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc0f-143">See Also</span></span>  
 <span data-ttu-id="abc0f-144">**IBaseMessage.AddPart 方法 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="abc0f-144">**IBaseMessage.AddPart Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
 <span data-ttu-id="abc0f-145">[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md) </span><span class="sxs-lookup"><span data-stu-id="abc0f-145">[XSD Resources on the Web](../core/xsd-resources-on-the-web.md) </span></span>  
 <span data-ttu-id="abc0f-146">[使用辨別的欄位和屬性欄位](../core/using-distinguished-fields-and-property-fields.md) </span><span class="sxs-lookup"><span data-stu-id="abc0f-146">[Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md) </span></span>  
 [<span data-ttu-id="abc0f-147">在協調流程中使用訊息</span><span class="sxs-lookup"><span data-stu-id="abc0f-147">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)