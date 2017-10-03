---
title: "SOAP 配接器組態屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, send ports
- SOAP adapters, code samples
- SOAP adapters, properties
- receive locations, adapters
- SOAP adapters, receive locations
- send ports, adapters
ms.assetid: 0d033371-ee31-4e43-a7d3-e0975791d981
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52fde9d80717d192d3a5b90548ccc01e87d2044
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-configuration-properties"></a>SOAP 配接器組態屬性
下表列出可為 SOAP 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|UseSSO|VT_BOOL|指定是否要使用「單一登入」。|無效的值為：<br />--1 (true)<br />-0 (false)|預設值為 0 (false)。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<UseSSO vt="11">0</UseSSO>  
</CustomProps>  
```  
  
 下表列出可為 SOAP 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|指定此傳送埠的 Proxy 伺服器連接埠。|無|除非 UseProxy 屬性設定為 -1 (true)，否則此屬性不需要值。<br /><br /> 預設值是 80。|  
|AuthenticationScheme|VT_BSTR|指定要提供給目的地伺服器的驗證類型。|有效值為：<br /><br /> 匿名<br />-基本<br />摘要<br />-NTLM|預設值為「匿名」。|  
|使用者名稱|VT_BSTR|指定要用於目的地伺服器驗證的使用者名稱。|最小長度：00<br /><br /> 最大長度：256|除非 AuthenticationScheme 屬性的值設定為「基本」或「摘要」，且 UseSSO 屬性設定為 0 (false)，否則此屬性不需要值。|  
|UseProxy|VT_BOOL|指定 SOAP 傳送處理常式是否要使用 Proxy 伺服器。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|UseSoap12|VT_BOOL|指定產生支援 SOAP 1.2 通訊協定的 Proxy 程式碼。|若未選取此選項，則會產生 SOAP 1.1 相容的 Proxy 程式碼。<br /><br /> 有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|UsingOrchestration|VT_BOOL|指定是否要使用與此傳送埠位址相關聯的 Web 服務 Proxy。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 -1 (true)。|  
|UseSSO|VT_BOOL|指定使用「企業單一登入」。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|ProxyAddress|VT_BSTR|指定 Proxy 伺服器的名稱。|此屬性只有在 UseProxy 屬性設定為 -1 (true) 時才有效。|無|  
|密碼|VT_NULL|指定要用於目的地伺服器驗證的密碼。|當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|除非 AuthenticationScheme 屬性的值設定為「基本」或「摘要」，且 UseSSO 屬性設定為 0 (false)，否則此屬性不需要值。|  
|AssemblyPath|VT_BSTR|指定包含 Web 服務 Proxy 的組件路徑。|無|無|  
|TypeName|VT_BSTR|指定包含要叫用的 Web 方法的類別名稱。|無|無|  
|MethodName|VT_BSTR|指定將要叫用之類別的方法。|無|無|  
|UseHandlerSetting|VT_BOOL|指定是否要使用 SOAP 傳送處理常式的預設 Proxy 組態。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 -1 (true)。|  
|ClientCertificate|VT_BSTR|指定要用來建立連線的用戶端憑證指紋。|最小長度：00<br /><br /> 最大長度： 59|無|  
|ProxyPassword|VT_NULL|指定要用於 Proxy 伺服器驗證的密碼。|當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|如果 UseProxy 設定為 0 (false)，則此屬性不需要值。|  
|ProxyUsername|VT_BSTR|指定要用於 Proxy 伺服器驗證的使用者名稱。|無|除非 UseProxy 屬性設定為 -1 (true)，否則此屬性不需要值。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">domain\testuser</Username>  
<UseProxy vt="11">-1</UseProxy>  
<UseSoap12 vt="11">-1</UseSoap12>  
<UsingOrchestration vt="11">-1</UsingOrchestration>  
<UseSSO vt="11">0</UseSSO>  
<ProxyAddress vt="8">proxy</ProxyAddress>  
<Password vt="1" />  
<ProxyPort vt="3">80</ProxyPort>  
<AssemblyPath vt="8">C:\Websvc.dll</AssemblyPath>  
<TypeName vt="8">Websvc.svc</TypeName>  
<MethodName vt="8">WebMethod</MethodName>  
<UseHandlerSetting vt="11">0</UseHandlerSetting></  
<ClientCertificate vt="8">23779A5EEA9693A37409021EFCDAB713A3680C34</ClientCertificate>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
</CustomProps>  
```