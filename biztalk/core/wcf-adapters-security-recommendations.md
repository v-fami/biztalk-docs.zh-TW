---
title: "WCF 配接器安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF adapters, security
- security, WCF adapters
ms.assetid: bbaaca56-9ad5-4122-a8e9-6e975d308230
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ea0334e2d6164091e54321de8e1dccab5c07bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapters-security-recommendations"></a><span data-ttu-id="b65c1-102">WCF 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="b65c1-102">WCF Adapters Security Recommendations</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b65c1-103"> 會使用 WCF 配接器來發佈 (接收) 和使用 (傳送) WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b65c1-103"> uses the WCF adapters to publish (receive) and consume (send) WCF services.</span></span> <span data-ttu-id="b65c1-104">建議您依照這些指導方針來保護和部署您作業環境中的 WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="b65c1-104">We recommend that you follow these guidelines for securing and deploying the WCF adapters in your environment.</span></span>  
  
 <span data-ttu-id="b65c1-105">如需 WCF 配接器的詳細資訊，請參閱[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-105">For more information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md).</span></span> <span data-ttu-id="b65c1-106">如需有關 WCF 服務的詳細資訊，請參閱[使用 WCF 服務](../core/using-wcf-services.md)s。</span><span class="sxs-lookup"><span data-stu-id="b65c1-106">For more information about WCF services, see [Using WCF Services](../core/using-wcf-services.md)s.</span></span>  
  
## <a name="security-recommendations-for-all-wcf-adapters"></a><span data-ttu-id="b65c1-107">針對所有 WCF 配接器的安全性建議</span><span class="sxs-lookup"><span data-stu-id="b65c1-107">Security Recommendations for All WCF Adapters</span></span>  
  
-   <span data-ttu-id="b65c1-108">您可以在需要將前端使用者的內容對應到後端系統之認證的實例中，使用「企業單一登入」(SSO)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-108">You can use Enterprise Single Sign-On (SSO) in scenarios where you need to map the content of the front-end user to credentials in a back-end system.</span></span>  
  
-   <span data-ttu-id="b65c1-109">並非所有的服務都必須發佈中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b65c1-109">Not all services must publish metadata.</span></span> <span data-ttu-id="b65c1-110">停用中繼資料發佈功能，可減少服務的攻擊面並降低無意間洩漏資訊的風險。</span><span class="sxs-lookup"><span data-stu-id="b65c1-110">Leaving metadata publishing disabled reduces the attack surface for your service and lowers the risk of unintentional information disclosure.</span></span> <span data-ttu-id="b65c1-111">中繼資料的相關安全性問題的詳細資訊，請參閱 「 安全性考量與中繼資料 」，網址[http://go.microsoft.com/fwlink/?LinkId=196671](http://go.microsoft.com/fwlink/?LinkId=196671)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-111">For more information about security issues related to metadata, see "Security Considerations with Metadata" at [http://go.microsoft.com/fwlink/?LinkId=196671](http://go.microsoft.com/fwlink/?LinkId=196671).</span></span>  
  
-   <span data-ttu-id="b65c1-112">並非所有中繼資料端點繫結和服務端點繫結的組合都有效。</span><span class="sxs-lookup"><span data-stu-id="b65c1-112">Not all combinations of metadata endpoint bindings and service endpoint bindings are valid.</span></span> <span data-ttu-id="b65c1-113">在某些狀況下，中繼資料端點的繫結組態必須與其服務端點的繫結組態一致。</span><span class="sxs-lookup"><span data-stu-id="b65c1-113">In some cases, the binding configurations for a metadata endpoint must be in agreement with the binding configurations of its service endpoint.</span></span> <span data-ttu-id="b65c1-114">例如，提供中繼資料的位置與接收位置相同時，如果接收位置使用依賴 HTTPS 的安全性模式，則中繼資料端點便無法設定為使用要求 HTTP 傳輸的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="b65c1-114">For example, when metadata is served from the same location as the receive location, the metadata endpoint cannot be configured with a security mode requiring the HTTP transport if the receive location uses a security mode that relies on HTTPS.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b65c1-115">透過使用相同位置但所需的安全性模式依賴 HTTPS 傳輸，會產生 「 BizTalk WCF 發佈精靈 」，在 Web.config 檔案中的服務端點的 HTTP 傳輸發佈中繼資料時您必須設定兩個**httpsGetEnabled**和**httpGetEnabled**屬性至**true**。</span><span class="sxs-lookup"><span data-stu-id="b65c1-115">When publishing metadata through the HTTP transport for a service endpoint with the same location but requiring a security mode that relies on the HTTPS transport, in the Web.config file that the BizTalk WCF Publishing Wizard generates, you must set both of the **httpsGetEnabled** and **httpGetEnabled** attributes to **true**.</span></span>  
  
-   <span data-ttu-id="b65c1-116">WCF 配接器會運用 Windows Communication Foundation (WCF) 的安全性功能來通訊。</span><span class="sxs-lookup"><span data-stu-id="b65c1-116">The WCF adapters leverage the security features of Windows Communication Foundation (WCF) to communicate.</span></span> <span data-ttu-id="b65c1-117">因此，瞭解 WCF 安全性功能和限制很重要。</span><span class="sxs-lookup"><span data-stu-id="b65c1-117">It is important to understand the capabilities and limitations of WCF in terms of security.</span></span> <span data-ttu-id="b65c1-118">WCF 的安全性功能的相關詳細資訊，請參閱 < Windows Communication Foundation 安全性 >，網址[http://go.microsoft.com/fwlink/?LinkId=87806](http://go.microsoft.com/fwlink/?LinkId=87806)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-118">For more information about the security features of WCF, see "Windows Communication Foundation Security" at [http://go.microsoft.com/fwlink/?LinkId=87806](http://go.microsoft.com/fwlink/?LinkId=87806).</span></span>  
  
## <a name="security-recommendations-for-the-isolated-wcf-adapters"></a><span data-ttu-id="b65c1-119">外掛式 WCF 配接器的安全性建議</span><span class="sxs-lookup"><span data-stu-id="b65c1-119">Security Recommendations for the Isolated WCF Adapters</span></span>  
  
-   <span data-ttu-id="b65c1-120">如需發佈 Web 服務的安全性建議，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-120">For security recommendations for publishing Web services, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
-   <span data-ttu-id="b65c1-121">外掛式 WCF 配接器 (例如 WCF-CustomIsolated、WCF-BasicHttp 和 WCF-WSHttp 配接器) 會利用「超文字傳輸通訊協定」(HTTP)，將訊息傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並從中接收訊息。</span><span class="sxs-lookup"><span data-stu-id="b65c1-121">The isolated WCF adapters such as the WCF-CustomIsolated, WCF-BasicHttp, and WCF-WSHttp adapters leverage the Hypertext Transfer Protocol (HTTP) to send and receive messages to and from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b65c1-122">因此，您必須遵循安全性建議來保護 Internet Information Services (IIS) 的安全。</span><span class="sxs-lookup"><span data-stu-id="b65c1-122">Therefore, you must follow the security recommendations for securing Internet Information Services (IIS).</span></span>  
  
-   <span data-ttu-id="b65c1-123">當您為外掛式 WCF 接收位置建立應用程式集區時，必須將它設定為在下列帳戶下執行：屬於執行 WCF 接收配接器的外掛式主控件之 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 群組以及「Internet Information Services 工作者處理序」群組 (IIS_WPG 群組) 的成員。</span><span class="sxs-lookup"><span data-stu-id="b65c1-123">When you create an application pool for an isolated WCF receive location, you must configure it to run under an account that is a member of the [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] group for the isolated host running the WCF receive adapter and the Internet Information Services Worker Process group (IIS_WPG group).</span></span> <span data-ttu-id="b65c1-124">接著您必須設定 WCF 接收配接器的主控件執行個體，才能使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="b65c1-124">You must then configure the host instance for the WCF receive adapter to use this account.</span></span> <span data-ttu-id="b65c1-125">若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="b65c1-125">If you change the account for the IIS_WPG group, you must ensure that you also update the host instance to run under the new account.</span></span>  
  
## <a name="security-recommendations-for-the-wcf-custom-adapter"></a><span data-ttu-id="b65c1-126">WCF-Custom 配接器的安全性建議</span><span class="sxs-lookup"><span data-stu-id="b65c1-126">Security Recommendations for the WCF-Custom Adapter</span></span>  
  
-   <span data-ttu-id="b65c1-127">如果 Wcf-custom 接收位置使用 HTTP 核心模式驅動程式 (HTTP.sys)，例如**httpsTransport**進行安全通訊端層 (SSL) 通訊，接收位置繫結項目必須有憑證針對每個通訊端 （IP 位址/連接埠組合） 登錄。</span><span class="sxs-lookup"><span data-stu-id="b65c1-127">If a WCF-Custom receive location happens to use the HTTP kernel-mode driver (HTTP.sys) such as the **httpsTransport** binding element for Secure Sockets Layer (SSL) communications, the receive location must have a certificate registered for each socket (IP address/port combination).</span></span> <span data-ttu-id="b65c1-128">請使用 HttpCfg.exe 工具將 SSL 憑證繫結到電腦上的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b65c1-128">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the computer.</span></span> <span data-ttu-id="b65c1-129">如需詳細資訊，請參閱 「 如何以:: 設定連接埠使用 SSL 憑證 」 在[http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-129">For more information, see "How To: Configure a Port with An SSL Certificate" at [http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384).</span></span>  
  
## <a name="security-recommendations-for-the-wcf-netmsmq-adapter"></a><span data-ttu-id="b65c1-130">WCF-NetMsmq 配接器的安全性建議</span><span class="sxs-lookup"><span data-stu-id="b65c1-130">Security Recommendations for the WCF-NetMsmq Adapter</span></span>  
  
-   <span data-ttu-id="b65c1-131">若要使用 Wcf-netmsmq 配接器，您必須針對相同的方式設定 Wcf-netmsmq 配接器的 MSMQ 安全性設定[netMsmqBinding](http://go.microsoft.com/fwlink/?LinkId=87813)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-131">To use the WCF-NetMsmq adapter, you have to configure MSMQ security settings for the WCF-NetMsmq adapter in the same way as for the [netMsmqBinding](http://go.microsoft.com/fwlink/?LinkId=87813).</span></span> <span data-ttu-id="b65c1-132">如需有關如何設定 MSMQ 安全性設定**netMsmqBinding**，請參閱 < 佇列訊息疑難排解" [http://go.microsoft.com/fwlink/?LinkId=87816](http://go.microsoft.com/fwlink/?LinkId=87816)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-132">For more information about how to configure MSMQ security settings for the **netMsmqBinding**, see "Troubleshooting Queued Messaging" at [http://go.microsoft.com/fwlink/?LinkId=87816](http://go.microsoft.com/fwlink/?LinkId=87816).</span></span>  
  
## <a name="wcf-adapters-use-the-chaintrust-mode-to-validate-certificates"></a><span data-ttu-id="b65c1-133">WCF 配接器會使用 ChainTrust 模式來驗證憑證</span><span class="sxs-lookup"><span data-stu-id="b65c1-133">WCF Adapters Use the ChainTrust Mode to Validate Certificates.</span></span>  
  
-   <span data-ttu-id="b65c1-134">因為標準的 WCF 接收配接器使用[ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960)模式來驗證用戶端和服務憑證，您必須安裝 CA 憑證鏈結來驗證 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b65c1-134">Because the standard WCF receive adapters use the [ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960) mode to validate the client and service certificates, you must install the CA certificate chain to validate the X.509 certificates.</span></span> <span data-ttu-id="b65c1-135">您可以使用 WCF-Custom 或 WCF-CustomIsolated 配接器變更此預設行為。</span><span class="sxs-lookup"><span data-stu-id="b65c1-135">You can use the WCF-Custom or the WCF-CustomIsolated adapter to change this default behavior.</span></span>  
  
## <a name="security-auditing-for-the-wcf-adapters"></a><span data-ttu-id="b65c1-136">WCF 配接器的安全性稽核</span><span class="sxs-lookup"><span data-stu-id="b65c1-136">Security Auditing for the WCF Adapters</span></span>  
  
-   <span data-ttu-id="b65c1-137">WCF 配接器預設不會使用 WCF 安全性稽核功能。</span><span class="sxs-lookup"><span data-stu-id="b65c1-137">The WCF adapters do not use the WCF security auditing features by default.</span></span> <span data-ttu-id="b65c1-138">有幾個方式可啟用 WCF 配接器的 WCF 安全性稽核功能。</span><span class="sxs-lookup"><span data-stu-id="b65c1-138">There are several ways to enable the WCF security auditing features for the WCF adapters.</span></span> <span data-ttu-id="b65c1-139">WCF 安全性稽核功能的詳細資訊，請參閱 < 稽核安全性事件 >，網址[http://go.microsoft.com/fwlink/?LinkId=88975](http://go.microsoft.com/fwlink/?LinkId=88975)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-139">For more information about the WCF security auditing features, see "Auditing Security Events" at [http://go.microsoft.com/fwlink/?LinkId=88975](http://go.microsoft.com/fwlink/?LinkId=88975).</span></span>  
  
-   <span data-ttu-id="b65c1-140">若要使用 WCF 安全性稽核使用 Wcf-custom 接收配接器的功能，您可以設定**ServiceSecurityAuditBehavior**接收位置。</span><span class="sxs-lookup"><span data-stu-id="b65c1-140">To use the WCF security auditing features with the WCF-Custom receive adapter, you can configure the **ServiceSecurityAuditBehavior** for the receive locations.</span></span>  
  
-   <span data-ttu-id="b65c1-141">對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b65c1-141">For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="b65c1-142">對於外掛式 WCF 配接器，您可以修改 Web.config 檔案 (「BizTalk WCF 服務發佈精靈」在 Web 應用程式資料夾中建立的檔案) 來啟用 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="b65c1-142">For the isolated WCF adapters, you can enable WCF tracing by modifying the Web.config file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder.</span></span> <span data-ttu-id="b65c1-143">若要修改 BTSNtSvc.exe.config 或 Web.config，請開啟組態檔並設定 WCF 追蹤，如以下組態範例所示：</span><span class="sxs-lookup"><span data-stu-id="b65c1-143">To modify BTSNtSvc.exe.config or Web.config, open the configuration file, and then configure WCF tracing, as indicated in the following configuration example:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b65c1-144">BTSNTSvc.exe.config 永遠與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b65c1-144">The BTSNTSvc.exe.config file is always located in the same directory as the BTSNTSvc.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b65c1-145">修改 BTSNTSvc.exe.config 檔案後，您必須重新啟動執行內含式 WCF 接收位置的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b65c1-145">After modifying the BTSNTSvc.exe.config file, you must restart the host instances running the in-process WCF receive locations.</span></span>  
  
    ```  
    <configuration>  
        <system.serviceModel>  
          <diagnostics performanceCounters="All" />  
          <behaviors>  
            <serviceBehaviors>  
              <behavior name="ServiceBehaviorConfiguration">  
                <serviceSecurityAudit  
                          auditLogLocation="Application"  
                          suppressAuditFailure="true"  
                          serviceAuthorizationAuditLevel="SuccessOrFailure"  
    messageAuthenticationAuditLevel="SuccessOrFailure" />  
              </behavior>  
            </serviceBehaviors>  
          </behaviors>  
          <services>  
            <service name="Microsoft.BizTalk.Adapter.Wcf.Runtime.BizTalkServiceInstance" behaviorConfiguration="ServiceBehaviorConfiguration">  
            </service>  
          </services>        
        </system.serviceModel>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="b65c1-146">您也可以使用與安全性有關的效能計數器 (例如 Security Calls Not Authorized) 來監視 WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="b65c1-146">You can also use a security-related performance counter such as Security Calls Not Authorized to monitor the WCF adapters.</span></span> <span data-ttu-id="b65c1-147">如需如何啟用 WCF 效能計數器的詳細資訊，請參閱[WCF 配接器效能計數器](../core/wcf-adapters-performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="b65c1-147">For more information about how to enable the WCF performance counters, see [WCF Adapters Performance Counters](../core/wcf-adapters-performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65c1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b65c1-148">See Also</span></span>  
 [<span data-ttu-id="b65c1-149">安全性規劃</span><span class="sxs-lookup"><span data-stu-id="b65c1-149">Planning for Security</span></span>](../core/planning-for-security.md)