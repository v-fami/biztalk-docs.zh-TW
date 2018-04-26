---
title: 使用基本或自訂組態進行設定 |Microsoft 文件
description: 步驟執行 BizTalk Server 中，基本或自訂設定，並了解每個組態會發生什麼事
ms.custom: ''
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 861a1237-d77a-42db-b563-d83f7930add6
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb5850c9dc32fd7b793e24cc08862d86a17abedd
ms.sourcegitcommit: 770523695b34cc54db81f7ab7eba46f2bc19baec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="configure-biztalk-server"></a>設定 BizTalk Server
使用基本組態或自訂組態來設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="basic-configuration-vs-custom-configuration"></a>基本組態與自訂組態

* 如果您要使用網域群組進行設定，請採取自訂組態。
* 如果您要使用自訂的群組名稱進行設定，而不是預設的群組名稱，請採取自訂組態。
* 如果您要使用自訂的資料庫名稱進行設定，而不是預設的資料庫名稱，請採取自訂組態。
* 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SQL Server 是在不同電腦上，就必須使用網域群組。 因此，請採取自訂組態。
* 您無法在 SQL Server 具名執行個體使用基本組態設定 BAM Analysis。 如果您使用具名執行個體，又想要設定 BAM 分析，請採取自訂組態。
* 如果使用者要在單一伺服器上進行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SQL Server 的完整安裝設定，則建議採取基本組態。
* 基本組態會使用預設名稱自動建立本機群組和資料庫，因此速度比較快。


## <a name="before-you-begin"></a>開始之前
* 您可以使用 SQL Server 預設執行個體與具名執行個體來設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 
* 您用來登入的帳戶必須是本機系統管理員群組的成員，並具有 SQL Server 的系統管理員 (SA) 權限。
* 如果您要使用網域群組，則必須先備妥網域群組，之後再設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。
* [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所產生並列在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態] 中的預設帳戶屬於本機群組。 在多伺服器環境中，請使用網域群組來取代本機群組。
* 如果您要設定 BAM 分析服務，則登入的帳戶必須是 OLAP 電腦上 OLAP 系統管理員群組的成員。


## <a name="basic-configuration"></a>基本組態

1. 在 [開始] 功能表中，以滑鼠右鍵選取 [BizTalk Server 組態]，然後選取 [以系統管理員​​身分執行​​]。 隨即開啟組態精靈。 
2. 請選取下列選項： 
    1. 選取 [基本組態]。
    2. [資料庫伺服器名稱] 會自動預設為本機電腦名稱。   
    3. 輸入要用來執行 BizTalk 服務之帳戶的**使用者名稱**和**密碼**。 最佳做法是建立一個唯一的帳戶。 請不要使用您個人的使用者名稱。  
        ![bts2016BasicConfig](../install-and-config-guides/media/bts2016basicconfig.gif)  
    如果您輸入具有這台電腦系統管理員認證的使用者名稱，則會收到警告。 這是正常的。 按一下 [確定] 繼續進行。
    
3. 選取 [設定]。
4. 檢閱您的組態詳細資料，並選取 [下一步]。
5. 組態精靈完成時，選取 [完成]。

暫存資料夾中即會產生組態記錄檔，其類似於 `
C:\Users\username\AppData\Local\Temp\ConfigLog(01-12-2017 0h37m59s).log`。

當您採取基本組態時，會發生下列狀況：

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動產生所有資料庫名稱。
- 所有適用的資料庫登入資訊都會以您輸入的帳戶執行。 
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動產生所有 BizTalk 服務。
- 所有 BizTalk 服務都會以您輸入的帳戶執行。 組態程序會授與此帳戶有關在伺服器與 SQL Server 物件的必要安全性權限。
- 所有功能都會根據您在電腦上安裝的先決條件軟體來進行設定。
- 系統會使用預設群組名稱，自動建立電腦本機的群組。
- 任何需要 IIS 的功能都會使用在 Internet Information Services (IIS) 中的預設網站。

## <a name="custom-configuration"></a>自訂組態
  
1. 在 [開始] 功能表中，以滑鼠右鍵選取 [BizTalk Server 組態]，然後選取 [以系統管理員​​身分執行​​]。 隨即開啟組態精靈。
2. 選取 [自訂組態]，然後選取 [設定]。

### <a name="configure-enterprise-single-sign-on-sso"></a>設定企業單一登入 (SSO)

* 設好 SSO 時，即無法使用 [BizTalk Server 組態] 將其重新設定。 若要重新設定 SSO，請使用 BizTalk Server 管理功能。
* 當您使用本機帳戶設定 SSO Windows 帳戶時，僅輸入帳戶名稱即可。 請不要輸入電腦名稱。
* 當您使用本機 SQL Server 具名執行個體作為資料存放區時，請使用 `LocalMachineName\InstanceName`。 請不要使用 `LocalMachineName\InstanceName, PortNumber`。 

1. 選取 [企業 SSO]。
2. 設定下列項目：

    | 使用 | 動作 |
    | --- | --- |
    |在此電腦上啟用「企業單一登入」。 | 使用 SSO 設定，完成此伺服器的設定。 |
    |建立新的 SSO 系統 | 如果這是您要設定的第一部 SSO 伺服器，請選取此選項。 這會建立和設定 SSO 資料庫、建立主要密碼 (加密的安全性金鑰)，並安裝 SSO 所使用的服務。 您也必須在此密碼伺服器備份密碼。<br/><br/>金鑰詳細資料： <br/><ul><li>建議您將主要密碼伺服器設為獨立伺服器。</li><li>您必須使用 SSO 系統管理員的身份登入，才能執行此組態設定工作。</li><li>一部主要密碼伺服器僅能與一個 BizTalk 群組關聯。 不支援將兩個主要密碼伺服器與相同的 BizTalk 群組關聯。</li></ul>|
    |加入現有的 SSO 系統 | 如果您要將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 新增至現有的群組，請選取此選項。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會與群組中的其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 共用相同 SSO 組態和資料庫。 |
    |資料存放區 | 輸入 SSO 伺服器的伺服器名稱。 如果您正在操作 SSO 伺服器，請選取本機伺服器名稱。 您可以保留 **SSODB** 作為預設的資料庫名稱，或輸入自訂內容。|
    |Windows 服務| 輸入要用來執行企業單一登入服務的帳戶。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |
    |Windows 帳戶|您可以保留預設的群組名稱，或輸入自訂內容。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |

3. 選取 [企業 SSO 密碼備份]。 此選項會將主要密碼儲存到加密的備份檔案。 
4. 設定下列項目：  

    |使用|動作|
    | --- | --- |
    |密碼備份密碼 | 輸入主要密碼的密碼。|
    |確認密碼|重新輸入主要密碼的密碼。|
    |密碼提示|輸入您所輸入的密碼之提示。 注意：請不要略過此步驟。 |
    |備份檔案位置|列出備份檔案的名稱和位置。 該檔案預設儲存在 \Program Files\Common Files\Enterprise Single Sign-On\ *FileName*.bak。|

請**一律**備份主要密碼，並與其他 BizTalk 系統管理員共用密碼。
    
### <a name="configure-groups"></a>設定群組

* 當您使用本機 SQL Server 具名執行個體作為資料存放區時，請使用 `LocalMachineName\InstanceName`。 請不要使用 `LocalMachineName\InstanceName, PortNumber`。

1. 選取 [群組]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    |在此電腦上啟用 BizTalk Server 群組|選取此選項時，即可在這台伺服器上，建立新的 BizTalk 群組，或加入現有的群組。 |
    |建立新的 BizTalk 群組| 如果這是群組中的第一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請選取此選項。 您可以使用此選項來建立資料庫，並新增群組。|
    |加入現有的 BizTalk 群組| 如果您要將這個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 加入現有的群組，請選取此選項。|
    |建立追蹤彙總的分析資料庫|請選取此選項以安裝 SQL Server Analysis Services，亦可追蹤並儲存狀況監控 OLAP Cube。|
    |資料存放區| 輸入裝載 BizTalk 資料庫的伺服器名稱。 如果這台伺服器上同時安裝 BizTalk 和 SQL，請輸入本機伺服器名稱。 如果 SQL Server 位於另一部電腦上，請輸入 SQL Server 名稱。<br/><br/>您可以保留預設的資料庫名稱，或輸入自訂內容。|
    |BizTalk 管理角色|您可以保留預設的群組名稱，或輸入自訂內容。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。|

### <a name="configure-the-biztalk-runtime"></a>設定 BizTalk 執行階段

* 設好 BizTalk 執行階段時，即無法使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態] 將其重新設定。 若要重新設定執行階段，請使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理功能。
* 您在群組中建立的第一個主控件必須為內含式主控件和主控件執行個體。
* 當您在相同群組中的多個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上設定執行階段時，同一個服務帳戶不能同時用於受信任與不受信任的主控件應用程式。 針對信任的應用程式和不受信任的應用程式，您必須分別使用唯一的帳戶。 

1. 選取 [BizTalk 執行階段]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    | 註冊 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段元件 | 選取此選項可在此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上建立主控件和主控件執行個體。 |
    | 建立內含式主控件與執行個體 | 在此電腦上建立 BizTalkServerApplication 主控件與執行個體。<br/><br/>其他選項： <ul><li>**信任的**：在提交訊息至 MessageBox 資料庫時，傳遞傳送者的認證 (SSID 和/或合作對象識別碼)。 這等同於在伺服器間建立信任關係。 大部分的主控件和執行個體皆不受信任。</li><li>**僅限 32 位元**：有些配接器只能在 32 位元處理序中執行，但大多數都與 64 位元相容。 在您設好 BizTalk 之後，可在 [BizTalk 管理] 中啟用/停用這項設定。 因此，不用太緊張。</li><li>**主控件名稱**：預設為 BizTalkServerApplication。 當您在 [BizTalk 管理] 中建立新的主控件和執行個體時，即可使用自己的名稱使其更加明確，例如 TrackingHost 或 ReceivingHost。 因此，此處先不作任何變更。</li></ul>|
    | 建立外掛式主控件與執行個體| 外掛式主控件會在 IIS 內執行。 在許多環境中，都最好保留預設值。<br/><br/>其他選項： <ul><li>**信任的**：在提交訊息至 MessageBox 資料庫時，傳遞傳送者的認證 (SSID 和/或合作對象識別碼)。 這等同於在伺服器間建立信任關係。 大部分的主控件和執行個體皆不受信任。</li><li>**僅限 32 位元**：有些配接器只能在 32 位元處理序中執行，但大多數都與 64 位元相容。 在您設好 BizTalk 之後，可在 [BizTalk 管理] 中啟用/停用這項設定。</li><li>**外掛式主控件名稱**：預設為 BizTalkServerIsolatedHost。 此處不作任何變更。 </li></ul>|
    |Windows 服務| 輸入用來執行主控件執行個體的帳戶。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |
    |Windows 群組|您可以保留預設的群組名稱，或輸入自訂內容。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |


### <a name="configure-business-rules-engine-bre"></a>設定商務規則引擎 (BRE)

如果不使用 BRE，您可以略過本節。

- 建議您先設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組，之後再設定商務規則引擎。 如果您在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組之前先設定 BRE，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態就不會將群組相關的管理角色新增到規則引擎資料庫。

1. 選取 [商務規則引擎]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    |在此電腦上啟用商務規則引擎 | 如果您要在此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上使用 BRE，請選取此選項。 |
    |資料存放區| 輸入裝載規則資料庫的伺服器名稱。 如果這台伺服器上同時安裝 BizTalk 和 SQL，請輸入本機伺服器名稱。 如果 SQL Server 位於另一部電腦上，請輸入 SQL Server 名稱。<br/><br/>您可以保留預設的資料庫名稱，或輸入自訂內容。|
    |Windows 服務| 輸入用來執行規則更新服務的帳戶。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |


### <a name="configure-bam-tools"></a>設定 BAM 工具

如果不使用 BAM 工具，您可以略過本節。

商務活動監控工具包括：

- 用於 Excel 的 BAM 增益集
- BAM Manager (BAM 管理員)
- BAM 入口網站


- 設定 BAM 工具時，需使用特定的 SQL Server 系統管理功能，而且必須從已安裝 Integration Services 的電腦執行。
- 可能有多個 BizTalk 群組使用 BAM 工具。 當您取消設定 BAM 工具時，會移除 BizTalk 群組的連線。 不過，BAM SQL Server 基礎結構會繼續運作，以供其他指向 BAM 主要匯入資料表的 BizTalk 群組使用。
- 使用 [商務活動監控工具] 頁面可以即時重新設定 BAM 資料庫。 例如，您不需移除現有的組態即可再次設定 BAM 資料庫。 重新設定這些 BAM 資料庫將會破壞已經部署的任何 OLAP 檢視以及任何警示。 如果您想在新設定的資料庫中保留現有的檢視和警示，請執行下列其中一項動作：  
    - 在重新設定之前解除部署警示和檢視，並於重新設定之後重新部署這些警示和檢視。 任何已封存的資料都不會出現在檢視中。
    - 如果您沒有使用 BAM 警示，請在重新設定之前備份資料庫， 然後在完成重新設定之後，將資料庫還原至新設定的位置。
- 如果您要合併 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫，則應該排除 BAM 封存和 BAM 分析資料庫。


1. 選取 [BAM 工具]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    |啟用商務活動監控工具 | 在這台電腦上啟用與安裝 BAM 工具。 |
    | 啟用 BAM 彙總的 Analysis Services | 提供 BAM 警示的追蹤資訊。|
    |資料存放區| 輸入裝載 BAM 資料庫的伺服器名稱。 如果這台伺服器上同時安裝 BizTalk 和 SQL，請輸入本機伺服器名稱。 如果 SQL Server 位於另一部電腦上，請輸入 SQL Server 名稱。<br/><br/>您可以保留預設的資料庫名稱，或輸入自訂內容。|
    |移除此 BizTalk 群組的商務活動監控工具 | 從 BizTalk 群組中解除安裝並移除 BAM 工具。 |
    
 ### <a name="configure-bam-alerts"></a>設定 BAM 警示 

BAM 警示必須啟用 BAM 工具。

1. 選取 [BAM 警示]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    | 啟用 BAM 警示 | 如果您要使用 BAM 警示，請核取此選項。 <br/><br/>請注意，您必須已設好 SQL Database Mail，才能使用 BAM 警示。 |
    | Windows 服務 | 輸入用來執行 BAM 警示服務的帳戶。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。 |
    | BAM 警示 SMTP 伺服器| 輸入您用來設定 SQL Database Mail 的 SMTP 伺服器名稱。 |
    | BAM 警示檔案位置| 輸入要儲存 BAM 警示的網路共用。 <br/><br/>**附註** <br/>您必須先手動建立此共用，BAM 警示才能儲存檔案。|
    | 警示資料庫的 SQL Server | 輸入裝載警示資料庫的 SQL Server 名稱。<br/><br/>**注意** <br/>不支援使用 IPv6 位址來指定警示資料庫的 NS SQL Server。 但是您可以使用電腦名稱，而 DNS 轉譯會處理此查閱。|
    |警示資料庫名稱的前置詞| 輸入警示資料庫要使用的前置詞。|  

### <a name="configure-the-bam-portal"></a>設定 BAM 入口網站

1. 選取 [BAM 入口網站]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    |啟用 BAM 入口網站 | 如果您使用 BAM 入口網站，請選取此選項。 | 
    |Web 服務帳戶 | 輸入用來執行 IIS 服務的帳戶。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。|
    |Windows 群組 | 您可以保留預設的群組名稱，或輸入自訂內容。 如果 SQL Server 位於另一部電腦上，請輸入網域帳戶。|
    |BAM 入口網站|選取要裝載 BAM 入口網站的網站。 在某些環境中，僅會設定 [預設的網站]。 |

### <a name="configure-biztalk-edias2-runtime"></a>設定 BizTalk EDI/AS2 執行階段 

* 在設定 BizTalk EDI/AS2 執行階段之前，必須先設定企業 SSO、群組和 BizTalk 執行階段。 
* 在設定 EDI/AS2 執行階段狀態報告功能之前，必須先啟用 BAM 工具。
* 如果您只要設定 EDI，則不需要 BAM。

1. 選取 [BizTalk EDI/AS2 執行階段]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    |在此電腦上啟用 BizTalk EDI/AS2 Runtime| 如果您將會使用 X12、EDIFACT 或 AS2 通訊協定來進行企業對企業的傳訊，請選取此選項。 |
    |啟用此 BizTalk 群組的 BizTalk EDI | 如果您是使用 X12 或 EDIFACT，請加以選取。 |
    | 啟用此 BizTalk 群組的 BizTalk AS2 | 如果您是使用 AS2，請加以選取。 |
    | 啟用此 BizTalk 群組的 BizTalk EDI/AS2 Runtime 狀態報告 | 啟用使用者體驗報告，以提供 EDI 交換和通知的狀態。 |
    |從此 BizTalk 群組移除 BizTalk EDI、AS2 和狀態報告功能 | 從群組中解除安裝和移除報告功能。 |

### <a name="configure-windows-sharepoint-services-web-service---biztalk-server-2013-and-r2-only"></a>設定 Windows SharePoint Services Web 服務 - 僅限 BizTalk Server 2013 和 R2 

> [!IMPORTANT] 
> 本節只適用於 BizTalk Server 2013 R2 和 BizTalk Server 2013。 如果您並非使用 BizTalk Server 2013 R2 或 BizTalk Server 2013，請略過本節。

* 自 BizTalk Server 2016 起，已移除這項 SharePoint Services Web 服務 (SSOM)，而在 BizTalk Server 2013 R2 中，則已將其取代。 由 SharePoint Services 配接器 (CSOM) 取代上述服務。 BizTalk 組態中不會顯示 CSOM 選項。 CSOM 選項會自動隨著 BizTalk 一起安裝；如同 FILE 配接器或 HTTP 配接器會自動安裝一樣。

1. 選取 [Windows SharePoint Services 配接器]。
2. 設定下列項目：

    |使用|動作|
    | --- | --- |
    | 在此電腦上啟用 Windows SharePoint Services 配接器 | 選取以安裝 SharePoint Services Web 服務。 您要安裝 IIS Web 服務的 SharePoint Services 電腦，可以是 BizTalk Server 所在的相同電腦或其他電腦。 在大部分的環境中，BizTalk Server 和 SharePoint 服務會位於不同的電腦上。|
    |Windows 群組|您可以保留預設的群組名稱，或輸入自訂內容。 |
    |Windows SharePoint Services 配接器網站|選取要用來裝載 Windows SharePoint Services 配接器 Web 服務的網站。|
    
    
### <a name="apply-your-configuration"></a>套用您的組態

選取 [套用組態]，並繼續設定。 

1. 在 [摘要] 中，請檢閱已選取的元件，然後選取 [下一步]。
2. 完成後，請選取 [完成]。

完成後，暫存資料夾中即會產生組態記錄檔，其類似於 `
C:\Users\username\AppData\Local\Temp\ConfigLog(1-12-2017 2h39m30s).log`。

## <a name="iis-application-pools-and-web-sites"></a>IIS 應用程式集區和網站
設定之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，可能會建立下列的網際網路資訊服務 (IIS) 應用程式集區和虛擬應用程式： 
  
### <a name="application-pools"></a>應用程式集區  
  
|應用程式集區|預設應用程式集區識別|Description|  
|----------------------|---------------------------------------|-----------------|  
|BAMAppPool|*使用者定義*|BAM 入口網站的應用程式集區。|  
|BTSSharePointAdapterWSAppPool|*使用者定義*|Windows SharePoint Service 配接器 Web 服務的應用程式集區。|  
|STSWebServiceAppPool|*使用者定義*|交易夥伴管理工具的應用程式集區。|  
|TpmWSAppPool|*使用者定義*|TPM 管理 Web 服務的應用程式集區。|  
  
### <a name="virtual-applications"></a>虛擬應用程式  
  
|虛擬應用程式|預設應用程式集區|Description|  
|-------------------------|------------------------------|-----------------|  
|BAM|BAMAppPool|裝載 BAM 入口網站元件 (頁面、圖像、先行編譯的程式碼及其他資源) 的虛擬應用程式。 此虛擬應用程式會呼叫 BAMManagementService 應用程式來與 BAM 資料庫進行通訊。 **注意︰**  品牌 BAM 入口網站，您可以修改此應用程式的內容。|  
|BAMManagementService|BAMAppPool|裝載 BAMManagementService Web 服務的虛擬應用程式。 BAM 入口網站應用程式會使用此 Web 服務與 BAM 主要匯入資料表 (PIT) 通訊。 與資料庫的通訊會使用儲存在登錄中的模擬認證 (在組態期間建立) 來執行。 自訂用戶端也可以使用此 Web 服務公開的方法來取得任何使用者的檢視與其詳細資料、相關的活動以及樞紐分析表版面配置。 這些方法也可以用來管理資料庫中的警示。|  
|BTSharePointAdapterWS|BTSSharePointAdapterWSAppPool|裝載 Windows SharePoint Service 配接器 Web 服務的虛擬應用程式。 適用於 BizTalk Server 2013 R2 和僅 2013年。|  

 
## <a name="more-configuration-topics"></a>更多設定主題  
  
 [在 Azure VM 上設定 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
[設定叢集中的 BizTalk Server](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)

[環境最佳化的後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)

 [保護 BizTalk Server 部署安全](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  
 
