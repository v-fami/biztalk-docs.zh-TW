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
# <a name="how-to-configure-the-bam-wcf-interception"></a><span data-ttu-id="aa588-102">如何設定 BAM WCF 攔截</span><span class="sxs-lookup"><span data-stu-id="aa588-102">How to Configure the BAM WCF Interception</span></span>
<span data-ttu-id="aa588-103">若要針對 WCF 攔截設定 BAM，您必須修改攔截器組態檔，以存取事件來源的適當組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="aa588-103">To configure BAM for WCF interception, you must modify the interceptor configuration file to access the proper assembly manifest for your event sources.</span></span>  
  
 <span data-ttu-id="aa588-104">當您設定事件時必須指定已正確格式化[XPath](../core/xpath.md)動作的運算式。</span><span class="sxs-lookup"><span data-stu-id="aa588-104">When you are configuring the events you must specify properly formatted [XPath](../core/xpath.md) expressions for the actions.</span></span>  
  
 <span data-ttu-id="aa588-105">您可以建立格式正確[XPath](../core/xpath.md)運算式使用攔截器組態中啟用 WCF 追蹤並執行應用程式來產生包含訊息範例 WCF 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="aa588-105">You can create properly formatted [XPath](../core/xpath.md) expressions to use in the interceptor configuration by enabling WCF tracing and running the application to produce a sample WCF log which contains the message.</span></span> <span data-ttu-id="aa588-106">您可以使用**Microsoft Service Trace Viewer** (SvcTraceViewer.exe) 來檢視記錄檔及擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="aa588-106">You can use the **Microsoft Service Trace Viewer** (SvcTraceViewer.exe) to view the log and extract the message.</span></span> <span data-ttu-id="aa588-107">此檢視器包含在 WCF SDK 中。</span><span class="sxs-lookup"><span data-stu-id="aa588-107">The viewer is included with the WCF SDK.</span></span> <span data-ttu-id="aa588-108">所需[XPath](../core/xpath.md)運算式可以再形成訊息中的 架構和套用至攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="aa588-108">The desired [XPath](../core/xpath.md) expression can then be formed based on the message and applied to the interceptor configuration.</span></span>  
  
 <span data-ttu-id="aa588-109">設定 BAM WCF 攔截時，machine.config 檔案中使用的行為副檔名，一定要符合接收位置之自訂行為組態內所使用的副檔名。</span><span class="sxs-lookup"><span data-stu-id="aa588-109">When configuring the BAM WCF interception, it is essential that the behavior extension used in the machine.config file matches the extension used in the custom behavior configuration of the receive location.</span></span> <span data-ttu-id="aa588-110">若是變更 machine.config 檔案內之已設定接收位置的副檔名，將會導致該行為無法載入。</span><span class="sxs-lookup"><span data-stu-id="aa588-110">Changing the extension name of a configured receive location in the machine.config file causes the behavior to fail to load.</span></span> <span data-ttu-id="aa588-111">此外，接收位置的組態 UI 也會失敗。</span><span class="sxs-lookup"><span data-stu-id="aa588-111">In addition, the configuration UI of the receive location will fail.</span></span>  
  
 <span data-ttu-id="aa588-112">若是在叢集化的環境，因為自訂行為只設定一次，所以您必須確定該叢集內電腦的所有 machine.config 檔案都是指定相同的副檔名。</span><span class="sxs-lookup"><span data-stu-id="aa588-112">In case of a clustered scenario, since the custom behavior is configured only once, you must ensure that all the machine.config files on the computers in the cluster specify the same file name extension.</span></span>  
  
### <a name="to-set-the-manifest"></a><span data-ttu-id="aa588-113">若要設定資訊清單</span><span class="sxs-lookup"><span data-stu-id="aa588-113">To set the manifest</span></span>  
  
1.  <span data-ttu-id="aa588-114">將攔截組態中 EventSource 的資訊清單設定為 'Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'</span><span class="sxs-lookup"><span data-stu-id="aa588-114">Set the manifest in the EventSource in the Interception Configuration to 'Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa588-115">這個介面會根據使用的服務/接收埠類型而變更。</span><span class="sxs-lookup"><span data-stu-id="aa588-115">The interface changes based on the type of service/receive port used.</span></span> <span data-ttu-id="aa588-116">請依照下表變更資訊清單行，以反映您所使用的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="aa588-116">Change the manifest line to reflect the type of port you are using according to the table below.</span></span>  
  
    |<span data-ttu-id="aa588-117">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="aa588-117">Port Type</span></span>|<span data-ttu-id="aa588-118">使用</span><span class="sxs-lookup"><span data-stu-id="aa588-118">Use</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="aa588-119">雙向連接埠</span><span class="sxs-lookup"><span data-stu-id="aa588-119">Two-way ports</span></span>|<span data-ttu-id="aa588-120">ITwoWayAsync</span><span class="sxs-lookup"><span data-stu-id="aa588-120">ITwoWayAsync</span></span>|  
    |<span data-ttu-id="aa588-121">單向連接埠，所包含的繫結本質上為雙向繫結 (例如，HTTP)。</span><span class="sxs-lookup"><span data-stu-id="aa588-121">One-way ports with binding that are inherently two 2 way (for example, HTTP).</span></span>|<span data-ttu-id="aa588-122">ITwoWayAsyncVoid</span><span class="sxs-lookup"><span data-stu-id="aa588-122">ITwoWayAsyncVoid</span></span>|  
    |<span data-ttu-id="aa588-123">單向連接埠，使用的繫結本質上是兩端為交易的雙向繫結。</span><span class="sxs-lookup"><span data-stu-id="aa588-123">One-way ports with binding that are inherently two two-way with transactions.</span></span>|<span data-ttu-id="aa588-124">ITwoWayAsyncVoidTxn</span><span class="sxs-lookup"><span data-stu-id="aa588-124">ITwoWayAsyncVoidTxn</span></span>|  
    |<span data-ttu-id="aa588-125">屬於單向的繫結 (例如，MSMQ)。</span><span class="sxs-lookup"><span data-stu-id="aa588-125">Bindings that are one way (for example, MSMQ).</span></span>|<span data-ttu-id="aa588-126">IOneWayAsync</span><span class="sxs-lookup"><span data-stu-id="aa588-126">IOneWayAsync</span></span>|  
    |<span data-ttu-id="aa588-127">兩端為交易之單向繫結的繫結。</span><span class="sxs-lookup"><span data-stu-id="aa588-127">Bindings that are one way with transactions.</span></span>|<span data-ttu-id="aa588-128">IOneWayAsyncTxn</span><span class="sxs-lookup"><span data-stu-id="aa588-128">IOneWayAsyncTxn</span></span>|  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="aa588-129">在篩選中，而不是使用[使用 GetOperationName](../core/getoperationname.md)作業，以反白顯示在下列範例中使用 XPath 作業。</span><span class="sxs-lookup"><span data-stu-id="aa588-129">In the filter, instead of using the [GetOperationName](../core/getoperationname.md) operation, use XPath operation as highlighted in the following sample.</span></span> <span data-ttu-id="aa588-130">若是泛型合約，所有訊息都會抵達某個泛型作業，此時這些訊息會根據本身的動作屬性路由至特定作業。</span><span class="sxs-lookup"><span data-stu-id="aa588-130">For generic contracts all messages arrive at some generic operation, at which point they get routed to specific operations based on the message itself (Action attribute).</span></span>  
  
2.  <span data-ttu-id="aa588-131">這時作業名稱一定是相同。</span><span class="sxs-lookup"><span data-stu-id="aa588-131">The operation name will always be the same at this point.</span></span> <span data-ttu-id="aa588-132">若是 WCF 配接器 (它會使用泛型合約)，就會使用方法 BizTalkSubmit。</span><span class="sxs-lookup"><span data-stu-id="aa588-132">In case of WCF adapters (which uses generic contracts) the method used is BizTalkSubmit.</span></span> <span data-ttu-id="aa588-133">您可以使用「動作」節點的 XPath 來擷取作業名稱，而不要使用 GetOperationName。</span><span class="sxs-lookup"><span data-stu-id="aa588-133">You can use an XPath for the Action node instead of GetOperationName to retrieve the operation name.</span></span> <span data-ttu-id="aa588-134">這樣您就可以接著篩選該作業名稱。</span><span class="sxs-lookup"><span data-stu-id="aa588-134">You can then filter on the operation name.</span></span>  
  
## <a name="sample-interceptor-configurations"></a><span data-ttu-id="aa588-135">範例攔截器組態</span><span class="sxs-lookup"><span data-stu-id="aa588-135">Sample Interceptor Configurations</span></span>  
 <span data-ttu-id="aa588-136">這個範例示範如何針對 WCF 配接器使用 ServiceRequest 和 ServiceReply。</span><span class="sxs-lookup"><span data-stu-id="aa588-136">This sample shows the usage of ServiceRequest and ServiceReply for the WCF adapter.</span></span> <span data-ttu-id="aa588-137">在反白顯示的區段[XPath](../core/xpath.md)動作的運算式用來篩選作業，而不使用[使用 GetOperationName](../core/getoperationname.md)。</span><span class="sxs-lookup"><span data-stu-id="aa588-137">In the highlighted section an [XPath](../core/xpath.md) expression on the Action is used to filter on the operation instead of using [GetOperationName](../core/getoperationname.md).</span></span> <span data-ttu-id="aa588-138">您也可以篩選回覆，但只有在使用 ITwoWayAsync 的情況下才可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="aa588-138">You can filter on the reply as well, but only in the case of ITwoWayAsync.</span></span> <span data-ttu-id="aa588-139">其他所有介面則不會傳回任何結果，或是傳回 void。</span><span class="sxs-lookup"><span data-stu-id="aa588-139">All other interfaces return nothing or void.</span></span>  
  
### <a name="servicerequest"></a><span data-ttu-id="aa588-140">ServiceRequest</span><span class="sxs-lookup"><span data-stu-id="aa588-140">ServiceRequest</span></span>  
  
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
  
### <a name="servicereply"></a><span data-ttu-id="aa588-141">ServiceReply</span><span class="sxs-lookup"><span data-stu-id="aa588-141">ServiceReply</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa588-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa588-142">See Also</span></span>  
 [<span data-ttu-id="aa588-143">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="aa588-143">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)