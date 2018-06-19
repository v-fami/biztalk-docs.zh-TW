---
title: 逸出字元 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af800b9-d31b-487a-9a06-6eda47d1574e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e961a205b77a9944a497d6e6cbed0df71f63e03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246126"
---
# <a name="escape-characters"></a>逸出字元

## <a name="overview"></a>概觀
逸出字元是隱藏其後任何特殊意義字元的單一字元。 例如，若您定義一般檔案記錄為具備下列特性：  
  
-   名稱 = Record1  
  
-   使用分隔符號  
  
-   子分隔符號 = 逗號字元 (,)  
  
-   子順序 = 前置詞  
  
-   逸出字元 = 反斜線字元 (\\)  
  
-   標記 = RECORD1  
  
-   兩個欄位分別名為 Field1 和 Field2  
  
 然後，下列一般檔案資料要求取得記錄。  
  
```  
RECORD1,testfield1\,testfield1,testfield2  
                  ^^  
  
```  
  
 資料將解譯為下列 XML 分割。  
  
```  
<Record1>  
    <Field1>testfield1,testfield1</Field1>  
    <Field2>testfield2</Field2>  
</Record1>  
  
```  
  
 請注意，在一般檔案記錄之後一行中指出的逸出字元順序 `\,` 已經轉換為單一逗號字元，對等 XML 記錄的 Field1 資料中沒有逸出字元。 此外，該逗號字元不會和另外兩個逗號一樣解譯為欄位分隔符號。  
  
 當一般檔案組合器執行反向作業，將記錄的 XML 版本轉換為其對等的一般檔案記錄時，會將逸出字元插入 Field1 中間的逗號之前，以此表示應該將它解譯為資料，而不是欄位分隔符號。  
  
 在建立時使用 「 BizTalk 編輯器的一般檔案結構描述，您可以定義預設的逸出字元整個結構描述使用**預設逸出字元**和**預設逸出字元類型**屬性**結構描述**節點。 然後，您可以設定為使用此預設逸出字元，或自訂的特定記錄的逸出字元使用結構描述中的每個個別記錄**逸出字元]** 和**逸出字元類型**屬性**記錄**節點。  
  
## <a name="see-also"></a>另請參閱  
- [如何將特殊字元解譯為欄位值的一部分](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- 逸出字元屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - 預設逸出字元 （一般檔案結構描述中的節點屬性）
    - 預設逸出字元類型 （一般檔案結構描述中的節點屬性）
    - 逸出字元 （一般檔案結構描述中的節點屬性）  
    - 逸出字元類型 （一般檔案結構描述中的節點屬性）