---
title: 元件介面使用者定義方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, user-defined methods
- user-defined methods, component interface
- custom component interfaces, limitations
- collection limitations
- custom methods, samples
- samples, custom methods
- component interfaces, limitations for custom CI
ms.assetid: e4b15889-35ff-44aa-819d-eade9690bdd6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68149876dc51d90b4dbc07772fd9b9b5c60fb7db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022564"
---
# <a name="component-interface-user-defined-methods"></a>元件介面使用者定義方法
Microsoft BizTalk Adapter for PeopleSoft Enterprise 支援在元件介面中使用使用者定義的方法。 簽章的格式如下：  
  
```  
myRet=myCI.myMethod(parameter1, parameter2, ...)  
```  
  
 其中：  
  
- `parameter1` 和 `parameter2` 為輸入參數。  
  
- `myRet` 是傳回的值。  
  
  這些參數只能是方法的輸入參數。 只有一個值可以從方法傳回當做傳回參數。  
  
> [!NOTE]
>  包含使用者定義方法的元件介面應只啟用 PeopleSoft `Get` 函數。 如果元件介面有索引鍵，自訂方法就無法運作。  
  
## <a name="custom-ci-limitation"></a>自訂 CI 限制  
 BizTalk Adapter for PeopleSoft Enterprise 可以處理所提供的自訂 PeopleSoft 方法，但元件介面不能有索引鍵。 如果元件介面有索引鍵，自訂方法就無法運作。  
  
### <a name="workaround"></a>解決方式  
 建立一個沒有索引鍵的新元件介面，然後寫入將索引鍵併為呼叫參數一部分的新自訂方法。 例如，您可以在 USER_PROFILE 元件介面中使用 SetPassword 自訂方法；但 USER_PROFILE 有索引鍵。 您可以建立一個沒有索引鍵的新元件介面，然後在新元件介面中建立自訂的方法。 這個方法會接受兩個參數、使用者識別碼和密碼。 自訂的方法接著就可以使用 `Get` 叫用 USER_PROFILE，然後再叫用 `SetPassword`。 如需詳細資訊，請參閱 PeopleSoft 文件。  
  
 因為 PeopleSoft 中的限制，使用者定義的方法中出現的 `Date`、`DateTime` 和 `Time` 類型在用戶端程式碼中會對應為字串。  
  
## <a name="collection-limitation"></a>集合限制  
 使用者定義的方法無法傳回集合，甚至是任何 API 物件。 這表示 您只能傳回簡單類型，例如字串和數字。 避開這個限制的一個方法是，以 XML 字串形式傳送集合，並將用戶端寫成剖析這個字串以用正確格式來擷取項目。 您可以檢視 GET_CI_INFO 自訂元件介面，以查看這個解決方法的範例。  
  
## <a name="sample-custom-method"></a>自訂方法範例  
 您可以使用下列的基本自訂方法 SayHello，測試您的元件介面使用自訂方法的功能。  
  
 下列 PeopleCode 函式是 ACB_EMPLOYEE 這個 PeopleSoft 元件介面的使用者定義方法。 範例會傳回字串，其中傳回的值是**Hello**後面輸入參數的值。  
  
```  
Function SayHello(&sName As string) Returns string  
      &EOL = Char(10);  
      &sResult = "Hello " | &sName | &EOL;  
      Return &sResult;  
End-Function;  
```  
  
> [!NOTE]
>  若要同時 (使用一個命令) 修改多個表格，您可以建立另一個元件介面，或是建立一個元件介面使用者定義方法。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 A：元件介面方法](../core/appendix-a-component-interface-methods.md)