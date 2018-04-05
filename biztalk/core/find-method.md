---
title: Find 方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Find method
ms.assetid: 676827a6-82af-4922-bf9e-aca5bd23624b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5432c68c36dcf8e769351af6d57f3cd3ed712b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="find-method"></a>Find 方法
用來傳回滿足提供的部分搜尋索引鍵的索引鍵清單。 請注意，對於只有一個執行個體的元件介面 (即沒有索引鍵)，則不會產生 `Find()` 函數。 另請參閱[Get 方法](../core/get-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
Find (partialKey, keyList)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|`partialKey`|一種結構，其中個別的索引鍵是選擇性的|  
|`keyList`|符合 `partialKey` 的索引鍵清單。 這是輸出參數。<br /><br /> 與為特定的元件介面定義的「尋找索引鍵」集合對應的索引鍵。|  
  
## <a name="remarks"></a>備註  
 當您指定部分索引鍵時，可以使用 PeopleSoft 內部的 `Find()` 函數所提供相同的萬用字元搜尋。 例如，"11" 的部分 ACCOUNT 索引鍵會傳回開頭為 "11" 的所有 ACCOUNT 索引鍵，而 "%40" 則會傳回索引鍵中的任何部分包含 "40" 的所有 ACCOUNT 索引鍵。 部分索引鍵 "_4_4" 會傳回第二個和第四個位置中含有字元 "4" 的所有 ACCOUNT 索引鍵。  
  
 注意： 與目前的 PeopleSoft Server 實作，超過 300 個項目符合搜尋條件，如果呼叫失敗。 這是 PeopleSoft Server 的限制。 如果在元件介面中啟用 PeopleSoft `Find()` 函數，並且可以使用 Get 索引鍵，就提供 Microsoft BizTalk Adapter for PeopleSoft Enterprise `Find` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)