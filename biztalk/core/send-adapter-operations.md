---
title: "傳送配接器作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4e0430-e3dc-4884-8411-bbcb579bd21e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444cf4ab7958b0d44838a8331b4b9e6a467baedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="send-adapter-operations"></a>傳送配接器作業
傳送配接器可以執行下列作業：  
  
-   **重新提交： void Resubmit （IBaseMessage msg，DateTime timeStamp）。** 訊息傳輸失敗之後，配接器會在適當時機重新提交訊息。 這是以每個訊息為基礎來呼叫。 如果批次訊息成功提交出去，配接器必須判斷導致失敗的訊息並再重新送出的項目不會個別呼叫中造成失敗的批次**重新提交**。 本主題的結尾資訊關於如何保留訊息內容屬性值，當您呼叫**重新提交**。  
  
-   **移至下一個傳輸： void MoveToNextTransport (IBaseMessage msg)。** 如果訊息在傳送作業期間發生失敗，而且訊息的重試次數已經用盡，則配接器可以將訊息傳送到下一個設定的傳輸，以重新傳輸。  
  
-   **暫止： void MoveToSuspendQ (IBaseMessage msg)。** 如果沒有設定其他備份傳輸，配接器便會將失敗的傳送訊息移到擱置佇列。 本主題的結尾資訊關於如何保留訊息內容屬性值，當您呼叫**暫停**。  
  
-   **Delete: void DeleteMessage (IBaseMessage msg)。** 在 BizTalk Server 通知訊息已成功傳輸之後，配接器便會刪除該訊息。 刪除訊息會告知 BizTalk Server，配接器已完成處理訊息。 通常**SubmitResponse**作業會在相同的批次相關聯的**刪除**作業。  
  
-   **提交回應： void SubmitResponseMessage （IBaseMessage solicitMsgSent，IBaseMessage responseMsgToSubmit）。** 配接器會將回應提交到要傳回給 BizTalk Server 的批次。 這個作業會包括呼叫中的原始訊息以及回應，因此，BizTalk Server 便可以將它們相互關聯。  
  
-   **取消回應： void 的 CancelResponseMessages (string correlationToken)。** 如果需要傳送回應訊息提交批次時之前, 就被取消**CancelResponseMessages**使用方法，傳入要刪除相關聯的回應訊息的相互關聯 token。  
  
 當呼叫**重新提交**或**暫停**訊息，您可能想要保留特定訊息內容屬性的值。 只要以 XML 格式儲存屬性值即可。 當您重新提交或擱置訊息時，訊息內容中的對應屬性仍會保持可用。  
  
 下列 XML 字串說明所儲存資訊的格式：  
  
```  
<PropertiesToUpdate>  
<Property name="StringProperty" nameSpace="http://MyNamespace1" vt="8">SomeString</Property>  
<Property name="IntProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="3">4</Property>  
<Property name="BoolProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="11">0</Property>  
</PropertiesToUpdate>  
```  
  
 這個 XML 字串由下列程式碼產生：  
  
```  
private string GetPropsToUpdateXml(int nextRetryAttempt)  
{  
string result = "<PropertiesToUpdate><Property name=\"RetryAttempts\" nameSpace=\"http://schemas.microsoft.com/BizTalk/2005/test-properties\" vt=\"3\">" + nextRetryAttempt.ToString() + "</Property></PropertiesToUpdate>";  
return result;  
}  
```  
  
 接著，使用這個程式碼即可將這個字串儲存到訊息內容：  
  
```  
Message.Context.Write("PropertiesToUpdate", "http://schemas.microsoft.com/BizTalk/2003/system-properties", GetPropsToUpdateXml(++retryAttempt));  
```  
  
 重新提交訊息時，配接器可以利用下列程式碼行讀取這個屬性：  
  
```  
propValue = inmsg.Context.Read("RetryAttempts", "http://schemas.microsoft.com/BizTalk/2005/test-properties");  
```