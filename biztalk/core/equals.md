---
title: 等於 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac93031a-9d18-443d-9e38-71ef9edd5a30
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b82ac5c779dc6b4d3624b48cebe9df1bc3d1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239814"
---
# <a name="equals"></a>等於
從堆疊移除前兩個項目，比較這兩個項目，然後將結果推入至堆疊。  
  
## <a name="syntax"></a>語法  
  
```  
  
<ic:Operation Name="Equals" />  
```  
  
#### <a name="parameters"></a>參數  
 堆疊上的前兩個項目。  
  
## <a name="pushed-value"></a>推入的值  
 比較作業的字串結果。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例篩選條件運算式會使用**等於**運算，比較目前的活動名稱與常數"CheckPO"。 如果兩者相等，運算式會評估為 `true`。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 您可能想要以撰寫 C# 陳述式執行比較的相同方式來建置運算式。 例如，您可能要比較三個值，在 C# 中，您會撰寫類似下面的陳述式：  
  
```  
bool res = a == b == c;  
```  
  
 不過，做為運算式篩選條件的模型，這不太符合標準。 因此，請考慮已修改 (但相等) 的陳述式：  
  
```  
Bool res = (a == b) && (a == c);  
```  
  
 這比較符合用來執行比較的篩選條件運算式。 如需詳細資訊和範例，請參閱[和](../core/and.md)。  
  
## <a name="see-also"></a>另請參閱  
 [攔截器作業](../core/interceptor-operations.md)