---
title: 命名空間管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4638c47c-3cdd-43af-aa00-da98e7293503
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa476034a578be24bf388c87f38f910565cd2548
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022468"
---
# <a name="namespace-management"></a>命名空間管理
「BizTalk 編輯器」可支援命名空間。 XML 命名空間是名稱的集合，可以用來做為 XML 訊息中的項目或屬性名稱。 命名空間限定項目和屬性名稱，以避免相同結構描述中其他地方所定義的相同項目和屬性名稱之間發生衝突。  
  
 命名空間由「通用資源識別項」(URI) 或「統一資源定位器」(URL) 識別。 它們通常還會有一個簡短的前置詞別名，在項目或屬性名稱本身之前加上分隔符號 (:) 區隔。 比方說，常會看到下列命名空間宣告內**結構描述**的結構描述之 XSD 表示中的項目。  
  
```  
xmlns:xs="http://www.w3.org/2001/XMLSchema"  
  
```  
  
 前置詞為 xs，您會看到在整個 XSD 表示法中，限定為這類項目**項目**項目 (xs: element) 和**屬性**元素 (xs: attribute)。  
  
 當您第一次建立新的結構描述，而不論其是否訊息結構描述或屬性結構描述，請務必設定**目標命名空間**屬性**結構描述**節點正確。 您必須在其他結構描述以匯入/包含/重新定義機制使用此結構描述之前，以及定義任何屬性升級之前，先建立目標命名空間。  
  
> [!WARNING]
>  如果您將會使用兩個只有大小寫不同的命名空間，BizTalk 資料庫必須安裝區分大小寫的定序。 區分大小寫定序的範例包括啟用區分大小寫的二進位和非二進位定序。 如果沒有完成這個動作，結構描述解析就會失敗，因為 XML 是區分大小寫的。  
  
 下列兩個命名空間會自動新增為結構描述的 XML 結構描述定義 (XSD) 語言表示法中結構描述項目的命名空間宣告。  
  
- xmlns:b ="<http://schemas.microsoft.com/BizTalk/2003>」  
  
- xmlns:xs ="<http://www.w3.org/2001/XMLSchema>」  
  
  在使用您正建立的結構描述中之其他結構描述的過程中，會宣告其他命名空間。 您可以檢查這些命名空間，以及自動包含的命名空間，在**匯入**對話方塊中，您可以使用存取**Imports**屬性**結構描述**節點。 多個您要建立使用其他結構描述內其他結構描述中宣告的資料類型的相關資訊，請參閱[，使用其他結構描述](../core/schemas-that-use-other-schemas.md)並[建立使用其他結構描述的](../core/how-to-create-schemas-that-use-other-schemas.md)。  
  
  可在中檢查屬性結構描述相關聯的命名空間**升級屬性** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [建立結構描述時的考量](../core/considerations-when-creating-schemas.md)