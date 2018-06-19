---
title: 如何設定 BAM WCF 攔截 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d85aa130-3219-4df1-8974-a44a51a15002
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90577a73abc0291635bf4b7d9bad34a11d1f806
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249206"
---
# <a name="how-to-configure-the-bam-wcf-interception"></a>如何設定 BAM WCF 攔截
若要針對 WCF 攔截設定 BAM，您必須修改攔截器組態檔，以存取事件來源的適當組件資訊清單。  
  
 當您設定事件時必須指定已正確格式化[XPath](../core/xpath.md)動作的運算式。  
  
 您可以建立格式正確[XPath](../core/xpath.md)運算式使用攔截器組態中啟用 WCF 追蹤並執行應用程式來產生包含訊息範例 WCF 記錄檔。 您可以使用**Microsoft Service Trace Viewer** (SvcTraceViewer.exe) 來檢視記錄檔及擷取訊息。 此檢視器包含在 WCF SDK 中。 所需[XPath](../core/xpath.md)運算式可以再形成訊息中的 架構和套用至攔截器組態。  
  
 設定 BAM WCF 攔截時，machine.config 檔案中使用的行為副檔名，一定要符合接收位置之自訂行為組態內所使用的副檔名。 若是變更 machine.config 檔案內之已設定接收位置的副檔名，將會導致該行為無法載入。 此外，接收位置的組態 UI 也會失敗。  
  
 若是在叢集化的環境，因為自訂行為只設定一次，所以您必須確定該叢集內電腦的所有 machine.config 檔案都是指定相同的副檔名。  
  
### <a name="to-set-the-manifest"></a>若要設定資訊清單  
  
1.  將攔截組態中 EventSource 的資訊清單設定為 'Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'  
  
    > [!NOTE]
    >  這個介面會根據使用的服務/接收埠類型而變更。 請依照下表變更資訊清單行，以反映您所使用的連接埠類型。  
  
    |連接埠類型|使用|  
    |---------------|---------|  
    |雙向連接埠|ITwoWayAsync|  
    |單向連接埠，所包含的繫結本質上為雙向繫結 (例如，HTTP)。|ITwoWayAsyncVoid|  
    |單向連接埠，使用的繫結本質上是兩端為交易的雙向繫結。|ITwoWayAsyncVoidTxn|  
    |屬於單向的繫結 (例如，MSMQ)。|IOneWayAsync|  
    |兩端為交易之單向繫結的繫結。|IOneWayAsyncTxn|  
  
    > [!IMPORTANT]
    >  在篩選中，而不是使用[使用 GetOperationName](../core/getoperationname.md)作業，以反白顯示在下列範例中使用 XPath 作業。 若是泛型合約，所有訊息都會抵達某個泛型作業，此時這些訊息會根據本身的動作屬性路由至特定作業。  
  
2.  這時作業名稱一定是相同。 若是 WCF 配接器 (它會使用泛型合約)，就會使用方法 BizTalkSubmit。 您可以使用「動作」節點的 XPath 來擷取作業名稱，而不要使用 GetOperationName。 這樣您就可以接著篩選該作業名稱。  
  
## <a name="sample-interceptor-configurations"></a>範例攔截器組態  
 這個範例示範如何針對 WCF 配接器使用 ServiceRequest 和 ServiceReply。 在反白顯示的區段[XPath](../core/xpath.md)動作的運算式用來篩選作業，而不使用[使用 GetOperationName](../core/getoperationname.md)。 您也可以篩選回覆，但只有在使用 ITwoWayAsync 的情況下才可以這樣做。 其他所有介面則不會傳回任何結果，或是傳回 void。  
  
### <a name="servicerequest"></a>ServiceRequest  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceRequest" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceRequest</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Header/a:Action</wcf:Argument>  
          </wcf:Operation>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>Operation1</ic:Argument>  
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
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Source" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceRequest</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
### <a name="servicereply"></a>ServiceReply  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceReply" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceReply</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
        </ic:Expression>  
      </ic:Filter>  
  
      <ic:CorrelationID>  
        <ic:Expression>  
          <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
        </ic:Expression>  
      </ic:CorrelationID>  
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Name" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceReply</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 配接器攔截 BAM 資料](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)