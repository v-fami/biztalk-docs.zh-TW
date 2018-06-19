---
title: MQSeries 配接器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, code sample
- receive locations, adapters
- MQSeries adapters, send ports
- MQSeries adapters, properties
- MQSeries adapters, receive location
- send ports, adapters
ms.assetid: 7517a8bf-aa65-4af9-aed0-7c74fb480328
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f7c24f15c916970926143cec4cb6bb33401efeb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972484"
---
# <a name="mqseries-adapter-configuration-properties"></a>MQSeries 配接器組態屬性
下表列出您可為 MQSeries 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|指定接收位置所監控之位置的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|queueDetails|VT_BSTR|指定來源 MQSeries 佇列的相關資訊，包括伺服器、佇列管理員和佇列。|-無|這個屬性之前會加上 MQS://，以建立 uri 屬性。|  
|transactionSupported|VT_BSTR|指定 MQSeries 配接器是否會開始 BizTalk Server 與 MQSeries Server 之間的 Microsoft Distributed Transaction Coordinator (DTC) 交易。|有效值為：<br /><br /> -[是]<br />-沒有|若設為 no，則無法確保訊息傳遞。<br /><br /> 預設值為 yes。|  
|suspendAsNonResumable|VT_BSTR|指定是否將擱置的訊息標示為可繼續。|有效值為：<br /><br /> -[是]<br />-沒有|預設值為 no。|  
|dataOffsetForHeaders|VT_BSTR|配接器會使用 MQSeries 標頭 (MQXQH、MQIIH 和 MQCIH 結構) 的值，在 BizTalk Server 內容屬性中填入對應值。 依照預設，配接器會從訊息內文移除這些 MQSeries 屬性。|有效值為：<br /><br /> -[是]<br />-沒有|將此屬性設為 no，以保留訊息內文中的屬性。<br /><br /> 預設值為 yes。|  
|pollingInterval|VT_BSTR|指定接收元件用於輪詢 MQSeries 佇列的間隔。|有效值從 1 到 10000。|pollingInterval 會與配接器內建的固定等待間隔 (3 秒) 搭配使用。 如果 pollingInterval 值少於 3 秒，則會將 pollingInterval 的值設為等待間隔。<br /><br /> 預設值是 3。|  
|pollingUnit|VT_BSTR|指定要用於輪詢間隔的時間單位。|有效值為：<br /><br /> -小時<br />-分鐘<br />-秒|預設值為 seconds。|  
|maximumBatchSize|VT_BSTR|指定一批訊息的大小上限 (以 KB 為單位)。|有效值從 1 到 10485760。|預設值為 100。|  
|maximumNumberOfMessages|VT_BSTR|指定批次中的訊息數目上限。|有效值是從 1 到 100000|預設值為 100。|  
|threadCount|VT_BSTR|指定每個接收位置所使用的執行緒數目。|有效值從 1 到 64。|預設值為 2。|  
|fragmentationSize|VT_BSTR|指定在 MQSAgent 與配接器之間傳送的訊息之訊息區塊大小 (以 KB 為單位)。|有效值從 1 到 1048576。|預設值為 500。|  
|characterSet|VT_BSTR|指定字元集，以及 MQSeries 在傳送訊息到接收位置前是否要轉換字元。|有效值為：<br /><br /> -無。 不轉換。<br />-Ucs-2 和 utf-16。 轉換成這些字元集。 MQSeries 不會區分這些字元集。<br />-UTF-8。 轉換為 UTF-8 字元集。|預設值為 none。|  
|errorThreshold|VT_BSTR|指定要記錄的錯誤數目上限。 配接器會繼續運作，且若配接器復原，會將事件記錄在事件記錄檔中。|有效值從 1 到 1000 之間。|預設值是 10。|  
|分割|VT_BSTR|指定 MQSeries 組合分割的訊息還是取得訊息原貌。|有效值為：<br /><br /> -無<br />-完整|指定 none，以不啟用分割的方式讀取 MQSeries 佇列的訊息。<br /><br /> 指定 complete，在傳送訊息到配接器之前，讓 MQSeries 組合分割的訊息。<br /><br /> 預設值為 none。|  
|Ordered|VT_BSTR|指定 MQSeries 在接收到 MQSeries 佇列的訊息時，是否維護訊息的順序。|有效值為：<br /><br /> -沒有<br />-noStop，<br />-yesStop，<br />-yesSuspend，|指定 no，以忽略訊息順序。<br /><br /> 指定 noStop，以忽略訊息順序並在發生錯誤時停用接收位置。<br /><br /> 指定 yesStop，以啟用排序。 此選項會結束交易並在發生錯誤時停用接收位置。<br /><br /> 指定 yesSuspend，以啟用排序。 此選項會在發生錯誤時將訊息移至擱置佇列。 此值在發生錯誤時不會保留順序，但可以讓接收位置繼續接收訊息。<br /><br /> 預設值為 no。|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1/RQ0</uri><queueDetails>TESTMQServer/DQM1/RQ0</queueDetails><transactionSupported>yes</transactionSupported><suspendAsNonResumable>no</suspendAsNonResumable><dataOffsetForHeaders>yes</dataOffsetForHeaders><pollingInterval>1</pollingInterval><pollingUnit>seconds</pollingUnit><maximumBatchSize>100</maximumBatchSize><maximumNumberOfMessages>100</maximumNumberOfMessages><threadCount>2</threadCount><fragmentationSize>500</fragmentationSize><characterSet>none</characterSet><errorThreshold>10</errorThreshold><segmentation>none</segmentation><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
 下表列出可為 MQSeries 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|指定資料傳送之目標位置的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|queueDetails|VT_BSTR|指定目標 MQSeries 佇列的相關資訊，包括伺服器、佇列管理員和佇列。|傳送埠或接收位置的 URI 不能超過 256 個字元。|這個屬性之前會加上 MQS://，以建立 uri 屬性。|  
|transactionSupported|VT_BSTR|指定 MQSeries 配接器是否會開始 BizTalk Server 與 MQSeries Server 之間的 Microsoft Distributed Transaction Coordinator (DTC) 交易。|有效值為：<br /><br /> -[是]<br />-沒有|若設為 no，則無法確保訊息傳遞。<br /><br /> 預設值為 yes。|  
|dataConversion|VT_BSTR|指定是否將訊息轉換為 MQSeries Server for Windows Server 的 ANSI 字碼頁。|有效值為：<br /><br /> -[是]<br />-沒有|預設值為 no。|  
|segmentationAllowed|VT_BSTR|若個別訊息超過 MQSeries 佇列的訊息最大長度，則指定是否使用「MQSeries 佇列管理員」分割。|有效值為：<br /><br /> -[是]<br />-沒有|預設值為 no。|  
|fragmentationSize|VT_BSTR|指定在配接器與 MQSAgent 之間傳送的訊息之訊息區塊大小 (以 KB 為單位)。|有效值從 1 到 1048576。|預設值為 500。|  
|Ordered|VT_BSTR|指定 MQSeries 在傳送到 MQSeries 佇列的訊息時，是否維護訊息的順序。|有效值為：<br /><br /> -[是]<br />-沒有|預設值為 no。|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1(QM1)/SQ0</uri><queueDetails>TESTMQServer/DQM1(QM1)/SQ0</queueDetails><transactionSupported>yes</transactionSupported><dataConversion>no</dataConversion><segmentationAllowed>no</segmentationAllowed><fragmentationSize>500</fragmentationSize><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  在指定的使用配接器架構所建置的配接器的 TransportTypeData 組態資料時，所使用的名稱/值組必須全部儲存到\<AdapterConfig\>項目。 因為\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料型別然後\<\>必須逸出字元資料中的。