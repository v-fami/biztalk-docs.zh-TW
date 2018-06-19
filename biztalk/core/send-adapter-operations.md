---
title: 傳送配接器作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf4e0430-e3dc-4884-8411-bbcb579bd21e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444cf4ab7958b0d44838a8331b4b9e6a467baedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270918"
---
# <a name="send-adapter-operations"></a><span data-ttu-id="1c54c-102">傳送配接器作業</span><span class="sxs-lookup"><span data-stu-id="1c54c-102">Send Adapter Operations</span></span>
<span data-ttu-id="1c54c-103">傳送配接器可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1c54c-103">Send adapters can perform the following operations:</span></span>  
  
-   <span data-ttu-id="1c54c-104">**重新提交： void Resubmit （IBaseMessage msg，DateTime timeStamp）。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-104">**Resubmit: void Resubmit(IBaseMessage msg, DateTime timeStamp).**</span></span> <span data-ttu-id="1c54c-105">訊息傳輸失敗之後，配接器會在適當時機重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="1c54c-105">After a transmission failure occurs on a message, an adapter resubmits it when appropriate.</span></span> <span data-ttu-id="1c54c-106">這是以每個訊息為基礎來呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c54c-106">This is called on a per-message basis.</span></span> <span data-ttu-id="1c54c-107">如果批次訊息成功提交出去，配接器必須判斷導致失敗的訊息並再重新送出的項目不會個別呼叫中造成失敗的批次**重新提交**。</span><span class="sxs-lookup"><span data-stu-id="1c54c-107">If a batch of messages was submitted unsuccessfully, the adapter must determine the messages causing the failure, and resubmit the ones that did not cause the batch to fail in separate calls to **Resubmit**.</span></span> <span data-ttu-id="1c54c-108">本主題的結尾資訊關於如何保留訊息內容屬性值，當您呼叫**重新提交**。</span><span class="sxs-lookup"><span data-stu-id="1c54c-108">There is information at the end of this topic about how to preserve message context property values when you call **Resubmit**.</span></span>  
  
-   <span data-ttu-id="1c54c-109">**移至下一個傳輸： void MoveToNextTransport (IBaseMessage msg)。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-109">**Move to Next Transport: void MoveToNextTransport(IBaseMessage msg).**</span></span> <span data-ttu-id="1c54c-110">如果訊息在傳送作業期間發生失敗，而且訊息的重試次數已經用盡，則配接器可以將訊息傳送到下一個設定的傳輸，以重新傳輸。</span><span class="sxs-lookup"><span data-stu-id="1c54c-110">If a message fails during a send operation and its retry attempts have been exhausted, the adapter can send the message to the next configured transport for retransmission.</span></span>  
  
-   <span data-ttu-id="1c54c-111">**暫止： void MoveToSuspendQ (IBaseMessage msg)。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-111">**Suspend: void MoveToSuspendQ(IBaseMessage msg).**</span></span> <span data-ttu-id="1c54c-112">如果沒有設定其他備份傳輸，配接器便會將失敗的傳送訊息移到擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="1c54c-112">The adapter moves a failed send message to the Suspended queue if no additional backup transport is configured.</span></span> <span data-ttu-id="1c54c-113">本主題的結尾資訊關於如何保留訊息內容屬性值，當您呼叫**暫停**。</span><span class="sxs-lookup"><span data-stu-id="1c54c-113">There is information at the end of this topic about how to preserve message context property values when you call **Suspend**.</span></span>  
  
-   <span data-ttu-id="1c54c-114">**Delete: void DeleteMessage (IBaseMessage msg)。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-114">**Delete: void DeleteMessage(IBaseMessage msg).**</span></span> <span data-ttu-id="1c54c-115">在 BizTalk Server 通知訊息已成功傳輸之後，配接器便會刪除該訊息。</span><span class="sxs-lookup"><span data-stu-id="1c54c-115">The adapter deletes a message after being notified by BizTalk Server of its successful transmission.</span></span> <span data-ttu-id="1c54c-116">刪除訊息會告知 BizTalk Server，配接器已完成處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1c54c-116">Deleting a message tells BizTalk Server that the adapter is finished with the message.</span></span> <span data-ttu-id="1c54c-117">通常**SubmitResponse**作業會在相同的批次相關聯的**刪除**作業。</span><span class="sxs-lookup"><span data-stu-id="1c54c-117">Generally the **SubmitResponse** operation is done in the same batch as its associated **Delete** operation.</span></span>  
  
-   <span data-ttu-id="1c54c-118">**提交回應： void SubmitResponseMessage （IBaseMessage solicitMsgSent，IBaseMessage responseMsgToSubmit）。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-118">**Submit Response: void SubmitResponseMessage(IBaseMessage solicitMsgSent, IBaseMessage responseMsgToSubmit).**</span></span> <span data-ttu-id="1c54c-119">配接器會將回應提交到要傳回給 BizTalk Server 的批次。</span><span class="sxs-lookup"><span data-stu-id="1c54c-119">The adapter submits a response to the batch to be sent back to BizTalk Server.</span></span> <span data-ttu-id="1c54c-120">這個作業會包括呼叫中的原始訊息以及回應，因此，BizTalk Server 便可以將它們相互關聯。</span><span class="sxs-lookup"><span data-stu-id="1c54c-120">This operation includes the original message in the call along with the response so that BizTalk Server can correlate them.</span></span>  
  
-   <span data-ttu-id="1c54c-121">**取消回應： void 的 CancelResponseMessages (string correlationToken)。**</span><span class="sxs-lookup"><span data-stu-id="1c54c-121">**Cancel Response: void CancelResponseMessages(string correlationToken).**</span></span> <span data-ttu-id="1c54c-122">如果需要傳送回應訊息提交批次時之前, 就被取消**CancelResponseMessages**使用方法，傳入要刪除相關聯的回應訊息的相互關聯 token。</span><span class="sxs-lookup"><span data-stu-id="1c54c-122">If the sending of a response message needs to be canceled before the batch is submitted, the **CancelResponseMessages** method is used, passing in the correlation token for the associated response message to be deleted.</span></span>  
  
 <span data-ttu-id="1c54c-123">當呼叫**重新提交**或**暫停**訊息，您可能想要保留特定訊息內容屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1c54c-123">When calling **Resubmit** or **Suspend** on a message you may want to preserve the values of certain message context properties.</span></span> <span data-ttu-id="1c54c-124">只要以 XML 格式儲存屬性值即可。</span><span class="sxs-lookup"><span data-stu-id="1c54c-124">You can do this by saving property values in XML format.</span></span> <span data-ttu-id="1c54c-125">當您重新提交或擱置訊息時，訊息內容中的對應屬性仍會保持可用。</span><span class="sxs-lookup"><span data-stu-id="1c54c-125">When the message is resubmitted or suspended the corresponding properties remain available in the message context.</span></span>  
  
 <span data-ttu-id="1c54c-126">下列 XML 字串說明所儲存資訊的格式：</span><span class="sxs-lookup"><span data-stu-id="1c54c-126">The following XML string describes the format in which the information is stored:</span></span>  
  
```  
<PropertiesToUpdate>  
<Property name="StringProperty" nameSpace="http://MyNamespace1" vt="8">SomeString</Property>  
<Property name="IntProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="3">4</Property>  
<Property name="BoolProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="11">0</Property>  
</PropertiesToUpdate>  
```  
  
 <span data-ttu-id="1c54c-127">這個 XML 字串由下列程式碼產生：</span><span class="sxs-lookup"><span data-stu-id="1c54c-127">This XML string is generated by the following code:</span></span>  
  
```  
private string GetPropsToUpdateXml(int nextRetryAttempt)  
{  
string result = "<PropertiesToUpdate><Property name=\"RetryAttempts\" nameSpace=\"http://schemas.microsoft.com/BizTalk/2005/test-properties\" vt=\"3\">" + nextRetryAttempt.ToString() + "</Property></PropertiesToUpdate>";  
return result;  
}  
```  
  
 <span data-ttu-id="1c54c-128">接著，使用這個程式碼即可將這個字串儲存到訊息內容：</span><span class="sxs-lookup"><span data-stu-id="1c54c-128">This string is then saved to the message context by using this code:</span></span>  
  
```  
Message.Context.Write("PropertiesToUpdate", "http://schemas.microsoft.com/BizTalk/2003/system-properties", GetPropsToUpdateXml(++retryAttempt));  
```  
  
 <span data-ttu-id="1c54c-129">重新提交訊息時，配接器可以利用下列程式碼行讀取這個屬性：</span><span class="sxs-lookup"><span data-stu-id="1c54c-129">When the message is resubmitted, the adapter can read this property by using the following line of code:</span></span>  
  
```  
propValue = inmsg.Context.Read("RetryAttempts", "http://schemas.microsoft.com/BizTalk/2005/test-properties");  
```