---
title: 如何部署管線 |Microsoft 文件
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
ms.openlocfilehash: db6047752c45a2f72b615102e14a4e66839e3e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249598"
---
# <a name="how-to-deploy-pipelines"></a>如何部署管線
管線已編譯和部署作為方案建置和部署程序的一部分。 編譯器呼叫**驗證**上每個元件，允許元件傳回方法的編譯錯誤的設定資訊。 在建置之後部署方案時，管線會部署在其餘方案的相同組件中。  
  
## <a name="per-instance-pipeline-configuration"></a>個別執行個體管線組態  
 個別執行個體管線組態用以修改在傳送埠或接收位置層級已部署管線中的管線元件屬性。 當只有一些管線元件屬性需要每個執行個體都修改時，個別執行個體管線組態會非常有用。 例如，如果您需要在多個接收位置支援不同的訊息類型，且具有單一的自訂 XML 接收管線，個別執行個體管線組態可讓您部署管線和覆寫預設組態 (包括指定不同的信封和文件規格名稱)。 這項機制在 BizTalk 管理主控台中受支援，且可透過總管物件模型以程式設計方式支援。  
  
### <a name="per-instance-pipeline-configuration-using-biztalk-administration-console"></a>使用 BizTalk 管理主控台的個別執行個體管線組態  
 您可使用 BizTalk 管理主控台執行個別執行個體管線組態。 在部署完自訂管線後，請視需要建立接收位置或傳送埠。 然後，對於每個接收位置或傳送埠，請透過 [設定管線] 對話方塊覆寫預設屬性值。 例如，若要指定不同的文件結構描述，輸入結構描述名稱 **[envelopedocspecnames]** 屬性。  
  
> [!WARNING]
>  在接收位置或傳送埠中指定的組態值將不會進行驗證。 如果組態不正確，訊息於執行階段透過管線傳遞時就會失敗。  
  
### <a name="per-instance-pipeline-configuration-using-the-explorer-object-model"></a>使用總管物件模型的個別執行個體管線組態  
 當描述管線元件的個別執行個體組態的 XML 檔案被讀取時，它會覆寫管線檔案中所設定的屬性。  
  
 藉由使用 BizTalk 總管物件模型可設定個別執行個體管線組態。 「 BizTalk 總管物件模型提供**Ireceivelocation**屬性**IReceiveLocation**和**Receivepipelinedata**介面設定的組態接收管線元件。 「 BizTalk 總管物件模型也提供**Ireceiveport**方法**Isendport**和**Receivepipelinedata**介面傳送的設定管線元件。  
  
 個別執行個體管線組態不支援下列動作：  
  
-   重新安排管線中的階段  
  
-   新增或移除階段  
  
-   重新安排階段中的元件  
  
-   新增或移除元件  
  
 僅支援在管線元件組態中的變更。 管線元件的個別執行個體組態會覆寫通用管線元件組態。 若在個別執行個體管線組態中未指定元件的參數，則會使用該參數的通用組態 (如「管線設計師」中所設定)。  
  
 以下是個別執行個體組態資料的範例。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [開發自訂管線元件](../core/developing-custom-pipeline-components.md)