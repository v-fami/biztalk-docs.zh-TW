---
title: "WCF 訊息的管線元件中使用 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: b02f2913-4948-4de9-bc59-73bab40aa1a0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf40cf5a81188dae0174199f16229daf61115796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-pipeline-components"></a><span data-ttu-id="a3db2-102">搭配管線元件使用 WCF 訊息中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="a3db2-102">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>
<span data-ttu-id="a3db2-103">您可以在管線元件中搭配 WCF 配接器設定自訂 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="a3db2-103">You can set the custom SOAP headers with the WCF adapters in pipeline components.</span></span> <span data-ttu-id="a3db2-104">您可以使用內容屬性名稱的組合**OutboundCustomHeaders**，和目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**。</span><span class="sxs-lookup"><span data-stu-id="a3db2-104">You use a combination of the context property name, **OutboundCustomHeaders**, and the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**.</span></span> <span data-ttu-id="a3db2-105">當您使用**OutboundCustomHeaders**屬性，屬性必須有\<**標頭**> 元素是根項目。</span><span class="sxs-lookup"><span data-stu-id="a3db2-105">When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**> element as the root element.</span></span> <span data-ttu-id="a3db2-106">所有自訂 SOAP 標頭必須置於\<**標頭**> 項目。</span><span class="sxs-lookup"><span data-stu-id="a3db2-106">All of the custom SOAP headers must be placed inside the \<**headers**> element.</span></span> <span data-ttu-id="a3db2-107">如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**>\</**標頭**> 或\< **標頭**/ > 若要**OutboundCustomHeaders**屬性。</span><span class="sxs-lookup"><span data-stu-id="a3db2-107">If the custom SOAP header value is an empty string, you must assign \<**headers**>\</**headers**> or \<**headers**/> to the **OutboundCustomHeaders** property.</span></span> <span data-ttu-id="a3db2-108">如需如何搭配 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭搭配 WCF 配接器，從[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。</span><span class="sxs-lookup"><span data-stu-id="a3db2-108">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
 <span data-ttu-id="a3db2-109">下列程式碼範例在名為屬性的傳送管線元件中設定自訂 SOAP 標頭**OutboundCustomHeaders**:</span><span class="sxs-lookup"><span data-stu-id="a3db2-109">The following code example sets custom SOAP headers in a send pipeline component for a property named **OutboundCustomHeaders**:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<headers>  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </headers>";  
inmsg.Context.Write("OutboundCustomHeaders","http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="a3db2-110">如需管線元件的詳細資訊，請參閱[開發自訂管線元件](../core/developing-custom-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="a3db2-110">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3db2-111">不可設定 WCF 基礎結構用於 Web 服務標準的標準 SOAP 標頭，例如 WS-Addressing、WS-Security 和 WS-AtomicTransaction。</span><span class="sxs-lookup"><span data-stu-id="a3db2-111">You must not set the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3db2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3db2-112">See Also</span></span>  
 <span data-ttu-id="a3db2-113">[WCF 訊息與協調流程中使用 SOAP 標頭](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="a3db2-113">[Using SOAP Headers in WCF Messages with Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md) </span></span>  
 <span data-ttu-id="a3db2-114">[SOAP 標頭與使用的 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="a3db2-114">[SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md) </span></span>  
 <span data-ttu-id="a3db2-115">[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a3db2-115">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="a3db2-116">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a3db2-116">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)