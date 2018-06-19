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
# <a name="extending-biztalk-editor"></a>延伸 BizTalk 編輯器
BizTalk 編輯器被為了允許支援替代的執行個體訊息格式的副檔名。 事實上，XML 格式是「BizTalk 編輯器」內建的唯一格式。 對一般檔案格式的均等支援 (包含在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中) 可實作為「BizTalk 編輯器」延伸模組，因此可做為由此類延伸模組新增之功能類型的良好範例。  
  
 一般而言，「BizTalk 編輯器」延伸模組保存其自訂資料為與對應至結構描述樹狀結構中的節點之 XSD 項目相關聯的 XML 結構描述定義 (XSD) 語言註解。 同樣的，由「一般檔案延伸模組」新增至「BizTalk 編輯器」的延伸註解組可做為「BizTalk 編輯器」延伸模組將其自訂資料保存在結構描述中的方式範例。  
  
 「BizTalk 編輯器」延伸模組是延伸「BizTalk 編輯器」功能的 .NET 組件。 若要識別做為擴充，組件必須實作一個類別**IExtension**介面，並必須位於產品安裝目錄中的 Developer Tools\Schema Editor Extensions 資料夾之下。  
  
 延伸模組的開發人員必須使其組件參考 Microsoft.BizTalk.SchemaEditor.Extensibility.dll，其中包含公佈延伸功能至「BizTalk 編輯器」所需之所有介面的定義。 在定義這些介面**Microsoft.BizTalk.SchemaEditor.Extensibility**命名空間。  
  
 **IExtension**介面是延伸模組，從 BizTalk 編輯器 中存取的擴充的功能，例如屬性管理員、 自訂檢視、 結構描述驗證、 原生執行個體產生以及原生進入點執行個體驗證。  
  
 指定的結構描述可以有多個與它相關聯的延伸模組，但只有一個可以設定為標準，在指定的時間。這在設定**標準**屬性**結構描述**節點。 目前設定為標準的延伸模組供原生執行個體產生與驗證以及結構描述驗證所使用。  
  
 擴充功能可以藉由編輯與特定結構描述相關聯**Schema Editor Extensions**屬性**結構描述**節點。 在結構描述相關聯的擴充功能的相關資訊儲存在結構描述本身，**註解**元素**結構描述**項目，如下列 XSD 片段中所述。  
  
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
  
 擴充物件之後，架構會叫用**初始化**方法**IExtension**介面，傳遞**ITree**物件使擴充功能可以存取結構描述樹狀結構的相關資訊。 例如，擴充功能時，無法藉由存取跨越所有子節點**ITree.RootNode**屬性。  
  
 本節描述可將「BizTalk 編輯器」延伸模組整合至「BizTalk 編輯器」環境，並將本身安裝至現有的「BizTalk 編輯器」命令的方式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [屬性管理員](../core/property-managers.md)  
  
-   [自訂檢視](../core/custom-views.md)  
  
-   [結構描述驗證](../core/schema-validation1.md)  
  
-   [執行個體驗證](../core/instance-validation.md)  
  
-   [執行個體產生](../core/instance-generation.md)