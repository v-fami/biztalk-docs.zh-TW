---
title: 如何設定用於攔截的 Windows Communication Foundation 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37f2ccde-aa79-470a-ac31-57e4168dc54a
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f8328268b82a377bb6d73f3bd7305122a830c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969652"
---
# <a name="how-to-configure-a-windows-communication-foundation-application-for-interception"></a><span data-ttu-id="9bcbd-102">如何設定用於攔截的 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="9bcbd-102">How to Configure a Windows Communication Foundation Application for Interception</span></span>
<span data-ttu-id="9bcbd-103">您必須安裝 BAM 攔截器軟體，並設定應用程式使用 BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 攔截器服務，才能開始收集 BAM 活動資料。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-103">You must install the BAM interceptor software and configure your application to use the BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor service before you can begin collecting BAM activity data.</span></span> <span data-ttu-id="9bcbd-104">假設您已成功安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及其相依性，而且至少已建立一個 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-104">It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.</span></span>  
  
## <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="9bcbd-105">安裝 BAM-Eventing 軟體</span><span class="sxs-lookup"><span data-stu-id="9bcbd-105">Installing the BAM-Eventing Software</span></span>  
 <span data-ttu-id="9bcbd-106">您必須使用 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 安裝程式安裝 BAM-Eventing 軟體，才能將 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式設定為使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BAM 攔截器。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-106">Before you can configure your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="9bcbd-107">如需有關安裝 Bam-eventing 軟體及註冊效能計數器的詳細資訊，請參閱[安裝 Bam-eventing 軟體](../core/installing-the-bam-eventing-software.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-107">For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).</span></span>  
  
## <a name="configuring-a-wcf-application-for-tracking"></a><span data-ttu-id="9bcbd-108">設定 WCF 應用程式進行追蹤</span><span class="sxs-lookup"><span data-stu-id="9bcbd-108">Configuring a WCF Application for Tracking</span></span>  
 <span data-ttu-id="9bcbd-109">[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式可以開始寫入 BAM 事件資訊前，必須先完成四項工作：</span><span class="sxs-lookup"><span data-stu-id="9bcbd-109">Four tasks must be completed before your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application can begin writing BAM event information:</span></span>  
  
-   <span data-ttu-id="9bcbd-110">必須使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 工具建立觀察模型，接著使用「BAM 管理員」命令列工具 (bm.exe) 加以部署。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-110">An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command line tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="9bcbd-111">必須使用「BAM 管理員」命令列工具 (bm.exe) 建立及部署攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-111">An interceptor configuration file must be created and deployed by using the BAM Manager command line tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="9bcbd-112">執行主應用程式的使用者必須屬於適當 BAM 活動事件寫入器 (bam_\<活動\>_EventWriter) 讓應用程式來讀取攔截器組態資訊和寫入 SQL Server 角色BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-112">The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity\>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.</span></span>  
  
-   <span data-ttu-id="9bcbd-113">伺服器和用戶端應用程式的 App.config 檔必須經過修改，才能載入 BAM 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-113">The App.config file for the server and client application must be modified to load the BAM tracking service.</span></span> <span data-ttu-id="9bcbd-114">App.config 檔經過修改之後，必須重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-114">After the App.config file has been modified, the application must be restarted.</span></span>  
  
 <span data-ttu-id="9bcbd-115">唯有成功完成這些工作，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 資料庫內才會開始出現事件。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-115">Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.</span></span>  
  
### <a name="deploying-an-observation-model"></a><span data-ttu-id="9bcbd-116">部署觀察模型</span><span class="sxs-lookup"><span data-stu-id="9bcbd-116">Deploying an Observation Model</span></span>  
 <span data-ttu-id="9bcbd-117">您必須部署觀察模型，才能部署攔截器組態檔或擷取您應用程式中的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-117">You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.</span></span>  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a><span data-ttu-id="9bcbd-118">若要使用 bm.exe 部署觀察模型</span><span class="sxs-lookup"><span data-stu-id="9bcbd-118">To deploy an observation model by using bm.exe</span></span>  
  
1.  <span data-ttu-id="9bcbd-119">按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-119">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="9bcbd-120">型別**cmd**中**開啟**欄位，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-120">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9bcbd-121">使用變更目錄命令移至內含要部署之觀察模型的目錄。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-121">Use the change directory command to move to the directory containing the observation model to deploy.</span></span> <span data-ttu-id="9bcbd-122">例如， **cd c:\businessprocess\Orders**。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-122">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="9bcbd-123">使用 bm.exe 部署觀察模型：</span><span class="sxs-lookup"><span data-stu-id="9bcbd-123">Deploy the observation model using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9bcbd-124">Tracking\bm.exe deploy-all-definitionfile-Definitionfile:\<*definitionfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="9bcbd-124">Tracking\bm.exe deploy-all -Definitionfile:\<*definitionfile.xml*\></span></span>  
  
     <span data-ttu-id="9bcbd-125">請確定您取代\< *definitionfile.xml* \>您想要部署的觀察模型檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-125">Make sure you replace \<*definitionfile.xml*\> with the name of the observation model file you want to deploy.</span></span> <span data-ttu-id="9bcbd-126">如需其他選項，請參閱[攔截器管理命令](../core/interceptor-management-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-126">For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-127">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="9bcbd-128">型別**結束**，然後按 enter 鍵關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-128">Type **Exit** and then press ENTER to close the command prompt.</span></span>  
  
### <a name="deploying-an-interceptor-configuration-file"></a><span data-ttu-id="9bcbd-129">部署攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="9bcbd-129">Deploying an Interceptor Configuration File</span></span>  
 <span data-ttu-id="9bcbd-130">您必須部署攔截器組態檔，應用程式才能擷取 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-130">You must deploy an interceptor configuration file before your application will be able to capture BAM activities.</span></span>  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a><span data-ttu-id="9bcbd-131">若要使用 bm.exe 部署攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="9bcbd-131">To deploy an interceptor configuration file by using bm.exe</span></span>  
  
1.  <span data-ttu-id="9bcbd-132">按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-132">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="9bcbd-133">型別**cmd**中**開啟**欄位，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-133">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9bcbd-134">使用變更目錄命令移至內含要部署之攔截器組態檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-134">Use the change directory command to move to the directory containing the interceptor configuration file to deploy.</span></span> <span data-ttu-id="9bcbd-135">例如， **cd c:\businessprocess\Orders**。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-135">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="9bcbd-136">使用 bm.exe 部署攔截器組態檔：</span><span class="sxs-lookup"><span data-stu-id="9bcbd-136">Deploy the interceptor configuration file by using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="9bcbd-137">Tracking\bm.exe 部署攔截器-Filename:\<*icfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="9bcbd-137">Tracking\bm.exe deploy-interceptor -Filename:\<*icfile.xml*\></span></span>  
  
     <span data-ttu-id="9bcbd-138">請確定您取代\< *icfile.xml* \>您想要部署攔截器組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-138">Make sure you replace \<*icfile.xml*\> with the name of the interceptor configuration file you want to deploy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-139">您可以使用 **-Force: True**覆寫現有的事件來源的攔截器組態檔中的相同名稱的旗標。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-139">You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file.</span></span> <span data-ttu-id="9bcbd-140">如果您這樣做，請務必先備份使用現有的組態**get 攔截器**命令。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-140">If you do so, make sure you back up the existing configuration by using the **get-interceptor** command.</span></span> <span data-ttu-id="9bcbd-141">使用 -Force:True 旗標可能會刪除任何參考要覆寫之事件來源的攔截器組態。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-141">Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-142">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-142">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="9bcbd-143">型別**結束**，然後按 enter 鍵關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-143">Type **Exit** and then press ENTER to close the command prompt.</span></span>  
  
 <span data-ttu-id="9bcbd-144">若您已經部署 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式，在下一個輪詢間隔前，不會載入新組態。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-144">If you have already deployed your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval.</span></span> <span data-ttu-id="9bcbd-145">然而，您若設定並重新啟動應用程式，就會立即收取組態。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-145">However, if you configure your application and restart it, the configuration will be picked up immediately.</span></span>  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a><span data-ttu-id="9bcbd-146">加入使用者至適合的 BAM 活動角色</span><span class="sxs-lookup"><span data-stu-id="9bcbd-146">Adding the User to the Appropriate BAM Activity Role</span></span>  
 <span data-ttu-id="9bcbd-147">BAM 攔截器架構會讓每個活動使用一個 SQL Server 角色，控制活動和組態資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-147">The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information.</span></span> <span data-ttu-id="9bcbd-148">您必須將執行 WCF 應用程式的使用者帳戶，加入至 BAMPrimaryImport 資料庫內的適當 BAM 活動角色。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-148">You must add the user account running your WCF application to the appropriate BAM activity role(s) in the BAMPrimaryImport database.</span></span>  
  
### <a name="configuring-the-windows-communication-foundation-application-to-load-the-bam-tracking-service"></a><span data-ttu-id="9bcbd-149">設定讓 Windows Communication Foundation 應用程式載入 BAM 追蹤服務</span><span class="sxs-lookup"><span data-stu-id="9bcbd-149">Configuring the Windows Communication Foundation Application to Load the BAM Tracking Service</span></span>  
 <span data-ttu-id="9bcbd-150">您可透過新增數行至伺服器或用戶端應用程式的 App.config 檔的方式，設定應用程式載入 BAM 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-150">You configure your application to load the BAM tracking service by adding a few lines to the App.config file for your server or client application.</span></span>  
  
 <span data-ttu-id="9bcbd-151">若要在 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 伺服器或用戶端應用程式中設定 BAM 追蹤，您將需要修改 App.config 組態檔來加入額外的端點行為與行為延伸模組，以及新增行為組態屬性。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-151">To enable BAM tracking in your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server or client application, you will need to modify the App.config configuration file to include an additional endpoint behavior and behavior extension and add a behavior configuration attribute.</span></span> <span data-ttu-id="9bcbd-152">服務和用戶端範本的格式相似。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-152">The formats of the service and client templates are similar.</span></span>  
  
 <span data-ttu-id="9bcbd-153">設定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式時，請注意下列事項。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-153">When configuring the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, note the following.</span></span> <span data-ttu-id="9bcbd-154">如果相同應用程式 (也就是相同的用戶端或服務) 的 App.config 中定義了多種 BAM 端點行為，則 BAM 將採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-154">If there is more than one BAM endpoint behaviors defined in the App.config for the same application, that is, the same client or service, BAM will take the following actions.</span></span>  
  
-   <span data-ttu-id="9bcbd-155">如果連接字串不同，則 BAM 將引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-155">If the connection strings differ, BAM will raise and exception.</span></span>  
  
-   <span data-ttu-id="9bcbd-156">如果只有輪詢間隔不同，則 BAM 將選取其中一種行為並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-156">If only the polling interval differs, BAM will select one and move on.</span></span> <span data-ttu-id="9bcbd-157">在設計階段無法判斷將選取哪一種行為。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-157">It is not possible at design time to determine which one will be selected.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bcbd-158">如果連接字串相同 (表示參考同一部電腦)，則 BAM 處理將正常執行。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-158">If the connection strings are the same, meaning that they reference the same computer, BAM processing will proceed normally.</span></span>  
  
 <span data-ttu-id="9bcbd-159">下列範例 App.config 範本是針對 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 伺服器應用程式所設定。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-159">The following sample App.config template is configured for a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server application.</span></span> <span data-ttu-id="9bcbd-160">它會定義使用自訂行為 "bamEndpointBehavior" 的端點，且該自訂行為設定為使用 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 攔截器。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-160">It defines an endpoint that uses a custom behavior "bamEndpointBehavior" that is configured to use the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor.</span></span>  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Service.CreditCardAuthorization">  
      <!-- The endpoint will use the "bamEndpointBehavior" -->   
      <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    </service>  
  </services>  
  <bindings>  
    <wsDualHttpBinding>  
      <binding name="wsDualHttpBinding_ICreditCardAuthorization" transactionFlow="true" />  
    </wsDualHttpBinding>  
  </bindings>  
  <behaviors>  
    <endpointBehaviors>  
      <!-- Define a new behavior named "bamEndpointBehavior" -->  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <extensions>  
    <behaviorExtensions>  
      <!-- Define a new enpoint behavior extension using WCF interceptor -->  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
  </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9bcbd-161">您將需要對此範本進行細部調整，才能在自己的 App.config 檔中使用。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-161">You will need to make small changes to this template before using it in your own App.config file.</span></span>  
  
##### <a name="to-use-this-template-in-your-wcf-service-appconfig-file"></a><span data-ttu-id="9bcbd-162">在您的 WCF 服務 App.config 檔中使用此範本</span><span class="sxs-lookup"><span data-stu-id="9bcbd-162">To use this template in your WCF service App.config file</span></span>  
  
1.  <span data-ttu-id="9bcbd-163">開啟與應用程式關聯的 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-163">Open the App.config file associated with your application.</span></span> <span data-ttu-id="9bcbd-164">使用 Notepad.exe 或其他文字編輯器開啟即可。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-164">You can use Notepad.exe or another text editor for this task.</span></span>  
  
2.  <span data-ttu-id="9bcbd-165">使用下列 XML 新增 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior 行為延伸模組至 `extensions` 項目：</span><span class="sxs-lookup"><span data-stu-id="9bcbd-165">Add the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior behavior extension to the `extensions` element by using the following XML:</span></span>  
  
    ```  
    <behaviorExtensions>  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-166">行為延伸模組命名為 "BamEndpointBehaviorExtension"，並且可以視您的環境需要進行變更。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-166">The behavior extension is named "BamEndpointBehaviorExtension" and can be changed as needed to suit your environment.</span></span>  
  
3.  <span data-ttu-id="9bcbd-167">使用下列 XML 將使用新的行為延伸模組的新端點行為新增至`behaviors` 項目。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-167">Add a new endpoint behavior that uses the new behavior extension to the `behaviors` element by using the following XML.</span></span> <span data-ttu-id="9bcbd-168">行為延伸模組會提供連接字串和以秒為單位的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-168">The behavior extension provides a connection string and polling interval in seconds.</span></span>  
  
    ```  
    <endpointBehaviors>  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
    ```  
  
     <span data-ttu-id="9bcbd-169">請將 [資料來源] 取代為您環境中裝載 BamPrimaryImport 資料庫的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-169">Replace the Data Source with the name of the computer hosting the BamPrimaryImport database in your environment.</span></span> <span data-ttu-id="9bcbd-170">配合您的環境變更輪詢間隔，數字越大，表示 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 攔截器偵測組態變更的時間間隔越長。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-170">Change the polling interval to suit your requirements; a higher number means that the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor will take longer to detect configuration changes.</span></span> <span data-ttu-id="9bcbd-171">如果您已變更行為延伸模組的名稱，請使用該名稱取代 "BamEndpointBehaviorExtension"。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-171">If you changed the name of the behavior extension, use it to replace "BamEndpointBehaviorExtension".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-172">行為命名為 "bamEndpointBehavior"，並且可以視您的環境需要進行變更。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-172">The behavior name is "bamEndpointBehavior" and can be changed to suit your environment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-173">指定 `ConnectionString` 時，避免使用純文字的使用者名稱/密碼組合。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-173">Avoid using a cleartext username/password combination when specifying `ConnectionString`.</span></span> <span data-ttu-id="9bcbd-174">否則可能危害您的資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-174">Doing so may compromise your database server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-175">您必須指定大於或等於 5 (秒) 的 `PollingIntervalSec`。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-175">You must specify an `PollingIntervalSec` greater than or equal to 5 (seconds).</span></span> <span data-ttu-id="9bcbd-176">如果您指定較小的值或略過 `PollingIntervalSec` 項目，則會發生錯誤而且將不會設定攔截。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-176">If you specify a lower value or omit the `PollingIntervalSec` element, an error will be raised and interception will not be configured.</span></span>  
  
4.  <span data-ttu-id="9bcbd-177">新增 `behaviorConfiguration` 屬性至您將追蹤的端點，並且提供新行為的名稱：</span><span class="sxs-lookup"><span data-stu-id="9bcbd-177">Add the `behaviorConfiguration` attribute to the endpoint you will be tracking and provide the name of the new behavior:</span></span>  
  
    ```  
    <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9bcbd-178">如果您使用不同的行為名稱，請提供該名稱。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-178">If you used a different behavior name, supply it instead.</span></span>  
  
     <span data-ttu-id="9bcbd-179">您可以套用行為組態至多個端點。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-179">You can apply the behavior configuration to multiple endpoints.</span></span>  
  
5.  <span data-ttu-id="9bcbd-180">儲存修改過的 App.config 檔，並且重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bcbd-180">Save the modified App.config file and restart your application.</span></span>