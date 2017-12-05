---
title: "多伺服器部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], multi-server deployment
- planning, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, deploying
- Windows SharePoint Services adapters, multi-server deployment
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
ms.assetid: 0c6e2aa0-e873-461b-8101-9b0988019597
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af87c78ef632ea9794d725cb70440d62371c349e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="multiserver-deployment"></a>多伺服器部署
本主題討論 Windows SharePoint Services 之 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器的多伺服器安裝和部署考量。  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-multiserver-deployment"></a>在多伺服器部署中安裝 Windows SharePoint Services 配接器  
 選取為 Windows SharePoint Services 配接器安裝必要軟體的「Windows SharePoint Service 配接器 Web 服務」元件，以透過 Windows SharePoint Services 處理內送和外寄文件。 此 Web 服務必須安裝在安裝 Windows SharePoint Services 的伺服器上。  
  
 配接器 Web 服務可以處理多個 SharePoint 網站，不論是在相同的 IIS 網站，或在不同的 IIS 網站上。  
  
 Windows SharePoint Services 配接器有三個元件：  
  
-   執行階段元件  
  
-   設計階段元件  
  
-   配接器 Web 服務  
  
 配接器執行階段已安裝並設定自動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。 配接器設計階段元件會安裝並設定與其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能。 設計階段元件互動藉由建立 Windows SharePoint Services 連接埠，透過系統管理工具、 開發人員工具和 SDK 中隨附的工具或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。 您無法為執行階段和設計階段元件自訂任何組態選項。 您只能自訂 Windows SharePoint Services 配接器 Web 服務選項。  
  
 只有「啟用 SharePoint 的主控件」群組的成員具備叫用配接器 Web 服務的權限。 如需 Windows SharePoint Services 配接器執行階段所需的 Windows SharePoint Services 權限的詳細資訊，請參閱 < 安全性 > 一節中的[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。  
  
> [!NOTE]
>  若您選擇安裝 BAS，將會自動選取 Windows SharePoint Services 配接器 Web 服務元件。  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a>安裝 Windows SharePoint Services 配接器  
  
1.  安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
2.  在**元件安裝**畫面上，於**可用元件**下**其他軟體**，選取**Windows SharePoint Services 配接器Web 服務**。  
  
> [!NOTE]
>  您必須安裝和設定在電腦上執行該主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 Windows SharePoint Services 的執行階段和電腦。  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-multiserver-deployment"></a>在多伺服器部署中設定 Windows SharePoint Services 配接器 Web 服務  
 您可以使用 [BizTalk Server 組態] 來設定 Windows SharePoint Services 配接器。 如需有關這些工具的詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的組態概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。  
  
### <a name="using-a-custom-configuration"></a>使用自訂組態  
 BizTalk Server 組態可提供本機電腦上所安裝之功能的組態狀態高層級分析。 此工具可讓您設定與取消設定功能、設定安全性設定，以及從其他電腦匯入和匯出組態。  
  
 使用**Windows SharePoint Services**頁面，即可在此電腦上設定 Windows SharePoint Services 配接器。 下表列出組態選項。  
  
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
  
 如需 BizTalk Server 組態的詳細資訊，請參閱[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-custom-configuration"></a>使用自訂組態設定 Windows SharePoint Services 配接器  
  
1.  在**BizTalk Server 組態**，選取**SharePoint 配接器**節點。  
  
2.  選取**啟用 Windows SharePoint Services 配接器在此電腦上**。  
  
3.  在下**Windows 群組**，選取您要將 Windows SharePoint Services 配接器的 Windows 群組。 依照預設，這個群組是「啟用 SharePoint 的主控件」。  
  
4.  在**Windows SharePoint Services 配接器網站**下拉式清單方塊中，選取網站將會安裝配接器元件。 依照預設，這是「預設的網站」。  
  
    > [!NOTE]
    >  在沒有安裝任何其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件的遠端 SharePoint Server 電腦上安裝 Windows SharePoint Services 配接器網站是一種完全支援的組態。  
  
5.  按一下 [套用組態]。  
  
## <a name="considerations-for-a-multiserver-deployment"></a>多伺服器部署的考量  
 ![](../core/media/adapters-wss-multiserver-screenshot01.gif "Adapters_WSS_Multiserver_Screenshot01")  
  
### <a name="general-considerations"></a>一般考量  
 當您在多伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列事項：  
  
-   新增 BizTalk Service 帳戶到每部伺服器的「啟用 SharePoint 的主控件」Windows 群組。  
  
-   使用 SharePoint [管理中心] 工具，將「啟用 SharePoint 的主控件」群組加入「SharePoint 投稿人」角色。  
  
-   在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上，執行 SharePoint 配接器 Web 服務所使用的識別需要以下權限：  
  
     **讀取**權限**Program Files\Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**資料夾。 如果使用 64 位元版本的 Windows 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，要在設定需要的權限**Program Files (x86) \Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**  
  
     **讀取**下列登錄機碼的權限： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**。  
  
     在包含 Sharepoint 資料庫的 SQL Server 上的登入權限。  
  
     成員**公用**和**WSS_Content_Application_Pools** SharePoint 組態資料庫中的角色。  
  
     成員**公用**和**db 擁有者**SharePoint 內容資料庫中的角色。  
  
-   您安裝 Web 服務的網站必須擴充為 SharePoint Services 網站。  
  
-   您可以使用無訊息安裝來安裝和設定 Windows SharePoint Services 配接器。 如需詳細資訊，請參閱[附錄 a： 無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)。  
  
### <a name="considerations-for-network-load-balancing-nlb"></a>網路負載平衡 (NLB) 的考量  
 Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器可支援 Windows SharePoint Services 伺服器的 NLB 叢集，並支援在相同群組中設定的多個 BizTalk 伺服器。 所以，依照 SharePoint 文件的建議，Windows SharePoint Services 必須安裝在 NLB 叢集上。  
  
 當您在使用 NLB 的多伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列事項：  
  
-   選取選項以指向現有的「BizTalk 管理」資料庫來設定 Windows SharePoint Services。 指向在第一部電腦上建立的「BizTalk 管理」資料庫。 這代表您想要有 Web 伺服器環境的 Windows SharePoint Services。 指向現有內容資料庫以擴充網站。  
  
-   您必須在 Web 伺服器環境中的每部 Windows SharePoint Services 電腦上擴充相同的網站 (例如，預設網站在連接埠 80)。  
  
-   在每部 NLB 主控件上必須以相同方式安裝和設定 BTSharePointAdapterWS。 您必須設定下列 NLB 設定：  
  
    -   通訊協定：TCP  
  
    -   連接埠：80 (已經安裝及設定 Windows SharePoint Services 配接器 Web 服務的 IIS 網站的 HTTP 連接埠)。  
  
    -   篩選模式：多個主控件  
  
    -   相似性：無  
  
> [!NOTE]
>  此設定只能用於不是為 HTTPS 設定的網站。 若 BTSharePointAdapterWS Web 服務是安裝在 HTTPS 的網站上，就必須使用單一用戶端相似性。  
  
## <a name="see-also"></a>請參閱  
 [Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md)   
 [單一伺服器部署](../core/single-server-deployment.md)