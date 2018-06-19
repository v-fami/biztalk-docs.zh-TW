---
title: 分隔記錄中的最小欄位長度 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d803eb311bda7c27db5a05830f7a84f9b9857e8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263638"
---
# <a name="minimum-field-lengths-within-delimited-records"></a>分隔記錄中的最小欄位長度
依照定義，序數記錄中的欄位都定義為具有指定的長度。 分隔記錄中的欄位也可以定義為具有最小長度。 這項特性由定義 **[Minimum Length with Pad Character**屬性**欄位項目**和**欄位屬性**節點。  
  
 當您提供非零值給**Minimum Length with Pad Character**屬性，一般檔案組合器將會決定欄位相關聯的資料字元數目是否小於設定**Minimum Length with Pad Character**屬性相關的填補字元會用來補足差距。  
  
 之前或之後的資料字元為基礎的設定，將會加入填補字元**理由**欄位的屬性。 當**理由**屬性設定為**左**，在資料字元之後，就會新增為滿足最小長度所需的任何填補字元。 當**理由**屬性設定為**右邊**，為滿足最小長度所需的任何填補字元將會加入在資料字元之前。  
  
 當您提供非零值給**Minimum Length with Pad Character**屬性，一般檔案解譯器會檢查的開頭或結尾 (根據設定的**理由**屬性) 的欄位值的相關填補字元，存在，如果有的話，填補字元會被捨棄，並且不會出現在要建構的對等 XML 訊息。  
  
## <a name="see-also"></a>另請參閱  
-  [欄位考量](../core/field-considerations.md)   
-  **對齊方式 （一般檔案結構描述中的節點屬性）** 和**Minimum Length with Pad Character （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]