---
title: 設定遠端偵錯的協調流程 |Microsoft 文件
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
ms.openlocfilehash: 4184b82efccd0ab2dcc2b871b6389b28148754c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233406"
---
# <a name="configuring-remote-debugging-for-orchestrations"></a><span data-ttu-id="9a28e-102">設定協調流程的遠端偵錯</span><span class="sxs-lookup"><span data-stu-id="9a28e-102">Configuring Remote Debugging for Orchestrations</span></span>
<span data-ttu-id="9a28e-103">您可以完整設定用戶端和伺服器之間的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="9a28e-103">You can completely configure remote debugging between client and server.</span></span> <span data-ttu-id="9a28e-104">Microsoft.XLANGs.BizTalk.Client.dll.config 中指定的用戶端組態。BTSNTSvc.exe.config 中指定的伺服器組態。以下是每個預設組態的清單。</span><span class="sxs-lookup"><span data-stu-id="9a28e-104">The client configuration is specified in Microsoft.XLANGs.BizTalk.Client.dll.config. The server configuration is specified in BTSNTSvc.exe.config. The following is a listing of the default configuration for each.</span></span>  
  
## <a name="client-microsoftxlangsbiztalkclientdllconfig"></a><span data-ttu-id="9a28e-105">用戶端 (Microsoft.XLANGs.BizTalk.Client.dll.config)</span><span class="sxs-lookup"><span data-stu-id="9a28e-105">Client (Microsoft.XLANGs.BizTalk.Client.dll.config)</span></span>  
  
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
  
## <a name="serverbtsntsvcexeconfig"></a><span data-ttu-id="9a28e-106">伺服器 (BTSNTSvc.exe.config)</span><span class="sxs-lookup"><span data-stu-id="9a28e-106">Server(BTSNTSvc.exe.config)</span></span>  
  
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
  
## <a name="configurable-parameters"></a><span data-ttu-id="9a28e-107">可設定的參數</span><span class="sxs-lookup"><span data-stu-id="9a28e-107">Configurable Parameters</span></span>  
 <span data-ttu-id="9a28e-108">預設組態可確保最高安全性。</span><span class="sxs-lookup"><span data-stu-id="9a28e-108">The default ensures maximum security configuration.</span></span> <span data-ttu-id="9a28e-109">不過，使用者可以變更這些預設組態，而且由於這些檔案位在 [Program Files] 資料夾內，所以它們會登錄在 ACL 中。</span><span class="sxs-lookup"><span data-stu-id="9a28e-109">However it is left to the user to change these defaults and these files are ACL'ed since they are in the program files folder.</span></span>  
  
 <span data-ttu-id="9a28e-110">項目\<提供者 / > 是選擇性的如果未提供，會讓通道不會使用自訂接收器相互驗證。</span><span class="sxs-lookup"><span data-stu-id="9a28e-110">The element \<provider/> is optional and if not provided will cause the channels not to be mutually authenticated using the custom sinks.</span></span> <span data-ttu-id="9a28e-111">但是，關閉這個選項很危險，因為這會開啟通道。</span><span class="sxs-lookup"><span data-stu-id="9a28e-111">However this is a dangerous option to turn off as it will open up the channels.</span></span> <span data-ttu-id="9a28e-112">為了更好的效能，並且安全攻擊不成問題時，可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="9a28e-112">This can be done for better performance and when security attacks are not a concern.</span></span>  
  
 <span data-ttu-id="9a28e-113">channel 項目可設定屬性 rejectRemoteRequests = true，這只會啟用區域呼叫並拒絕遠端要求。</span><span class="sxs-lookup"><span data-stu-id="9a28e-113">The channel element can have property rejectRemoteRequests = true which will enable only local calls and reject remote requests.</span></span>  
  
 <span data-ttu-id="9a28e-114">中的 securityPackage 屬性\<s / > 項目可以有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="9a28e-114">The securityPackage attribute in the \<serverProviders/> element can have any of the following values:</span></span>  
  
-   <span data-ttu-id="9a28e-115">negotiate</span><span class="sxs-lookup"><span data-stu-id="9a28e-115">negotiate</span></span>  
  
-   <span data-ttu-id="9a28e-116">ntlm</span><span class="sxs-lookup"><span data-stu-id="9a28e-116">ntlm</span></span>  
  
-   <span data-ttu-id="9a28e-117">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9a28e-117">Kerberos</span></span>  
  
 <span data-ttu-id="9a28e-118">中的 authenticationLevel 屬性\<s / > 項目可以有下列值之一：</span><span class="sxs-lookup"><span data-stu-id="9a28e-118">The authenticationLevel attribute in the \<serverProviders/> element can have any of the following values:</span></span>  
  
-   <span data-ttu-id="9a28e-119">packetPrivacy  - 訊息會加密/解密</span><span class="sxs-lookup"><span data-stu-id="9a28e-119">packetPrivacy  - the messages will be encrypted/decrypted</span></span>  
  
-   <span data-ttu-id="9a28e-120">packetIntegrity – 訊息會經過簽署/驗證</span><span class="sxs-lookup"><span data-stu-id="9a28e-120">packetIntegrity – the messages will be signed/verified</span></span>  
  
-   <span data-ttu-id="9a28e-121">call  - 訊息會以原始格式傳送</span><span class="sxs-lookup"><span data-stu-id="9a28e-121">call  - the messages will be sent as is</span></span>  
  
 <span data-ttu-id="9a28e-122">中的 ref 屬性\<通道 / > 項目可以變更為 tcp 或 http。</span><span class="sxs-lookup"><span data-stu-id="9a28e-122">The ref attribute in the \<channel/> element can be changed to tcp or http.</span></span> <span data-ttu-id="9a28e-123">中的屬性名稱與連接埠\<通道 / > 項目可以變更以及明確的值。</span><span class="sxs-lookup"><span data-stu-id="9a28e-123">The port and name attribute in the \<channel/> element can be changed as well to explicit values.</span></span>  
  
 <span data-ttu-id="9a28e-124">如需詳細資訊，請參閱《.NET Framework 開發人員手冊》(通道和格式子組態屬性)。</span><span class="sxs-lookup"><span data-stu-id="9a28e-124">For more information, see .NET Framework Developer's Guide (Channel and formatter configuration properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a28e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a28e-125">See Also</span></span>  
 [<span data-ttu-id="9a28e-126">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="9a28e-126">Debugging Orchestrations</span></span>](../core/debugging-orchestrations.md)