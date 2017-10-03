---
title: "GetEndpointName |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5a06850-ff6d-4fe4-9834-61d14b117391
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1567f0b4bceb756381c4033f3243ac7a58fda366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getendpointname"></a>GetEndpointName
將目前攔截端點的名稱推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name="GetEndpointName" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前攔截端點名稱的字串。  
  
## <a name="remarks"></a>備註  
 請務必注意，對於 App.config 檔案中指定的相同端點名稱，用戶端和伺服器應用程式會傳回不同的名稱。  
  
 在用戶端應用程式方面，GetEndPointName 作業擷取的端點名稱是後面接著底線和合約名稱的繫結名稱。  
  
 例如，如果 ServiceEndpoint 上的 [名稱] 屬性未設定，但有設定繫結，名稱會設定為\<*繫結*> _\<*合約*>。  
  
 如果未設定的名稱和繫結，將 [名稱] 屬性設定為\<*合約*>。  
  
 在服務方面，擷取到的名稱會是指定於 App.config 檔案中的端點名稱。  
  
## <a name="example"></a>範例  
 下列範例篩選條件運算式會針對 PurchaseOrder_EP 端點的 ServiceRequest 合約呼叫點，定義其接收作業的攔截。 這個作業會依照下列邏輯步驟完成：  
  
1.  以目前的作業名稱來比較 "Receive"，並將結果 (true 或 false) 推至堆疊上。  
  
2.  以目前的服務合約呼叫點來比較 "ServiceRequest"，並將結果 (true 或 false) 推至堆疊上。 堆疊上現在有兩個布林值。  
  
3.  比較使用布林值的上述步驟的結果**和**作業並將結果推至堆疊上的。 最後堆疊上只會出現一個布林值。  
  
4.  以目前的端點來比較 "PurchaseOrder_EP"，並將結果 (true 或 false) 推至堆疊上。 堆疊上現在有兩個布林值。  
  
5.  最後，比較兩個布林值，使用布林值在堆疊上的**和**作業並將結果推至堆疊。 這個運算會以某個布林值來檢查端點比較的結果，如果作業名稱和合約呼叫點相符則為 true，否則為 false。  
  
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
      <ic:Argument>ServiceRequest</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wcf:Operation Name="GetEndpointName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>PurchaseOrder_EP</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)