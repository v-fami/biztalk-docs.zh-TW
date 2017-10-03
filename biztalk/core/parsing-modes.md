---
title: "剖析模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], parsing
ms.assetid: b1188720-e5ae-47ae-ab8e-16d7ed08b778
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf8f9b2618b8cafd7813f08217457227a0f21809
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-modes"></a>剖析模式
剖析模式是 schemaInfo 記錄上的屬性，它有兩個模式：速度和複雜性。 您可在 BizTalk 結構描述編輯器中設定「剖析器最佳化」屬性。  
  
## <a name="example"></a>範例  
  
```  
<b:schemaInfo count_positions_by_byte="false" standard="Flat File"   
root_reference="document" parser_optimization="complexity" />.  
```  
  
 在速度模式中，剖析器會嘗試如同在資料流中一般提供資料。 例如，提供下列結構描述。  
  
```  
<schema>  
   Root ("," prefix)  
      Field1   opt  
      Field2   opt  
      Field3   opt  
      Field4   opt  
      Record ("," infix)  
            Field5  
            Field6  
</schema>  
```  
  
 及輸入訊息。  
  
```  
,1,2,3,4  
```  
  
 在速度模式中，會取得下列 XML 文件。  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
   <Field3>3</Field3>  
   <Field4>4</Field4>  
</Root>  
```  
  
 在複雜性模式中，相同的結構描述則會產生下列輸出。  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
      <Record>  
         <Field5>3</Field5>  
         <Field6>4</Field6>  
      </Record>  
</Root>  
```  
  
 在複雜性模式中，一般檔案剖析引擎會同時使用由上至下和由下至上的剖析，並嘗試提供更精確的資料。 在速度模式中，剖析器會嘗試如同在資料流中一般提供資料。  
  
 例如，如果您擁有具有必要項目的選用項目時。  
  
```  
<schema>  
   Root  
      Record1 (required)  
  
      Record2 (optional)  
  
      Record3 (required)  
  
```  
  
 您必須使用複雜性模式才可正確剖析資料，因為剖析器會在內部將剖析器表示為  
  
```  
<schema>  
   Root  
      Record1 (required)  
      <sequence> (optional)  
         Record2 (required)  
         Record3 (required)  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用一般檔案剖析引擎](../core/using-the-flat-file-parsing-engine.md)