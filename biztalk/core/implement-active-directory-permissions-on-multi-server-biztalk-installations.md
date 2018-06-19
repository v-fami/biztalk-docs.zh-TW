---
title: 在 BizTalk 多伺服器安裝上實作 Active Directory 權限的指導方針 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 315e25c4-b21d-4b5f-a1d2-1e2777b57f9e
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ff7b45e560278053cec99208fd06917d079d6b8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975972"
---
# <a name="guidelines-for-implementing-active-directory-permissions-on-multi-server-biztalk-installations"></a>在 BizTalk 多伺服器安裝上實作 Active Directory 權限的指導方針
本主題描述建立 Active Directory 組織單位的指導方針，這些組織單位是由您在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝中使用的使用者帳戶和群組所構成的。  
  
 在此建立的帳戶不需要在一般使用者的網域以外具有權限。 網域帳戶可能需要在以下信任界限內具有更高的權限：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 伺服器上)  
  
-   Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]  
  
-   外部資料庫一  
  
-   外部資料庫二  
  
-   外部資料庫*N*  
  
 例如，對於網域帳戶可能需要授與權限，以便在裝載外部資料庫的系統上執行某些動作。 在另一種情況下，帳戶可能需要將檔案寫入檔案放置資料夾，因而需要該資料夾的寫入存取。  
  
 使用**Active Directory 使用者和電腦**主控台來建立及管理網域使用者和群組帳戶。 按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。  
  
## <a name="biztalk-server-installation-and-configuration-account"></a>BizTalk Server 安裝和設定帳戶  
 在開發環境中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 都需要使用在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 系統上具有系統管理權限的帳戶。 在完成設定和組態之後，立即就可以叫用權限或停用帳戶。 帳戶也必須屬於幾個 BizTalk 群組，以下幾節會對這些提供說明。  
  
> [!NOTE]
>  如果用於安裝的帳戶屬於不同伺服器的 Active Directory 樹系，您將無法設定 SSO 元件。 如果沒有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式帳戶，請使用本機系統管理員帳戶進行 SSO 組態。 這個方法可能會在安裝期間造成其他問題，例如需要使用不同的認證登入資源。  
  
## <a name="biztalk-server-development-accounts"></a>BizTalk Server 開發帳戶  
 進行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發的個人需要存取配接器、接收和傳送處理常式，以及接收位置。 這項存取需要網域開發人員群組的成員**BizTalk Server 系統管理員**和**SSO 分支機構系統管理員**群組。  
  
> [!NOTE]
>  對於可以包含外部網域使用者的群組類型，以及可以包含在其他群組中的群組類型，Active Directory 都具有限制。 以下所建立的群組及帳戶都在單一網域上的多伺服器環境中經過測試。  
  
## <a name="biztalk-server-deployment-accounts"></a>BizTalk Server 部署帳戶  
 部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式的個人將需要是本機系統上的系統管理員，而且可能需要在該環境中的其他權限。 BizTalk Server 部署帳戶是為此目的，本主題中參考。  
  
 這項存取需要網域部署群組的成員**BizTalk Server 系統管理員**和**SSO 分支機構系統管理員**群組。  
  
> [!NOTE]
>  如果用於安裝的帳戶屬於不同伺服器的 Active Directory 樹系，您將無法設定 SSO 元件。 如果您沒有 BizTalk Server 部署帳戶，請使用本機系統管理員帳戶進行 SSO 組態。 這個方法可能會在安裝期間造成其他問題，例如需要使用不同的認證登入資源。  
  
## <a name="biztalk-server-support-accounts"></a>BizTalk Server 支援帳戶  
 支援 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式的個人將需要是本機系統上的系統管理員。 在本主題中為此目的而參考 BizTalk 支援帳戶。  
  
 這項存取需要網域支援群組的成員**BizTalk Server 系統管理員**群組。  
  
## <a name="sql-server-service-accounts"></a>SQL Server 服務帳戶  
 執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 執行個體的服務必須屬於和安裝、開發及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件所使用之帳戶相同的 Active Directory 網域。  
  
-   使用**SQLAdmin**系統管理功能 （互動式登入）。  
  
-   使用**SQLService**管理服務 （無互動式登入）。  
  
-   使用**SQLAccess**存取外部資料庫。  
  
-   SQLAdmin 必須是 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 系統上本機系統管理員群組的成員。  
  
-   SQLService 必須是本機 Administrators 群組的成員上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]系統和必須授與**以服務方式登入**使用者權限。  
  
-   SQLAccess 需要遠端資料庫伺服器上的適當權限。  
  
 **SQL 帳戶：**  
  
|**使用者名稱**|**First Name**|**Last Name**|**全名**|  
|-------------------|--------------------|-------------------|-------------------|  
|SQLService|SQL|SQLService|SQL 服務帳戶|  
|SQLAdmin|管理|SQLService|SQL 管理帳戶|  
|SQLAccess|存取|SQLService|SQL 存取帳戶|  
  
 根據公司標準設定帳戶密碼。  
  
> [!IMPORTANT]
>  在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦上，修改 SQL Server 和 SQLServerAgent 服務的啟動密碼，以使用 SQLService 帳戶和認證。  
  
> [!NOTE]
>  這個 [使用者名稱] 欄位是範例，您可能需要變更名稱以避免與其他 Active Directory 帳戶發生衝突。  
  
## <a name="windows-sharepoint-services-account"></a>Windows SharePoint Services 帳戶  
 在安裝 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 之前，必須先建立 Windows SharePoint Services 帳戶。  
  
 關於 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 帳戶的建議和注意事項：  
  
-   請使用 SharePoint 管理帳戶 (SPAdmin) 運用系統管理功能、SharePoint 計時器服務和所有 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 存取。  
  
-   SPAdmin 是網站擁有者，而且將需要電子郵件別名。  
  
-   SPAdmin 必須是本機 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上本機系統管理員群組的成員 (Windows SharePoint Services 安裝會做到這點)。  
  
-   SPAdmin 必須在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上具有安全性系統管理員和資料庫建立者角色 (Windows SharePoint Services 安裝會做到這點)。  
  
 **Sharepoint 帳戶：**  
  
|**使用者名稱**|**First Name**|**Last Name**|**全名**|  
|-------------------|--------------------|-------------------|-------------------|  
|SPAdmin|管理|SPService|SharePoint 管理帳戶|  
  
 根據公司標準設定帳戶密碼，而且能在進行組態步驟的期間擷取這些密碼。 請參閱**密碼**區段本主題適用於周圍的問題產生密碼。  
  
> [!NOTE]
>  這個 [使用者名稱] 欄位是範例，您可能需要變更名稱以保護其他 AD 帳戶。  
  
> [!IMPORTANT]
>  在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上安裝 Windows SharePoint Services 後，確認 SharePoint 計時器服務的啟動參數有使用 SPAdmin 帳戶和認證。  
  
## <a name="biztalk-groups-and-users"></a>BizTalk 群組及使用者  
 在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 之前，必須先建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組及使用者。 在單一系統安裝中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用在進行組態時所建立的本機群組及帳戶。 不過，如果部署個別的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主機，或是在兩部不同的電腦上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，您就必須使用網域使用者及群組帳戶。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] [組態精靈] 無法建立網域帳戶。  
  
 關於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務及使用者帳戶的建議和注意事項：  
  
-   建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的組織單位 (OU)。 所有的帳戶及群組都將屬於這個 OU。  
  
-   請運用完整名稱提供描述，下列清單中的名稱應該讓安裝程式能在進行組態時選取適當的群組/帳戶/使用者。  
  
-   名字和姓氏是選擇性的，只因為一致性而包括。  
  
-   區分文字**BTService**和**BTUser**指的是服務帳戶 （自動化） 與一般/共用人員使用者。  
  
-   建立網域帳戶並透過 ADSI 指令碼，為上線路環境建立使用者及群組帳戶。  
  
 **BizTalk 服務帳戶**  
  
|**使用者名稱**|**First Name**|**Last Name**|**全名**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTService|BTS|BTService|BizTalk 服務帳戶|  
|BTServiceHost|Host|BTService|BizTalk 主控件執行個體帳戶|  
|BTServiceHostIso|HostIso|BTService|BizTalk 外掛式主控件執行個體帳戶|  
|SSOService|SSO|BTService|企業單一登入服務|  
|BTServiceREU|REU|BTService|規則引擎更新服務|  
  
 根據公司和環境標準設定使用者名稱 (例如，devBTService、alphaBTService)。 根據公司標準設定帳戶密碼，而且能在進行組態步驟時擷取這些密碼。 請參閱**開發的密碼考量**區段本主題適用於周圍的問題產生密碼。  
  
 安裝程式會注意到服務帳戶相當精細，對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所建立的服務，這些幾乎具有一對一的對應。 這種粒度讓企業 IT 安全性能夠視需要而追蹤或限制存取。 雖然這是建議的粒度，卻必須由系統設計人員和企業安全性人員來決定在企業環境中是否有必要如此。  
  
 在上一個群組中的服務帳戶，其用途只是要進行自動存取，而非由使用者進行互動式登入。  
  
#### <a name="to-set-the-appropriate-account-options"></a>設定適當的帳戶選項  
  
1.  在**Active Directory 使用者和電腦**主控台，按一下以展開網域，然後再按一下展開**使用者**容器。  
  
2.  以滑鼠右鍵按一下 帳戶，然後選取**屬性**顯示**屬性**帳戶 對話方塊。  
  
3.  按一下**帳戶** 索引標籤**屬性** 對話方塊。  
  
4.  按一下以核取下列選項：  
  
    -   **使用者不得變更密碼**(企業安全性會批次處理變更的密碼)。  
  
    -   **密碼永久有效**  
  
5.  按一下**登入到** 按鈕以顯示**登入工作站** 對話方塊。  
  
6.  按一下選項**下列電腦**，新增每台電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後按一下 **確定**。  
  
7.  按一下**遙控器** 索引標籤**屬性**對話方塊，然後按一下以清除選項以**啟用遠端控制**。  
  
8.  按一下**終端機服務設定檔** 索引標籤**屬性** 對話方塊。  
  
9. 按一下以核取選項**拒絕此使用者的權限登入任何終端機伺服器**。  
  
10. 按一下**確定**關閉**屬性**帳戶 對話方塊。  
  
11. 針對每個服務帳戶重複步驟 3 到 10。  
  
 **BizTalk 使用者帳戶**  
  
|**使用者名稱**|**First Name**|**Last Name**|**全名**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTUserAdmin|管理|BTUser|BizTalk 系統管理使用者帳戶|  
|BTUserDeploy|部署|BTUser|BizTalk 部署使用者帳戶|  
|BTUserHostInstance|HostInstance|BTUser|BizTalk 主控件執行個體帳戶|  
|BTUserHostIsolated|IsolatedlHost|BTUser|BizTalk 外掛式主控件執行個體帳戶|  
|BTUserInstall|Install|BTUser|BizTalk 安裝使用者帳戶|  
|BTUserSupport|支援|BTUser|BizTalk 支援存取帳戶|  
  
#### <a name="to-set-the-appropriate-account-options-follow-these-steps"></a>遵循以下步驟設定適當的帳戶選項  
  
1.  在**Active Directory 使用者和電腦**主控台中，按一下以展開網域，然後再按一下以展開**使用者**容器。  
  
2.  以滑鼠右鍵按一下 帳戶，然後選取**屬性**顯示**屬性**帳戶 對話方塊。  
  
3.  按一下**帳戶** 索引標籤**屬性** 對話方塊。  
  
4.  按一下以核取下列選項：  
  
    -   **使用者不得變更密碼**(企業安全性會批次處理變更的密碼)。  
  
    -   **密碼永久有效**  
  
5.  按一下**登入到** 按鈕以顯示**登入工作站** 對話方塊。  
  
6.  按一下選項**下列電腦**，新增每台電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後按一下 **確定**。  
  
7.  按一下**遙控器** 索引標籤**屬性**對話方塊，然後按一下以核取選項**啟用遠端控制**。  
  
8.  按一下**終端機服務設定檔** 索引標籤**屬性** 對話方塊。  
  
9. 按一下以清除選項以**拒絕此使用者的權限登入任何終端機伺服器**。  
  
10. 按一下**確定**關閉**屬性**帳戶 對話方塊。  
  
11. 針對每個使用者帳戶重複步驟 3 到 10。  
  
    > [!NOTE]
    >  如果這些帳戶所提供的角色都有指派給實際的使用者，便可以停用任何這些帳戶。 在第一版和第二版的早期階段，都假設會在開發、Alpha 測試和 Beta 測試的環境下使用這些帳戶。  
  
 **BizTalk 群組帳戶**  
  
|**群組名稱**|**群組類型**|**成員**|  
|--------------------|--------------------|-----------------|  
|BizTalk 應用程式使用者|全域或萬用|-BTServiceHost<br />-BTUserHostInstance|  
|BizTalk 開發使用者|全域或萬用|（開發使用者的本機網域帳戶）**附註：** 最佳做法，請勿啟用 BizTalk 開發使用者群組在上線路環境中的。|  
|BizTalk 部署使用者|全域或萬用|(部署使用者的本機網域帳戶)|  
|BizTalk 主控件使用者|全域或萬用|BTUserHostInstance|  
|BizTalk 外掛式主控件使用者|全域或萬用|-BTServiceHostIso<br />-BTUserHostInstance|  
|BizTalk Server 系統管理員|全域或萬用|-BTUserAdmin<br />-BTUserInstall<br />BizTalk 開發使用者<br />BizTalk 部署使用者|  
|BizTalk 支援使用者|全域或萬用|BTUserSupport (支援使用者的本機網域帳戶)|  
|SSO 系統管理員|全域或萬用|-SSOService<br />-BTUserInstall<br />本機系統管理員|  
|SSO 分支機構系統管理員|全域或萬用|BizTalk 開發使用者<br />BizTalk 部署使用者<br />-BTServiceHostIso<br />-   \<主控台使用者\>|  
|Windows SharePoint Services 系統管理員|全域或萬用|-SPAdmin<br />-BTUserInstall<br />-BTUserDeploy<br />BizTalk 開發使用者<br />BizTalk 部署使用者|  
  
 關於網域群組的建議和注意事項：  
  
-   請在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前先建立群組和新增成員。  
  
-   網域群組可以是「全域」或「萬用」群組。  
  
-   使用 *\<DomainName\>\\< 使用者名稱\>* 當組態精靈中指定網域帳戶資訊。  
  
-   群組與使用者/服務帳戶必須屬於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的所屬網域 ([組態精靈] 會檢查此項，而且不會顯示包含其他網域之帳戶的帳戶或群組)。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要在所有叢集案例使用網域帳戶。  
  
-   在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，主控台使用者需要是下列群組的成員：  
  
    -   BizTalk Server 系統管理員  
  
    -   SSO 系統管理員 (僅限設定主要密碼伺服器時)  
  
    -   Windows 系統管理員  
  
    -   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 系統管理員  
  
    -   OLAP 系統管理員  
  
     在進行安裝和組態時都必須使用 BTUserInstall 帳戶，而且在組態完成後，便應該要停用組態。  
  
-   若要讓訊息事件和服務執行個體追蹤以偵錯工具附加協調流程，開發人員必須屬於 BizTalk Server 系統管理員群組中，如上面所述的區段中**BizTalk 開發帳戶**.  
  
## <a name="local-administrator-accounts"></a>本機系統管理員帳戶  
 確認下列帳戶和群組的存在，或是將其新增到 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上的「本機系統管理員」群組：  
  
-   Domain\BTUserInstall (在組態完成時停用)  
  
-   Domain\BTUserDeploy (當部署完成時便會在實際執行中停用)  
  
-   Domain\SPAdmin  
  
-   Domain\SQLAdmin  
  
-   Domain\SQLService  
  
-   Domain\BizTalk Development Users （在上線路環境省略）  
  
-   Domain\BizTalk Deployment Users (在開發環境中省略)  
  
 確認下列帳戶和群組的存在，或是將其新增到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的「本機系統管理員」群組：  
  
-   Domain\BTUserInstall (在組態完成時停用)  
  
-   Domain\BTUserDeploy (當部署完成時便會在實際執行中停用)  
  
-   Domain\BTUserSupport  
  
-   Domain\SPAdmin  
  
-   Domain\BizTalk Development Users (在上線路環境中省略)  
  
-   Domain\BizTalk Deployment Users (在開發環境中省略)  
  
## <a name="sql-server-administrator-accounts"></a>SQL Server 系統管理員帳戶  
 安裝程式 (Setup Program) 會接受安裝程式 (Installer) 的輸入，並將 SQL 角色指派給使用者及群組：  
  
-   在進行 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 安裝期間，會對 SPAdmin 帳戶授與 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上「安全性系統管理員」和「資料庫建立者」的權限。 如果 SPAdmin 帳戶是「本機系統管理員」群組的成員，便可移除這些權限。  
  
## <a name="e-mail-account"></a>電子郵件帳戶  
 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]傳送郵件，根據特定系統事件。 在進行組態程序時，安裝程式會提示您輸入電子郵件地址。 針對此用途建立電子郵件別名，並在安裝和單元測試期間監視的別名。 在實際執行環境中，這個帳戶應該都能由監視系統的系統管理員所存取。  
  
 所使用的電子郵件帳戶[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]是**WSS 系統管理員電子郵件**帳戶。  
  
## <a name="password-considerations-for-development"></a>開發的密碼考量  
 在開發和測試環境中，都可以用一套標準設定帳戶密碼並加以散發。 安裝程式的標準都不一樣，因此本主題使用首字大寫的字母縮寫服務元件，後面接著小寫的字母縮寫帳戶其餘部分 (服務或使用者) 的範本。 對於服務帳戶，本主題使用 'Serv'；對於使用者帳戶則使用 'User'。  
  
 例如：  
  
-   Windows SharePoint Services (SharePoint) 服務和系統管理員帳戶 (SPAdmin) 密碼: 'SPServ'。  
  
-   BizTalk 服務帳戶密碼: 'BTServ'。  
  
-   BizTalk 使用者帳戶密碼: 'BTUser'。  
  
 某些 IT 環境需要密碼包含非字母和 (或) 數字字元。 在此案例中，您可以用錢幣符號 ($) 取代 "s"，並用 At 符號 (@) 取代 "a"。 這些符號只是範例，請發展最能配合自己的模式，以便使用半公開的密碼共用帳戶。  
  
 在開發環境中使用的可轉散發密碼範例為：  
  
-   BT$erv99           BizTalk 服務帳戶  
  
-   BTU$er99          BizTalk 使用者帳戶  
  
-   SP$erv99           WSS 服務帳戶 (SPAdmin)  
  
-   SQL$erv99         SQL 服務/存取/管理帳戶  
  
> [!NOTE]
>  這些建議僅適用於開發和共用的環境，而且既不建議也不反對使用企業密碼原則。 如需瞭解密碼需求，請洽詢您的網路管理員。  
  
> [!NOTE]
>  如果企業密碼原則包括產生的密碼，請注意一些符號和符號組合在 XML 是具有特殊用途的字元。 不適當地使用這些字元，將會使組態 XML 檔無法在進行組態程序時開啟。 這些符號包括"&"、"\<"，"\>」、 單一-和雙引號，並且可能包括其他。 請在執行以檔案為基礎的組態之前，先行測試組態 XML 檔案。 您只要在 Internet Explorer (或 XML 編輯器) 中開啟其中內嵌產生之密碼的文件，便能可靠地測試適當的 XML 格式設定。  
  
 如需有關部署安全密碼在上線路環境中 (包括要測試的方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態檔)，請參閱[BizTalk Server 2013 和 2013 R2 的組態概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md)