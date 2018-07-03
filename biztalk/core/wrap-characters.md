---
title: 換行字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7268f46-9bf6-4c76-9b3a-b4ee0e8db997
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7d88c412c94505600443d351a150b6ca8a6876a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996591"
---
# <a name="wrap-characters"></a>換行字元

## <a name="overview"></a>概觀
換行字元是在欄位中用來將資料字元換行的單一字元，目的在於抑制任何資料字元可能另外具有的特殊意義。 例如，若您定義一般檔案記錄為具備下列特性：  
  
- 名稱 = Record1  
  
- 使用分隔符號  
  
- 子分隔符號 = 逗號字元 (,)  
  
- Child order = infix  
  
- 逸出字元 = 反斜線字元 (\\)  
  
- 標記 = RECORD1  
  
- 三個名為 Field1、Field2 及 Field3 的欄位，每個都已定義為使用數字符號字元 (#) 做為其換行字元。  
  
  然後，下列一般檔案資料要求取得記錄。  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 資料會解譯為下列 XML 分割。  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2></Field2>  
    <Field3></Field3>  
</Record1>  
  
```  
  
 請注意，包圍在粗體資料字元 field1、field2 及 field3 的換行字元 (#) 已移除。  
  
 當一般檔案組合器執行反向作業時，將記錄的 XML 版本轉換為其相等的一般檔案記錄時，插入之前和之後的每個欄位，產生的原始順序的資料字元換行字元一般檔案字元。  
  
 定義的逸出字元可與定義的換行字元搭配使用。 例如，假設 Field1 的值已變更，如下所示 (以粗體顯示)。  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2>field2</Field2>  
    <Field3>field3</Field3>  
</Record1>  
  
```  
  
 使用提供的記錄與欄位定義來組合此 XML 分割時，會產生一般檔案字元的下列順序 (逸出的數字符號字元順序會以粗體顯示)。  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 在建立時使用 「 BizTalk 編輯器的一般檔案結構描述，您可以定義整個結構描述使用的預設換行字元**預設換行字元**並**預設換行字元類型**屬性**結構描述**節點。 然後，您可以設定為使用此預設換行字元或自訂的特定欄位的換行字元，使用結構描述中的每個個別的欄位**換行字元**並**Wrap Character Type**屬性**欄位項目**或是**Field 屬性**一般檔案結構描述中的節點。
  
## <a name="see-also"></a>另請參閱  
- [解譯特殊字元作為欄位值一部分的方式](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- 換行字元屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    -  預設換行字元 （一般檔案結構描述的節點屬性
    -  預設換行字元類型 （一般檔案結構描述的節點屬性
    -  換行字元 （一般檔案結構描述的節點屬性  
    -  換行字元類型 （一般檔案結構描述的節點屬性