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
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a>修改 2.xml 結構描述才能使用 BizTalk 編輯器
HL7 2.xml 結構描述需要進行修改才能正常使用 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。 以下說明如何修改 HL7 V2。可讓您使用它們在 「 BizTalk 編輯器 」 使用的 XML 結構描述。  
  
> [!IMPORTANT]
>  Update2XMLSchema 工具會自動執行這些步驟。 請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)如需詳細資訊。  
> 
> [!NOTE]
>  **Nillable**屬性可能會發生在結構描述中的項目上。 如果設定為 **，則為 true**，它會指出可以有父項目的執行個體**xsi: nil ="true"** 屬性。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 在編譯期間，在剖析/序列化期間，會忽略這個屬性。  
  
### <a name="to-modify-2xml-schemas"></a>若要修改 2.xml 結構描述  
  
1. 在 fields.xsd 檔案中，您必須移除的執行個體**匯入**並將其取代為**包含**。 例如，搜尋下列文字的 fields.xsd 檔案：  
  
   ```  
   <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
   ```  
  
    並將文字變更為下列：  
  
   ```  
   <xsd:include schemaLocation="datatypes.xsd"/>   
   ```  
  
2. 在 segments.xsd 檔案中，您必須移除所有執行個體的行，其中包含文字 processContents ="lax"。 例如，搜尋下列文字的 segments.xsd 檔案：  
  
   ```  
   <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
   ```  
  
    And  
  
   ```  
   <xsd:any processContents="lax" namespace="##any"/>   
   ```  
  
    然後移除這幾行。  
  
3. 您必須將標記 2&gt;xsd:schema&lt;2} 之下的所有結構描述新增下面這一行：  
  
   > [!NOTE]
   >  如果您已使用 Microsoft 的結構描述，請勿將新增此行[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]因為[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會為您自動。  
  
   ```  
   xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
   ```  
  
    例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="urn:hl7-org:v2xml"   
    targetNamespace="urn:hl7-org:v2xml">   
   ```  
  
    並將文字變更為下列：  
  
   ```  
   <xsd:schema  
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:hl7-org:v2xml"  
    targetNamespace="urn:hl7-org:v2xml"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
   ```  
  
4. 所有的結構描述，您必須新增根參考。 例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：  
  
   ```  
   <xsd:include schemaLocation="segments.xsd" />   
   ```  
  
    並變更所要的文字：  
  
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
   >  如果您使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以使用下列程序來新增此 root_reference。  
  
### <a name="to-add-the-root-reference"></a>若要加入根參考  
  
1.  在 [方案總管] 中，按兩下您想要編輯的結構描述。  
  
2.  在 屬性 窗格中，向下捲動屬性**root_reference**，然後從下拉式清單中，按一下 具有相同的結構描述名稱的屬性。  
  
3.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)