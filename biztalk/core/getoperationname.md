---
title: "使用 GetOperationName |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f858269c-d412-43e3-85e1-398afa9375ab
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e22020add39840b0d2fe4c2fd88156321a18c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getoperationname"></a>GetOperationName
將目前作業的名稱推入到堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name="GetOperationName" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前作業之名稱的字串。  
  
## <a name="remarks"></a>備註  
 當使用 GetOperationName 時，請確定將作業名稱比照為應用程式所叫用的作業名稱。 例如，如果您使用服務合約上的名稱屬性 (Attribute) 來指派自訂名稱，用戶端便會以方法的自訂名稱來產生其預設 Proxy。 然而，伺服器應用程式將會使用對應之作業的實際方法名稱，而不是在名稱屬性中指定的名稱。  
  
## <a name="example"></a>範例  
 下列範例會使用 `GetOperationName`，建置可篩選名為 "AuthorizePayment" 之作業的運算式。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>AuthorizePayment</ic:Argument>  
    </ic:Operation>  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)