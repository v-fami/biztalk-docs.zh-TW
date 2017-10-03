---
title: "MSMQ 配接器組態屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, send ports
- receive locations, adapters
- MSMQ adapters, properties
- MSMQ adapters, code sample
- send ports, adapters
ms.assetid: d660d0ce-bff9-4bc5-be1d-38954c2fdbe2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2460f359e0a9a3954d9417fdf441e9bd01de58b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-configuration-properties"></a>MSMQ 配接器組態屬性
下表列出可為 MSMQ 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|queue|VT_BSTR|指定接收位置所監控之位置的有效佇列路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|batchSize|VT_BSTR|指定提交訊息佇列至 MessageBox 資料庫時，MSMQ 配接器使用的批次大小。|有效值從 1 到 4294967295。|預設值為 20。|  
|transactional|VT_BSTR|指定是否從 Microsoft Distributed Transaction (MSDTC) 內容下的來源佇列讀取訊息。|有效值為：<br /><br /> 為 true<br />-false<br /><br /> 此配接器不支援在遠端佇列上的交易式讀取。|預設值為 false。|  
|serialProcessing|VT_BSTR|指定是否要依序處理訊息。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|onFailure|VT_BSTR|指定配接器如何回應錯誤。|有效值為：<br /><br /> -stopOnFailure<br />-suspendNonResumable<br />-suspendResumable|預設值為 suspendResumable。|  
|uri|VT_BSTR|指定接收位置所監控之佇列的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</queue><batchSize>20</batchSize><transactional>false</transactional><serialProcessing>false</serialProcessing><onFailure>suspendResumable</onFailure><uri>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</uri></Config></AdapterConfig></CustomProps>  
```  
  
 下表列出可為 MSMQ 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|佇列|VT_BSTR|指定目的地佇列。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|maximumMessageSiz|VT_BSTR|指定傳送到指定佇列的訊息之訊息大小上限 (以 KB 為單位)。|如果 segmentationSupport 和 transactional 設定為 true，有效值為 1 到 4294967295， 否則有效值便為 1 到 4095。|預設值為 1024年。|  
|acknowledgeType|VT_BSTR|指定一或多種通知類型。|有效值為.NET 成員**System.Messaging.AcknowledgeTypes**列舉型別。|預設值為 [無]。|  
|administrationQueue|VT_BSTR|指定 MSMQ 管理佇列。|無|無|  
|timeOut|VT_BSTR|指定等待訊息到達目的地佇列的時間上限。|這個屬性只有在 transactional 屬性設定為 true 時才適用。<br /><br /> 當指定 Days 的 timeOutUnits 值時，無效的值為 1 到 10675199。<br />當指定 Hours 的 timeOutUnits 值時，無效的值為 1 到 596523。<br />當指定 Minutes 的 timeOutUnits 值時，無效的值為 1 到 35791394。<br />當指定 Seconds 的 timeOutUnits 值時，無效的值為 1 到 2147483647。|無|  
|priority|VT_BSTR|指定訊息優先順序。|有效值為.NET 成員**System.Messaging.MessagePriority**列舉型別。|無|  
|recoverable|VT_BSTR|指定是否保證訊息的復原能力。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|encryptionAlgorithm|VT_BSTR|指定要使用的加密演算法。|有效值為.NET 成員**System.Messaging.EncryptionAlgorithm**列舉型別。|預設值為 [無]。|  
|useAuthentication|VT_BSTR|指定是否要使用驗證。|將此屬性與 certificate 屬性搭配使用以驗證訊息。 請使用 userName 和 password 屬性取得佇列的存取權。|無|  
|憑證 (certificate)|VT_BSTR|指定用來驗證訊息的憑證。|輸入 40 個字元的憑證指紋。|無|  
|segmentationSupport|VT_BSTR|指定是否支援分割。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|transactional|VT_BSTR|指定是否支援在 Microsoft Distributed Transaction (MSDTC) 內容下傳送訊息。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|useJournalQueue|VT_BSTR|指定是否要在每次處理訊息時儲存訊息的複本。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|useDeadLetterQueue|VT_BSTR|指定是否要在發生失敗時，傳送訊息到無法寄出的信件佇列。|有效值為：<br /><br /> 為 true<br />-false|預設值為 true。|  
|ackTypeEnumsValue|VT_BSTR|指定與所指定 acknowledgeType 值關聯之值的位元 OR。|無|預設值是 0。|  
|timeOutUnits|VT_BSTR|指定要與為 timeOut 屬性指定之值搭配使用的單位。|有效值為：<br /><br /> 天<br />-小時<br />-分鐘<br />秒|預設值為日。|  
|userName|VT_BSTR|指定遠端佇列的使用者名稱。|預設值為空白。|  
|密碼|VT_BSTR|指定要與為 userName 屬性指定之值搭配使用以存取遠端佇列的密碼。|當匯出繫結檔案時，一定會遮罩這個值。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|預設值為空白。|  
|bodyType|VT_BSTR|在 MSMQ 中指定訊息內文類型。|有效值為成員的.net **VarEnum**列舉型別。|預設值是 8209。|  
|uri|VT_BSTR|指定目的地佇列的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</queue><maximumMessageSize>1024</maximumMessageSize><acknowledgeType>None</acknowledgeType><administrationQueue>Direct=OS:TestServer\Private$\AdminQueue</administrationQueue><timeOut>4</timeOut><priority>Normal</priority><recoverable>false</recoverable><encryptionAlgorithm>None</encryptionAlgorithm><useAuthentication>false</useAuthentication><segmentationSupport>false</segmentationSupport><transactional>false</transactional><useJournalQueue>false</useJournalQueue><useDeadLetterQueue>true</useDeadLetterQueue><ackTypeEnumsValue>0</ackTypeEnumsValue><timeOutUnits>Days</timeOutUnits><userName>TestUser</userName><password>******</password><bodyType>8209</bodyType><uri>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</uri></Config></AdapterConfig>  
```  
  
> [!NOTE]
>  在指定的使用配接器架構所建置的配接器的 TransportTypeData 組態資料時，所使用的名稱/值組必須全部儲存到\<AdapterConfig > 項目。 因為\<AdapterConfig > 項目會指定 VT_BSTR (vt ="8") 資料型別然後\<> 必須逸出字元資料中的。