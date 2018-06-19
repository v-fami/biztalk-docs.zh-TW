---
title: 修改 2.使用 [BizTalk 編輯器] 中的 XML 結構描述 |Microsoft 文件
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
ms.openlocfilehash: cf68f39e4e4c36587b889490b28541e5a690ed05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206102"
---
# <a name="modifying-2xml-schemas-to-work-with-biztalk-editor"></a>修改 2.若要使用 [BizTalk 編輯器] 中的 XML 結構描述
HL7 2.XML 結構描述需要使用適當的修改[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。 以下描述如何修改 HL7 V2。XML 結構描述，您可以使用 BizTalk 編輯器中使用它們。  
  
> [!IMPORTANT]
>  Update2XMLSchema 工具會自動執行這些步驟。 請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)如需詳細資訊。  
  
> [!NOTE]
>  **Nillable**屬性可能會發生在結構描述中的項目上。 如果設定為**true**，它會指出父項目的執行個體可以有**xsi: nil ="true"** 屬性。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]在編譯和剖析/序列化期間，會忽略這個屬性。  
  
### <a name="to-modify-2xml-schemas"></a>若要修改 2.XML 結構描述  
  
1.  在 fields.xsd 檔案中，您必須移除的執行個體**匯入**並將其取代為**包含**。 例如，搜尋 fields.xsd 檔中的下列文字：  
  
    ```  
    <xsd:import namespace="urn:hl7-org:v2xml" schemaLocation="datatypes.xsd"/>   
    ```  
  
     然後將文字變更為下列：  
  
    ```  
    <xsd:include schemaLocation="datatypes.xsd"/>   
    ```  
  
2.  在 segments.xsd 檔案中，您必須移除所有的執行個體，包含文字 processContents 的線條 ="lax"。 例如，搜尋 segments.xsd 檔中的下列文字：  
  
    ```  
    <xsd:any processContents="lax" namespace="##any" minOccurs="0"/>   
    ```  
  
     And  
  
    ```  
    <xsd:any processContents="lax" namespace="##any"/>   
    ```  
  
     然後移除這些行。  
  
3.  所有結構描述，在標記 」 xsd: schema，您必須加入下列行：  
  
    > [!NOTE]
    >  如果您新增結構描述使用，請勿將加入這一行[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]因為[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會為您自動。  
  
    ```  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    ```  
  
     例如，ADT_A01.xsd 檔案中搜尋下列文字：  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns="urn:hl7-org:v2xml"   
     targetNamespace="urn:hl7-org:v2xml">   
    ```  
  
     然後將文字變更為下列：  
  
    ```  
    <xsd:schema  
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     xmlns="urn:hl7-org:v2xml"  
     targetNamespace="urn:hl7-org:v2xml"  
     xmlns:b="http://schemas.microsoft.com/BizTalk/2003">   
    ```  
  
4.  所有的結構描述，您必須加入根參考。 例如，在 ADT_A01.xsd 檔案中，搜尋下列文字：  
  
    ```  
    <xsd:include schemaLocation="segments.xsd" />   
    ```  
  
     並將變更的文字：  
  
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
    >  如果您使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您就可以使用下列程序來新增此 root_reference。  
  
### <a name="to-add-the-root-reference"></a>若要加入根參考  
  
1.  在 [方案總管] 中，按兩下您想要編輯的結構描述。  
  
2.  在 屬性 窗格中，向下捲動屬性**root_reference**，並從下拉式清單中，按一下 以相同的結構描述名稱屬性。  
  
3.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)