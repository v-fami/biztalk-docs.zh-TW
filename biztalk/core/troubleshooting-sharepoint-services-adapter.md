---
title: 疑難排解 SharePoint Services 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f88174-118d-4ed6-8449-c89ca195ce5c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3bc6cb2d7569e7d1ee0c8816bafa91151294df7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979311"
---
# <a name="troubleshooting-sharepoint-services-adapter"></a><span data-ttu-id="f4ef2-102">SharePoint Services 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="f4ef2-102">Troubleshooting SharePoint Services Adapter</span></span>
<span data-ttu-id="f4ef2-103">本主題著重於疑難排解[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)](WSS) 配接器。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-103">This topic focuses on troubleshooting the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS) adapter.</span></span>  

## <a name="installation"></a><span data-ttu-id="f4ef2-104">安裝</span><span class="sxs-lookup"><span data-stu-id="f4ef2-104">Installation</span></span>  
 <span data-ttu-id="f4ef2-105">當使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)](WSS) 配接器，有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-105">When using the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS) adapter, there are two options:</span></span>  


|                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f4ef2-106">**使用用戶端 OM**設定為**是**。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-106">**Use Client OM** set to **Yes**.</span></span> |                                                                                                                                     <span data-ttu-id="f4ef2-107">**建議**。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-107">**Recommended**.</span></span> <span data-ttu-id="f4ef2-108">當設定為 [是]，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]會使用用戶端物件模型 (CSOM)。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-108">When set to Yes, the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM) is used.</span></span> <span data-ttu-id="f4ef2-109">此配接器會在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時一併安裝。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-109">The adapter is installed when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span> <span data-ttu-id="f4ef2-110">不需執行其他安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-110">There are no additional installation steps.</span></span> <span data-ttu-id="f4ef2-111">**注意︰** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝也會自動安裝 SharePoint 用戶端物件模型可轉散發套件可從[ http://go.microsoft.com/fwlink/p/?LinkId=263482 ](http://go.microsoft.com/fwlink/p/?LinkId=263482)。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-111">**Note:**  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation also automatically installs the SharePoint Client Object Model Redistributable available at [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span></span>                                                                                                                                     |
| <span data-ttu-id="f4ef2-112">**使用用戶端 OM**設定為**No**。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-112">**Use Client OM** set to **No**.</span></span>  | <span data-ttu-id="f4ef2-113">**已取代**。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-113">**Deprecated**.</span></span> <span data-ttu-id="f4ef2-114">使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM)。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-114">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM).</span></span><br /><br /> <span data-ttu-id="f4ef2-115">安裝 web 服務[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]可以是同一部電腦的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-115">A web service is installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, which can be on the same computer as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a separate computer.</span></span><br /><br /> <span data-ttu-id="f4ef2-116">若要安裝 web 服務，請執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的安裝[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦，檢查**Windows SharePoint Services 配接器**。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-116">To install the web service, run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer and check **Windows SharePoint Services Adapter**.</span></span> <span data-ttu-id="f4ef2-117">請參閱[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)如需特定安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-117">See [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) for specific installation steps.</span></span> |

 <span data-ttu-id="f4ef2-118">**使用用戶端 OM**設定為**是**建議。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-118">**Use Client OM** set to **Yes** is recommended.</span></span> <span data-ttu-id="f4ef2-119">當設定為**是**，SharePoint 電腦上未安裝 web 服務。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-119">When set to **Yes**, the web service is NOT installed on the SharePoint computer.</span></span> <span data-ttu-id="f4ef2-120">如果您想要使用的 web 服務選項，您必須設定**使用用戶端 OM**要**No**上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-120">If you prefer to use the web service option, you must set **Use Client OM** to **No** on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  

## <a name="iis"></a><span data-ttu-id="f4ef2-121">IIS</span><span class="sxs-lookup"><span data-stu-id="f4ef2-121">IIS</span></span>  
 <span data-ttu-id="f4ef2-122">**BTSharePointAdapterWS.asmx web 服務**</span><span class="sxs-lookup"><span data-stu-id="f4ef2-122">**BTSharePointAdapterWS.asmx web service**</span></span>  

 <span data-ttu-id="f4ef2-123">當[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]SharePoint 電腦上安裝配接器、 BTSharePointAdapterWS.asmx web 服務在 IIS 中建立 SharePoint 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-123">When the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter is installed on the SharePoint computer, the BTSharePointAdapterWS.asmx web service is created in IIS on the SharePoint computer.</span></span> <span data-ttu-id="f4ef2-124">一般而言，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和不同的電腦上安裝 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-124">Typically, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SharePoint are installed on different computers.</span></span> <span data-ttu-id="f4ef2-125">SharePoint 安裝時，內容的 SQL database 可以是本機 SharePoint 電腦或遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-125">When SharePoint is installed, the content SQL database can be local to the SharePoint computer or on a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  

 <span data-ttu-id="f4ef2-126">**應用程式集區會使用網域帳戶**</span><span class="sxs-lookup"><span data-stu-id="f4ef2-126">**Application Pool uses Domain account**</span></span>  

 <span data-ttu-id="f4ef2-127">當 BizTalk 與 SharePoint 在不同電腦上，執行 BTSharePointAdapterWS.asmx web 服務的 IIS 應用程式集區必須使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-127">When BizTalk and SharePoint are on different computers, the IIS application pool running the BTSharePointAdapterWS.asmx web service must use a domain account.</span></span> <span data-ttu-id="f4ef2-128">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，BizTalk 資料庫中，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]而[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SharePoint 資料庫都安裝在同一部電腦，則可以使用本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-128">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the BizTalk databases, [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SharePoint databases are all installed on the same computer, then a local account can be used.</span></span>  

 <span data-ttu-id="f4ef2-129">**雙躍點案例**</span><span class="sxs-lookup"><span data-stu-id="f4ef2-129">**Double-Hop Scenario**</span></span>  

 <span data-ttu-id="f4ef2-130">當有相關的三部電腦 ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)])，沒有需要 Kerberos 驗證的雙躍點案例。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-130">When there are three computers involved ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]), there is a double-hop scenario that requires Kerberos authentication.</span></span> <span data-ttu-id="f4ef2-131">SharePoint 配接器的 BizTalk 電腦上執行 BTSharePointAdapterWS.asmx web 服務，SharePoint 電腦上的 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-131">The SharePoint adapter on the BizTalk computer does a POST request to the BTSharePointAdapterWS.asmx web service on the SharePoint computer.</span></span> <span data-ttu-id="f4ef2-132">SharePoint 電腦然後查詢其資料庫上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-132">The SharePoint computer then queries its databases on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  

 <span data-ttu-id="f4ef2-133">這個 POST 要求，從 BizTalk 配接器必須順利完成。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-133">This POST request from the BizTalk adapter must complete successfully.</span></span> <span data-ttu-id="f4ef2-134">如果您懷疑發生驗證錯誤，請檢閱 IIS 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-134">If you suspect an authentication failure, review the IIS logs.</span></span> <span data-ttu-id="f4ef2-135">根據預設，IIS 記錄檔會位於 c:\inetpub\logs\LogFiles\W3SVC*x*。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-135">By default, the IIS logs are in c:\inetpub\logs\LogFiles\W3SVC*x*.</span></span> <span data-ttu-id="f4ef2-136">POST 要求應該會顯示 200 （成功） 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-136">The POST request should display a 200 (success) status code.</span></span> <span data-ttu-id="f4ef2-137">如果傳回失敗的狀態碼，例如 401.2，後面接著 401.1，之後由另一部 4*xx* error，則驗證可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-137">If a failed status code is returned, like a 401.2, followed by a 401.1, following by another 4*xx* error, then authentication may be failing.</span></span>  

 <span data-ttu-id="f4ef2-138">使用 Kerberos 驗證時，服務主體名稱 (SPN) 所需，且必須啟用委派。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-138">When Kerberos authentication is used, service principal names (SPN) are required and delegation must be enabled.</span></span>  

## <a name="enable-kerberos-authentication"></a><span data-ttu-id="f4ef2-139">啟用 Kerberos 驗證</span><span class="sxs-lookup"><span data-stu-id="f4ef2-139">Enable Kerberos Authentication</span></span>  
 <span data-ttu-id="f4ef2-140">在雙躍點案例中，Kerberos 驗證和啟用委派是必要的。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-140">In a double-hop scenario, Kerberos authentication and enabling delegation are required.</span></span> <span data-ttu-id="f4ef2-141">步驟包括：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-141">Steps include:</span></span>  

1. <span data-ttu-id="f4ef2-142">啟用**交涉**IIS/SharePoint 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-142">Enable **Negotiate** on the IIS/SharePoint server.</span></span> <span data-ttu-id="f4ef2-143">[215383： 如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://support.microsoft.com/kb/215383)列出的步驟。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-143">[215383: How to configure IIS to support both the Kerberos protocol and the NTLM protocol for network authentication](http://support.microsoft.com/kb/215383) lists the steps.</span></span>  

2. <span data-ttu-id="f4ef2-144">服務主體名稱 (Spn) 所需的網域帳戶執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]服務和應用程式集區的 IIS/SharePoint 電腦上。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-144">Service Principal Names (SPNs) are required for the domain accounts executing the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Service and the Application Pool on the IIS/SharePoint computer.</span></span> <span data-ttu-id="f4ef2-145">若要建立 SPN，請使用 SetSPN.exe 命令列工具：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-145">To create an SPN, use the SetSPN.exe command-line tool:</span></span>  

    [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]<span data-ttu-id="f4ef2-146">:[有可用的 Windows Server 2003 中的 Setspn.exe 的更新](http://support.microsoft.com/kb/970536)</span><span class="sxs-lookup"><span data-stu-id="f4ef2-146">: [An update for Setspn.exe in Windows Server 2003 is available](http://support.microsoft.com/kb/970536)</span></span>  

    [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]<span data-ttu-id="f4ef2-147"> 第 8 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]並[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)</span><span class="sxs-lookup"><span data-stu-id="f4ef2-147"> 8, [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="f4ef2-148">SetSPN 需要網域系統管理員權限，而且可以從網域中的任何電腦執行。</span><span class="sxs-lookup"><span data-stu-id="f4ef2-148">SetSPN requires Domain Administrator rights and can be executed from any computer in the domain.</span></span>  

    <span data-ttu-id="f4ef2-149">若要傳回之所有註冊的網域帳戶的 Spn 的清單：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-149">To return a list of all SPNs registered to a domain account:</span></span>  

   ```  
   setspn.exe -l Domain\UserAccount  
   ```  

    <span data-ttu-id="f4ef2-150">建立 Spn:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-150">Create the SPNs:</span></span>  

   1.  <span data-ttu-id="f4ef2-151">建立 IIS/SharePoint 電腦的 FQDN 的 SPN:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-151">Create an SPN for the FQDN of the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s http/IISSharePointComputerName.domain.com domain\IISApplicationPoolDomainAccount  
       ```  

   2.  <span data-ttu-id="f4ef2-152">建立 IIS/SharePoint 電腦的 NETBIOS 名稱的 SPN:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-152">Create an SPN for the NETBIOS name of the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s http/IISSharePointComputerNamedomain\IISApplicationPoolDomainAccount  
       ```  

   3.  <span data-ttu-id="f4ef2-153">建立 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 FQDN 的 SPN:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-153">Create an SPN for the FQDN of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s mssqlsvc/SQLComputerName.domain.com domain\SQLServerServiceDomainAccount  
       ```  

   4.  <span data-ttu-id="f4ef2-154">建立 SPN，FQDN 和 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 TCP 連接埠：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-154">Create an SPN for the FQDN and TCP Port of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s mssqlsvc/SQLComputerName.domain.com:1433 domain\SQLServerServiceDomainAccount  
       ```  

   5.  <span data-ttu-id="f4ef2-155">建立 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 NETBIOS 名稱的 SPN:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-155">Create an SPN for the NETBIOS name of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s mssqlsvc/SQLComputerNamedomain\SQLServerServiceDomainAccount  
       ```  

   6.  <span data-ttu-id="f4ef2-156">建立 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 NETBIOS 名稱： TCP 連接埠的 SPN:</span><span class="sxs-lookup"><span data-stu-id="f4ef2-156">Create an SPN for the NETBIOS name:TCP Port of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  

       ```  
       setspn.exe -s mssqlsvc/SQLComputerName:1433 domain\SQLServerServiceDomainAccount  
       ```  

3. <span data-ttu-id="f4ef2-157">在網域控制站，請移至**Active Directory 使用者和電腦**並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-157">On the Domain controller, go to **Active Directory Users & Computers** and do the following:</span></span>  

   1.  <span data-ttu-id="f4ef2-158">請檢查**信任這台電腦所委派的任何服務**下列電腦：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-158">Check **Trust this computer for delegation to any service** for the following computers:</span></span>  

       -   <span data-ttu-id="f4ef2-159">SharePoint/IIS 伺服器</span><span class="sxs-lookup"><span data-stu-id="f4ef2-159">SharePoint/IIS server</span></span>  

       -   <span data-ttu-id="f4ef2-160">SharePoint 所使用的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4ef2-160">SQL Server used by SharePoint</span></span>  

   2.  <span data-ttu-id="f4ef2-161">請檢查**帳戶受信任可以委派**並取消核取**是機密帳戶，無法委派**下列網域帳戶：</span><span class="sxs-lookup"><span data-stu-id="f4ef2-161">Check **Account is Trusted for Delegation** and uncheck **Account is sensitive and cannot be delegated** for the following domain accounts:</span></span>  

       -   <span data-ttu-id="f4ef2-162">SQL Server 服務的網域帳戶</span><span class="sxs-lookup"><span data-stu-id="f4ef2-162">SQL Server service domain account</span></span>  

       -   <span data-ttu-id="f4ef2-163">IIS 應用程式集區網域帳戶</span><span class="sxs-lookup"><span data-stu-id="f4ef2-163">IIS Application Pool domain account</span></span>  

   <span data-ttu-id="f4ef2-164">如需其他疑難排解，請移至[Windows SharePoint Services 配接器疑難排解](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="f4ef2-164">For additional troubleshooting, go to [Troubleshooting the Windows SharePoint Services Adapter](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)</span></span>  

## <a name="see-also"></a><span data-ttu-id="f4ef2-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4ef2-165">See Also</span></span>  
 <span data-ttu-id="f4ef2-166">[設定 SharePoint Services 接收位置](../core/configure-sharepoint-services-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="f4ef2-166">[Configure SharePoint Services Receive Location](../core/configure-sharepoint-services-receive-location.md) </span></span>  
 <span data-ttu-id="f4ef2-167">[設定 SharePoint Services 傳送埠](../core/configure-sharepoint-services-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="f4ef2-167">[Configure SharePoint Services Send Port](../core/configure-sharepoint-services-send-port.md) </span></span>  
 [<span data-ttu-id="f4ef2-168">CSOM：SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="f4ef2-168">CSOM: SharePoint Services Adapter</span></span>](../core/csom-sharepoint-services-adapter.md)