---
title: 升級到 BizTalk Server 2016 |Microsoft Docs
ms.custom: ''
ms.prod: biztalk-server
ms.date: 06/08/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 975ec82b-ed27-4545-8e4a-0e567507c9ba
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbd6debef5517e95295be0b7680244ee433b6e2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976575"
---
# <a name="upgrade-to-biztalk-server-2016"></a>升級到 BizTalk Server 2016
從 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] 或 BizTalk Server 2013 升級至 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。

本文件提供 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 升級程序的概觀、重要資訊，以及從 BizTalk Server 2013 R2 或 BizTalk Server 2013 升級的逐步指示。


## <a name="upgrade-overview"></a>升級概觀

- 升級之前請完整閱讀本文件。 BizTalk Server 會將許多不同元件的內部和外部都連線到您的企業中。 在現實世界中，通常會部署到多部伺服器，最後得到同時混合了實體電腦與虛擬電腦的叢集。

- 沒有 BizTalk Server 部署會彼此相同。 在升級前，請收集企業需求的資訊，並與 IT 專業人員、系統管理員和要使用 BizTalk Server 的開發人員一起討論部署範圍。 只要詳閱本升級指南並決定企業的特殊需求，您就可以建立自己的部署藍圖。

- 使用 BizTalk Server Best Practices Analyzer (BPA) 檢查 BizTalk Server 部署，並產生最佳做法清單。 BPA 會執行組態層級驗證 (僅讀取和報告)，並運用所收集的資料來研判是否已遵循最佳作法。

### <a name="planning-your-upgrade"></a>規劃升級

以下是升級程序的高等級檢視。 每個所列出的步驟都必須依顯示的順序執行。

- 作業系統升級路徑
- Microsoft SQL Server® 升級路徑
- Windows® SharePoint® Services 升級
- 並存安裝 Visual Studio
- 並存安裝 Microsoft Office 2016/2013

### <a name="supported-upgrade-paths"></a>支援的升級路徑
下表列出可以升級至 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 的支援作業系統。 「是」表示在該作業系統上執行的 BizTalk Server 版本可以升級。 「否」表示在該作業系統上執行的 BizTalk Server 版本無法升級。 當出現「否」時，必須在支援的作業系統上重新建立 BizTalk 環境。  [BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)會列出支援的作業系統。

| 作業系統 | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| Windows Server 2012 R2 | 是 | 否 |
| Windows Server 2012 | 否 | 否 |
| Windows 8.1 | 是 | 否 |
| Windows 8 | 否 | 否
| Windows 7 SP1 | 否 | 否 |

下表列出可以升級至 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 的支援 SQL Server 版本。 SQL Server 會主控 BizTalk Server 所使用的資料庫。 「是」表示可以升級使用該 SQL Server 版本的 BizTalk Server。 「否」表示不能升級使用該 SQL Server 版本的 BizTalk Server。 當出現「否」時，必須在支援的 SQL Server 版本上重新建立 BizTalk 環境。 [BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)會列出支援的 SQL Server 版本。 

> [!TIP]
> 如果您的 SQL Server 版本不受支援或不在下列清單中，請參閱 SQL Server 升級文件。 SQL 升級涵蓋的版本比 BizTalk 支援的多。 例如，如果您使用 SQL Server 2008，您可以升級至 SQL Server 2016。 然後可以升級至 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 [升級到 SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx) 和[升級至 SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx) 會列出可以升級的 SQL Server 版本。

| [SQL Server] | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| SQL Server 2014 | 是 | 否 |
| SQL Server 2012 SP1| 否 | 否 |
| SQL Server 2012 | 否 | 否 |
| SQL Server 2008 R2 SP1 | 否 | 否 |


下表列出從 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 到 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 的支援版本升級路徑。 「是」表示 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 版本可以升級至該版本。 「否」表示 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 版本不能升級至該版本。 當出現「否」時，就必須重新建立 BizTalk 環境。

| BizTalk Server 2013 R2/2013 | BizTalk Server 2016 Evaluation Edition | BizTalk Server 2016 Branch Edition | BizTalk Server 2016 Developer Edition | BizTalk Server 2016 Standard Edition | BizTalk Server 2016 Enterprise Edition |
| --- | --- | --- | --- | --- | --- |
| Evaluation | 否 | 否 | 否 | 否 | 是 | 
| 分支 | 否 | 是 | 否 | 否 | 是 | 
| 開發人員 | 否 | 否 | 是 | 否 | 是 | 
| Standard | 否 | 否 | 否 | 是 | 是 | 
| Enterprise | 否 | 否 | 否 | 否 | 是 | 

## <a name="before-the-upgrade--what-you-need-to-know"></a>在升級之前 – 您必須了解的事項


- **權限**：執行升級的使用者必須為下列使用者群組成員，或擁有對等的權限：

    - 本機電腦的 Administrators 群組
    - SQL Server 的 SQL Server 系統管理員群組
    - BizTalk Server 系統管理員群組
    - 單一登入 (SSO) 系統管理員群組

- **SSO**：單一登入主要密碼伺服器與主控 SSO 資料庫的 SQL Server 必須在升級期間執行。

- **網路服務帳戶**：必須具有 %windir%\temp 的寫入權限。

- **憑證**：備份 Windows 憑證存放區：  

    [Windows 7 和 Windows Server 2008 R2︰匯入憑證](http://technet.microsoft.com/library/cc754489.aspx)  
    [Windows 7 和 Windows Server 2008 R2︰匯出憑證](http://technet.microsoft.com/library/cc730988.aspx)  

- **DTC**：啟用 Microsoft 分散式交易協調器 (MSDTC) ([環境最佳化的後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md))，然後再啟用輸入/輸出 DTC 規則：

    1. 在 [伺服器管理員] 中選取 [工具]，並開啟 [具有進階安全性的 Windows 防火牆]。
    2. 選取 [輸入規則]。
    3. 在 **輸入規則**，以滑鼠右鍵按一下**分散式交易協調器*** （適合的話），然後**啟用規則**。
    4.  在 [具有進階安全性的 Windows 防火牆] 中，選取 [輸出規則]。
    5.  在 **輸出規則**，以滑鼠右鍵按一下**分散式交易協調器*** （適合的話），然後**啟用規則**。

- **SharePoint**：用戶端物件模型 (CSOM) 用來連接到 SharePoint Services。 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 已移除伺服器端物件模型 (SSOM) (web 服務)。

    如果您使用不支援 CSOM 的 SharePoint 版本，您可以升級至支援的 SharePoint 版本︰

    [升級到 SharePoint 2016](https://technet.microsoft.com/library/cc303420(v=office.16).aspx)  
    [升級到 SharePoint 2013](https://technet.microsoft.com/library/cc303420(v=office.15).aspx)

- **.NET framework**︰.NET Framework 4.5 和 .NET Framework 4.6 之間沒有並存安裝的概念。 .NET Framework 4.6 二進位檔會覆寫 .NET Framework 4.5 二進位檔。 .NET framework 4.6 是 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 需求，舊版 BizTalk Server 並不支援 (也不應該安裝)。

- **Office 2016 和 Office 2013**：[在同一部電腦上安裝和使用不同版本的 Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF)。 亦請查看[這些問題](https://support.microsoft.com/kb/3094527)。

- **Biztalkserverapplication 主控件**︰升級時需要有預設主控件存在。 如已移除與 SQL 配接器傳送埠和接收位置關聯的預設主控件執行個體，請在升級前建立預設主控件與 SQL 配接器的關聯。 完成升級之後，您可以從清單中移除預設主控件。

- **自訂繫結**：升級之後，使用舊版 .NET Framework 建置的使用者定義自訂繫結將無法使用。 若要使用自訂繫結，請在 .NET Framework 4.6 machine.config 檔案中手動新增自訂繫結。

- **設定檔**：備份 BizTalk Server 2013 R2/2013 中的所有自訂設定檔。 BizTalk Server 只支援移轉 `btsntsvc.exe.config` 和 `bm.exe.config` 檔案中的變更。



### <a name="bam-alerts"></a>BAM 警示

需要 SQL Server Database Mail 才能使用 BAM 警示。 如果 SQL Server 正在從使用現有 BAM 警示定義與通知服務的 SQL 版本進行升級，您可以備份 BAM 警示定義並在升級之後部署它們。 使用 BM.exe 命令列工具 (`\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`)。 特定步驟包含：

1. 開啟命令提示字元，並移至 `\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`。
2. 在命令提示字元中建立定義檔：`bm.exe get-defxml -FileName:YourBAMDefinition.xml`
3. 在 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 設定中，取消設定 BAM 警示。
4. 升級到 SQL Server 2016 或 SQL Server 2014 SP1。
5. 設定 SQL Server Database Mail。
6. 升級到 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。
7. 在 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 設定中，設定 BAM 警示。
8. 將已儲存的定義檔部署在命令提示字元中：`bm.exe update-all -DefinitionFile:YourBAMDefinition.xml`

> [!IMPORTANT]
> 如果您不依列出的順序進行這些步驟或建立定義檔案，您必須在 BizTalk Server 升級之後重新建立定義檔。
> 
> 若要檢視 BM.exe 說明，請輸入：`bm.exe help`。


### <a name="bam"></a>BAM 

- **BAM DTS 套件**：停止所有 BAM Data Transformation Services (DTS) 套件。 否則資料可能遺失，或是線上分析處理 (OLAP) Cube 可能會損毀。 

- **磁碟空間**：可用磁碟空間應該至少為現有 BAM 資料庫的大小。

- **即時彙總**：如果您在目前的 BizTalk Server 版本中使用 BAM 即時彙總，且已升級為 SQL Server，請安裝或升級為 SQL Server Enterprise Edition。 否則，升級會失敗。

- **maxTimeout 值**：如果您有大型的 BAM 資料庫，請更新 machine.config 檔中分散式交易的 `maxTimeout` 值，以：  

    ```
    <system.transactions>
       <machineSettings maxTimeout="23:59:59" />
    </system.transactions>
    ```

- **使用追蹤設定檔編輯器 (TPE) 啟用的 BAM 追蹤**：升級之後，會升級先前部署的追蹤設定檔；不過，它們對應的攔截器設定不會升級。 攔截到的任何新 BAM 訊息可能仍然會有 BizTalk Server 2013 R2/2013 參考。 若要升級對應的攔截器設定，請使用追蹤設定檔編輯器來擷取活動的設定檔，然後重新套用設定檔。

- **即時資料活頁簿**：如果您在 BizTalk Server 2013 R2/2013 中使用 BAM，則升級之後，就必須手動重新產生即時資料活頁簿。 若要重新產生即時資料活頁簿：

  1. 執行下列命令，擷取 BAM 定義：  
     `BM get-defxml MyDef.xml`
  2. 開啟 Microsoft Office Excel，再選取 BAM 增益集，重新建立樞紐分析表。匯入步驟 (1) 中建立的 *MyDef.xml* 檔案，然後重新建立樞紐分析表。 將新的 BAM 活頁簿儲存為 *MyNewBook.xls*。
  3. 在 `<BAMDefinition>\<Extension>\<OWC>\<PivotTableView>\<PivotTable>\<PivotView>\<Label>` 路徑的 `<Caption>` 下，於 *MyDef.xml* 中尋找樞紐分析表的名稱。 使用這些名稱重新命名 *MyNewBook.xls* 中的樞紐分析表。
  4. 執行下列命令，重新產生即時資料活頁簿：  
     `BM regenerate-livedataworkbook MyNewBook.xls`

     > [!NOTE]
     > 重新產生的即時資料活頁簿不會重新建立原始即時資料活頁簿中的 Excel 成品 (例如，圖表)。 手動重新建立成品。


### <a name="enterprise-single-sign-on-esso"></a>企業單一登入 (ESSO)

|                            狀況                            |                                                                                                                                                                                                                                                                                                                                          其他資訊                                                                                                                                                                                                                                                                                                                                          |
|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 從舊版企業單一登入升級 | BizTalk Server 包含更新版企業單一登入 (ESSO)。 如果您在具有舊版 BizTalk 的電腦上安裝此版本，則安裝期間會自動更新 ESSO。 建議您先執行下列步驟，再進行升級： <br/><br/> 1.確認已將目前版本的單一登入資料庫 (SSODB) 備份至安全的位置。 <br/>2.確認已將目前的主要密碼金鑰備份至安全的位置。<br/>3.知道主要密碼的密碼。<br/><br/>將 BizTalk 群組中的所有伺服器都升級至相同版本。 此需求也適用於獨立的主要密碼伺服器。 |
|  使用企業單一登入獨立安裝程式進行升級  |             使用下列步驟，在已安裝獨立企業單一登入的電腦 (如專用的主要密碼伺服器) 上執行升級。<br/><br/>1.確認已將目前的主要密碼金鑰備份至安全的位置。<br/>2.確認已將目前版本的 SSODB 備份至安全的位置。<br/>3.從 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 安裝媒體中執行 ESSO **Setup.exe**。 預設的安裝資料夾是 `\Platform\SSO`。<br/>4.在 [自動執行] 對話方塊中，選取 [Microsoft 企業單一登入]。<br/>5.在 [摘要] 對話方塊中，選取 [升級]。              |

### <a name="multicomputer-environment"></a>多重電腦環境
在多重電腦環境中，升級 SSO 主要密碼伺服器電腦。 接著，升級其他 BizTalk Server 電腦。 不支援同時升級同一群組中的 BizTalk 電腦。 依照下列順序一次升級一部電腦：

1. 單一登入主要密碼伺服器
2. 執行 BizTalk Server 的執行階段電腦
3. 管理工具與監控電腦
4. 開發電腦和其餘執行 BizTalk Server 的任何電腦

**其他**  
設定儀表板可讓您大幅調整 BizTalk Server 設定來達到最佳效能。 您也可以修改 BizTalk 群組、BizTalk 主控件與 BizTalk 主控件執行個體的設定。 請參閱[針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。

### <a name="general-information"></a>一般資訊

- **帳戶名稱**：您應該盡量使用預設帳戶名稱。 BizTalk Server 安裝程式會自動將已安裝的元件設定成使用預設帳戶。 如果在 Active Directory 樹系中有多個 BizTalk Server 群組，請變更帳戶名稱以避免發生衝突。 針對服務帳戶和 Windows 群組，BizTalk Server 只支援 `<NetBIOS domain name>\<user>` 名稱格式。

- **帳戶名稱與 BAM 管理 Web 服務**：BizTalk Server 不支援使用內建帳戶或無密碼的帳戶作為 BAM 管理 Web 服務使用者。 

  使用這類帳戶來設定 BizTalk Server 或許看似成功，但 BAM 管理 Web 服務會失敗。 

  支援在 BAM 應用程式集區使用這類帳戶。

- 64 位元作業系統不支援 **BizTalk 組件檢視工具**。

- **安裝與解除安裝**：當您解除安裝 BizTalk Server 時，請手動刪除 BizTalk Server 資料庫。 如果以開發人員或評估員身分來安裝 BizTalk Server，請考慮安裝在虛擬機器上。 如此一來，當您需要重新安裝時，就可以輕鬆地回復至預設的檢查點，而不需要經過解除安裝程序。

- **32 位元和 64 位元電腦**：在 32 位元 Windows 或 64 位元 Windows 上安裝 BizTalk Server 時有幾項差異。 本文件同時包含 32 位元與 64 位元的安裝。 它們之間的差異會被註明。

- **工作群組**：支援在工作群組環境的單一電腦上安裝和設定 BizTalk Server。 在此情況下，SQL Server 與 BizTalk Server 的功能和元件都是在同一部電腦上安裝和設定。

- **終端機伺服器**：不支援使用在應用程式模式下執行的終端機伺服器來安裝 BizTalk Server。 請參閱 [KB 832027](https://support.microsoft.com/kb/832027)。

- 不支援**無訊息升級**。

- **不支援的應用程式**：BizTalk Server 不支援以不支援的 API 建置的自訂應程式，例如 PAM API、預存程序或直接資料庫存取。 在升級生產環境之前，請至少執行一次測試升級。

- **SQL Server 執行個體**：您最好在升級平台之前先升級任何的 SQL Server 執行個體。

## <a name="prepare-your-computer-for-upgrade"></a>備妥電腦準備升級

|                 工作                  |                                                                                                                                                                                                                                        資訊                                                                                                                                                                                                                                         |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   安裝 Windows 重大更新    |                                                                                                                                                                                                從 [程式] 功能表中選取 [Windows Update]。 您可能需要重新啟動電腦。                                                                                                                                                                                                 |
|      儲存 BAM 警示定義       |                                    只有目前使用現有的 BAM 警示定義與 SQL Server 通知服務時才適用。 使用 BM.exe 建立一個定義檔案並取消設定 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 設定中的 BAM 警示。<br/><br/>**在升級之前** (在本主題中) 列出特定的步驟。<br/><br/>否則在升級之後重新建立 BAM 警示定義。                                    |
|          升級 SQL Server           |                                         升級至支援的 SQL Server 版本。 請參閱：<br/><br/>[BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)<br/>[升級到 SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx)<br/>[升級到 SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx)                                          |
|    升級 SQL Server 用戶端工具    |                                                                                                                                                在多重電腦環境中，管理工具可能被安裝在另一部電腦上。 升級 SQL Server 管理用戶端工具，包括管理工具。                                                                                                                                                |
|         安裝 Visual Studio         |                         請參閱 [BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)取得支援的版本。 不同的 Visual Studio 版本可以並存安裝。 請參閱 [Visual Studio 2015](https://msdn.microsoft.com/library/ms246609(v=vs.140).aspx) 和 [Visual Studio 2013](https://msdn.microsoft.com/library/ms246609(v=vs.120).aspx)。                         |
|            安裝 Office             |                                     請參閱[在同一部電腦上安裝和使用不同版本的 Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF)。 [BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)會列出支援的 Office 版本。                                     |
| 停止 BizTalk 和 Windows 服務 |                                                                                                      - BizTalk 服務 BizTalk 群組：*<應用程式名稱>*<br/>- BizTalk 基底 EDI 服務<br/>- 規則引擎更新服務<br/>- World Wide Web Publishing Service<br/><br/>**注意**<br/>如果您已安裝任何 BizTalk Server 加速器，請停止 HL7 記錄服務。                                                                                                      |
|         備份資料庫         | - Master<br/>- MSDB<br/>- BAMArchive<br/>- BAMPrimaryImport<br/>- BAMStarSchema<br/>- BizTalkDTADb<br/>- BizTalkEDIDb<br/>- BizTalkHwsDb<br/>- BizTalkMgmtDb<br/>- BizTalkMsgBoxDb<br/>- BizTalkRuleEngineDb<br/>- TPM<br/>- BizTalkAnalysisDb<br/>- BAMAnalysis<br/><br/>[SQL Server 2014：備份概觀](https://technet.microsoft.com/library/ms175477(v=sql.120).aspx)<br/>[SQL Server 2012：備份概觀](https://technet.microsoft.com/library/ms175477(v=sql.110).aspx) |
|  設定 SQL Server Database Mail   |                                                                                                                      只有使用 BAM 警示定義與 SQL Server 通知服務時才適用。<br/><br/>**在升級之前** (在本主題中) 列出特定的步驟。<br/><br/>否則在升級之後重新建立 BAM 警示定義。                                                                                                                       |

## <a name="do-the-upgrade"></a>執行升級作業

> [!IMPORTANT]
> 安裝 SQL Server 之後，安裝程式會將系統管理員權限授與您已登入的帳戶。 安裝 BizTalk Server 也需要系統管理員權限。 執行下列其中之一：
> 
> - 使用您在安裝 SQL Server 時所使用的相同帳戶  
> **或**  
> - 確定目前的已登入帳戶具有系統管理員權限

### <a name="upgrade-steps"></a>升級步驟

1. 關閉所有開啟的程式。
2. 從安裝媒體執行 **Setup.exe**。
3. 在 [開始] 功能表中，選取 [安裝 Microsoft BizTalk Server]。
4. 在 [客戶資訊] 輸入您的使用者名稱、組織以及產品金鑰。 選取 **[下一步]**。
5. 接受授權合約，然後選取 [下一步]。
6. 在客戶經驗改進計畫中輸入您的喜好設定。 請參閱本主題中的**附錄 A** 以取得相關資訊。
7. 在 [元件安裝] 檢閱可用的元件，然後選取 [下一步]。
8. 如果電腦缺少必要元件，安裝程式可以安裝必要的可轉散發套件。 您可以：

    - 選取 [從 Web 自動安裝必要的可轉散發套件]  

      OR  

    - 如果您已下載封包檔，則可以選取 [從封包檔自動安裝必要的可轉散發套件]。 瀏覽至封包檔位置，然後選取該檔案。

9. 在 [摘要] 檢視可升級的元件。
10. 選取 [升級] 啟動作業。
11. 或者：選取 [在我檢查更新時使用 Microsoft Update (建議使用)]。
12. 在 [升級已完成] 中清除 [啟動 BizTalk Server 組態] 核取方塊，然後選取 [完成]。

**其他**  
在 BizTalk Server 升級過程中會經常發生，且過程中發生錯誤也屢見不鮮。 不過，只要事前有所準備，很容易解決大部分錯誤。 建議您閱讀本主題的**附錄 B**，以取得如何避免升級錯誤的秘訣，並了解發生錯誤時如何因應。

升級程序只會升級舊版 BizTalk Server 中的功能。 在升級期間不會安裝新的功能。 若要安裝這些功能，請在升級之後重新執行安裝程式，選擇 [修改]，然後選取您要安裝的功能。 安裝後，請使用 **BizTalk Server 組態管理員**來設定它們。

若要確認升級是否成功，請開啟 [程式和功能] 並尋找 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 如果有列出，即表示安裝成功。

## <a name="post-upgrade"></a>升級之後
您無法回復到 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013。

- **如已建立 BAM 警示定義 XML 檔**︰在 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 設定中，設定 BAM 警示。 然後部署已儲存的定義。

    **在升級之前** (在本主題中) 列出特定的步驟。 否則在升級之後重新建立 BAM 警示定義。

- **安裝 MQSAgent**：如果 MQsagent.dll 檔案安裝在遠端 WebSphere MQ Server 上，請將來自 [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 的新版 MQ 代理程式安裝在遠端的 WebSphere MQ Server 上。

- **啟動 MSMQ**：如果您使用 MSMQ 配接器，請啟動訊息佇列服務。

- **自訂 EXE 及 BRE**：如果您有自訂的受管理可執行檔，而且此檔案參考 BizTalk Server 2010 中的商務規則引擎組件，請將下列項目加入應用程式設定檔案，以在 .NET Framework 2.0 中執行此程序。

    ```
    <?xml version="1.0" encoding="Windows-1252"?>
    <configuration> 
     <startup>
      <supportedRuntime version="v2.0.50727" />
     </startup>   
    </configuration>
    ```

- **SQL Agent 作業**：重新設定下列 SQL Server Agent 作業：

    -   DTA 清除與封存 (BizTalkDTADb)：請參閱[如何設定 DTA 的清除與封存作業](../core/how-to-configure-the-dta-purge-and-archive-job.md)
    -   備份 BizTalk Server (BizTalkMgmtDb)：請參閱 [如何設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)

- **重新啟動應用程式**：重新啟動已升級的所有部署應用程式。

- **BAM 入口網站錯誤**︰當您開啟 BAM 入口網站時，您可能會收到下列錯誤訊息︰ 

    `The server encountered a critical failure while trying to access the list of Views. The Business Management Web Service requires Administrator's attention.` 

    如果 BAM 入口網站是設定在執行 .NET Framework 2.0 的應用程式所使用的網站上，則可能會發生此錯誤。 在此情況下，請將 BAM 入口網站架設在新的網站上。 若要加入網站，請參閱 [Create a Web Site (IIS 7)](http://go.microsoft.com/fwlink/p/?LinkID=196470) (建立網站 (IIS 7))。 建立網站之後，重新設定 BAM 入口網站：

    1. 開啟 [BizTalk Server 組態]。
    2. 選取 [取消設定功能]。 在 [取消設定功能] 中選取 [BAM 入口網站] 核取方塊，然後選取 [確定]。
    3. 從 [BAM 入口網站] 清單中選取新的網站，以重新設定 BAM 入口網站。

- **BizTalk 2016 Accelerator for SWIFT**：BizTalk Server 升級程序不會更新編輯過的 *BREDeployment.exe.config* 檔案。 在 `\Program Files\Microsoft BizTalk 2016 Accelerator for SWIFT\SDK\Tools` 資料夾的 *BREDeployment.exe.config* 檔案中手動變更路徑。

    此外，A4SWIFT Web 服務和 Message Pack 設定遺失。 BizTalk Server 升級之後重新設定這些項目。

## <a name="appendix-a-customer-experience-improvement-program"></a>附錄 A：客戶經驗改進計畫
做為在 BizTalk Server 中的客戶經驗改進計畫的一部分，您可以針對 BizTalk Server 的功能使用提供實用的意見，並反應給 Microsoft。 收集的資料會是匿名形式，無法用來識別您的身分。 加入這項計畫後，Microsoft 也會收集使用統計資料。

如果您參與這項計畫，將能協助我們改善 BizTalk Server 各項功能的可靠性和效能。 如需這項計畫和其隱私權原則的詳細資訊，請參閱 [Microsoft BizTalk Server CEIP 隱私權原則](http://go.microsoft.com/fwlink/p/?LinkId=188553)。

## <a name="appendix-b-known-issues"></a>附錄 B：已知問題

- **在管理電腦上設定 BAM 警示**：這是一個管理、執行階段和 SQL Server 元件安裝在不同電腦上的多重電腦環境。 當使用 BAM 工具或 BAM 警示時，可能會發生下列問題：

    **問題**：當您在 BizTalk 管理電腦上設定 BAM 工具時，發生下列錯誤：

    `Service BAMAlerts was not found on computer ‘.’.The specified service does not exist as an installed service.`

    **問題**：當您從執行階段電腦部署 BAM 活動定義時，發生下列錯誤：

    `A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)`

    如果在執行階段電腦上設定 BAM 警示就會發生這種情況。 若要解決，請在相同電腦上的 BizTalk 管理主控台中設定 BAM 警示。 請勿在執行階段電腦上設定 BAM 警示。

- **從失敗的升級復原**︰升級期間隨時都會發生升級失敗。 從升級失敗中復原的方式取決於每個階段中發生失敗的時間點而定。

  - 如果在安裝先決條件時升級失敗，安裝程式就會停止進一步安裝必要元件，並傳回錯誤訊息。 然後，您可以更正問題，並重新執行安裝程式。

  - 如果在升級資料庫、從現有的 BizTalk Server 版本中移除功能，或安裝新的版本時升級失敗，安裝程式會停止進一步安裝並傳回錯誤訊息。 所有變更都會復原。 對 BizTalk Server 資料庫所做的變更無法回復。

      如果 BizTalk Server 舊版安裝的元件在升級期間移除，您的電腦可能會處於沒有任何 BizTalk Server 元件的情況。 可能會保留舊版安裝的功能組態資訊。 而且根據升級程序失敗的位置，BizTalk Server 資料庫可能已經升級。 此時，您可能必須先還原之前備份的資料庫，然後再次執行安裝程式。

  - 如果在重新設定 BizTalk Server 功能時升級失敗，安裝程式會傳回完成程度的訊息。 如果設定升級失敗或部分成功，請執行 BizTalk Server 設定完成升級。

    如果升級持續失敗，且您需要回復至舊版 BizTalk Server，您必須還原已備份的資料庫，然後重新安裝舊版的 BizTalk Server。

- **使用相同的版本**：在 BizTalk 應用程式群組中，您無法執行具有不同 BizTalk Server 版本的電腦。 例如，在 BizTalk 管理主控台中，您無法將執行某版 BizTalk Server 的傳送埠繫結至執行不同版本 BizTalk Server 的接收位置。 

- **重新啟動 SSO 服務**：如果您在電腦上安裝舊版的 Visual Studio 或 .NET Framework 4.5，則舊版 BizTalk Server 中的 SSO 服務就會停止運作。 請從 Visual Studio 命令提示字元執行 `regasm SSOSQL.dll` 命令，以解決此問題。 此命令會重新啟動 SSO 服務。

    > [!NOTE]
    > 在 64 位元的電腦上，執行 32 位元和 64 位元版本的 regasm 命令。

- **無法使用 SOAP**：在平台升級之後，因為權限問題，您可能無法傳送 SOAP 訊息。 若要解決此問題，請使用下列文字來編輯 `C:\inetpub\wwwroot\<SOAPExternalAppName>\` 中的 Web.config 檔案：

    ```
    <securityPolicy>
    <trustLevel name="Full" policyFile="internal" />
    <trustLevel name="High" policyFile="web_hightrust.config" />
    <trustLevel name="Medium" policyFile="web_mediumtrust.config" />
    <trustLevel name="Low" policyFile="web_lowtrust.config" />
    <trustLevel name="Minimal" policyFile="web_minimaltrust.config"/>
    </securityPolicy>
    <trust level="Full" originUrl="" processRequestInApplicationTrust="true"/>
    ```

    您也可能必須將自訂錯誤模式從 [Remote Only (僅限遠端)] 變更為 [關閉]。

- **憑證存放區**：升級後，從 BizTalk Server 管理主控台開啟傳送埠或接收位置時，發生錯誤：`Could not open certificate store, the system cannot find the file specified (System).`。

    如果憑證存放區遺失就會發生此錯誤。

- **BAM 入口網站**：在 64 位元電腦上，升級之後就無法存取 BAM 入口網站。 可能的解決方案：

  1. 建立 `%BizTalkInstallDir%\BAMPortal\web.config` 的 web.config 檔案的備份副本。

  2. 使用 BizTalk Server Tracking 資料夾中的 bm.exe，在命令提示字元中執行下列命令：`bm.exe get-config –FileName:<filepath> -Server:MyServer -Database:MyDB`

     從 Config XML 檔案中取得 *BAMVRoot* 的值 (xpath: BAMConfiguration\ GlobalProperty\Name="BAMVRoot")。

  3. 在列為 BAMVRoot 值的電腦上開啟 BizTalk Server 組態，並取消設定 BAM 入口網站。

  4. 開啟 BizTalk Server 組態，並設定 BAM 入口網站。

  5. 從步驟 (1) 提及的位置開啟新的 web.config 檔案。

  6. 使用 web.config 檔案的備份副本，設定下列值 (在 `configuration\appSettings` 下)：

      - key="MainPageContentUrl"
      - key="AlertNotificationOptions"

     > [!NOTE] 
     > 在 64 位元電腦上，在您升級作業系統之後，我們建議您重新設定 BAM 入口網站。

- **部署 EDI BAM 活動**：升級時，升級可能只有部分成功。 當您升級 SQL Server (已設定 EDI) 時可能發生這種情況。 可能未正確升級 EDI BAM 活動。 若要解決此問題，請在命令提示字元中，使用系統管理認證執行下列命令，以部署 BAM 活動：

    `"<BizTalk Installation Folder>\Tracking\bm.exe" deploy-all -DefinitionFile:"<BizTalk Installation Folder>\AS2ResendActivityDefs.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

    `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.EdiAS2.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

    `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.Batching.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

- **叢集上的 SSO 錯誤**：在 BizTalk Server 執行階段叢集環境中，當您嘗試升級時，可能會收到錯誤訊息：

    `SSO Master Secret Server service is not running on <Cluster name>.Please start the service to continue the upgrade.` 

    若要解決此問題，請重新整理 SSO 和 BizTalk Server 執行階段叢集中的 SSO 服務。

    **重新整理 SSO 叢集中的 SSO 服務**：

  1. 在叢集系統管理員中，將包含叢集化企業 SSO 服務資源的叢集群組**上線**。 這樣應該會啟動叢集群組中的所有資源。

  2. [離線] 企業 SSO 服務的叢集執行個體。 然後，再讓它回到**線上**。

  3. [移動] 叢集群組。 這個步驟應該會將包含叢集企業 SSO 服務資源的叢集群組從第一個節點移動到第二個節點。

  4. [離線] 企業 SSO 服務的叢集執行個體。 然後，再讓它回到**線上**。

     **重新整理 BizTalk Server 執行階段叢集中的 SSO 服務**：

  5. 在叢集系統管理員中，將包含叢集化BizTalk Server 執行階段資源的叢集群組**上線**。 這樣應該會啟動叢集群組中的所有資源。

  6. [離線] 企業 SSO 服務的叢集執行個體。 然後，再讓它回到**線上**。

  7. [移動] 叢集群組。 這個步驟應該會將包含叢集 BizTalk Server 執行階段資源的叢集群組從第一個節點移動到第二個節點。

  8. [離線] 企業 SSO 服務的叢集執行個體。 然後，再讓它回到**線上**。
