---
title: "常數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0af49bf5-e7de-41da-ac27-70301b8ee4d4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674307acea439bc260399cc01da4165eedaa2da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="constant"></a>常數
將單一常數值推入至堆疊。  
  
## <a name="syntax"></a>語法  
  
```  
  
<ic:Operation Name="Constant">  
  <ic:Argument>val</ic:Argument>  
</ic:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 常數值。  
  
## <a name="pushed-value"></a>推入的值  
 包含常數值的字串。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例篩選條件運算式使用**常數**運算推入值，然後將使用在**等於**作業以確定目前的活動名稱為"FoodAndDrinksPolicy"。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 這是常見的使用方式模式**常數**作業。  
  
## <a name="see-also"></a>另請參閱  
 [攔截器作業](../core/interceptor-operations.md)