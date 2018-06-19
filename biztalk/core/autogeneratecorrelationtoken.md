---
title: AutoGenerateCorrelationToken |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a24357c9-34e5-4caa-b41c-19551cfe81f9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e396fd0b2c6153a5252d336b9af9c22bf9421fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230254"
---
# <a name="autogeneratecorrelationtoken"></a>AutoGenerateCorrelationToken
自動產生相互關聯 Token 並將它置於堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name="AutoGenerateCorrelationToken" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含相互關聯 Token 的字串。  
  
## <a name="remarks"></a>備註  
 訊息中並未存在相互關聯 Token 時可以使用此作業，但您仍想要將要求和回覆中的資訊相互關聯。 此作業可以用來在用戶端或服務端將特定要求/回覆相互關聯。  
  
> [!NOTE]
>  如果想將用戶端和服務 (接續) 之要求和回覆所收集的資料相互關聯，就必須使用您訊息中的資料元素或元素。  
  
## <a name="example"></a>範例  
 下列範例相互關聯運算式依賴 `AutoGenerateCorrelationToken` 來產生相互關聯 Token。  
  
```  
<ic:CorrelationID>  
  <ic:Expression>            
    <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)