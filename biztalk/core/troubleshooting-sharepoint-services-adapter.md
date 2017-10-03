---
title: "疑難排解 SharePoint Services 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77f88174-118d-4ed6-8449-c89ca195ce5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f9885696df24cd5c5f8321ad3c6dd79d444559a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-sharepoint-services-adapter"></a>SharePoint Services 配接器疑難排解
本主題著重在疑難排解[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)](WSS) 配接器。  
  
## <a name="installation"></a>安裝  
 當使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)](WSS) 配接器，有兩個選項：  
  
|||  
|-|-|  
|**使用用戶端 OM**設**是**。|**建議**。 當設定為 [是]， [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM) 使用。 此配接器會在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時一併安裝。 不需執行其他安裝步驟。 **注意：** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝也會自動安裝 SharePoint 用戶端物件模型可轉散發套件可在[http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482)。|  
|**使用用戶端 OM**設**否**。|**已取代**。 使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM)。<br /><br /> Web 服務安裝在上[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]可以是同一部電腦的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或另一部電腦。<br /><br /> 若要安裝 web 服務，請執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的安裝[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦並檢查**Windows SharePoint Services 配接器**。 請參閱[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)如需特定安裝步驟。|  
  
 **使用用戶端 OM**設**是**建議。 當設定為**是**，SharePoint 電腦上未安裝 web 服務。 如果您想要使用的 web 服務選項，您必須設定**使用用戶端 OM**至**否**上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="iis"></a>IIS  
 **BTSharePointAdapterWS.asmx web 服務**  
  
 當[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器是電腦上安裝 SharePoint，BTSharePointAdapterWS.asmx web 服務在 IIS 中建立 SharePoint 電腦上。 一般而言，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SharePoint 安裝在不同的電腦。 SharePoint 安裝時，內容的 SQL 資料庫可以是本機 SharePoint 電腦，或是在遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
 **應用程式集區會使用網域帳戶**  
  
 當 BizTalk 與 SharePoint 不同的電腦上，執行 BTSharePointAdapterWS.asmx web 服務的 IIS 應用程式集區必須使用網域帳戶。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，BizTalk 資料庫中，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SharePoint 資料庫都安裝在同一部電腦，則可以使用本機帳戶。  
  
 **雙躍點案例**  
  
 當有相關的三部電腦 ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)])，沒有雙躍點案例且需要進行 Kerberos 驗證。 SharePoint 配接器的 BizTalk 電腦上執行 POST 要求到 BTSharePointAdapterWS.asmx web 服務 SharePoint 電腦上。 SharePoint 電腦然後查詢其資料庫上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
 此 POST 要求，從 BizTalk 配接器必須成功完成。 如果您懷疑發生驗證錯誤，請檢視 IIS 記錄檔。 根據預設，IIS 記錄檔會位於 c:\inetpub\logs\LogFiles\W3SVC*x*。 POST 要求應該會顯示 200 （成功） 狀態碼。 如果傳回失敗的狀態碼，例如 401.2，後面接著 401.1，遵循由另一部 4*xx*錯誤，然後驗證可能失敗。  
  
 使用 Kerberos 驗證時，服務主要名稱 (SPN) 所需，且必須啟用委派。  
  
## <a name="enable-kerberos-authentication"></a>啟用 Kerberos 驗證  
 在雙躍點案例中，Kerberos 驗證和啟用委派所需。 這些步驟包括：  
  
1.  啟用**交涉**IIS/SharePoint 伺服器上。 [215383： 如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://support.microsoft.com/kb/215383)列出的步驟。  
  
2.  服務主要名稱 (Spn) 所需執行的網域帳戶的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]服務和應用程式集區的 IIS/SharePoint 電腦上。 若要建立 SPN，使用 SetSPN.exe 命令列工具：  
  
     [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]:[可更新在 Windows Server 2003 Setspn.exe 的功能](http://support.microsoft.com/kb/970536)  
  
     [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]8 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)  
  
    > [!IMPORTANT]
    >  SetSPN 需要網域系統管理員權限，而且可以從任何電腦在網域中執行。  
  
     傳回一份所有已註冊的網域帳戶的 Spn:  
  
    ```  
    setspn.exe -l Domain\UserAccount  
    ```  
  
     建立 Spn:  
  
    1.  建立 IIS/SharePoint 電腦的 FQDN 的 SPN:  
  
        ```  
        setspn.exe -s http/IISSharePointComputerName.domain.com domain\IISApplicationPoolDomainAccount  
        ```  
  
    2.  建立 IIS/SharePoint 電腦的 NETBIOS 名稱的 SPN:  
  
        ```  
        setspn.exe -s http/IISSharePointComputerNamedomain\IISApplicationPoolDomainAccount  
        ```  
  
    3.  建立 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 FQDN 的 SPN:  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com domain\SQLServerServiceDomainAccount  
        ```  
  
    4.  建立的 FQDN 與 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 TCP 通訊埠的 SPN:  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
    5.  建立 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 NETBIOS 名稱的 SPN:  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerNamedomain\SQLServerServiceDomainAccount  
        ```  
  
    6.  建立的 IIS/SharePoint 電腦所使用的 SQL Server 電腦的 NETBIOS 名稱： TCP 連接埠的 SPN:  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
3.  在網域控制站，請移至**Active Directory 使用者和電腦**並執行下列動作：  
  
    1.  請檢查**信任這台電腦所委派的任何服務**下列電腦：  
  
        -   SharePoint/IIS 伺服器  
  
        -   SharePoint 所使用的 SQL Server  
  
    2.  請檢查**帳戶受信任可以委派**並取消核取**是機密帳戶，無法委派**下列網域帳戶：  
  
        -   SQL Server 服務的網域帳戶  
  
        -   IIS 應用程式集區網域帳戶  
  
 如需其他疑難排解，請移至[Windows SharePoint Services 配接器疑難排解](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定 SharePoint Services 接收位置](../core/configure-sharepoint-services-receive-location.md)   
 [設定 SharePoint Services 傳送埠](../core/configure-sharepoint-services-send-port.md)   
 [CSOM: SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)