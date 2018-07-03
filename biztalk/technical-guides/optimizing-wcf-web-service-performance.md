---
title: 最佳化 WCF Web 服務效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93947cef-469c-4126-85a5-06456fa37443
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b0dc200135d65f179d565ba0fe03cc8df897eeb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999375"
---
# <a name="optimizing-wcf-web-service-performance"></a><span data-ttu-id="740f4-102">最佳化 WCF Web 服務效能</span><span class="sxs-lookup"><span data-stu-id="740f4-102">Optimizing WCF Web Service Performance</span></span>
<span data-ttu-id="740f4-103">WCF 服務公開多個會影響效能的組態參數。</span><span class="sxs-lookup"><span data-stu-id="740f4-103">WCF services expose numerous configuration parameters that affect performance.</span></span> <span data-ttu-id="740f4-104">本主題提供一般指導方針來設定這些組態參數，以改善效能的 WCF 服務的最佳值。</span><span class="sxs-lookup"><span data-stu-id="740f4-104">This topic provides general guidance for setting optimal values for these configuration parameters to improve performance of WCF services.</span></span>  
  
## <a name="implement-servicethrottling-behavior-for-backend-wcf-services"></a><span data-ttu-id="740f4-105">實作 serviceThrottling 行為的後端 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="740f4-105">Implement serviceThrottling behavior for backend WCF services</span></span>  
 <span data-ttu-id="740f4-106">實作後端 WCF 服務的 serviceThrottling 行為。</span><span class="sxs-lookup"><span data-stu-id="740f4-106">Implement serviceThrottling behavior for backend WCF services.</span></span> <span data-ttu-id="740f4-107">服務節流，可讓您以您的後端 WCF 伺服器上的負載平均，並強制執行資源配置。</span><span class="sxs-lookup"><span data-stu-id="740f4-107">Service throttling allows you to even out the load on your backend WCF servers and to enforce resource allocation.</span></span> <span data-ttu-id="740f4-108">藉由修改的值設定的後端 WCF 服務的 serviceThrottling 行為**maxConcurrentCalls**， **maxConcurrentSessions**，和**maxConcurrentInstances** WCF 服務組態檔中的參數。</span><span class="sxs-lookup"><span data-stu-id="740f4-108">serviceThrottling behavior for backend WCF services is configured by modifying the values for the **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** parameters in the config file for the WCF service.</span></span> <span data-ttu-id="740f4-109">設定**maxConcurrentCalls**， **maxConcurrentSessions**，和**maxConcurrentInstances**值大於 16 \* 數目的 Cpu 或 CPU 核心。</span><span class="sxs-lookup"><span data-stu-id="740f4-109">Set **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** to a value greater than 16 \* the number of CPUs or CPU cores.</span></span> <span data-ttu-id="740f4-110">例如，在具有 8 顆 CPU 核心的電腦，設定**maxConcurrentCalls**， **maxConcurrentSessions**，並**maxConcurrentInstances**大於 128 (16 \* 8 = 128) 的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="740f4-110">For example, on a computer with 8 CPU cores, set **maxConcurrentCalls**, **maxConcurrentSessions**, and **maxConcurrentInstances** to a value greater than 128 (16 \* 8 = 128) as follows:</span></span>  
  
```  
<serviceThrottling  
maxConcurrentCalls="200"  
maxConcurrentSessions="200"  
maxConcurrentInstances="200" />  
```  
  
## <a name="increase-the-default-values-for-the-nettcpbindinglistenbacklog-and-nettcpbindingmaxconnections-properties-in-the-backend-wcf-service-webconfig-file"></a><span data-ttu-id="740f4-111">增加後端 WCF 服務的 web.config 檔案中的 NetTcpBinding.ListenBacklog 」 和 「 NetTcpBinding.MaxConnections 屬性的預設值</span><span class="sxs-lookup"><span data-stu-id="740f4-111">Increase the default values for the NetTcpBinding.ListenBacklog and NetTcpBinding.MaxConnections properties in the backend WCF service web.config file</span></span>  
 <span data-ttu-id="740f4-112">**NetTcpBinding.ListenBacklog**屬性會控制可以擱置的佇列的連線要求的數目上限為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="740f4-112">The **NetTcpBinding.ListenBacklog** property controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="740f4-113">**NetTcpBinding.MaxConnections**屬性會控制用戶端後續重複使用共用連接的最大數目的允許在伺服器上暫止分派的連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="740f4-113">The **NetTcpBinding.MaxConnections** property controls the maximum number of connections to be pooled for subsequent reuse on the client and the maximum number of connections allowed to be pending dispatch on the server.</span></span> <span data-ttu-id="740f4-114">每個屬性會使用預設值是 10，這可能是次佳，特別是針對文件處理需要高輸送量的案例。</span><span class="sxs-lookup"><span data-stu-id="740f4-114">Each of these properties uses a default value of 10 which may be suboptimal, especially for document processing scenarios that require high throughput.</span></span>  
  
 <span data-ttu-id="740f4-115">請考慮增加高輸送量、 文件處理的情況下，使用 WCF 服務實作，這些屬性的預設值**netTcpBinding**繫結類別。</span><span class="sxs-lookup"><span data-stu-id="740f4-115">Consider increasing the default value of these properties for high-throughput, document-processing scenarios that use WCF services which implement the **netTcpBinding** binding class.</span></span>  
  
 <span data-ttu-id="740f4-116">在下列範例中，同時**listenBacklog**並**maxConnections**參數會設定為"200"的值。</span><span class="sxs-lookup"><span data-stu-id="740f4-116">In the following example, both the **listenBacklog** and **maxConnections** parameters are set to a value of “200”.</span></span>  
  
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
  
 <span data-ttu-id="740f4-117">如需有關 NetTcpBinding.ListenBacklog 屬性的詳細資訊，請參閱[NetTcpBinding.ListenBacklog 屬性](http://go.microsoft.com/fwlink/?LinkId=157752)(http://go.microsoft.com/fwlink/?LinkId=157752) MSDN 上。</span><span class="sxs-lookup"><span data-stu-id="740f4-117">For more information about the NetTcpBinding.ListenBacklog property, see [NetTcpBinding.ListenBacklog Property](http://go.microsoft.com/fwlink/?LinkId=157752) (http://go.microsoft.com/fwlink/?LinkId=157752) on MSDN.</span></span>  
  
 <span data-ttu-id="740f4-118">如需有關 NetTcpBinding.MaxConnections 屬性的詳細資訊，請參閱[NetTcpBinding.MaxConnections 屬性](http://go.microsoft.com/fwlink/?LinkID=157751)(http://go.microsoft.com/fwlink/?LinkID=157751) MSDN 上。</span><span class="sxs-lookup"><span data-stu-id="740f4-118">For more information about the NetTcpBinding.MaxConnections property, see [NetTcpBinding.MaxConnections Property](http://go.microsoft.com/fwlink/?LinkID=157751) (http://go.microsoft.com/fwlink/?LinkID=157751) on MSDN.</span></span>  
  
## <a name="eliminate-aspnet-httpmodules-that-are-not-required-to-run-wcf-web-services"></a><span data-ttu-id="740f4-119">排除不需要執行 WCF Web 服務的 ASP.NET httpModules</span><span class="sxs-lookup"><span data-stu-id="740f4-119">Eliminate ASP.NET httpModules that are not required to run WCF Web services</span></span>  
 <span data-ttu-id="740f4-120">根據預設，數個 ASP.NET httpModules 被定義在要求管線在 IIS 6.0 和傳統或整合式管線在 IIS 7.5/7.0 中。</span><span class="sxs-lookup"><span data-stu-id="740f4-120">By default, several ASP.NET httpModules are defined in the Request Pipeline in IIS 6.0 and in the Classic or Integrated Pipeline in IIS 7.5/7.0.</span></span> <span data-ttu-id="740f4-121">這些元件會攔截並處理所有的連入要求。</span><span class="sxs-lookup"><span data-stu-id="740f4-121">These components intercept and process all incoming requests.</span></span> <span data-ttu-id="740f4-122">包含在 %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG 資料夾中 32 位元 ASP.NET 應用程式，並在 64 位元 ASP %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG 資料夾中的 web.config 檔案中定義的預設模組。NET 應用程式，由下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="740f4-122">The default modules are defined in the web.config file contained in the %windir%\Microsoft.NET\Framework\v2.0.50727\CONFIG folder for 32-bit ASP.NET applications and in the %windir%\Microsoft.NET\Framework64\v2.0.50727\CONFIG folder for 64-bit ASP.NET applications, as shown by the following snippet.</span></span>  
  
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
  
 <span data-ttu-id="740f4-123">在大部分情況下不需要載入所有這些模組。</span><span class="sxs-lookup"><span data-stu-id="740f4-123">In most scenarios it is not necessary to load all of these modules.</span></span> <span data-ttu-id="740f4-124">因此，就可以藉由消除下列 httpModules，執行 WCF Web 服務時改善效能：</span><span class="sxs-lookup"><span data-stu-id="740f4-124">Therefore, it is possible to improve performance by eliminating the following httpModules when running WCF Web services:</span></span>  
  
-   <span data-ttu-id="740f4-125">Session</span><span class="sxs-lookup"><span data-stu-id="740f4-125">Session</span></span>  
  
-   <span data-ttu-id="740f4-126">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="740f4-126">WindowsAuthentication</span></span>  
  
-   <span data-ttu-id="740f4-127">FormsAuthentication</span><span class="sxs-lookup"><span data-stu-id="740f4-127">FormsAuthentication</span></span>  
  
-   <span data-ttu-id="740f4-128">PassportAuthentication</span><span class="sxs-lookup"><span data-stu-id="740f4-128">PassportAuthentication</span></span>  
  
-   <span data-ttu-id="740f4-129">RoleManager</span><span class="sxs-lookup"><span data-stu-id="740f4-129">RoleManager</span></span>  
  
-   <span data-ttu-id="740f4-130">AnonymousIdentification</span><span class="sxs-lookup"><span data-stu-id="740f4-130">AnonymousIdentification</span></span>  
  
-   <span data-ttu-id="740f4-131">設定檔</span><span class="sxs-lookup"><span data-stu-id="740f4-131">Profile</span></span>  
  
## <a name="use-the-wcf-modulehandler-registration-tool-to-configure-wcf-moduleshandlers-and-improve-scalability-of-iis-7570-hosted-wcf-services"></a><span data-ttu-id="740f4-132">使用 WCF 模組/處理常式註冊工具，以設定 WCF 模組/處理常式，並改善延展性的 IIS 7.5/7.0 中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="740f4-132">Use the WCF Module/Handler Registration tool to configure WCF modules/handlers and improve scalability of IIS 7.5/7.0 hosted WCF services</span></span>  
 <span data-ttu-id="740f4-133">WCF 模組/處理常式註冊工具可供下載： [ http://go.microsoft.com/fwlink/?LinkId=157593 ](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593)。</span><span class="sxs-lookup"><span data-stu-id="740f4-133">The WCF Module/Handler Registration Tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=157593](http://go.microsoft.com/fwlink/?LinkId=157593) (http://go.microsoft.com/fwlink/?LinkId=157593).</span></span> <span data-ttu-id="740f4-134">此公用程式可用來安裝，清單中，或設定下列 WCF 模組：</span><span class="sxs-lookup"><span data-stu-id="740f4-134">This utility can be used to install, list, or configure the following WCF modules:</span></span>  
  
- <span data-ttu-id="740f4-135">WCF 的同步 HTTP 模組和處理常式</span><span class="sxs-lookup"><span data-stu-id="740f4-135">WCF Synchronous HTTP module and handler</span></span>  
  
- <span data-ttu-id="740f4-136">WCF 的非同步 HTTP 模組和處理常式</span><span class="sxs-lookup"><span data-stu-id="740f4-136">WCF Asynchronous HTTP module and handler</span></span>  
  
- <span data-ttu-id="740f4-137">WCF HTTP 模組和處理常式</span><span class="sxs-lookup"><span data-stu-id="740f4-137">WCF HTTP module and handler</span></span>  
  
  <span data-ttu-id="740f4-138">如需有關使用非同步 WCF HTTP 模組/處理常式來改善延展性的 IIS 7.5/7.0 中裝載 WCF 服務，請參閱 Wenlong 盾部落格[Orcas SP1 改進： 非同步 WCF HTTP 模組/處理常式以便更妥善的 IIS7伺服器延展性](http://go.microsoft.com/fwlink/?LinkId=157428)(http://go.microsoft.com/fwlink/?LinkId=157428)。</span><span class="sxs-lookup"><span data-stu-id="740f4-138">For more information about using the asynchronous WCF HTTP modules/handlers to improve the scalability of IIS 7.5/7.0 hosted WCF services, see Wenlong Dong’s blog [Orcas SP1 Improvement: Asynchronous WCF HTTP Module/Handler for IIS7 for Better Server Scalability](http://go.microsoft.com/fwlink/?LinkId=157428) (http://go.microsoft.com/fwlink/?LinkId=157428).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740f4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="740f4-139">See Also</span></span>  
 [<span data-ttu-id="740f4-140">最佳化 BizTalk Server WCF 配接器效能</span><span class="sxs-lookup"><span data-stu-id="740f4-140">Optimizing BizTalk Server WCF Adapter Performance</span></span>](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)