---
title: "使用錯誤處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc793386-d2ec-4e02-9283-3237f65c9e01
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00547917da65253123cb2067715a09633547eb4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-fault-handling"></a><span data-ttu-id="8f879-102">使用錯誤處理</span><span class="sxs-lookup"><span data-stu-id="8f879-102">Using Fault Handling</span></span>
<span data-ttu-id="8f879-103">期間[!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]除非不處理例外狀況訊息的錯誤傳回給用戶端**FaultException** （或子類型） 就會擲回或**FaultContract**實作。</span><span class="sxs-lookup"><span data-stu-id="8f879-103">During [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] fault handling an exception message is not returned to the client unless a **FaultException** (or a subtype) is thrown or a **FaultContract** is implemented.</span></span> <span data-ttu-id="8f879-104">因此，您只能在這些情況下的錯誤訊息本身追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="8f879-104">So you can only track data from the fault message itself in these scenarios.</span></span> <span data-ttu-id="8f879-105">回呼實作中的例外狀況自動傳回做為錯誤訊息同時**ServerFault**和**ClientFault**追蹤點。</span><span class="sxs-lookup"><span data-stu-id="8f879-105">An exception in callback implementations automatically comes back as a fault message for both **ServerFault** and **ClientFault** track points.</span></span> <span data-ttu-id="8f879-106">不過，它一定會傳回具有泛型訊息的泛型錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f879-106">However, it will always return a generic fault with a generic message.</span></span> <span data-ttu-id="8f879-107">如需有關 WCF 錯誤合約的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132)。</span><span class="sxs-lookup"><span data-stu-id="8f879-107">For more information about WCF fault contracts, see [http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132).</span></span>  
  
 <span data-ttu-id="8f879-108">您也可以透過錯誤追蹤點來追蹤常數和內容屬性。</span><span class="sxs-lookup"><span data-stu-id="8f879-108">You can also track constants and context properties through the fault track points.</span></span>  
  
 <span data-ttu-id="8f879-109">如果例外狀況詳細資料會使用錯誤中傳回**IncludeExceptionDetailInFaults**屬性，擷取實際的例外狀況訊息透過 XPath。</span><span class="sxs-lookup"><span data-stu-id="8f879-109">If exception details are returned in faults using the **IncludeExceptionDetailInFaults** attribute, you extract the actual exception message through the XPath.</span></span>  
  
 <span data-ttu-id="8f879-110">會提供錯誤處理中定義的錯誤追蹤點所[GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):</span><span class="sxs-lookup"><span data-stu-id="8f879-110">Fault handling is provided by the fault track points defined in [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):</span></span>  
  
-   <span data-ttu-id="8f879-111">ServiceFault</span><span class="sxs-lookup"><span data-stu-id="8f879-111">ServiceFault</span></span>  
  
-   <span data-ttu-id="8f879-112">ClientFault</span><span class="sxs-lookup"><span data-stu-id="8f879-112">ClientFault</span></span>  
  
-   <span data-ttu-id="8f879-113">CallbackFault</span><span class="sxs-lookup"><span data-stu-id="8f879-113">CallbackFault</span></span>  
  
 <span data-ttu-id="8f879-114">使用這些錯誤追蹤點時，即使是以交易為基礎的實例作業，錯誤資料都會保存下來。</span><span class="sxs-lookup"><span data-stu-id="8f879-114">When using these fault track points, fault data is always persisted, even when operating in a transaction-based scenario.</span></span> <span data-ttu-id="8f879-115">系統會針對所有非錯誤的追蹤資料維護其交易整合性，同時回復非錯誤的追蹤資料來回應該錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f879-115">Transactional integrity is maintained on all non-fault tracked data and non-fault tracked data is rolled back as a response to the fault.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f879-116">這些追蹤點套用至回覆路徑，而只會套用到的 ServiceReply、 ClientReply 和 CallbackReply 服務合約呼叫點所提供[GetServiceContractCallPoint](../core/getservicecontractcallpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="8f879-116">These track points are applied to the reply path and apply only to the ServiceReply, ClientReply and CallbackReply service contract call points provided by [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md).</span></span>  
  
## <a name="fault-configuration-sample"></a><span data-ttu-id="8f879-117">錯誤組態範例</span><span class="sxs-lookup"><span data-stu-id="8f879-117">Fault Configuration Sample</span></span>  
 <span data-ttu-id="8f879-118">下列範例將示範如何在追蹤例外狀況訊息**ServiceFault**服務會擲回**FaultException**中**AuthorizationServiceFault**事件。否則它會追蹤中的作業所傳回的布林運算式**AuthorizationServiceReply**事件。</span><span class="sxs-lookup"><span data-stu-id="8f879-118">The following sample demonstrates tracking the exception message on a **ServiceFault** when the service throws a **FaultException** in the **AuthorizationServiceFault** event; otherwise it tracks the Boolean expression returned by the operation in the **AuthorizationServiceReply** event.</span></span> <span data-ttu-id="8f879-119">任一**AuthorizationServiceReply** OnEvent 或**AuthorizationServiceFault** OnEvent 會保存。</span><span class="sxs-lookup"><span data-stu-id="8f879-119">Either the **AuthorizationServiceReply** OnEvent or the **AuthorizationServiceFault** OnEvent is persisted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f879-120">這個範例的實作會示範 ServiceReply 和 ServiceFault 追蹤點的互斥現象。</span><span class="sxs-lookup"><span data-stu-id="8f879-120">The implementation of this sample demonstrates the mutual exclusivity of the ServiceReply and ServiceFault trackpoints.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f879-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f879-121">See Also</span></span>  
 [<span data-ttu-id="8f879-122">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="8f879-122">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)