---
title: "和 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bd8f1f-edae-476d-b488-78e6c5ee70bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 676940dfa5cbc23d0c8127923d292e382a4e3cad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="and"></a>And
移除前兩個項目從堆疊中，執行布林**AND**的兩個項目，並再將推送至堆疊的結果。  
  
## <a name="syntax"></a>語法  
  
```  
  
<ic:Operation Name="And" />  
```  
  
#### <a name="parameters"></a>參數  
 堆疊上的前兩個項目。  
  
## <a name="pushed-value"></a>推入的值  
 布林值的字串結果**AND**作業。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 **和**作業時，您需要評估多個陳述式。 下列範例篩選條件運算式檢查是否活動名稱為"CheckPO"，並使用關閉活動事件**和**作業。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 在此範例中**和**是在運算式中的最終作業，因為它依賴比較結果 （並取出它們從堆疊來執行比較）。 您可以延伸這個概念，若要執行**和**兩個以上的項目上的作業。 例如，若要評估「條件 A」、「條件 B」和「條件 C」是否為 true，您可以使用如下所示的運算式：  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityType"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyType</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>   
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器作業](../core/interceptor-operations.md)