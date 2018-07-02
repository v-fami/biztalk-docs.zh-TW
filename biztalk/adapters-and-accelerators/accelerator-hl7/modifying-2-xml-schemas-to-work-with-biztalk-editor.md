---
title: 修改 2.xml 結構描述以使用 BizTalk 編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, modifying
- modifying, 2.XML schemas
ms.assetid: 07316826-84b6-494e-81b9-f64a3d46ffb0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96dd1c4cd8909564ff39c78b5b1a9e4fc248d93f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972855"
---
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a><span data-ttu-id="51531-102">修改 2.xml 結構描述才能使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="51531-102">Modifying 2.XML Schemas to Work with BizTalk Editor</span></span>
<span data-ttu-id="51531-103">HL7 2.xml 結構描述需要進行修改才能正常使用 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="51531-103">HL7 2.XML schemas require modification to work properly with Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span> <span data-ttu-id="51531-104">以下說明如何修改 HL7 V2。可讓您使用它們在 「 BizTalk 編輯器 」 使用的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="51531-104">The following describes how to modify HL7 V2.XML schemas to enable you to use them with BizTalk Editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51531-105">Update2XMLSchema 工具會自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="51531-105">The Update2XMLSchema tool performs these steps automatically.</span></span> <span data-ttu-id="51531-106">請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="51531-106">See [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) for more information.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="51531-107">**Nillable**屬性可能會發生在結構描述中的項目上。</span><span class="sxs-lookup"><span data-stu-id="51531-107">The **nillable** attribute can occur in a schema on an element.</span></span> <span data-ttu-id="51531-108">如果設定為 **，則為 true**，它會指出可以有父項目的執行個體**xsi: nil ="true"** 屬性。</span><span class="sxs-lookup"><span data-stu-id="51531-108">If set to **true**, it indicates that the instance of the parent element can have an **xsi:nil="true"** attribute.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="51531-109"> 在編譯期間，在剖析/序列化期間，會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="51531-109"> ignores this attribute during compilation and during parsing/serialization.</span></span>  
  
### <a name="to-modify-2xml-schemas"></a><span data-ttu-id="51531-110">若要修改 2.xml 結構描述</span><span class="sxs-lookup"><span data-stu-id="51531-110">To modify 2.XML schemas</span></span>  
  
1. <span data-ttu-id="51531-111">在 fields.xsd 檔案中，您必須移除的執行個體**匯入**並將其取代為**包含**。</span><span class="sxs-lookup"><span data-stu-id="51531-111">In the fields.xsd file, you must remove instances of **import** and replace them with **include**.</span></span> <span data-ttu-id="51531-112">例如，搜尋下列文字的 fields.xsd 檔案：</span><span class="sxs-lookup"><span data-stu-id="51531-112">For example, search the fields.xsd file for the following text:</span></span>  
  
   ```  
   <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
   ```  
  
    <span data-ttu-id="51531-113">並將文字變更為下列：</span><span class="sxs-lookup"><span data-stu-id="51531-113">And change the text to the following:</span></span>  
  
   ```  
   <xsd:include schemaLocation="datatypes.xsd"/>   
   ```  
  
2. <span data-ttu-id="51531-114">在 segments.xsd 檔案中，您必須移除所有執行個體的行，其中包含文字 processContents ="lax"。</span><span class="sxs-lookup"><span data-stu-id="51531-114">In the segments.xsd file, you must remove all instances of the lines that contain the text processContents="lax".</span></span> <span data-ttu-id="51531-115">例如，搜尋下列文字的 segments.xsd 檔案：</span><span class="sxs-lookup"><span data-stu-id="51531-115">For example, search the segments.xsd file for the following text:</span></span>  
  
   ```  
   <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
   ```  
  
    <span data-ttu-id="51531-116">And</span><span class="sxs-lookup"><span data-stu-id="51531-116">And</span></span>  
  
   ```  
   <xsd:any processContents="lax" namespace="##any"/>   
   ```  
  
    <span data-ttu-id="51531-117">然後移除這幾行。</span><span class="sxs-lookup"><span data-stu-id="51531-117">And remove those lines.</span></span>  
  
3. <span data-ttu-id="51531-118">您必須將標記 2&gt;xsd:schema&lt;2} 之下的所有結構描述新增下面這一行：</span><span class="sxs-lookup"><span data-stu-id="51531-118">For all schemas, under the tag xsd:schema, you must add the following line:</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="51531-119">如果您已使用 Microsoft 的結構描述，請勿將新增此行[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]因為[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會為您自動。</span><span class="sxs-lookup"><span data-stu-id="51531-119">Do not add this line if you have added the schema using Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] because [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does this for you automatically.</span></span>  
  
   ```  
   xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
   ```  
  
    <span data-ttu-id="51531-120">例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：</span><span class="sxs-lookup"><span data-stu-id="51531-120">For example, in the file ADT_A01.xsd, search for the following text:</span></span>  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="urn:hl7-org:v2xml"   
    targetNamespace="urn:hl7-org:v2xml">   
   ```  
  
    <span data-ttu-id="51531-121">並將文字變更為下列：</span><span class="sxs-lookup"><span data-stu-id="51531-121">And change the text to the following:</span></span>  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:hl7-org:v2xml"  
    targetNamespace="urn:hl7-org:v2xml"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
   ```  
  
4. <span data-ttu-id="51531-122">所有的結構描述，您必須新增根參考。</span><span class="sxs-lookup"><span data-stu-id="51531-122">For all schemas, you must add a root reference.</span></span> <span data-ttu-id="51531-123">例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：</span><span class="sxs-lookup"><span data-stu-id="51531-123">For example, in the ADT_A01.xsd file, search for the following text:</span></span>  
  
   ```  
   <xsd:include schemaLocation="segments.xsd" />   
   ```  
  
    <span data-ttu-id="51531-124">並變更所要的文字：</span><span class="sxs-lookup"><span data-stu-id="51531-124">And change the text to:</span></span>  
  
   ```  
   <xsd:include schemaLocation="segments.xsd" />  
   <xsd:annotation>   
     <xsd:appinfo>   
       <schemaInfo root_reference="ADT_A01"  
    xmlns="http://schemas.microsoft.com/BizTalk/2003" />   
     </xsd:appinfo>   
   </xsd:annotation>   
   ```  
  
   > [!NOTE]
   >  <span data-ttu-id="51531-125">如果您使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以使用下列程序來新增此 root_reference。</span><span class="sxs-lookup"><span data-stu-id="51531-125">If you are using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can add this root_reference by using the following procedure.</span></span>  
  
### <a name="to-add-the-root-reference"></a><span data-ttu-id="51531-126">若要加入根參考</span><span class="sxs-lookup"><span data-stu-id="51531-126">To add the root reference</span></span>  
  
1.  <span data-ttu-id="51531-127">在 [方案總管] 中，按兩下您想要編輯的結構描述。</span><span class="sxs-lookup"><span data-stu-id="51531-127">In Solution Explorer, double-click the schema you want to edit.</span></span>  
  
2.  <span data-ttu-id="51531-128">在 屬性 窗格中，向下捲動屬性**root_reference**，然後從下拉式清單中，按一下 具有相同的結構描述名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="51531-128">In the Properties pane, scroll down to the property **root_reference**, and from the drop-down list, click the property with the same schema name.</span></span>  
  
3.  <span data-ttu-id="51531-129">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="51531-129">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51531-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51531-130">See Also</span></span>  
 [<span data-ttu-id="51531-131">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="51531-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)