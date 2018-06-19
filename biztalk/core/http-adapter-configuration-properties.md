---
title: HTTP 配接器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, properties
- receive locations, adapters
- HTTP adapters, code sample
- HTTP adapters, send ports
- HTTP adapters, receive locations
- send ports, adapters
ms.assetid: 3d4e9d88-ea40-4478-a0cf-77057fadd3b2
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f08106c698d50e95c36b8325cc3d92aa0debb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22258654"
---
# <a name="http-adapter-configuration-properties"></a>HTTP 配接器組態屬性
下表列出可為 HTTP 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|ReturnCorrelationHandle|VT_BOOL|指定若成功，接收位置將傳送 HTTP 回應上已提交之訊息的相互關聯 Token 給用戶端。|此屬性只適用於單向接收位置。<br /><br /> 有效值為：<br /><br /> --1 (true)<br />-0 (false)|無|  
|ResponseContentType|VT_BSTR|指定接收位置傳回給用戶端的 HTTP 回應訊息內容類型。|此屬性只適用於要求-回應接收位置。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|預設值為 text/xml。|  
|SuspendFailedRequests|VT_BOOL|指定是否要擱置輸入處理失敗的 HTTP 要求。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|0 (false) 值表示要捨棄失敗的要求，並將錯誤狀態碼 (401 或 500) 傳送至用戶端。<br /><br /> -1 (true) 值表示要擱置失敗的要求，並將「已接受」狀態碼 (200) 傳送給單向接收埠的用戶端，或是將「錯誤」狀態碼 (500) 傳送給雙向接收埠的用戶端。<br /><br /> 預設值為 0 (false)。|  
|UseSSO|VT_BOOL|指定使用「企業單一登入」。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|回送|VT_BOOL|指定對於在此位置接收到的要求訊息，是要設定路由至傳送埠或傳回此接收位置，以做為回應傳送。|此屬性只適用於要求-回應接收位置。<br /><br /> 有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
<ResponseContentType vt="8">text/xml</ResponseContentType>  
<SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
<UseSSO vt="11">-1</UseSSO>  
<LoopBack vt="11">-1</LoopBack>  
</CustomProps></  
```  
  
 下表列出可為 HTTP 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|指定此傳送埠的 Proxy 伺服器連接埠。|有效值介於 0 到 65535 之間。|如果 UseProxy 設定為 0 (false)，則此屬性不需要值。<br /><br /> 預設值是 80。|  
|RequestTimeout|VT_I4|指定 HTTP/HTTPS 傳輸逾時 (以秒為單位)。|有效值是從 0 到 MAX_LONG。|若 HTTP 配接器在此時間內未接收到回應，則服務會記錄錯誤，並根據重試基礎結構重新提交訊息。<br /><br /> 若設定為 0，則 BizTalk 傳訊引擎會根據要求訊息的大小來計算逾時。 若未提供任何值，則會使用處理常式的值。|  
|憑證|VT_BSTR|指定用來建立「安全通訊端層」(SSL) 連線的用戶端憑證指紋。|最小長度：00<br /><br /> 最大長度： 59|預設值為空白。|  
|AuthenticationScheme|VT_BSTR|指定要提供給目的地伺服器的驗證類型。|有效值為：<br /><br /> 匿名<br />-基本<br />摘要<br />Kerberos|預設值為「匿名」。|  
|使用者名稱|VT_BSTR|指定要用於目的地伺服器驗證的使用者名稱。|如果使用 [基本] 或 [摘要] 的 AuthenticationScheme，而且未使用「企業單一登入」，則此屬性需要一個值。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|無|  
|EnableChunkedEncoding|VT_BOOL|指定使用區塊編碼。|若 HTTP 傳送處理常式是設為 [使用 Proxy]，則區段編碼會隱含停用。<br /><br /> 有效值為：<br /><br /> --1 (true)<br />-0 (false)|若啟用此選項，HTTP 配接器將會使用其最大區塊大小為 8 KB 的 HTTP 區段編碼。<br /><br /> 預設值為 0 (false)。|  
|UseProxy|VT_BOOL|指定 HTTP 傳送處理常式是否要使用 Proxy 伺服器。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|ProxyName|VT_BSTR|指定此傳送埠的 Proxy 伺服器位址。|最小長度：00<br /><br /> 最大長度：256|如果 UseProxy 設定為 0 (false)，則此屬性不需要值。|  
|UseSSO|VT_BOOL|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|密碼|VT_NULL|指定要用於目的地伺服器驗證的密碼。|如果使用 [基本] 或 [摘要] 的 AuthenticationScheme，而且未使用「企業單一登入」，則此屬性需要一個值。<br /><br /> 當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|若您有為此欄位提供值，請在匯入繫結檔之前，將此屬性的型別設定為 VT_BSTR (vt="8")。|  
|MaxRedirects|VT_I4|指定允許訊息傳送的重新導向上限。|有效值介於 0 到 10。|預設值為 5。|  
|ContentType|VT_BSTR|指定要求訊息的內容類型。|最小長度：00<br /><br /> 最大長度：256|若未設定此值，則使用處理常式的值。|  
|ProxyPassword|VT_NULL|指定要用於 Proxy 伺服器驗證的使用者密碼。|當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|如果 UseProxy 設定為 0 (false)，則此屬性不需要值。|  
|ProxyUsername|VT_BSTR|指定要用於 Proxy 伺服器驗證的使用者名稱。|最小長度：00<br /><br /> 最大長度：256|如果 UseProxy 設定為 0 (false)，則此屬性不需要值。|  
|UseHandlerSetting|VT_BOOL|指定傳送埠組態必須使用為 HTTP 傳送處理常式所指定的 Proxy 設定。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 -1 (true)。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<RequestTimeout vt="3">60</RequestTimeout>  
<Certificate vt="8">A7 6D F9 06 5E FC 97 66 75 59 B5 D6 67 0C 84 DC 64 F5 BF B9</Certificate>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">authenticateduser</Username>  
<EnableChunkedEncoding vt="11">-1</EnableChunkedEncoding>  
<UseProxy vt="11">-1</UseProxy>  
<ProxyName vt="8">proxyserver</ProxyName>  
<UseSSO vt="11">0</UseSSO>  
<Password vt="1" />  
<MaxRedirects vt="3">5</MaxRedirects>  
<ContentType vt="8">text/xml</ContentType>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
<UseHandlerSetting vt="11">0</UseHandlerSetting>  
</CustomProps>  
```