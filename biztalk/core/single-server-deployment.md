---
title: "單一伺服器部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, deploying
- configuring [Windows SharePoint Services adapters], customizing
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
- Windows SharePoint Services adapters, configuring
- configuring [Windows SharePoint Services adapters], single-server deployment
- Windows SharePoint Services adapters, single-server deployment
ms.assetid: 94ba8241-9a30-46ca-b962-721e2d00f420
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38bb6aa65a77c5473ac2934bd2bd0c59268eb2af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-server-deployment"></a>單一伺服器部署
這個主題針對 Windows SharePoint Services 討論其 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器的單一伺服器安裝及部署考量。  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-single-server-deployment"></a>在單一伺服器部署中安裝 Windows SharePoint Services 配接器  
 選取為 Windows SharePoint Services 配接器安裝必要軟體的「Windows SharePoint Service 配接器 Web 服務」元件，以透過 Windows SharePoint Services 處理內送和外寄文件。 此 Web 服務必須安裝在安裝 Windows SharePoint Services 的伺服器上。 不論不同的 SharePoint 網站是在相同的 IIS 站台或是在不同的 IIS 站台上，配接器 Web 服務都可以處理多個 SharePoint 網站，包括裝載「商務活動服務」(BAS) 的網站。  
  
 Windows SharePoint Services 配接器有三個元件：  
  
-   執行階段元件  
  
-   設計階段元件  
  
-   配接器 Web 服務  
  
 配接器執行階段已安裝並設定自動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。 配接器設計階段元件會安裝並設定與其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能。 設計階段元件互動藉由建立 Windows SharePoint Services 連接埠，透過系統管理工具、 開發人員工具和 SDK 中隨附的工具或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。 您無法為執行階段和設計階段元件自訂任何組態選項。 您只能自訂 Windows SharePoint Services 配接器 Web 服務選項。  
  
 只有「啟用 SharePoint 的主控件」群組擁有叫用配接器 Web 服務的權限。 如需 Windows SharePoint Services 配接器執行階段所需的 Windows SharePoint Services 權限的詳細資訊，請參閱 < 安全性 > 一節中的[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。  
  
> [!NOTE]
>  若您選擇安裝 BAS，將會自動選取 Windows SharePoint Services 配接器 Web 服務元件。  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a>安裝 Windows SharePoint Services 配接器  
  
1.  安裝 BizTalk Server。 如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
2.  在**元件安裝**畫面上，於**可用元件**下**其他軟體**，選取**Windows SharePoint Services 配接器Web 服務**。  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-single-server-deployment"></a>在單一伺服器部署中設定 Windows SharePoint Services 配接器 Web 服務  
 您可以使用基本組態或自訂組態，來設定 Windows SharePoint Services 配接器。 如需有關這些工具的詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的組態概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。  
  
### <a name="using-a-basic-configuration"></a>使用基本組態  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 允許您使用預設設定來設定伺服器。 伺服器的預設設定是使用您輸入組態精靈中的資料庫伺服器名稱、使用者名稱和密碼所設定。 當您使用基本組態來設定 Windows SharePoint Services 配接器時，會發生以下狀況：  
  
-   會建立「啟用 SharePoint 的主控件」Windows 群組。  
  
-   會使用「預設的網站」來裝載 Windows SharePoint Services 配接器  
  
-   會建立和設定 BTSSharePointAdapterWSAppPool 應用程式集區，以也是用來執行 Windows SharePoint Services 應用程式集區的帳戶執行。  
  
-   會建立和設定 BTSharePointAdapterWS 虛擬應用程式，以便在 BTSSharePointAdapterWSAppPool 應用程式集區中執行  
  
> [!NOTE]
>  若此虛擬目錄已經存在，組態將不會更新 Metabase 中的屬性。 您必須刪除虛擬目錄並再次執行組態。  
  
-   BTSharePointAdapterWS 虛擬應用程式包含 Web 服務  
  
 如需有關基本組態的詳細資訊，請參閱[基本組態](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5)。  
  
### <a name="using-a-custom-configuration"></a>使用自訂組態  
 BizTalk Server 組態可提供本機電腦上所安裝之功能的組態狀態高層級分析。 此工具可讓您設定與取消設定功能、設定安全性設定，以及從其他電腦匯入和匯出組態。  
  
 使用**Windows SharePoint Services 配接器 Web 服務**頁面，即可在此電腦上設定 Windows SharePoint Services 配接器。 下表列出組態選項。  
  
|使用|動作|  
|--------------|----------------|  
|**此電腦上啟用 Windows SharePoint Services 配接器**|選取**啟用 Windows SharePoint Services 配接器在此電腦上**若要啟用這台電腦上的介面卡。|  
|**Windows 群組**|**Windows 群組**清單所提供的檢視，您可以編輯的 BizTalk SharePoint 配接器啟用主控件 」 Windows 群組。|  
|**Windows SharePoint Services 配接器網站**|選取要用來裝載 Windows SharePoint Services 配接器 Web 服務的網站。|  
  
 當您使用自訂組態設定 Windows SharePoint Services 配接器時，會發生以下狀況：  
  
-   除非您指定另一個 Windows 群組，否則預設會建立「啟用 SharePoint 的主控件」Windows 群組  
  
-   除非您指定另一個網站，否則會使用「預設網站」來裝載 Windows SharePoint Services 配接器  
  
-   會建立和設定 BTSSharePointAdapterWSAppPool 應用程式集區，以也是用來執行 Windows SharePoint Services 應用程式集區的帳戶執行  
  
-   會建立和設定 BTSharePointAdapterWS 虛擬應用程式，以便在 BTSSharePointAdapterWSAppPool 應用程式集區中執行  
  
> [!NOTE]
>  若此虛擬目錄已經存在，組態將不會更新 Metabase 中的屬性。 您必須刪除虛擬目錄並再次執行組態。  
  
-   BTSharePointAdapterWS 虛擬應用程式包含 Web 服務  
  
 如需有關自訂組態管理員的詳細資訊，請參閱[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-a-custom-configuration"></a>使用自訂組態設定 Windows SharePoint Services 配接器  
  
1.  在**BizTalk Server 組態**，選取**SharePoint 配接器**節點。  
  
2.  選取**啟用 Windows SharePoint Services 配接器在此電腦上**。  
  
3.  在下**Windows 群組**，選取您要將 Windows SharePoint Services 配接器的 Windows 群組。 依照預設，這個群組是「啟用 SharePoint 的主控件」。  
  
4.  在**Windows SharePoint Services 配接器網站**下拉式清單方塊中，選取網站將會安裝配接器元件。 依照預設，這是「預設的網站」。  
  
5.  按一下 [套用組態]。  
  
## <a name="considerations-for-a-single-server-deployment"></a>單一伺服器部署的考量  
 當您在單一伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列項目：  
  
-   新增 BizTalk Service 帳戶到該伺服器的「啟用 SharePoint 的主控件」Windows 群組。  
  
-   使用 SharePoint [管理中心] 工具，將「啟用 SharePoint 的主控件」群組加入「SharePoint 投稿人」角色。  
  
-   在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上，執行 SharePoint 配接器 Web 服務所使用的識別需要以下權限：  
  
     **讀取**權限**Program Files\Microsoft BizTalk Server\<版本 > \Business Activity Services\BTSharePointV3AdapterWS**資料夾。 如果使用 64 位元版本的 Windows 和 BizTalk Server，需要設定權限**Program Files (x86) \Microsoft BizTalk Server\<版本 > \Business Activity Services\BTSharePointV3AdapterWS**  
  
     **讀取**下列登錄機碼的權限： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**。  
  
     在包含 Sharepoint 資料庫的 SQL Server 上的登入權限。  
  
     成員**公用**和**WSS_Content_Application_Pools** SharePoint 組態資料庫中的角色。  
  
     成員**公用**和**db 擁有者**SharePoint 內容資料庫中的角色。  
  
-   您安裝 Web 服務的網站必須擴充為 SharePoint Services 網站。  
  
-   您可以使用無訊息安裝，來安裝和設定 Windows SharePoint Services 配接器。 如需詳細資訊，請參閱[附錄 a： 無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md)   
 [多伺服器部署](../core/multiserver-deployment.md)