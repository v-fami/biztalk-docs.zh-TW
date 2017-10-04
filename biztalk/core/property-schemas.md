---
title: "屬性結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8018bb72-a037-4eeb-bbbe-dd0cc6209aec
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2fb50536b2521e77994baf0b6457206614b7eed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-schemas"></a><span data-ttu-id="7fb34-102">屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="7fb34-102">Property Schemas</span></span>

## <a name="promoted-properties"></a><span data-ttu-id="7fb34-103">升級屬性</span><span class="sxs-lookup"><span data-stu-id="7fb34-103">Promoted properties</span></span>
<span data-ttu-id="7fb34-104">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，升級的屬性可以讓各種 BizTalk Server 元件存取資料的主要項目，在此內容中即為送達執行個體訊息內的辨別欄位與屬性欄位，而不需要瞭解如何在訊息本身之中找尋這些項目。</span><span class="sxs-lookup"><span data-stu-id="7fb34-104">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], promoted properties enable various BizTalk Server components to access key items of data, known in this context as distinguished fields and property fields that arrive within an instance message without needing to know how to look for them within the message itself.</span></span> <span data-ttu-id="7fb34-105">您可以針對不同類型的訊息，決定哪些資料項目需要升級至更高的可見層級。</span><span class="sxs-lookup"><span data-stu-id="7fb34-105">For different types of messages, you can determine which items of data require promotion to a more visible level.</span></span> <span data-ttu-id="7fb34-106">根據您選擇升級這類欄位的方式，您可能需要建立和定義關聯的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-106">Depending on how you choose to promote such fields, you may need to create and define an associated property schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fb34-107">升級屬性僅限非重複項目/屬性。</span><span class="sxs-lookup"><span data-stu-id="7fb34-107">Promoted properties are restricted to non-repeating elements/attributes.</span></span>  
  
 <span data-ttu-id="7fb34-108">辨別欄位只能在協調流程中存取，不需要建立對應的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-108">Distinguished fields are accessible only within orchestrations and do not require the creation of a corresponding property schema.</span></span> <span data-ttu-id="7fb34-109">若您只需要從協調流程中存取升級的訊息資料，可以將資料升級為一或多個辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="7fb34-109">If you only need to access promoted message data from within an orchestration, you can promote the data as one or more distinguished fields.</span></span>  
  
 <span data-ttu-id="7fb34-110">屬性欄位可以從各種 BizTalk Server 元件 (包括管線和協調流程) 中存取。</span><span class="sxs-lookup"><span data-stu-id="7fb34-110">Property fields are accessible from within various BizTalk Server components, including pipelines and orchestrations.</span></span> <span data-ttu-id="7fb34-111">屬性欄位也可用於訊息路由。</span><span class="sxs-lookup"><span data-stu-id="7fb34-111">Property fields can also be used for message routing.</span></span> <span data-ttu-id="7fb34-112">若您需要從內容而不是從協調流程存取升級的訊息資料，則必須建立一或多個屬性結構描述以描述要升級的資料。</span><span class="sxs-lookup"><span data-stu-id="7fb34-112">If you need to access promoted message data from contexts other than within orchestrations, you must create one or more property schemas to describe the data you are promoting.</span></span>  
  
 <span data-ttu-id="7fb34-113">屬性結構描述是與訊息結構描述相關聯的特殊結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-113">A property schema is a special schema that you associate with a message schema.</span></span> <span data-ttu-id="7fb34-114">它用於將執行個體訊息中的特定值升級為訊息內容。</span><span class="sxs-lookup"><span data-stu-id="7fb34-114">It is used for promoting specific values from within an instance message into the message context.</span></span> <span data-ttu-id="7fb34-115">屬性升級提供集中的機制，以提取您從執行個體訊息中定義的訊息之主要部分，並且讓處理訊息的 BizTalk Server 元件，在處理透過 BizTalk Server 傳送的訊息時更容易存取。</span><span class="sxs-lookup"><span data-stu-id="7fb34-115">Property promotion provides a centralized mechanism for pulling key pieces of information that you define from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server.</span></span>  
  
## <a name="create-property-schema-overview"></a><span data-ttu-id="7fb34-116">建立屬性結構描述的概觀</span><span class="sxs-lookup"><span data-stu-id="7fb34-116">Create property schema overview</span></span>
 <span data-ttu-id="7fb34-117">您可以使用 BizTalk Server 的快速升級功能自動建立預設屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-117">You can automatically create a default property schema by using the quick promotion feature of BizTalk Server.</span></span> <span data-ttu-id="7fb34-118">這是建立屬性欄位升級必要的屬性結構描述最容易的方式。</span><span class="sxs-lookup"><span data-stu-id="7fb34-118">This is the easiest way to create the property schema required for property field promotion.</span></span> <span data-ttu-id="7fb34-119">如需如何執行快速升級的詳細資訊，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。</span><span class="sxs-lookup"><span data-stu-id="7fb34-119">For more information about how to perform quick promotions, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
 <span data-ttu-id="7fb34-120">您也可以建立新的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-120">You can also create new property schema.</span></span> <span data-ttu-id="7fb34-121">開啟 BizTalk 專案時，選取 BizTalk 專案，以滑鼠右鍵按一下並選取**新增**，按一下 **新項目**，然後按一下 **結構描述**。</span><span class="sxs-lookup"><span data-stu-id="7fb34-121">When a BizTalk project is open, select the BizTalk project, right-click and select **Add**, click **New Item**, and then click **Schema**.</span></span>  
  
> [!NOTE]
>  - <span data-ttu-id="7fb34-122">若屬性結構描述與訊息結構描述相關聯，則這兩個結構描述必須在相同的 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="7fb34-122">If a property schema is associated with a message schema, then these two must be in the same BizTalk project.</span></span> <span data-ttu-id="7fb34-123">不支援將屬性結構描述與其相關的訊息結構描述分隔在不同的 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="7fb34-123">Separating property schema from its associated message schema in different BizTalk projects is not supported.</span></span>  
>
>  - <span data-ttu-id="7fb34-124">如果您有兩個具有相同命名空間的屬性結構描述，則即使這兩個結構描述是在不同的組件中定義，它們將無法在執行階段正確解析。</span><span class="sxs-lookup"><span data-stu-id="7fb34-124">If you have two property schemas that have the same namespace, even though they are defined in different assemblies, the schemas will not resolve properly at runtime.</span></span> <span data-ttu-id="7fb34-125">您將在執行階段收到路由失敗。</span><span class="sxs-lookup"><span data-stu-id="7fb34-125">You will get a routing failure at runtime.</span></span>  

## <a name="distinguished-fields-and-property-fields"></a><span data-ttu-id="7fb34-126">辨別的欄位和屬性欄位</span><span class="sxs-lookup"><span data-stu-id="7fb34-126">Distinguished fields and property fields</span></span> 
 <span data-ttu-id="7fb34-127">有兩個屬性升級類型：辨別欄位和屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="7fb34-127">There are two types of property promotion: distinguished fields and property fields.</span></span> <span data-ttu-id="7fb34-128">後者使用屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-128">The latter type uses property schemas.</span></span> <span data-ttu-id="7fb34-129">在 [BizTalk 編輯器] 中，您管理這兩種類型的屬性升級使用**升級屬性**對話方塊中，您可以使用存取**升級屬性**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="7fb34-129">In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which you access by using the **Promote Properties** property of the **Schema** node.</span></span>  
  
> [!NOTE]
>  - <span data-ttu-id="7fb34-130">您可升級的值有部分限制。</span><span class="sxs-lookup"><span data-stu-id="7fb34-130">There are some restrictions on values that you can promote.</span></span> <span data-ttu-id="7fb34-131">如需詳細資訊，請參閱中的資料表[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7fb34-131">For more information, see the table in [Promoting Properties](../core/promoting-properties.md).</span></span>  
>
>  - <span data-ttu-id="7fb34-132">[辨別] 欄位不會出現在篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="7fb34-132">Distinguished fields do not appear in filter expressions.</span></span> <span data-ttu-id="7fb34-133">只有屬性欄位會出現在篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="7fb34-133">Only property fields appear in filter expressions.</span></span>  
  
 <span data-ttu-id="7fb34-134">與訊息結構描述比較，屬性結構描述較簡單。</span><span class="sxs-lookup"><span data-stu-id="7fb34-134">Property schemas are simple when compared to message schemas.</span></span> <span data-ttu-id="7fb34-135">在結構描述樹狀目錄中，您只允許插入**欄位項目**直屬子節點的節點**結構描述**節點，建立兩層的結構。</span><span class="sxs-lookup"><span data-stu-id="7fb34-135">In the schema tree, you are only allowed to insert **Field Element** nodes as immediate child nodes of the **Schema** node, creating a structure that is two levels deep.</span></span> <span data-ttu-id="7fb34-136">大部分的情況下，您可以設定的屬性**欄位項目**節點做為您用來處理**欄位項目**訊息結構描述中出現的節點。</span><span class="sxs-lookup"><span data-stu-id="7fb34-136">For the most part, you set the properties of the **Field Element** nodes as you would for **Field Element** nodes appearing in a message schema.</span></span> <span data-ttu-id="7fb34-137">限制您只能使用 XSD 簡單類型。</span><span class="sxs-lookup"><span data-stu-id="7fb34-137">You are limited to using only XSD simple types.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fb34-138">您不能重新命名任何一個已經用於其他結構描述的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-138">You should not rename any schema that is being used by another schema.</span></span> <span data-ttu-id="7fb34-139">這包含已經建立其升級的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-139">This includes property schemas for which promotions have already been established.</span></span> <span data-ttu-id="7fb34-140">若這麼做，所使用的結構描述將找不到其他結構描述，因為它所包含的名稱已經不正確。</span><span class="sxs-lookup"><span data-stu-id="7fb34-140">If you do so, the schema that is being used will not be able to find the other schema because the name it contains will no longer be accurate.</span></span>  
  
 <span data-ttu-id="7fb34-141">**Property Schema Base**屬性是唯一**欄位項目**節點出現在屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="7fb34-141">The **Property Schema Base** property is unique to **Field Element** nodes as they appear in property schemas.</span></span> <span data-ttu-id="7fb34-142">這個屬性是空白的根據預設，不過可以設定為  **MessageDataPropertyBase**或**MessageContextPropertyBase**，並產生**propSchFieldBase**屬性正在加入**fieldInfo**或其他這些值的其中一種註釋項目。</span><span class="sxs-lookup"><span data-stu-id="7fb34-142">This property is blank by default, but can be set to either **MessageDataPropertyBase** or **MessageContextPropertyBase**, resulting in a **propSchFieldBase** attribute being added to the **fieldInfo** annotation element with one or the other of these values.</span></span>  
  
 <span data-ttu-id="7fb34-143">當**propSchFieldBase**屬性設為**MessageDataPropertyBase**，這表示 升級屬性的值對應至訊息，例如某些欄位的值中的資料。</span><span class="sxs-lookup"><span data-stu-id="7fb34-143">When the **propSchFieldBase** attribute is set to **MessageDataPropertyBase**, it means that the value of the promoted property corresponds to data in the message, such as the value of some field.</span></span> <span data-ttu-id="7fb34-144">當**propSchFieldBase**屬性設為**MessageContextPropertyBase**，就表示升級屬性的值可能會從信封時，例如，其他地方，或者它可能是由設定管線元件。</span><span class="sxs-lookup"><span data-stu-id="7fb34-144">When the **propSchFieldBase** attribute is set to **MessageContextPropertyBase**, it means that the value of the promoted property may be from somewhere else, such as an envelope, or that it may be set by a pipeline component.</span></span>  
  
 <span data-ttu-id="7fb34-145">**欄位項目**屬性結構描述中的節點也有一個屬性呼叫**機密資訊**，而當設定為**是**，會顯示從保留的相對應的值BizTalk 總管 以及訊息事件和服務執行個體追蹤，因此能保持其機密的性質。</span><span class="sxs-lookup"><span data-stu-id="7fb34-145">**Field Element** nodes in property schemas also have a property called **Sensitive Information**, which when set to **Yes**, will keep the corresponding value from being visible from within BizTalk Explorer and message event and service instance tracking, thereby preserving its sensitive nature.</span></span>  <span data-ttu-id="7fb34-146">請參閱**機密資訊**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7fb34-146">See **Sensitive Information** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for more details.</span></span>
  
 <span data-ttu-id="7fb34-147">以下屬性結構描述的 XML 結構描述定義 (XSD) 語言表示法包含與識別此結構描述為屬性結構描述 (schema_type="property") 的結構描述項目相關聯的註解。</span><span class="sxs-lookup"><span data-stu-id="7fb34-147">The following XML Schema definition (XSD) language representation of a property schema contains an annotation associated with the schema element that identifies this schema as a property schema (schema_type="property").</span></span> <span data-ttu-id="7fb34-148">它也包含三種**欄位項目**節點之下**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="7fb34-148">It also contains three **Field Element** nodes below the **Schema** node.</span></span> <span data-ttu-id="7fb34-149">第一個**欄位項目**名為 PromProp1，節點沒有值，定義其**Property Schema Base**屬性，但後面兩個**欄位項目**節點的方式屬性設定為**MessageDataPropertyBase**和**MessageContextPropertyBase**分別。</span><span class="sxs-lookup"><span data-stu-id="7fb34-149">The first **Field Element** node, named PromProp1, does not have a value defined for its **Property Schema Base** property, but the latter two **Field Element** nodes have that property set to **MessageDataPropertyBase** and **MessageContextPropertyBase**, respectively.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
           targetNamespace="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
       <xs:appinfo>  
  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fb34-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb34-150">See Also</span></span>  
 [<span data-ttu-id="7fb34-151">不同類型的 BizTalk 結構描述</span><span class="sxs-lookup"><span data-stu-id="7fb34-151">Different Types of BizTalk Schemas</span></span>](../core/different-types-of-biztalk-schemas.md)