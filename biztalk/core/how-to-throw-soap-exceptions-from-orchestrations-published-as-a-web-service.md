---
title: 擲回 SOAP 例外狀況，從協調流程發佈為 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, SOAP exceptions
- orchestrations, SOAP errors
- Web services, orchestrations
ms.assetid: e1c7cd74-d1c8-4b9d-a418-4601b1f040d7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ef3d975632b6230cf1e3df299d0d9455f39da0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255574"
---
# <a name="how-to-throw-soap-exceptions-from-orchestrations-published-as-a-web-service"></a><span data-ttu-id="c3ef1-102">如何從協調流程發佈為 Web 服務擲回 SOAP 例外狀況</span><span class="sxs-lookup"><span data-stu-id="c3ef1-102">How to Throw SOAP Exceptions from Orchestrations Published as a Web Service</span></span>
<span data-ttu-id="c3ef1-103">您可以從已發佈為 Web 服務的協調流程擲回 SOAP 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-103">You can return a SOAP exception from an orchestration that you have published as a Web service.</span></span> <span data-ttu-id="c3ef1-104">您會將錯誤訊息加入到 SOAP 連接埠中，並傳回該錯誤訊息不是傳回回應。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-104">You add a fault message to your SOAP port and send the fault message instead of the response.</span></span>  
  
### <a name="to-throw-a-soap-exception-from-an-orchestration-published-as-a-web-service"></a><span data-ttu-id="c3ef1-105">若要從發佈為 Web 服務的協調流程擲回 SOAP 例外狀況</span><span class="sxs-lookup"><span data-stu-id="c3ef1-105">To throw a SOAP exception from an orchestration published as a Web service</span></span>  
  
1.  <span data-ttu-id="c3ef1-106">將錯誤訊息加入到 SOAP 連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-106">Add a fault message to the SOAP port type.</span></span> <span data-ttu-id="c3ef1-107">錯誤訊息的訊息類型可以是符合 XML 結構描述 (XSD) 標準的任何結構描述或簡單類型。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-107">The message type for the fault message can be any XML Schema (XSD) compliant schema or simple type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3ef1-108">若要傳回字串做為**SoapException**資訊時發生錯誤，您可以使用簡單類型字串做為錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-108">To return a string as a **SoapException** with error information, you can use the simple type string as the fault message type.</span></span>  
  
2.  <span data-ttu-id="c3ef1-109">在協調流程中建立錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-109">In your orchestration, create the fault message.</span></span>  
  
3.  <span data-ttu-id="c3ef1-110">使用**傳送**圖形，連結到 SOAP 連接埠對應至錯誤訊息中的錯誤作業。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-110">Use the **Send** shape to link to the fault operation in the SOAP port that corresponds to the fault message.</span></span> <span data-ttu-id="c3ef1-111">SOAP 例外狀況會包裝傳回的訊息錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-111">A SOAP exception wraps the returned fault message.</span></span>  
  
 <span data-ttu-id="c3ef1-112">如果您的協調流程不會傳回錯誤，使用不同**傳送**傳送標準 SOAP 回應訊息使用一般回應作業的圖形。</span><span class="sxs-lookup"><span data-stu-id="c3ef1-112">If your orchestration does not return an error, use a different **Send** shape to send the standard SOAP response message using the usual response operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ef1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ef1-113">See Also</span></span>  
 <span data-ttu-id="c3ef1-114">[錯誤訊息](../core/fault-messages.md) </span><span class="sxs-lookup"><span data-stu-id="c3ef1-114">[Fault Messages](../core/fault-messages.md) </span></span>  
 [<span data-ttu-id="c3ef1-115">協調流程發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="c3ef1-115">Publishing an Orchestration as a Web Service</span></span>](../core/publishing-an-orchestration-as-a-web-service.md)