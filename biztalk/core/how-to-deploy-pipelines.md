---
title: 如何部署管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IReceiveLocation interface
- IReceivePort interface
- deploying, pipelines
- pipelines, deploying
- pipelines, compiling
- SendPipelineData method
- pipelines, configuring
- pipelines, code sample
- ReceivePipelineData property
- Validate method
- ISendPort interface
ms.assetid: 7a56c753-a0d4-48ed-a61d-e454bc9cd507
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23028db559864368bb091fb15abfca7e49d73808
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986319"
---
# <a name="how-to-deploy-pipelines"></a><span data-ttu-id="8bd08-102">如何部署管線</span><span class="sxs-lookup"><span data-stu-id="8bd08-102">How to Deploy Pipelines</span></span>
<span data-ttu-id="8bd08-103">管線已編譯和部署作為方案建置和部署程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="8bd08-103">Pipelines are compiled and deployed as part of the solution build and deploy process.</span></span> <span data-ttu-id="8bd08-104">編譯器會呼叫**驗證**上每個元件，允許元件傳回方法的編譯錯誤的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="8bd08-104">The compiler calls the **Validate** method on each component, allowing the components to return compile errors on the configured information.</span></span> <span data-ttu-id="8bd08-105">在建置之後部署方案時，管線會部署在其餘方案的相同組件中。</span><span class="sxs-lookup"><span data-stu-id="8bd08-105">After building, the pipeline is deployed in the same assembly with the rest of the solution when the solution is deployed.</span></span>  
  
## <a name="per-instance-pipeline-configuration"></a><span data-ttu-id="8bd08-106">個別執行個體管線組態</span><span class="sxs-lookup"><span data-stu-id="8bd08-106">Per-instance pipeline configuration</span></span>  
 <span data-ttu-id="8bd08-107">個別執行個體管線組態用以修改在傳送埠或接收位置層級已部署管線中的管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="8bd08-107">Per-instance pipeline configuration is used to modify properties of pipeline components within a deployed pipeline at the send port or receive location level.</span></span> <span data-ttu-id="8bd08-108">當只有一些管線元件屬性需要每個執行個體都修改時，個別執行個體管線組態會非常有用。</span><span class="sxs-lookup"><span data-stu-id="8bd08-108">Per-instance pipeline configuration is useful when only a few pipeline component properties need to be modified per instance.</span></span> <span data-ttu-id="8bd08-109">例如，如果您需要在多個接收位置支援不同的訊息類型，且具有單一的自訂 XML 接收管線，個別執行個體管線組態可讓您部署管線和覆寫預設組態 (包括指定不同的信封和文件規格名稱)。</span><span class="sxs-lookup"><span data-stu-id="8bd08-109">For example, if you need to support different message types in multiple receive locations and have a single custom XML receive pipeline, per-instance pipeline configuration enables you to deploy the pipeline and override the default configuration (including specifying different envelope and document spec names).</span></span> <span data-ttu-id="8bd08-110">這項機制在 BizTalk 管理主控台中受支援，且可透過總管物件模型以程式設計方式支援。</span><span class="sxs-lookup"><span data-stu-id="8bd08-110">This mechanism is supported in the BizTalk Management console and programmatically through the Explorer object model.</span></span>  
  
### <a name="per-instance-pipeline-configuration-using-biztalk-administration-console"></a><span data-ttu-id="8bd08-111">使用 BizTalk 管理主控台的個別執行個體管線組態</span><span class="sxs-lookup"><span data-stu-id="8bd08-111">Per-Instance Pipeline Configuration Using BizTalk Administration console</span></span>  
 <span data-ttu-id="8bd08-112">您可使用 BizTalk 管理主控台執行個別執行個體管線組態。</span><span class="sxs-lookup"><span data-stu-id="8bd08-112">You can perform per-instance pipeline configuration using the BizTalk Management console.</span></span> <span data-ttu-id="8bd08-113">在部署完自訂管線後，請視需要建立接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8bd08-113">Once you have deployed your custom pipeline, create as many receive locations or send ports as required.</span></span> <span data-ttu-id="8bd08-114">然後，對於每個接收位置或傳送埠，請透過 [設定管線] 對話方塊覆寫預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="8bd08-114">Then for each receive location or send port, override default property values through the Configure Pipeline dialog box.</span></span> <span data-ttu-id="8bd08-115">比方說，若要指定不同的文件結構描述，請輸入的結構描述名稱 **[envelopedocspecnames]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="8bd08-115">For example, to specify a different document schema, enter a schema name for the **EnvelopeDocSpecNames** property.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8bd08-116">在接收位置或傳送埠中指定的組態值將不會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="8bd08-116">No validation of the configuration values specified in the receive location or send port will be performed.</span></span> <span data-ttu-id="8bd08-117">如果組態不正確，訊息於執行階段透過管線傳遞時就會失敗。</span><span class="sxs-lookup"><span data-stu-id="8bd08-117">If the configuration is incorrect, messages will fail at runtime when passing through the pipeline.</span></span>  
  
### <a name="per-instance-pipeline-configuration-using-the-explorer-object-model"></a><span data-ttu-id="8bd08-118">使用總管物件模型的個別執行個體管線組態</span><span class="sxs-lookup"><span data-stu-id="8bd08-118">Per-Instance Pipeline Configuration Using the Explorer Object Model</span></span>  
 <span data-ttu-id="8bd08-119">當描述管線元件的個別執行個體組態的 XML 檔案被讀取時，它會覆寫管線檔案中所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bd08-119">When the XML file describing the per-instance configuration of the pipeline components is read, it overrides the properties set in the pipeline file.</span></span>  
  
 <span data-ttu-id="8bd08-120">藉由使用 BizTalk 總管物件模型可設定個別執行個體管線組態。</span><span class="sxs-lookup"><span data-stu-id="8bd08-120">Per-instance pipeline configuration is set by using the BizTalk Explorer object model.</span></span> <span data-ttu-id="8bd08-121">BizTalk 總管物件模型會提供**Ireceivelocation**屬性上的**IReceiveLocation**並**Receivepipelinedata**介面設定的組態接收管線元件。</span><span class="sxs-lookup"><span data-stu-id="8bd08-121">The BizTalk Explorer object model provides the **ReceivePipelineData** property on the **IReceiveLocation** and **ISendPort** interfaces for setting the configuration of receive pipeline components.</span></span> <span data-ttu-id="8bd08-122">「 BizTalk 總管物件模型也會提供**Ireceiveport**方法**Isendport**並**Receivepipelinedata**介面傳送的設定組態管線元件。</span><span class="sxs-lookup"><span data-stu-id="8bd08-122">The BizTalk Explorer object model also provides the **SendPipelineData** method on the **IReceivePort** and **ISendPort** interfaces for setting configuration of send pipeline components.</span></span>  
  
 <span data-ttu-id="8bd08-123">個別執行個體管線組態不支援下列動作：</span><span class="sxs-lookup"><span data-stu-id="8bd08-123">Per-instance pipeline configuration does not support the following:</span></span>  
  
- <span data-ttu-id="8bd08-124">重新安排管線中的階段</span><span class="sxs-lookup"><span data-stu-id="8bd08-124">Rearranging stages within the pipeline</span></span>  
  
- <span data-ttu-id="8bd08-125">新增或移除階段</span><span class="sxs-lookup"><span data-stu-id="8bd08-125">Adding or removing stages</span></span>  
  
- <span data-ttu-id="8bd08-126">重新安排階段中的元件</span><span class="sxs-lookup"><span data-stu-id="8bd08-126">Rearranging components within stages</span></span>  
  
- <span data-ttu-id="8bd08-127">新增或移除元件</span><span class="sxs-lookup"><span data-stu-id="8bd08-127">Adding or removing components</span></span>  
  
  <span data-ttu-id="8bd08-128">僅支援在管線元件組態中的變更。</span><span class="sxs-lookup"><span data-stu-id="8bd08-128">The only supported changes are in the configuration of pipeline components.</span></span> <span data-ttu-id="8bd08-129">管線元件的個別執行個體組態會覆寫通用管線元件組態。</span><span class="sxs-lookup"><span data-stu-id="8bd08-129">Per-instance configuration of a pipeline component overrides the common pipeline component configuration.</span></span> <span data-ttu-id="8bd08-130">若在個別執行個體管線組態中未指定元件的參數，則會使用該參數的通用組態 (如「管線設計師」中所設定)。</span><span class="sxs-lookup"><span data-stu-id="8bd08-130">If a parameter of a component is not specified in per-instance pipeline configuration, the common configuration for that parameter (as configured in Pipeline Designer) is used.</span></span>  
  
  <span data-ttu-id="8bd08-131">以下是個別執行個體組態資料的範例。</span><span class="sxs-lookup"><span data-stu-id="8bd08-131">The following is an example of per-instance configuration data.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<Root xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
    <Stages>  
        <Stage CategoryId="9d0e4103-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft Microsoft.BizTalk.Component.MIME_SMIME_Decoder>  
                    <Properties>  
                        <AllowNonMIMEMessage vt=11>true</AllowNonMIMEMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e4105-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft.BizTalk.Component.XmlDasmComp>  
                    <Properties>  
                        <EnvelopeSpecNames vt=8>MySchemas.EnvelopeSpecNames</EnvelopeSpecNames>  
                        <AllowUnrecognizedMessage vt=11>false</AllowUnrecognizedMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e410d-4cce-4536-83fa-4a5040674ad6" ExecutionSequence="2">  
            <Components>  
                 <Component Name=Microsoft.BizTalk.Component.XmlValidator >  
                    <Properties>  
                        <DocumentSpecName vt=8>MySchemas.DocspecName</DocumentSpecName>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
    </Stages>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd08-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bd08-132">See Also</span></span>  
 [<span data-ttu-id="8bd08-133">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="8bd08-133">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)