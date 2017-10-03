---
title: "修改 2.使用 [BizTalk 編輯器] 中的 XML 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, modifying
- modifying, 2.XML schemas
ms.assetid: 07316826-84b6-494e-81b9-f64a3d46ffb0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf68f39e4e4c36587b889490b28541e5a690ed05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a><span data-ttu-id="7b185-102">修改 2.若要使用 [BizTalk 編輯器] 中的 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="7b185-102">Modifying 2.XML Schemas to Work with BizTalk Editor</span></span>
<span data-ttu-id="7b185-103">HL7 2.XML 結構描述需要使用適當的修改[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="7b185-103">HL7 2.XML schemas require modification to work properly with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span> <span data-ttu-id="7b185-104">以下描述如何修改 HL7 V2。XML 結構描述，您可以使用 BizTalk 編輯器中使用它們。</span><span class="sxs-lookup"><span data-stu-id="7b185-104">The following describes how to modify HL7 V2.XML schemas to enable you to use them with BizTalk Editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b185-105">Update2XMLSchema 工具會自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="7b185-105">The Update2XMLSchema tool performs these steps automatically.</span></span> <span data-ttu-id="7b185-106">請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7b185-106">See [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md) for more information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b185-107">**Nillable**屬性可能會發生在結構描述中的項目上。</span><span class="sxs-lookup"><span data-stu-id="7b185-107">The **nillable** attribute can occur in a schema on an element.</span></span> <span data-ttu-id="7b185-108">如果設定為**true**，它會指出父項目的執行個體可以有**xsi: nil ="true"**屬性。</span><span class="sxs-lookup"><span data-stu-id="7b185-108">If set to **true**, it indicates that the instance of the parent element can have an **xsi:nil="true"** attribute.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="7b185-109">在編譯和剖析/序列化期間，會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="7b185-109"> ignores this attribute during compilation and during parsing/serialization.</span></span>  
  
### <a name="to-modify-2xml-schemas"></a><span data-ttu-id="7b185-110">若要修改 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="7b185-110">To modify 2.XML schemas</span></span>  
  
1.  <span data-ttu-id="7b185-111">在 fields.xsd 檔案中，您必須移除的執行個體**匯入**並將其取代為**包含**。</span><span class="sxs-lookup"><span data-stu-id="7b185-111">In the fields.xsd file, you must remove instances of **import** and replace them with **include**.</span></span> <span data-ttu-id="7b185-112">例如，搜尋 fields.xsd 檔中的下列文字：</span><span class="sxs-lookup"><span data-stu-id="7b185-112">For example, search the fields.xsd file for the following text:</span></span>  
  
    ```  
    <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
    ```  
  
     <span data-ttu-id="7b185-113">然後將文字變更為下列：</span><span class="sxs-lookup"><span data-stu-id="7b185-113">And change the text to the following:</span></span>  
  
    ```  
    <xsd:include schemaLocation="datatypes.xsd"/>   
    ```  
  
2.  <span data-ttu-id="7b185-114">在 segments.xsd 檔案中，您必須移除所有的執行個體，包含文字 processContents 的線條 ="lax"。</span><span class="sxs-lookup"><span data-stu-id="7b185-114">In the segments.xsd file, you must remove all instances of the lines that contain the text processContents="lax".</span></span> <span data-ttu-id="7b185-115">例如，搜尋 segments.xsd 檔中的下列文字：</span><span class="sxs-lookup"><span data-stu-id="7b185-115">For example, search the segments.xsd file for the following text:</span></span>  
  
    ```  
    <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
    ```  
  
     <span data-ttu-id="7b185-116">And</span><span class="sxs-lookup"><span data-stu-id="7b185-116">And</span></span>  
  
    ```  
    <xsd:any processContents="lax" namespace="##any"/>   
    ```  
  
     <span data-ttu-id="7b185-117">然後移除這些行。</span><span class="sxs-lookup"><span data-stu-id="7b185-117">And remove those lines.</span></span>  
  
3.  <span data-ttu-id="7b185-118">所有結構描述，在標記 」 xsd: schema，您必須加入下列行：</span><span class="sxs-lookup"><span data-stu-id="7b185-118">For all schemas, under the tag xsd:schema, you must add the following line:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7b185-119">如果您新增結構描述使用，請勿將加入這一行[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]因為[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會為您自動。</span><span class="sxs-lookup"><span data-stu-id="7b185-119">Do not add this line if you have added the schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] because [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does this for you automatically.</span></span>  
  
    ```  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    ```  
  
     <span data-ttu-id="7b185-120">例如，ADT_A01.xsd 檔案中搜尋下列文字：</span><span class="sxs-lookup"><span data-stu-id="7b185-120">For example, in the file ADT_A01.xsd, search for the following text:</span></span>  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns="urn:hl7-org:v2xml"   
     targetNamespace="urn:hl7-org:v2xml">   
    ```  
  
     <span data-ttu-id="7b185-121">然後將文字變更為下列：</span><span class="sxs-lookup"><span data-stu-id="7b185-121">And change the text to the following:</span></span>  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="urn:hl7-org:v2xml"  
     targetNamespace="urn:hl7-org:v2xml"  
     xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
    ```  
  
4.  <span data-ttu-id="7b185-122">所有的結構描述，您必須加入根參考。</span><span class="sxs-lookup"><span data-stu-id="7b185-122">For all schemas, you must add a root reference.</span></span> <span data-ttu-id="7b185-123">例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：</span><span class="sxs-lookup"><span data-stu-id="7b185-123">For example, in the ADT_A01.xsd file, search for the following text:</span></span>  
  
    ```  
    <xsd:include schemaLocation="segments.xsd" />   
    ```  
  
     <span data-ttu-id="7b185-124">並將變更的文字：</span><span class="sxs-lookup"><span data-stu-id="7b185-124">And change the text to:</span></span>  
  
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
    >  <span data-ttu-id="7b185-125">如果您使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您就可以使用下列程序來新增此 root_reference。</span><span class="sxs-lookup"><span data-stu-id="7b185-125">If you are using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you can add this root_reference by using the following procedure.</span></span>  
  
### <a name="to-add-the-root-reference"></a><span data-ttu-id="7b185-126">若要加入根參考</span><span class="sxs-lookup"><span data-stu-id="7b185-126">To add the root reference</span></span>  
  
1.  <span data-ttu-id="7b185-127">在 [方案總管] 中，按兩下您想要編輯的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7b185-127">In Solution Explorer, double-click the schema you want to edit.</span></span>  
  
2.  <span data-ttu-id="7b185-128">在 屬性 窗格中，向下捲動屬性**root_reference**，並從下拉式清單中，按一下 以相同的結構描述名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="7b185-128">In the Properties pane, scroll down to the property **root_reference**, and from the drop-down list, click the property with the same schema name.</span></span>  
  
3.  <span data-ttu-id="7b185-129">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="7b185-129">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b185-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b185-130">See Also</span></span>  
 [<span data-ttu-id="7b185-131">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="7b185-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)