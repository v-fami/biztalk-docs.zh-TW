---
title: 延伸 BizTalk 編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77c93ab2-0a9b-4c9d-81e5-3871fc8e6e13
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8e4f574e652420ae11410e52268a199639cf6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246238"
---
# <a name="extending-biztalk-editor"></a><span data-ttu-id="26c9d-102">延伸 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="26c9d-102">Extending BizTalk Editor</span></span>
<span data-ttu-id="26c9d-103">BizTalk 編輯器被為了允許支援替代的執行個體訊息格式的副檔名。</span><span class="sxs-lookup"><span data-stu-id="26c9d-103">BizTalk Editor is designed to allow extensions that support alternative instance message formats.</span></span> <span data-ttu-id="26c9d-104">事實上，XML 格式是「BizTalk 編輯器」內建的唯一格式。</span><span class="sxs-lookup"><span data-stu-id="26c9d-104">In fact, the XML format is the only format that is built into BizTalk Editor.</span></span> <span data-ttu-id="26c9d-105">對一般檔案格式的均等支援 (包含在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中) 可實作為「BizTalk 編輯器」延伸模組，因此可做為由此類延伸模組新增之功能類型的良好範例。</span><span class="sxs-lookup"><span data-stu-id="26c9d-105">Even support for flat file formats, which is included in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], is implemented as a BizTalk Editor extension, thereby serving as a good example of the type of functionality that can be added by such extensions.</span></span>  
  
 <span data-ttu-id="26c9d-106">一般而言，「BizTalk 編輯器」延伸模組保存其自訂資料為與對應至結構描述樹狀結構中的節點之 XSD 項目相關聯的 XML 結構描述定義 (XSD) 語言註解。</span><span class="sxs-lookup"><span data-stu-id="26c9d-106">In general, BizTalk Editor extensions persist their custom data as XML Schema definition (XSD) language annotations associated with the XSD elements that correspond to the nodes in the schema tree.</span></span> <span data-ttu-id="26c9d-107">同樣的，由「一般檔案延伸模組」新增至「BizTalk 編輯器」的延伸註解組可做為「BizTalk 編輯器」延伸模組將其自訂資料保存在結構描述中的方式範例。</span><span class="sxs-lookup"><span data-stu-id="26c9d-107">Again, the extensive set of annotations added by the Flat File Extension to BizTalk Editor serves as a good example of the way in which BizTalk Editor extensions can persist their custom data in the schema.</span></span>  
  
 <span data-ttu-id="26c9d-108">「BizTalk 編輯器」延伸模組是延伸「BizTalk 編輯器」功能的 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="26c9d-108">BizTalk Editor extensions are .NET assemblies that extend the functionality of BizTalk Editor.</span></span> <span data-ttu-id="26c9d-109">若要識別做為擴充，組件必須實作一個類別**IExtension**介面，並必須位於產品安裝目錄中的 Developer Tools\Schema Editor Extensions 資料夾之下。</span><span class="sxs-lookup"><span data-stu-id="26c9d-109">To be identified as an extension, an assembly must have one class that implements the **IExtension** interface, and must be located under the Developer Tools\Schema Editor Extensions folder in the product installation directory.</span></span>  
  
 <span data-ttu-id="26c9d-110">延伸模組的開發人員必須使其組件參考 Microsoft.BizTalk.SchemaEditor.Extensibility.dll，其中包含公佈延伸功能至「BizTalk 編輯器」所需之所有介面的定義。</span><span class="sxs-lookup"><span data-stu-id="26c9d-110">The developer of an extension must have its assembly reference the Microsoft.BizTalk.SchemaEditor.Extensibility.dll, which contains the definition of all the interfaces needed for exposing extended functionality to BizTalk Editor.</span></span> <span data-ttu-id="26c9d-111">在定義這些介面**Microsoft.BizTalk.SchemaEditor.Extensibility**命名空間。</span><span class="sxs-lookup"><span data-stu-id="26c9d-111">Those interfaces are defined under the **Microsoft.BizTalk.SchemaEditor.Extensibility** namespace.</span></span>  
  
 <span data-ttu-id="26c9d-112">**IExtension**介面是延伸模組，從 BizTalk 編輯器 中存取的擴充的功能，例如屬性管理員、 自訂檢視、 結構描述驗證、 原生執行個體產生以及原生進入點執行個體驗證。</span><span class="sxs-lookup"><span data-stu-id="26c9d-112">The **IExtension** interface is the entry point for the extension, from which BizTalk Editor accesses the extended functionality, such as property managers, custom views, schema validation, native instance generation, and native instance validation.</span></span>  
  
 <span data-ttu-id="26c9d-113">指定的結構描述可以有多個與它相關聯的延伸模組，但只有一個可以設定為標準，在指定的時間。這在設定**標準**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="26c9d-113">A given schema can have multiple extensions associated with it, but only one can be set as the standard at a given time; this is set in the **Standard** property of the **Schema** node.</span></span> <span data-ttu-id="26c9d-114">目前設定為標準的延伸模組供原生執行個體產生與驗證以及結構描述驗證所使用。</span><span class="sxs-lookup"><span data-stu-id="26c9d-114">The extension currently set as the standard is the one used for native instance generation and validation, and for schema validation.</span></span>  
  
 <span data-ttu-id="26c9d-115">擴充功能可以藉由編輯與特定結構描述相關聯**Schema Editor Extensions**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="26c9d-115">Extensions can be associated with a given schema by editing the **Schema Editor Extensions** property of the **Schema** node.</span></span> <span data-ttu-id="26c9d-116">在結構描述相關聯的擴充功能的相關資訊儲存在結構描述本身，**註解**元素**結構描述**項目，如下列 XSD 片段中所述。</span><span class="sxs-lookup"><span data-stu-id="26c9d-116">The information about the extensions associated with a schema is stored in the schema itself, within the **annotation** element of the **schema** element, as illustrated in the following XSD fragment.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema11"  
        xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
        targetNamespace="http://BizTalk_Server_Project1.Schema11"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <schemaEditorExtension:schemaInfo namespaceAlias="b"  
                extensionClass="Microsoft.BizTalk.FlatFileExtension.FlatFileExtension"  
                standardName="Flat File"  
                xmlns:schemaEditorExtension="http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions" />  
            <b:schemaInfo schema_type="document" root_reference="Root"  
                is_receipt="no" schema_name="abc"  
                standard="Flat File"  
                count_positions_by_byte="false" />   
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="Root">  
        ...  
  
```  
  
 <span data-ttu-id="26c9d-117">擴充物件之後，架構會叫用**初始化**方法**IExtension**介面，傳遞**ITree**物件使擴充功能可以存取結構描述樹狀結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="26c9d-117">After instantiating the extension object, the framework invokes the **Initialize** method of the **IExtension** interface, passing an **ITree** object so that the extension can access information about the schema tree.</span></span> <span data-ttu-id="26c9d-118">例如，擴充功能時，無法藉由存取跨越所有子節點**ITree.RootNode**屬性。</span><span class="sxs-lookup"><span data-stu-id="26c9d-118">For example, the extension could traverse all child nodes by accessing the **ITree.RootNode** property.</span></span>  
  
 <span data-ttu-id="26c9d-119">本節描述可將「BizTalk 編輯器」延伸模組整合至「BizTalk 編輯器」環境，並將本身安裝至現有的「BizTalk 編輯器」命令的方式。</span><span class="sxs-lookup"><span data-stu-id="26c9d-119">This section describes the ways in which a BizTalk Editor extension can integrate into the BizTalk Editor environment and hook itself into existing BizTalk Editor commands.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26c9d-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="26c9d-120">In This Section</span></span>  
  
-   [<span data-ttu-id="26c9d-121">屬性管理員</span><span class="sxs-lookup"><span data-stu-id="26c9d-121">Property Managers</span></span>](../core/property-managers.md)  
  
-   [<span data-ttu-id="26c9d-122">自訂檢視</span><span class="sxs-lookup"><span data-stu-id="26c9d-122">Custom Views</span></span>](../core/custom-views.md)  
  
-   [<span data-ttu-id="26c9d-123">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="26c9d-123">Schema Validation</span></span>](../core/schema-validation1.md)  
  
-   [<span data-ttu-id="26c9d-124">執行個體驗證</span><span class="sxs-lookup"><span data-stu-id="26c9d-124">Instance Validation</span></span>](../core/instance-validation.md)  
  
-   [<span data-ttu-id="26c9d-125">執行個體產生</span><span class="sxs-lookup"><span data-stu-id="26c9d-125">Instance Generation</span></span>](../core/instance-generation.md)