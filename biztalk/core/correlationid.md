---
title: "CorrelationID |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4faf210-7e7f-450d-8bb1-84d3d31c3022
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1192de4a49c300220ce0b297bbc1ee02ce64c6dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlationid"></a>CorrelationID
`CorrelationID` 項目用來指定訊息的相互關聯識別碼。  
  
## <a name="format"></a>格式  
 `CorrelationID` 項目由一個 `Expression` 項目組成，後者使用一或多個 `Operation` 項目以指定做為相互關聯識別碼的字串。  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="remarks"></a>備註  
 相互關聯識別碼運算式中不允許執行下列常見的運算：  
  
-   And  
  
-   等於  
  
## <a name="example"></a>範例  
 下列 Workflow Foundation (WF) 攔截器範例組態區塊會使用 "OrderNum" 來建立相互關聯識別碼。 您可以使用 WF 和常見的運算來建置複雜運算式，以建構工作流程的適當相互關聯識別碼。  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>OrderNum</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 對於 Windows Communication Foundation (WCF) 應用程式，您可以使用 WCF 專有和常見的運算以建構相互關聯識別碼。 下列範例會使用**XPath**運算和 XPath，從使用做為相互關聯識別碼的訊息擷取信用卡號碼：  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wcf:Operation Name ="XPath">  
      <wcf:Argument>//s:Body/creditCard:CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)