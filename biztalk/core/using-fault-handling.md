---
title: 使用錯誤處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc793386-d2ec-4e02-9283-3237f65c9e01
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90cb589894b9bb2166cf701866575092da53540e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015119"
---
# <a name="using-fault-handling"></a>使用錯誤處理
期間[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]錯誤處理的例外狀況訊息不傳回給用戶端除非**FaultException** （或子類型） 會擲回或**FaultContract**實作。 因此，您只能在這些情況下的錯誤訊息本身追蹤資料。 回呼實作中的例外狀況會自動恢復為錯誤訊息兩者**ServerFault**並**ClientFault**追蹤點。 不過，它一定會傳回具有泛型訊息的泛型錯誤。 如需有關 WCF 錯誤合約的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=83132 ](http://go.microsoft.com/fwlink/?LinkId=83132)。  
  
 您也可以透過錯誤追蹤點來追蹤常數和內容屬性。  
  
 如果使用錯誤中傳回的例外狀況詳細資料**IncludeExceptionDetailInFaults**屬性，擷取實際的例外狀況訊息，透過 XPath。  
  
 會提供錯誤處理中定義的錯誤追蹤點所[GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):  
  
- ServiceFault  
  
- ClientFault  
  
- CallbackFault  
  
  使用這些錯誤追蹤點時，即使是以交易為基礎的實例作業，錯誤資料都會保存下來。 系統會針對所有非錯誤的追蹤資料維護其交易整合性，同時回復非錯誤的追蹤資料來回應該錯誤。  
  
> [!NOTE]
>  這些追蹤點會套用至回覆路徑，而且僅適用於的 ServiceReply、 ClientReply 和 CallbackReply 服務合約呼叫點所提供[GetServiceContractCallPoint](../core/getservicecontractcallpoint.md)。  
  
## <a name="fault-configuration-sample"></a>錯誤組態範例  
 下列範例會示範在追蹤例外狀況訊息**ServiceFault**服務會擲回**FaultException**中**AuthorizationServiceFault**事件;會追蹤中的作業所傳回的布林運算式**AuthorizationServiceReply**事件。 任一**AuthorizationServiceReply** OnEvent 或有**AuthorizationServiceFault** OnEvent 會保存。  
  
> [!NOTE]
>  這個範例的實作會示範 ServiceReply 和 ServiceFault 追蹤點的互斥現象。  
  
```  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceReply" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceReply</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Success</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName="Result" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name ="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:AuthorizeWithDataContractResult</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceFault" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceFault</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Fault</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
      <ic:Update DataItemName="Source" Type="NVARCHAR">  
        <ic:Expression>  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Body/Fault/Reason/Text</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
```  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 配接器攔截 BAM 資料](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)