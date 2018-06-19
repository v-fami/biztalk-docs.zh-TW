---
title: 攔截器 OnEvent 項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d684ac8e-61bc-410b-97a2-6fd3549e0d97
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fb70b2536dbf5db5b0abc03bc194de154b4317
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257606"
---
# <a name="interceptor-onevent-element"></a>攔截器 OnEvent 項目
**OnEvent**元素描述一個對應至封入 BAM 活動的真實事件。  
  
## <a name="format"></a>格式  
 `OnEvent` 項目所包含的子項目，則會指定事件篩選條件、相互關聯識別碼、選擇性指定要更新的資料、參考資料和接續 Token。  
  
### <a name="attributes"></a>屬性  
  
|屬性名稱|Description|  
|--------------------|-----------------|  
|名稱|此事件的使用者定義名稱。|  
|Source|事件的名稱出現在來源**EventSource**項目。|  
|IsBegin|布林值，表示事件是 (`true`) 否 (`false`) 為新 BAM 活動的開始。|  
|IsEnd|布林值，表示事件是 (`true`) 否 (`false`) 為新 BAM 活動的結束。|  
  
### <a name="child-elements"></a>子元素  
  
|執行狀態|Description|  
|----------------------|-----------------|  
|篩選|提供限制事件符合特定準則的方法。|  
|CorrelationID|指定關聯識別碼 (活動執行個體識別碼)。|  
|ContinuationToken|指定接續 Token，也就是日後會導致相同活動執行個體的事件所使用的相互關聯識別碼。|  
|Update|指定資料要從事件中加以擷取，並且匯入至 BAM 活動。|  
|參考|將關係加入至 BAM 活動。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例示範典型**OnEvent** WF 區塊：  
  
```  
<ic:OnEvent Name="BeginAct" IsBegin="true" Source="ResWF">  
  <ic:Filter>  
    <ic:Expression>  
      <wf:Operation Name="GetActivityName"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
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
  <ic:CorrelationID>  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>InstanceId</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>EventTime</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  <ic:Update DataItemName="FoodItem" Type="NVARCHAR">  
    <ic:Expression>  
      <wf:Operation Name="GetWorkflowProperty">  
        <wf:Argument>foodItem</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
 這個範例示範典型**OnEvent** WCF 服務的區塊：  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="AuthorizationRequestService" Source="ESCreditCardService">  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals" />  
      <ic:Operation Name ="And" />  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="Name" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:FirstName</wcf:Argument>  
      </wcf:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:LastName</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name ="Concatenate"/>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
## <a name="in-this-section"></a>本節內容  
  
-   [篩選](../core/filter.md)  
  
-   [相互關聯識別碼](../core/correlationid.md)  
  
-   [ContinuationToken](../core/continuationtoken.md)  
  
-   [參考](../core/reference.md)  
  
-   [Update](../core/update2.md)  
  
## <a name="see-also"></a>另請參閱  
 [攔截器組態檔的結構](../core/structure-of-an-interceptor-configuration-file.md)