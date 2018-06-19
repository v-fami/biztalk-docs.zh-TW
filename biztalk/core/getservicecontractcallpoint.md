---
title: GetServiceContractCallPoint |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be03d100-0cba-4b80-8056-b582a2cd74ce
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e291bcf733129991f6d3b5000ca8e9bc1353057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246406"
---
# <a name="getservicecontractcallpoint"></a>GetServiceContractCallPoint
將目前服務合約呼叫點推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name="GetServiceContractCallPoint" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前合約呼叫點的字串。  
  
## <a name="remarks"></a>備註  
 Windows Communication Framework 服務可在服務合約存留期間的不同點來攔截。 這些位置是由 `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` 列舉定義：  
  
|合約呼叫點|說明|  
|-------------------------|-----------------|  
|ClientReply|用戶端回覆呼叫點。|  
|ClientRequest|用戶端要求呼叫點。|  
|ClientFault|用戶端錯誤點。|  
|ServiceReply|服務回覆呼叫點。|  
|ServiceRequest|服務要求呼叫點。|  
|ServiceFault|服務錯誤點。|  
|CallbackRequest|回呼要求呼叫點。|  
|CallbackReply|回呼回覆呼叫點。|  
|CallbackFault|回呼錯誤點。|  
  
## <a name="example"></a>範例  
 下列範例包含事件篩選器運算式，這是設定來尋找用戶端回覆狀態中的特定作業 ("Receive")。 這是使用包括 `GetOperationName`、`GetServiceContractCallPoint` 和邏輯運算等運算組合所完成。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ClientReply</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)