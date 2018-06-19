---
title: POP3 配接器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, adapters
- POP3 adapters, receive locations
- POP3 adapters, code sample
- POP3 adapters, properties
ms.assetid: e30c848d-afff-42f3-8162-c7ea8c7e3b9a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bf7aa17f36143f80a82f664dbabd257d7b924db
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972436"
---
# <a name="pop3-adapter-configuration-properties"></a>POP3 配接器組態屬性
下表列出可為 POP3 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|mailServer|VT_BSTR|指定接受 POP3 配接器輪詢之信箱所在的 POP3 郵件伺服器。|無|無|  
|serverPort|VT_BSTR|指定 POP3 郵件伺服器的連接埠。|有效值介於 0 到 65535 之間。|若值為 0，表示當 sslRequired 屬性設定為 False 時，就使用預設的 POP3 連接埠 110；當 sslRrequired 設定為 True 時，則使用連接埠 995。<br /><br /> 預設值是 0。|  
|userName|VT_BSTR|指定要用於 POP3 伺服器驗證的使用者名稱。|無|無|  
|密碼|VT_BSTR|指定要用於 POP3 伺服器驗證的使用者密碼。|當匯出繫結檔案時，一定會遮罩這個值。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|無|  
|authenticationScheme|VT_BSTR|指定要提供給目的地伺服器的驗證類型。|有效值為：<br /><br /> -基本<br />摘要<br />-SPA|此屬性沒有預設值。|  
|sslRequired|VT_BSTR|指定是否要使用 SSL 來與目的地伺服器通訊。|有效值為：<br /><br /> 為 true<br />-false|預設值為 false。|  
|applyMIME|VT_BSTR|指定是否將 MIME 解碼套用到 POP3 配接器接收的訊息。|有效值為：<br /><br /> 為 true<br />-false|預設值為 true。|  
|bodyPartContentType|VT_BSTR|指定要提交到 BizTalk Server 的內送電子郵件訊息的內文部分內容類型。|有效值為：<br /><br /> -主體<br />-text/xml<br />-文字/純文字<br />-文字 /|此屬性沒有預設值。|  
|bodyPartIndex|VT_BSTR|指定要提交到 BizTalk Server 的內送電子郵件訊息的內文部分。|有效值介於 0 到 128。|預設值是 0。|  
|errorThreshold|VT_BSTR|指定在關閉配接器前需等待的網路或通訊協定錯誤的最大數目。|有效值介於 0 到 4294967295。|指定 0 值可避免配接器關閉。<br /><br /> 預設值是 10。|  
|pollingInterval|VT_BSTR|指定每次嘗試從 POP3 伺服器擷取訊息之間的間隔。|有效值為：<br /><br /> -120 如果 pollingUnitOfMeasure 值為 1 天。<br />-2880年如果 pollingUnitOfMeasure 值為 1 小時。<br />-從 1 到 172800 如果 pollingUnitOfMeasure 值為分鐘。<br />-從 2 到 10368000 如果 pollingUnitOfMeasure 值為秒。|預設值為 5。|  
|pollingUnitOfMeasure|VT_BSTR|指定要與 pollingInterval 的值搭配使用的度量單位。|有效值為：<br /><br /> 天<br />-小時<br />-分鐘<br />秒|預設值為 [分]。|  
|uri|VT_BSTR|指定接收位置所監控之信箱的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test.microsoft.com</mailServer><serverPort>0</serverPort><userName>testuser</userName><password>******</password><authenticationScheme>Basic</authenticationScheme><sslRequired>false</sslRequired><applyMIME>true</applyMIME><bodyPartContentType>text/xml</bodyPartContentType><bodyPartIndex>1</bodyPartIndex><errorThreshold>10</errorThreshold><pollingInterval>5</pollingInterval><pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri>POP3://test.microsoft.com#testuser</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  在指定的使用配接器架構所建置的配接器的 TransportTypeData 組態資料時，所使用的名稱/值組必須全部儲存到\<AdapterConfig > 項目。 因為\<AdapterConfig > 項目會指定 VT_BSTR (vt ="8") 資料型別然後\<\>必須逸出字元資料中的。