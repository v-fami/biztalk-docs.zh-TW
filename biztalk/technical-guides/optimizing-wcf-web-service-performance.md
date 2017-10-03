---
title: "WCF Web 服務效能最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93947cef-469c-4126-85a5-06456fa37443
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 413642931fcf9580ade280c2e7b3472599859d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-wcf-web-service-performance"></a>WCF Web 服務效能最佳化
WCF 服務會公開多個會影響效能的組態參數。 本主題提供一般指導方針設定這些組態參數，以改善效能的 WCF 服務的最佳值。  
  
## <a name="implement-servicethrottling-behavior-for-backend-wcf-services"></a>後端 WCF 服務的實作 serviceThrottling 行為  
 實作 serviceThrottling 後端 WCF 服務的行為。 節流的服務可讓您以您的後端 WCF 伺服器上的負載平均和強制執行資源配置。 藉由修改的值設定後端 WCF 服務的 serviceThrottling 行為**maxConcurrentCalls**， **maxConcurrentSessions**，和**maxConcurrentInstances** WCF 服務組態檔中的參數。 設定**maxConcurrentCalls**， **maxConcurrentSessions**，和**maxConcurrentInstances**值大於 16 * 數目的 Cpu 或 CPU 核心。 例如，在具有 8 顆 CPU 核心的電腦，設定**maxConcurrentCalls**， **maxConcurrentSessions**，和**maxConcurrentInstances**大於 128 (16 * 8 = 128) 值如下所示：  
  
```  
<serviceThrottling  
maxConcurrentCalls="200"  
maxConcurrentSessions="200"  
maxConcurrentInstances="200" />  
```  
  
## <a name="increase-the-default-values-for-the-nettcpbindinglistenbacklog-and-nettcpbindingmaxconnections-properties-in-the-backend-wcf-service-webconfig-file"></a>增加 NetTcpBinding.ListenBacklog 和 NetTcpBinding.MaxConnections 屬性的後端 WCF 服務的 web.config 檔案中的預設值  
 **NetTcpBinding.ListenBacklog**屬性會控制可以擱置之佇列的連線要求的數目上限為 Web 服務。 **NetTcpBinding.MaxConnections**屬性會控制在用戶端後續重複使用的共用連接數量上限，以及允許在伺服器上暫止分派的連線數目上限。 每個屬性會使用預設值是 10，可能是次佳，特別是針對文件處理需要高輸送量的案例。  
  
 請考慮增加針對高輸送量、 文件處理的案例，使用 WCF 服務實作這些屬性的預設值**netTcpBinding**繫結類別。  
  
 在下列範例中，同時**listenBacklog**和**maxConnections**參數已設為"200"的值。  
  
```  
<netTcpBinding>  
   <binding name="netTcpBinding"  
      closeTimeout="00:10:00"  
      openTimeout="00:10:00"  
      receiveTimeout="00:10:00"  
      sendTimeout="00:10:00"  
      transactionFlow="false"  
      transferMode="Buffered"  
      transactionProtocol="OleTransactions"  
      hostNameComparisonMode="StrongWildcard"  
      listenBacklog="200"  
      maxBufferPoolSize="1048576"  
      maxBufferSize="10485760"  
      maxConnections="200"  
      maxReceivedMessageSize="10485760">  
      <readerQuotas  
         maxDepth="32"  
         maxStringContentLength="8192"  
         maxArrayLength="16384"  
         maxBytesPerRead="4096"  
         maxNameTableCharCount="16384" />  
      <reliableSession  
         ordered="true"  
         inactivityTimeout="00:10:00"  
         enabled="false" />  
      <security mode="None">  
         <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
         <message clientCredentialType="Windows" />  
      </security>  
   </binding>  
</netTcpBinding>  
```  
  
 如需 NetTcpBinding.ListenBacklog 屬性的詳細資訊，請參閱[NetTcpBinding.ListenBacklog 屬性](http://go.microsoft.com/fwlink/?LinkId=157752)(http://go.microsoft.com/fwlink/?LinkId=157752) MSDN 上。  
  
 如需 NetTcpBinding.MaxConnections 屬性的詳細資訊，請參閱[NetTcpBinding.MaxConnections 屬性](http://go.microsoft.com/fwlink/?LinkID=157751)(http://go.microsoft.com/fwlink/?LinkID=157751) MSDN 上。  
  
## <a name="eliminate-aspnet-httpmodules-that-are-not-required-to-run-wcf-web-services"></a>排除不需要執行 WCF Web 服務的 ASP.NET httpModules  
 根據預設，在 IIS 6.0 和傳統 」 或 「 整合式管線 IIS 7.5/7.0 中要求管線中定義數個 ASP.NET httpmodules 進行。 這些元件會攔截並處理所有連入要求。 預設的模組所包含的 32 位元 ASP.NET 應用程式的 %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG 資料夾中，在 64 位元 ASP %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG 資料夾中的 web.config 檔案中定義。NET 應用程式，由下列程式碼片段所示。  
  
```  
<httpModules>  
<add name="OutputCache" type="System.Web.Caching.OutputCacheModule"/>  
<add name="Session" type="System.Web.SessionState.SessionStateModule"/>  
<add name="WindowsAuthentication" type="System.Web.Security.WindowsAuthenticationModule"/>  
<add name="FormsAuthentication" type="System.Web.Security.FormsAuthenticationModule"/>  
<add name="PassportAuthentication" type="System.Web.Security.PassportAuthenticationModule"/>  
<add name="RoleManager" type="System.Web.Security.RoleManagerModule"/>  
<add name="UrlAuthorization" type="System.Web.Security.UrlAuthorizationModule"/>  
<add name="FileAuthorization" type="System.Web.Security.FileAuthorizationModule"/>  
<add name="AnonymousIdentification" type="System.Web.Security.AnonymousIdentificationModule"/>  
<add name="Profile" type="System.Web.Profile.ProfileModule"/>  
<add name="ErrorHandlerModule" type="System.Web.Mobile.ErrorHandlerModule, System.Web.Mobile, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
<add name="ServiceModel" type="System.ServiceModel.Activation.HttpModule, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
</httpModules>  
```  
  
 在大部分情況下不需要載入這些模組的所有。 因此，就可以藉由執行 WCF Web 服務時，排除下列 httpModules 改善效能：  
  
-   Session  
  
-   Windows 驗證  
  
-   FormsAuthentication  
  
-   PassportAuthentication  
  
-   RoleManager  
  
-   AnonymousIdentification  
  
-   設定檔  
  
## <a name="use-the-wcf-modulehandler-registration-tool-to-configure-wcf-moduleshandlers-and-improve-scalability-of-iis-7570-hosted-wcf-services"></a>使用 WCF 模組/處理常式註冊工具，以設定 WCF 模組處理常式，並改善延展性的 IIS 7.5/7.0 中裝載 WCF 服務  
 WCF 的模組/處理常式註冊工具是下載[http://go.microsoft.com/fwlink/?LinkId=157593](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593)。 此公用程式可用來安裝，清單中，或設定下列 WCF 模組：  
  
-   WCF 的同步 HTTP 模組和處理常式  
  
-   WCF 的非同步 HTTP 模組和處理常式  
  
-   WCF HTTP 模組和處理常式  
  
 如需提升可調適性的 IIS 7.5/7.0 中使用非同步 WCF HTTP 模組/處理常式的詳細資訊裝載 WCF 服務，請參閱 < Wenlong 同部落格[Orcas SP1 改進： 非同步 WCF HTTP 模組/處理常式是好的 iis7伺服器延展性](http://go.microsoft.com/fwlink/?LinkId=157428)(http://go.microsoft.com/fwlink/?LinkId=157428)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server WCF 配接器效能最佳化](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)