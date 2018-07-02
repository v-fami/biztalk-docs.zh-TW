---
title: 設定協調流程的遠端偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Microsoft.XLANGs.BizTalk.Client.dll.config, code sample
- BTSNTSvc.exe.config, code sample
- orchestrations, debugging
- building, debugging
- building, code sample
ms.assetid: 722efaec-d160-48dc-b94b-0733c9904d98
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f5d28c13cb9da4454efcad1a43a4048c8881ea8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967287"
---
# <a name="configuring-remote-debugging-for-orchestrations"></a>設定協調流程的遠端偵錯
您可以完整設定用戶端和伺服器之間的遠端偵錯。 用戶端組態是在 Microsoft.XLANGs.BizTalk.Client.dll.config 中指定。BTSNTSvc.exe.config 中指定的伺服器組態。以下是每個預設組態的清單。  
  
## <a name="client-microsoftxlangsbiztalkclientdllconfig"></a>用戶端 (Microsoft.XLANGs.BizTalk.Client.dll.config)  
  
```  
<configuration>  
     <system.runtime.remoting>  
  
 <channelSinkProviders>  
       <clientProviders>  
         <provider id="sspi" type="Microsoft.BizTalk.XLANGs.Client.SecurityClientChannelSinkProvider,Microsoft.XLANGs.BizTalk.Client" securityPackage="negotiate" authenticationLevel="packetPrivacy"/>  
       </clientProviders>  
</channelSinkProviders>  
  
<application>  
<channels>  
    <channel ref="tcp" port="0" name="">  
       <clientProviders>  
             <formatter ref="binary"/>  
             <provider ref="sspi" />  
        </clientProviders>  
       <serverProviders>  
             <formatter ref="binary" typeFilterLevel="Full"/>  
       </serverProviders>  
    </channel>  
</channels>  
</application>  
  </system.runtime.remoting>  
</configuration>  
```  
  
## <a name="serverbtsntsvcexeconfig"></a>伺服器 (BTSNTSvc.exe.config)  
  
```  
<?xml version="1.0" ?>  
<configuration>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
            <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking;Tracking\interop" />  
        </assemblyBinding>  
    </runtime>  
  
    <system.runtime.remoting>  
  
        <channelSinkProviders>  
            <serverProviders>  
                <provider id="sspi" type="Microsoft.BizTalk.XLANGs.BTXEngine.SecurityServerChannelSinkProvider,Microsoft.XLANGs.BizTalk.Engine" securityPackage="ntlm" authenticationLevel="packetPrivacy" />  
            </serverProviders>  
        </channelSinkProviders>  
  
        <application>  
            <channels>  
                <channel ref="tcp" port="0" name="">  
                <serverProviders>  
                    <provider ref="sspi" />  
                        <formatter ref="binary" typeFilterLevel="Full"/>  
                    </serverProviders>  
                </channel>  
            </channels>  
        </application>  
    </system.runtime.remoting>  
  
</configuration>  
```  
  
## <a name="configurable-parameters"></a>可設定的參數  
 預設組態可確保最高安全性。 不過，使用者可以變更這些預設組態，而且由於這些檔案位在 [Program Files] 資料夾內，所以它們會登錄在 ACL 中。  
  
 項目\<提供者 / > 是選擇性的如果未提供，會讓通道不會使用自訂接收器相互驗證。 但是，關閉這個選項很危險，因為這會開啟通道。 為了更好的效能，並且安全攻擊不成問題時，可以這樣做。  
  
 channel 項目可設定屬性 rejectRemoteRequests = true，這只會啟用區域呼叫並拒絕遠端要求。  
  
 中的 securityPackage 屬性\<s / > 項目可以有下列值之一：  
  
- negotiate  
  
- ntlm  
  
- Kerberos  
  
  中的 authenticationLevel 屬性\<s / > 項目可以有下列值之一：  
  
- packetPrivacy  - 訊息會加密/解密  
  
- packetIntegrity – 訊息會經過簽署/驗證  
  
- call  - 訊息會以原始格式傳送  
  
  中的 ref 屬性\<通道 / > 項目可以變更為 tcp 或 http。 中的屬性名稱與連接埠\<通道 / > 項目可以變更以及明確的值。  
  
  如需詳細資訊，請參閱《.NET Framework 開發人員手冊》(通道和格式子組態屬性)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯協調流程](../core/debugging-orchestrations.md)