---
title: 分隔記錄中的最小欄位長度 |Microsoft Docs
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
ms.openlocfilehash: 992ffbc6a2e0568bc000413bf90b3c92012d4d59
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983311"
---
# <a name="minimum-field-lengths-within-delimited-records"></a>分隔記錄中的最小欄位長度
依照定義，序數記錄中的欄位都定義為具有指定的長度。 分隔記錄中的欄位也可以定義為具有最小長度。 這項特性由定義 **[Minimum Length with Pad Character**屬性**欄位項目**並**欄位屬性**節點。  

 當您提供非零的值給**Minimum Length with Pad Character**屬性，一般檔案組合器會判斷與欄位相關聯的資料字元數目是否小於設定**Minimum Length with Pad Character**屬性相關的填補字元會用來補足差距。  

 之前或之後的資料字元為基礎的設定，將會加入填補字元**理由**欄位屬性。 當**理由**屬性設定為**左**，符合的最小長度所需的任何填補字元將會新增在資料字元之後。 當**理由**屬性設定為**右**，符合的最小長度所需的任何填補字元會在資料字元之前新增。  

 當您提供非零的值給**Minimum Length with Pad Character**屬性，一般檔案解譯器會檢查的開頭或結尾 (根據設定的**理由**屬性) 的欄位值存在相關填補字元，以及如果有的話，填補字元都會被捨棄，不會出現在對等所建構的 XML 訊息。  

## <a name="see-also"></a>另請參閱  
- [欄位考量](../core/field-considerations.md)   
- **（一般檔案結構描述中的節點屬性） 的理由**和**Minimum Length with Pad Character （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
