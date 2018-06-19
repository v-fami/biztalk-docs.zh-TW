---
title: 使用管線從服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, pipelines
- pipelines, service solutions
ms.assetid: 0870fce1-52ec-4ff8-884f-a3199bd7ccbb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d6b8021a22db366b31cde26abdc3ef48f3e51a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287206"
---
# <a name="using-pipelines-from-the-service-oriented-solution"></a><span data-ttu-id="5f1ca-102">使用管線從服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="5f1ca-102">Using Pipelines from the Service Oriented Solution</span></span>
<span data-ttu-id="5f1ca-103">客戶服務協調流程的內嵌版本 (**CustomerService**) 呼叫付款追蹤系統直接。</span><span class="sxs-lookup"><span data-stu-id="5f1ca-103">The inline version of the customer service orchestration (**CustomerService**) calls the payment tracking system directly.</span></span> <span data-ttu-id="5f1ca-104">為了準備已傳送訊息和處理已接收訊息，協調流程會從程式碼呼叫管線。</span><span class="sxs-lookup"><span data-stu-id="5f1ca-104">To prepare the sent message and process the received message, the orchestration calls the pipelines from code.</span></span> <span data-ttu-id="5f1ca-105">這可從其他實例版本重複使用管線。</span><span class="sxs-lookup"><span data-stu-id="5f1ca-105">This allows the reuse of the pipelines from the other scenarios versions.</span></span> <span data-ttu-id="5f1ca-106">它也維持從管線階段減少協調流程。</span><span class="sxs-lookup"><span data-stu-id="5f1ca-106">It also maintains the decoupling of the orchestration from the pipeline stages.</span></span>  
  
## <a name="calling-the-pipelines"></a><span data-ttu-id="5f1ca-107">呼叫管線</span><span class="sxs-lookup"><span data-stu-id="5f1ca-107">Calling the Pipelines</span></span>  
 <span data-ttu-id="5f1ca-108">若要從程式碼使用管線，您必須建立訊息集合、將要處理的訊息新增到集合、建立空的訊息以接收結果訊息，以及叫用管線。</span><span class="sxs-lookup"><span data-stu-id="5f1ca-108">To use the pipelines from code, you must create a message collection, add the message to process to the collection, create an empty message to receive the result message, and invoke the pipeline.</span></span>  
  
 <span data-ttu-id="5f1ca-109">下列程式碼會從**CustomerService**協調流程處於**ConstructRequestMessageAfterSendPipeline**圖形：</span><span class="sxs-lookup"><span data-stu-id="5f1ca-109">The following code from the **CustomerService** orchestration is in the **ConstructRequestMessageAfterSendPipeline** shape:</span></span>  
  
```  
// Create the collection of messages to be sent to the send pipeline...  
sendPipelineInputMessages =   
    new Microsoft.XLANGs.Pipeline.SendPipelineInputMessages();  
sendPipelineInputMessages.Add(LastPaymentRequest);  
  
// Create an empty message for the output from the pipeline...  
LastPaymentRequestAfterSendPipeline = null;  
  
// Execute the send pipeline and get the message output from   
// the send pipeline.  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.  
    ExecuteSendPipeline(  
        typeof(  
            Microsoft.Samples.BizTalk.  
                WoodgroveBank.PaymentTrackerPipelines.  
                    PaymentTrackerSendPipeline  
        ),  
        sendPipelineInputMessages,  
        LastPaymentRequestAfterSendPipeline  
    );  
```  
  
 <span data-ttu-id="5f1ca-110">**GetLastPaymentResponse**圖形接受來自上述的程式碼的訊息、 將它傳送到付款追蹤系統，和處理傳回的訊息透過接收管線：</span><span class="sxs-lookup"><span data-stu-id="5f1ca-110">The **GetLastPaymentResponse** shape takes the message from the above code, sends it to the payment tracking system, and processes the returned message through the receive pipeline:</span></span>  
  
```  
// Execute the inline method to send the message to the   
// Payment Tracking System and get the response.  
// The response message received should be passed through the   
// receive pipeline.  
  
LastPaymentResponseBeforeReceivePipeline =   
    Microsoft.Samples.BizTalk.  
        WoodgroveBank.  
            PaymentTrackerCall.  
                PaymentTrackerCaller.  
                    GetPaymeTrackerResponse  
                    (  
                        LastPaymentRequestAfterSendPipeline  
                    );   
  
// Execute the receive pipeline using the helper class so that we don't  
// need to declare the non-serializable types involved.  
  
// Set the documentspec name so the xml disassembler in the   
// pipeline can resolve the schemas for the received message  
// without ambiguity.  
LastPaymentResponseBeforeReceivePipeline(XMLNORM.DocumentSpecName) =   
"Microsoft.Samples.BizTalk.WoodgroveBank.Schemas.LastPaymentResponse, Microsoft.Samples.BizTalk.WoodgroveBank.Schemas, Version=1.0.0.0, Culture=neutral, PublicKeyToken=5f57a322d27bc5fb";  
// Create an empty response message and fill it in with the   
// real response from the Payment Tracking System  
LastPaymentResponse = null;  
  
Microsoft.Samples.BizTalk.WoodgroveBank.Utilities.  
    ReceivePipelineHelper.CallReceivePipeLine (  
        typeof(  
            Microsoft.Samples.BizTalk.WoodgroveBank.  
                PaymentTrackerPipelines.PaymentTrackerReceivePipeline  
            ),  
            LastPaymentResponseBeforeReceivePipeline,  
            LastPaymentResponse  
        );  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f1ca-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f1ca-111">See Also</span></span>  
 [<span data-ttu-id="5f1ca-112">實作會反白顯示的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="5f1ca-112">Implementation Highlights of the Service Oriented Solution</span></span>](../core/implementation-highlights-of-the-service-oriented-solution.md)