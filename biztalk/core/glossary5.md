---
title: 一般詞彙和定義 |Microsoft 文件
description: 詞彙解釋，以便讓 BizTalk Server 及其意義
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac9c7c7d-a97e-425a-9666-02ca6edd8be6
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742b695338d7038f830b823af720bd3048399473
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="glossary"></a>詞彙
以下是「Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」中所採用的詞彙及其定義。  
  
## <a name=""></a>。  
  
|詞彙|定義|  
|----------|----------------|  
|.brl file (.brl 檔)|商務規則定義檔。|  
|.btm file (.btm 檔)|BizTalk Server 對應檔。|  
|.btp file (.btp 檔)|BizTalk Server 管線檔。|  
|.btproj|BizTalk 專案檔。|  
|.btt file (.btt 檔)|追蹤設定檔。|  
|.odx file (.odx 檔)|BizTalk Server 協調流程檔。|  
|.xsd file (.xsd 檔)|BizTalk Server 結構描述檔。|  
|||  
  
## <a name="a"></a>A  
  
|詞彙|定義|  
|----------|----------------|  
|action|對應到規則 "THEN" 部分的一或多個函數，用來指定條件為真時該執行哪些動作。|  
|Activate property (啟動屬性)|「接收」圖形的屬性，用來表示收到訊息時即啟動協調流程。 在協調流程中，可標示為啟動的「接收」圖形僅限於第一個傳送或接收的啟動圖形。|  
|activation block (啟動區塊)|活動模型內的一組步驟或動作。|  
|activation receive (啟動接收)|用於簡稱「接收」圖形的啟動屬性設定為 True 的表達方式。|  
|activity model (活動模型)|預先定義的一連串動作。 在啟動區塊中可以叫用這些動作序列。|  
|activity model step (活動模型步驟)|從活動模型的觀點而言，就是動作的同義字。 當動作包含於活動模型內時，就是所謂的活動模型步驟。|  
|activity node (活動節點)|包含里程碑和資料項目的節點，這些項目代表商務分析師有興趣的資料，他們透過 Microsoft Excel 精靈建立這些資料。|  
|activity window (活動視窗)|定義活動執行個體資料可見的時間週期。 這些資料永遠都在變更中，因為時間點永遠都在變更。 當透過活動視窗傳遞資料之後，您可以執行資料維護 DTS/SSIS 套件，將資料移到 BAM 封存資料庫。 當您將資料移到 BAM 封存資料庫之後，就無法再使用這些資料來進行 BAM 入口網站上的查詢。|  
|actor (執行者)|開始活動或參與活動的人或程序。 執行者可以是啟動者或目標。|  
|adapter (配接器)|COM 或 .NET 元件，協助在應用程式 (例如商業實務系統) 與 BizTalk Server 之間交換訊息。 配協器由設計階段元件和執行階段元件組成，進行接收和傳送的作業。|  
|adapter framework (配接器架構)|建置 BizTalk 配接器的規格，使用以 Web 服務為基礎的開放標準。|  
|addendum (增補)|協議的一小部分。 協議是由多個增補所組成，以定義採用的商務程序、您的角色、夥伴的角色、在此關係中使用的原則或參數，以及商務與法律條款等表列文件。|  
|affiliate application (分支應用程式)|企業單一登入 (Single Sign-On，SSO) 中的邏輯實體，由管理員定義，表示主機、後端系統或商業實務應用程式等應用程式的系統或子系統，您透過 SSO 與這些系統進行連接。 分支應用程式代表非 Windows 系統，如大型主機或 UNIX 電腦。 它也可以代表應用程式 (如 SAP)，或系統的子部分 (如 Benefits 或 Pay stub 子系統)。|  
|agenda (議程)|由規則引擎執行的排序規則動作清單。|  
|彙總 (aggregation)|資料表或結構，其中包含為線上分析處理 (OLAP) Cube 預先計算的資料。 彙總支援以快速及有效率的方式查詢多維度資料庫。|  
|agreement (協議)|關係組態中的闡述項目。 協議是以基礎的商務程序及合作對象管理成品為依據，而在您本身的設定檔與夥伴設定檔之間定義的， 且由一或多個增補所組成。 增補定義所使用的商務程序、貴組織和夥伴扮演的角色，以及關係中使用的參數。 協議也可以參考夥伴群組設定檔而不參考個別的夥伴設定檔。 這有助於管理和貴組織有完全相同的交易關係之所有夥伴。|  
|alert notification (警示通知)|用來通知使用者或一群使用者關於可顯示的特定預先定義情況的方法。|  
|alias|合作對象的別稱。 每個合作對象各有其指定的預設別名，包含組織名稱、OrganizationName 的辨識符號，以及合作對象名稱的值。 此別名永遠視為預設別名。 別名是由名稱、辨識符號和值三項組合而成的。 同一個 BizTalk 管理資料庫中的兩個合作對象，不可擁有相同的辨識符號值組。|  
|All、FirstMatch|管線階段的兩種執行模式。 All 表示階段中管線元件的線性執行。 FirstMatch 表示探索執行，其中第一個識別出訊息格式的元件會使用該訊息。 在線性執行中，階段中所有元件都依序執行後，才會將訊息傳遞到下個階段。|  
|ANSI X.12|由美國國家標準局 (American National Standards Institute) 開發出來的訊息格式。 美國主要使用 X.12 格式。|  
|應用程式配接器|建立與特定應用程式或通訊協定 (如 SQL) 搭配使用的配接器。|  
|封存的資料|已經由 BizTalk Server 處理而且儲存於適當資料庫的資料。|  
|artifact (成品)|最常稱為 BizTalk 應用程式的一部分 (此應用程式是 BizTalk 解決方案的一個邏輯單位)。 成品是透過 BizTalk Server 管理主控台進行管理和部署。 範例包括協調流程、管線、訊息結構描述、安全性憑證、商務規則原則和繫結。 成品也是 BizTalk 專案的一部分 (此專案是 BizTalk 解決方案的另一個邏輯單位)。 在此內容中，成品是用來產生 Visual Studio 中組成 BizTalk 解決方案的組件。|  
|assembler (組合器)|將個別文件結合到一個批次的管線元件。 BizTalk Server 中提供的組合器管線元件包括一般檔案組合器、BizTalk Framework 組合器和 XML 組合器三種管線元件。|  
|組件 (assembly)|BizTalk 應用程式中使用的 dll 檔案，內有協調流程、管線、結構描述、對應等資源，以及並非 BizTalk Server 特有的其他資源。|  
|assembly deployment (組件部署)|將組件的資源從 Visual Studio 部署至 BizTalk 應用程式的過程。|  
|Assembly Deployment Wizard (組件部署精靈)|BizTalk Server 2004 提供的精靈，能引導您執行新增、移除、匯入和匯出組件；匯入和匯出繫結；以及安裝或解除安裝全域組件快取 (GAC) 內各組件的必要步驟。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，匯入精靈、安裝精靈和匯出精靈均不再提供此功能。|  
|assembly version (組件版本)|組件的識別項，由主要版本和次要版本組合而成。|  
|atomic orchestration (不可部分完成的協調流程)|短期生效的交易，強迫 ACID (Atomicity、Consistency、Isolation 和 Durability) 交易的認可和回復，與使用 DTC 服務的 COM+ 應用程式相似。|  
|屬性|在 XML 中，用來關聯其他資訊與 XML 項目的 XML 建構。|  
|信任的驗證|標示每個應用程式的方法，指示應用程式可以提交訊息到訊息方塊，該訊息方塊的合作對象識別碼 (PID) 與應用程式執行個體服務帳戶的 Windows 安全性識別碼不同。|  
  
## <a name="b"></a>B  
  
|詞彙|定義|  
|----------|----------------|  
|BAM|請參閱 Business Activity Monitoring (BAM) (商務活動監控)。|  
|BAM activity (BAM 活動)|BAM 根據所要監控的工作單位而擷取的端對端里程碑和資料之清單。 例如，貸款申請活動可能包含如「已核准貸款」的里程碑，以及如「申請者名稱」和「貸款金額」等資料。 BAM 活動通常直接對應到商務程序。|  
|BAM alert (BAM 警示)|由 BAM 基礎結構 (特別是 SQL Server Notification Services) 所產生的通知，以提醒收件者有特定狀況發生。 使用者定義警示的條件，而自動化服務則在這些條件符合時產生警示。|  
|BAM checkpoint (BAM 檢查點)|也稱為 Excel BAM 增益集中的項目。|  
|BAM Configuration (BAM 組態)|含有 BAM 資訊清單之各項設定 (如 BAM 主要匯入資料庫和伺服器名稱) 的 XML 檔案。|  
|BAM definition (BAM 定義)|BAM 觀察模型的 XML 表示法。|  
|BAM Framework (BAM 架構)|一組受管理的 API，支援動態建立的基礎結構和事件集中。|  
|BAM infrastructure (BAM 基礎結構)|由 BAM 資料庫 (主要匯入、封存、星狀結構描述和分析) 中的 SQL Server 資料表、BAM 檢視、預存程序以及 Data Transformation Services (DTS) 封裝所組成，這些項目是透過 BAM 定義的累加部署所設定和管理。 此基礎結構即是執行階段時，事件相互關聯、彙總，然後可供使用者查詢的地方。|  
|BAM Manager (BAM 管理員)|管理商務活動監控動態基礎結構的內部元件。|  
|BAM observational model (BAM 觀察模型)|商務程序中可見性需求的高階定義，詳細說明里程碑和蒐集的資料事件 (BAM 活動)、任何資料彙總的描述，以及向使用者呈現資訊的方式 (BAM 檢視)。|  
|BAM view (BAM 檢視)|構成 BAM 活動的資料依特定角色區別的觀點。 檢視中包含篩選的資料、所篩選資料的彙總，以及呈現篩選資料的方式，例如樞紐分析圖報表。 每個 BAM 活動支援一或多個檢視的定義。|  
|base data item (基底資料項)|在 BAM 中，做為維度或量值之基準的活動項目。 例如，基底資料項「產品識別碼」可做為「計數」量值 (特定產品銷售數量) 之基準。|  
|繫結|軟體元件與軟體層連結在一起的程序。 安裝網路元件時，便會建立元件的繫結關聯性與相依性。 繫結使元件得以彼此通訊。 在 BizTalk Server 中，此為協調流程配接器-不特定結束點 (連接埠或角色連結) 與實體配接器-特定結束點 (傳送埠/接收埠或合作對象) 之間的已建立對應。|  
|binding file (繫結檔案)|包含繫結之快照的檔案，此快照正是擷取當時的繫結狀態。 它不包含與協調流程相關的繫結的完整細節。|  
|BizTalk Administration console (BizTalk 管理主控台)|用來管理 BizTalk Server 群組的 Microsoft Management Console (MMC)。|  
|BizTalk Administrators group (BizTalk 系統管理員群組)|管理 BizTalk Server 的群組。 管理工作包括存取訊息擱置佇列、更新組態資料庫等等。|  
|BizTalk application (BizTalk 應用程式)|集中公開的一組相關成品、資源及設定，可從 BizTalk 管理主控台內部進行管理。 應用程式中的任何成品可能參考該應用程式中的其他任一成品，甚至參考任何所參考之應用程式中的任一成品。|  
|BizTalk Application 1 (BizTalk 應用程式 1)|每次全新安裝 BizTalk Server 時預設建立的應用程式。 建立此應用程式主要是基於回溯相容性。 部署時未指定應用程式的成品均顯示於此資料夾中。 此外，未指定應用程式的新成品一律部署至 [預設應用程式]。 其他任何應用程式則可藉由變更使用者設定而設定為預設應用程式。|  
|BizTalk Application Users group (BizTalk 應用程式使用者群組)|可以存取特定 BizTalk 群組的 MessageBox 的使用者群組。|  
|BizTalk Application view (BizTalk 應用程式檢視)|開啟 BizTalk Server 的 System Center Operations Manager 主控台時所顯示的兩個檢視之一 (另一個是 [BizTalk 部署檢視])。 BizTalk 系統管理員會使用這個檢視來監視 BizTalk Server 成品和應用程式的健全狀況，如協調流程、傳送埠和接收位置。|  
|BizTalk assembly (BizTalk 組件)|Microsoft Windows DLL 檔案，包含 BizTalk Server 商務方案中所使用的資源資訊，例如協調流程、管線、結構描述及對應。 組件還有其版本號碼、文化特性，以及公開金鑰 Token。|  
|BizTalk Deployment view (BizTalk 部署檢視)|開啟 BizTalk Server 的 System Center Operations Manager 主控台時所顯示的兩個檢視之一 (另一個是 [BizTalk 應用程式檢視])。 企業 IT 管理員會使用這個檢視來監視 BizTalk Server 安裝程式之「實體部署」的整體健全狀況。|  
|BizTalk Editor (BizTalk 編輯器)|裝載於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 內的視覺化工具，用來建構 BizTalk Server 結構描述，可定義 XML 格式和原生格式執行個體訊息兩者的結構。|  
|BizTalk Explorer (BizTalk 總管)|Visual Studio 工具視窗，顯示 BizTalk 組態資料庫的內容。 它在階層樹狀結構中顯示的項目如組件、連接埠和合作對象。 您可以使用 BizTalk 總管設定和管理 BizTalk 專案、合作對象和協調流程。|  
|BizTalk Explorer Object Model (BizTalk 總管物件模型)|用來建立工具和指令碼的 API，可以自動化在 BizTalk 總管中執行的後部署工作。 您可以將 BizTalk 總管物件模型用於後續部署工作，例如建立連接埠、繫結協調流程、管理合作對象屬性，或是任何其他會用到 BizTalk 總管的工作。 BizTalk 總管物件模型 API 位於 Microsoft.BizTalk.ExplorerOM 命名空間內。|  
|BizTalk Framework|一種平台中性電子商務架構，以延伸標記語言 (XML) 結構描述和產業標準為建構基礎。 這種架構可以整合產業和各種商務系統，無論平台、作業系統或基礎技術為何。|  
|BizTalk 群組|包含 MessageBox、主控件、接收位置、傳送埠、傳送埠群組、協調流程、伺服器和配接器的群組。|  
|BizTalk host (BizTalk 主控件)|BizTalk Server 中的邏輯程序與安全性界限。 每個主控件各有其指派的安全性群組，並且可能包含多個主控件執行個體，分別位於不同的電腦以執行該主控件的工作。 因而，每個主控件執行個體均隸屬於單一主控件，主控件執行個體的服務帳戶則隸屬於該主控件的安全性群組。 安全性群組可用來授與主控件的任一主控件執行個體使用實體資源 (如資料庫) 的權限。|  
|BizTalk Management Pack alert (BizTalk 管理封包警示)|系統管理員可以在 BizTalk Server 管理組件中訂閱通知。 訂閱某個警示之後，只要符合特定條件，系統管理員就會收到通知。 例如，若進行節流的主控件執行個體達到特定數目，即可能引發警示。|  
|BizTalk Management Pack diagnostics (BizTalk 管理封包診斷)|系統管理員可以使用這項功能來查看某個問題的原因和疑難排解資訊。 例如，若傳送埠的健全狀況呈現紅色，則 Operations Manager 主控台的 [狀態變更事件] 索引標籤會顯示健全狀況由綠變紅的原因。|  
|BizTalk Mapper (BizTalk 對應工具)|裝載於 Visual Studio 內的視覺化工具，用來建構 BizTalk 對應以定義資料轉換。|  
|BizTalk 訊息佇列|BizTalk Server 中的訊息佇列傳輸元件。 它隨附為 BizTalk Server 產品的內部核心元件，也是 BizTalk Server 眾多配接器元件之一。|  
|BizTalk message store (BizTalk 訊息儲存區)|Microsoft SQL Server 資料表，此資料表儲存所有訊息與其部分。 取用協調流程使用儲存區中包含的訊息參考，取消在訊息儲存區中訊息副本及其屬性的佇列。|  
|BizTalk project (BizTalk 專案)|Visual Studio 專案類型之一，用來建立在 BizTalk Server 上執行的應用程式。|  
|BizTalk project file (.btproj) (BizTalk 專案檔)|包含 BizTalk 專案之專案特有設定的檔案。|  
|BizTalk project system (BizTalk 專案系統)|用來建立部分或整個 BizTalk Server 應用程式或商務方案的系統。 您可以用此系統新增、編輯或移除 BizTalk Server 項目 (協調流程、對應、結構描述和管線)。 該系統包含如編譯和部署之類的命令。|  
|BizTalk Server 管理組件|一項 BizTalk 增強功能，有助於確保對 BizTalk 應用程式和基礎結構的完整監視能力。 其中包含診斷和警示等功能，可協助監視 BizTalk 部署的健全狀況。|  
|BizTalk Server Administration (BizTalk Server 管理)|用來管理伺服器和其屬性，BizTalk Server 群組，監視的 Microsoft Management Console (MMC) 介面接收函式，並監視工作項目在 Microsoft SQL server 群組所使用的伺服器佇列。|  
|BizTalk Server map file (.btm) (BizTalk Server 對應檔案)|BizTalk 對應的永久格式，由 BizTalk 對應工具建立並編譯，以產生使用「可延伸樣式表語言轉換」(Extensible Stylesheet Language Transformations，XSLT) 指定的執行階段轉換指示詞。|  
|BizTalk Mapper (BizTalk 對應工具)|這項功能可讓使用者以視覺化方式在 BizTalk 應用程式中建立兩個結構描述之間的轉換。 同時具有使用性增強功能，有助於處理複雜的對應。|  
|BizTalk Server Messaging Engine (BizTalk Server 傳訊引擎)|中介軟體產品所需要的一組服務，幫助客戶實例執行解決方案。 這些執行階段服務是 BizTalk Server 平台的基本部分。 在這些服務間是訊息的可執行管線處理。 管理處理提供資料格式標準化和屬性擷取。|  
|BizTalk Server pipeline file (.btp) (BizTalk Server 管線檔案)|描述管線組態與其中之元件的檔案。 這種檔案類型可以編譯為 BizTalk 專案的一部分。|  
|BizTalk Server schema (BizTalk Server 結構描述)|以 XML 結構描述定義語言 (XSD) 為基礎、一或多個 BizTalk Server 執行個體訊息的結構描述。|  
|BizTalk Server schema file (.xsd) (BizTalk Server 結構描述檔案)|包含 BizTalk 結構描述之永久格式的檔案。|  
|BizTalk 設定儀表板|BizTalk 系統管理員可以使用這項 BizTalk 功能，集中管理與修改 BizTalk 引擎設定。 系統管理員可以在不同環境之間匯出與匯入設定，例如從臨時環境到實際執行環境。|  
|body part (內文部分)|請參閱 message body part (訊息內文部分)。|  
|BTSTask|用於管理應用程式和組件的命令列工具。 您可以使用 BTSTask 將 BizTalk 應用程式加入 BizTalk 管理資料庫、在應用程式中加入資源、將應用程式匯出至 MSI 檔案、將繫結資訊匯出至檔案、從 MSI 檔案匯入應用程式、從檔案匯入繫結資訊、列出應用程式中的所有資源、列出 BizTalk 管理資料庫中的所有應用程式、列出 MSI 檔案的內容、從 BizTalk 管理資料庫和 BizTalk 管理主控台移除應用程式，以及從應用程式移除資源。|  
|商務活動監控 (BAM)|BizTalk Server 功能，讓商務使用者即時檢視他們的不同商務程序，讓他們能夠制定重要的商業決策。|  
|Business Activity view (商務活動檢視)|顯示商務程序的一組階層檢視，可為特定類別的商務使用者定義商務活動的檢視方式。 相同的商務活動資料 (BAM 追蹤) 可能有一種以上的解讀方式。|  
|business analyst (商務分析師)|擁有企業管理和經濟分析技能的使用者。 商務分析師主要的責任是取用商業層級的資料並針對商務趨勢進行分析。|  
|business end user (商務使用者)|負責監控和疑難排解商務程序及 (或) 商務訊息交換的知識工作者。 此使用者不需要是技術人員。|  
|Business Process Configuration services (商務程序組態服務)|讓商務使用者透過商務原則來設定和管理較低層級協調流程項目的工具。 開發人員或 ISV 使用這些工具定義商務程序後，即可利用商務原則和參數設定這些程序。|  
|Business Process Workspace (商務程序工作區)|讓商務經理人追蹤和管理 SharePoint Team Services 中所有商務程序的介面。|  
|business profile (商務設定檔)|組織的商務面孔。 組織內每個與其他組織內的其他商務部門往來交易的商務部門，都會以交易夥伴管理 (TPM) 方案中的某個商務設定檔表示。 商務部門、商務單位或商務系統所有專屬用來定義 B2B 傳訊參數的屬性，都會放在其商務設定檔中。|  
|Business Rule Composer tool (商務規則編輯器工具)|用來編寫原則的圖形使用者介面工具。|  
|商務規則引擎|根據事實評估規則，並依照其評估結果啟始動作的執行階段推斷引擎。|  
|Business Rule Language (商務規則語言)|XML 格式的規則標記語言，做為宣告規則定義。|  
|B2B|業務類別關係，特指商業機構和消費者除外的其他買方 (例如政府機構、公司及轉售商) 之間的交易及相關活動。 意指商業機構彼此間溝通或銷售的關係。|  
  
## <a name="c"></a>C  
  
|詞彙|定義|  
|----------|----------------|  
|calculated duration (計算持續時間)|可以使用自訂公式計算資料行的屬性。|  
|code list (代碼清單)|一對縮寫/解釋組，做為設計階段的輔助，提供 XML 結構描述定義語言 (XSD) 列舉值組。|  
|command-line deployment tool (命令列部署工具)|用來新增、移除、匯入和匯出組件；匯入和匯出繫結；以及安裝或解除安裝全域組件快取 (GAC) 內部組件的工具。|  
|commit change request (認可變更要求)|請參閱＜其他詞彙：end type change request (結束類型變更要求)＞|  
|communication pattern (通訊模式)|決定連接埠上的通訊是單向或雙向 (要求-回應) 的屬性。|  
|compensation (補償)|旨在復原或減弱認可交易的效果的一組動作。|  
|Compensation tab (補償索引標籤)|用來新增補償到協調流程的設計介面。|  
|compile (編譯)|在 BizTalk Server 內容中，將 BizTalk Server 項目的設計階段表示法 (如結構描述、對應和協調流程) 轉換為其執行階段的對等物件 (存放於 Visual Studio 組件) 的過程。|  
|Composition service (組合服務)|處理動作啟動、干擾功能和工作回應傳送的元件。 服務會組成動作通訊協定訊息，再將它們傳送到 HTTP 待命程式，接著傳送到 MessageBox 資料庫以供取用。|  
|condition (條件)|規則的 "IF" 部分，用來指定應該要評估的條件，也就是以評估為真或假的單一邏輯運算式來表示。 條件可以延伸以支援使用者定義條件。|  
|configuration cache refresh Interval (組態快取重新整理間隔)|收取 BizTalk 群組 (如 SMTP 主機) 的一般屬性所做之變更的秒數間隔。 此間隔設定為群組組態的一部分。 當 BizTalk Server 啟動後，BizTalk Server 管理中所有的項目 (例如：MessageBox 資料庫、伺服器屬性、配接器以及追蹤資料庫的連線) 均儲存於管理快取中。 根據預設，快取中所有的項目每隔 60 秒會重新整理一次，但伺服器資料庫連線和伺服器屬性除外。|  
|Configuration database server name (組態資料庫伺服器名稱)|UI 項目。 管理資料庫 (組態資料庫) 所在的伺服器名稱。|  
|connector (連接器)|與交易夥伴或內部系統交換文件的通訊服務。|  
|connector point (連接器端點)|協調流程設計師中的項目，讓使用者連接「傳送」/「接收」圖形與連接埠作業。|  
|constraint (條件約束)|限制活動模型內根動作之啟動者及任何其他動作之目標的屬性。|  
|以內容為基礎的路由|根據從文件內容擷取的資訊作為文件路由。 在 BizTalk Server 中，在傳送埠和協調流程上使用文件屬性升級和篩選條件運算式，可以進行以內容為基礎的路由。|  
|continuation (接續)|指使用兩個不同的唯一識別碼作為 ActivityID，從不同的應用程式完成單一 BAM 活動的能力。 例如，在商務程序的某一部分中，可能會使用客戶的訂單號碼來追蹤某項活動。 在該程序的另一個部分中，則可能會使用內部訂單履行號碼來追蹤同一項活動。 您可以啟用接續功能，並使訂單號碼與訂單履行號碼產生關聯，如此一來，該程序的兩個部分便可以新增資訊到同一項活動。|  
|Continuation token (接續 Token)|從「應用程式 1」送出的一段唯一資訊。|  
|conversion rate (轉換率)|用於將網站的基準貨幣轉換成買方貨幣或供應商貨幣的乘數。 儲存於 SDK Order Sitelet 中的轉換率僅供示範用途，且應交由具有公信力的第三方或生產網站上的會計系統定期追蹤。|  
|correlation|指將內送訊息對應到適當協調流程執行個體的程序。 此對應是透過訊息中使訊息連結到協調流程的屬性來進行。 如果與同一個商務程序有關的訊息包含不相容的屬性 (例如訂單結構描述具有 POId 項目，而搭配的發票結構描述具有 OrderID 項目)，則開發人員會透過建立屬性結構描述，並讓這些屬性結構描述包含這些項目的抽象化屬性名稱，來達到相互關聯的目的。|  
|correlation ID (相互關聯識別碼)|隨機產生的識別碼，與訊息關聯，並隨著指定訊息的存續期一起傳遞。|  
|correlation set (相互關聯集合)|相互關聯類型的執行個體；也就是用來決定訊息是否屬於協調流程指定執行個體的列出屬性。|  
|correlation type (相互關聯類型)|一組訊息屬性，做為商業程序的唯一識別，用來相互關聯訊息與協調流程執行個體。|  
|culture (文化特性)|文字和資料的語言及可當地語系化的屬性。|  
|custom adapter (自訂配接器)|由開發人員撰寫的自訂程式碼，放在接收管線之前或傳送管線之後，當作配接器和 (或) 應用程式的介面。|  
|custom numbers (自訂編號)|由計數器指派的編號數列，每個編號的值以一為單位遞增。|  
|cyclical reference (循環參考)|XML 結構描述的模式，其中子系節點宣告為與其中上階節點的相同複雜類型，因此可以建立可以有無限深度、表示執行個體訊息的結構描述。|  
  
## <a name="d"></a>D  
  
|詞彙|定義|  
|----------|----------------|  
|Data Description Language (DDL) (資料描述語言)|用來定義資料及其與其他資料之關係的語言。 用來在資料庫內建立資料結構。 多數資料庫管理系統 (DBMS) 都使用 SQL 資料描述語言。|  
|data dimension (資料維度)|在追蹤設定檔編輯器建立為階層式檢視的特定節點，做為特定追蹤設定檔的直接子系，以便描述邏輯群組或資料維度。 每個資料維度都有唯一名字，而且由一或多個資料欄位組成。|  
|data item (資料項目)|在追蹤設定檔編輯器中建立為階層式檢視的特定節點，為資料類別的直接子系。 資料欄位存在為商務內容的特定欄位。|  
|data mapping (資料對應)|設計階段程序，定義來源結構描述中節點與目的結構描述中節點之間的對應。|  
|DDL|請參閱 Data Description Language (資料描述語言)。|  
|default host (預設主控件)|方便部署和協調流程登錄的管理物件。 這些物件在 BizTalk Server 管理主控台中以核選符號加以識別。 在協調流程登錄程序期間，會自動使用預設主控件來裝載協調流程，除非使用者明確選取不同的主控件。|  
|default pipelines (預設管線)|已編譯且部署的 BizTalk Server 組件，包含已設定階段的管線及管線元件。|  
|dehydrate (凍結)|當協調流程閒置特定時間後，用來將正在執行的協調流程狀態儲存至永久存放區，並從記憶體中移除。|  
|delimited flat file (分隔式一般檔案)|用來表示商務文件的檔案格式類型，其中記錄和記錄內的欄位會以特定字元或字元序列加以分隔。|  
|分隔符號 (delimiter)|一或多個特殊字元，在任何層級 (欄位、記錄等) 的分隔結構中用來分隔同層物件。|  
|demotion (降級)|從內容屬性將日期/時間資料撰寫到文件內容裡的動作。|  
|Destination database (目的資料庫)|與 BizTalk Server 一起安裝時唯一支援的目的資料庫，儘管 BAM 事件匯流排服務基礎結構支援多個目的資料庫。|  
|destination schema (目的結構描述)|BizTalk Server 對應中使用的結構描述，表示輸出執行個體訊息的結構。|  
|Development Tools Environment (DTE) (開發工具環境)|讓開發人員能以程式設計方式透過整合式開發環境 (IDE) 達成許多主要工作的一組介面。|  
|維度階層|一種邏輯樹狀結構，它將維度的各個成員組織起來，使每個成員都有一個父成員及零或多個子成員。|  
|維度層級|指出一組資料項目視為是維度階層各層級的項目。 DataPerspective 定義是由 OLAP 維度階層所產生的。|  
|disassembler pipeline component (解譯器管線元件)|將一批訊息分開到個別文件的管線元件。 BizTalk Server 所提供的解譯器管線元件包括：一般檔案解譯器、BizTalk Framework 解譯器和 XML 解譯器。|  
|distinguished field (辨別欄位)|訊息中的 .NET 類別成員或 XML 結構描述定義語言 (XSD) 結構描述欄位，已明確提供給協調流程用於運算式及自訂管線元件中，做為寫入的屬性欄位。 不能用於篩選條件運算式中。|  
|distributed transaction coordinator (DTC) (分散式交易協調器)|與 COM+ 整合的服務，讓分散式交易可以運作。  DTC 讓交易可以從一個電腦延展到許多電腦上，而不需要特別的程式碼。|  
|DMZ|非軍事區域。 請參閱 perimeter network (周邊網路)。|  
|document (文件)|在 EDI 中為一組邏輯結合的區段。 文件類型包括：發票、運輸訂單、客戶宣告等。|  
|文件類型定義 (DTD)|可以描述 XML 文件結構的數種方式之一。 BizTalk Server 可以開啟以 DTD 描述的結構描述，並在程序中將它轉換為 XSD。|  
|DTC|請參閱 distributed transaction coordinator (DTC) (分散式交易協調器)。|  
|DTD|請參閱 document type definition (DTD) (文件類型定義)。|  
|DTE|請參閱 Development Tools Environment (DTE) (開發工具環境)。|  
|duration|指示 BAM 編譯器在表示檢查點之間持續時間的檢視中建立其他資料行的項目。|  
|dynamic adapter (動態配接器)|有自訂使用者介面的配接器。|  
|dynamic binding (動態繫結)|在執行階段套用到連接埠的連接埠繫結，一般是從訊息屬性 (如回覆位址) 衍生來的。|  
|dynamic policy update (動態原則更新)|使用規則引擎更新服務在執行階段擷取原則。|  
|dynamic port (動態連接埠)|沒有目的位址也沒有關聯的配接器類型的傳送埠。 動態傳送埠允許在執行階段執行期間將其自身與目的位址和配接器類型建立關聯，因此提供使用相同連接埠傳送訊息至使用不同配接器類型的目的彈性。|  
  
## <a name="e"></a>E  
  
|詞彙|定義|  
|----------|----------------|  
|EDI|請參閱 electronic data interchange (EDI) (電子資料交換)。|  
|EDIFACT|請參閱 Electronic Data Interchange for Administration, Commerce and Trade (EDIFACT) (管理、商務和商業的電子資料交換)。|  
|EDIFACT UNOA syntax (EDIFACT UNOA 語法)|僅允許下列的 EDIFACT 語法字元： 大寫字母、 所有數字，保留空白，驚嘆號 （！）、 引號 （"）、 百分比符號 （%）、 連字號 (&)、 左和右括號 ("("and")")、 星號 （*）、 逗號、 虛線 （-），小數點 （.），斜線 （/）、 分號 （;），較不-符號 (\<)，和更新版本-符號 (\>)。|  
|EDIFACT UNOB syntax (EDIFACT UNOB 語法)|僅字元可讓下列的 EDIFACT 語法： 小寫及大寫字母、 所有數字，保留空白，驚嘆號 （！）、 引號 （"）、 百分比符號 （%）、 連字號 (&)、 單一引號 （'）、 左右括號 （"（"和")")、 星號 （*）、 加號 （+）、 逗號、 虛線 （-）、 小數點 （.）、 可轉送斜線 （/）、 冒號 （:）、 分號 （;），較不-符號 (\<)，等號 （=）、 大於-符號 (\>)，和問號 （？）。|  
|EIF|請參閱 Engine Input File (EIF) (引擎輸入檔)。|  
|EIP|請參閱 Enterprise Integration Platform (EIP) (企業應用系統整合平台)。|  
|electronic data interchange (EDI) (電子資料交換)|兩台電腦應用程式之間已建立結構及標準化文件的電子交換，使用一組標準來控制電腦之間文件的傳輸，例如訂單及發票。|  
|Electronic Data Interchange for Administration, Commerce and Trade (EDIFACT) (管理、商務和商業的電子資料交換)|全世界的電子資料交換 (EDI)|  
|element|在 EDI 中文件中的最低層級資訊。 例如，發票編號。 在 XML 中，以階層方式組織資訊的 XML 建構，在其他項目內套疊一些項目，具有無限深度。|  
|element groups (項目群組)|XML 結構中同層級項目的群組，依不同的條件約束分組：順序序列 (序列群組)、無順序序列 (所有群組) 以及一對多 (選擇群組)。|  
|encoding agreement (編碼協議)|指兩個交易夥伴的商務設定檔之間，規定要使用特定編碼通訊協定 (X12 或 EDIFACT) 來交換訊息的協議。|  
|encoding protocol (編碼通訊協定)|指負責控管 B2B 訊息結構和內容的通訊協定。 商務設定檔的編碼通訊協定設定會定義商務部門用來傳送和接收 B2B 訊息的編碼通訊協定。 編碼通訊協定的一些範例包括 X12、EDIFACT、HIPAA 和 EANCOM。|  
|加密金鑰|用來加密或解密認證資訊的字串。|  
|end type change request (結束類型變更要求)|使用管理主控台或 BTSTask 匯入 BizTalk 應用程式 MSI 檔案期間，將成品類型部署至目的端電腦的最後階段。 也稱為認可變更要求，或認可匯入特定成品類型。|  
|端點|位置的邏輯表示法，一般以 URL 形式表達，為擷取或傳送的資料提供實體位址。|  
|Engine Input File (EIF) (引擎輸入檔)|文件結構描述的編譯版本。 EIF 用來促進翻譯，在非公開使用者群組內其他使用者之間散佈。 只要使用 BizTalk Server 產生或編輯 XML 結構描述定義語言 (XSD) 結構描述，就會自動編譯 EIF。|  
|enlist (登錄)|將協調流程與其執行所在實體環境建立關聯的程序。 其中包括：指定傳輸訊息到協調流程或從協調流程傳輸訊息所需的配接器、指定用於裝載協調流程的應用程式程序，並建立路由指示的 MessageBox 訂閱。|  
|enterprise application integration (企業應用程式整合)|將企業應用程式中的資料或功能與其他應用程式中的資料或功能結合在一起的程序。|  
|Enterprise Integration Platform (EIP) (企業應用系統整合平台)|企業應用程式進行整合的環境。 此實例實際是將同類的實例群組成單一實例。|  
|Enterprise Single Sign-On system (企業單一登入系統)|SSO 資料庫、主要密碼伺服器以及一或多個企業單一登入 (SSO) 伺服器。 這些伺服器會在 Windows 與非 Windows 認證間進行對應，在 SSO 資料庫中尋找認證，然後用來管理 SSO 系統。 SSO 資料庫也做為組態存放區，保留配接器的自訂組態資料。|  
|envelope (信封)|有結構的一組資訊，包裝並伴隨執行個體訊息，通常是用來描述傳遞和處理資訊。 信封可以巢狀堆疊。|  
|envelope schema (信封結構描述)|結構描述的類型，指定信封的結構，使用信封專用的數個額外屬性，指定諸如識別信封資料流中信封內容的資訊。|  
|execution cycle (執行循環)|商務規則引擎內的事實判斷提示、條件評估和動作執行。|  
|執行模式|管線階段屬性，決定階段中管線元件的執行模式。 執行模式可以設定為「全部」或「第一個符合的階段」。 在「全部」模式下，階段內的所有元件會依設定的序列依次執行。 當需要數個元件完成特定邏輯工作，且必須全部執行時，請使用此模式。 如果任何元件在處理此管線階段的訊息時碰到錯誤，就會發生執行階段錯誤。|  
|Export Wizard (匯出精靈)|從 BizTalk 管理主控台啟動的精靈，用於從 BizTalk 應用程式產生 MSI 檔案。 接著便可將此 MSI 檔案複製到不同的 BizTalk Server 執行個體，然後使用匯入精靈來匯入 MSI 檔案的資源。|  
|express delivery (快遞)|暗指永久性 (儲存於 SQL 資料庫內) 的訊息傳遞類型，指內送訊息及外寄訊息兩者。|  
|可延伸樣式表語言轉換 (XSLT)|從原先的 Extensible Stylesheet Language (XSL) 標準進化而來。 XSL 指定 XML 資料簡報和資料轉換的語言定義。 資料簡報表示以某種格式和 (或) 媒體顯示資料，並與樣式有關。 資料轉換則是指將輸入 XML 文件剖析到節點樹狀結構，接著再將來源樹狀結構轉換為結果樹狀結構。 轉換與資料交換有關。|  
|external message format (外部訊息格式)|由 BizTalk Server 處理之前或之後的訊息格式。 指稱外部訊息格式時有時候也會使用 "wire" 格式一詞。|  
  
## <a name="f"></a>F  
  
|詞彙|定義|  
|----------|----------------|  
|facet|XML 結構描述定義語言 (XSD) 概念，限制項目或屬性可以採用的值，為結構描述的執行個體提供驗證參數。 例如，可以指定字串資料的最小及最大長度。 不同類型的 facet 套用至不同類型的資料。|  
|事實|套用規則條件的使用者資料。 在設計階段，事實是該資料的參考。|  
|fact base (事實資料庫)|評估規則條件所根據的事實集合。|  
|fact retriever (事實擷取器 (規則引擎))|實作 IFactRetriever 介面、由使用者定義的選擇性外掛程式元件，因此可收集長期事實以供商務原則使用。|  
|fact store (事實存放區)|儲存執行者的資訊 (包括角色和屬性) 的資料庫。 事實存放區也提供階層式巡覽，這樣動作可以決定組織內執行者的相對位置。|  
|fact store manager (事實存放區管理員)|從各種 FactRetriever 物件擷取事實資訊的元件。|  
|failover transport (容錯移轉傳輸)|一種次要傳輸。|  
|fallback trading partner agreement (後援交易夥伴協議)|在沒有明確協議的情況下，BizTalk Server 用於處理 B2B 訊息的設定集合。|  
|File adapter (FILE 配接器)|可從檔案系統讀取訊息然後傳送到伺服器的配接器。 FILE 配接器也會將伺服器傳來的訊息寫入檔案系統上的檔案中。|  
|Filter Expression property (篩選條件運算式屬性)|決定可以接收哪些訊息的接收圖形的屬性。 接收圖形必須將啟動屬性設定為真才能具有篩選條件運算式。|  
|Find Message view (尋找訊息檢視)|讓使用者根據追蹤的訊息屬性尋找訊息的報告檢視。|  
|FTP 配接器|能夠在 BizTalk Server 與 FTP 伺服器之間交換檔案的配接器。|  
|函數|用來存取動作和述詞定義兩者中類別成員的抽象概念。 函式用於動作中，而且做為述詞中的詞彙。|  
|functoid (運算質)|執行特定計算或資料操作的可執行模組，建構 BizTalk Server 對應時以圖形方式使用，以自身為 XSLT 隨附的更豐富資訊提供基礎。|  
|運算質 IntelliSense|一項 BizTalk 對應工具功能，當運算質組態有錯誤時，此功能會在格線表面上提供視覺提示。|  
|functoid toolbox (運算質工具箱)|Visual Studio 中的可停駐視窗，做為對應建構期間可用之運算質的工具板。 運算質根據其使用目的組織成不同的工具箱索引標籤。|  
  
## <a name="g"></a>G  
  
|詞彙|定義|  
|----------|----------------|  
|GAC|請參閱 global assembly cache (全域組件快取)。|  
|global assembly cache (GAC) (全域組件快取)|BizTalk Server 上的容器，針對存放相同組件的群組，為該群組部署到組態資料庫。|  
|global port (全域連接埠)|用於關聯連接埠與夥伴設定檔的易記名稱。|  
|group header (群組標頭)|在 EDI 中，用來指示文件功能群組的開頭的訊息部分。|  
|group-level setting (群組層級設定)|BizTalk 系統管理員可以在 [BizTalk 設定儀表板] 中修改的其中一項設定。 其範例包括組態重新整理間隔、訊息批次大小上限和群組層級追蹤等屬性。|  
|group trailer (群組結尾)|在 EDI 中，用來指示文件功能群組的結尾的訊息部分。|  
|GS segment (GS 區段)|在 EDI 中，相同文件類型的一組 ANSI X.12 文件 (交易集) 的功能群組標頭區段。 這需要區段包含有關交換中交易集群組的資訊，如應用程式傳送者代碼 ( Application Sender Code)、應用程式接收代碼 (Application Receive Code)、群組控制編號 (Group Control Number)、版本/發行/產業識別碼 (Version/Release/Industry ID) 等。|  
  
## <a name="h"></a>H  
  
|詞彙|定義|  
|----------|----------------|  
|handler (處理常式)|執行配接器的 BizTalk 主控件的執行個體。|  
|hash (雜湊)|對任意資料量套用單向數學函式 (有時稱為雜湊演算法) 所獲得的固定大小結果。 如果輸入資料有所變更，雜湊會隨之變更。 雜湊可用於多種作業，包括驗證及數位簽章。 也稱為訊息摘要。|  
|健康情況監控|監控應用程式、元件及實作 BizTalk Server 解決方案之伺服器的程序，達到預先偵側或修正問題的目的。|  
|Health Monitoring cube (狀況監控 Cube)|包含訊息和服務相關資訊的線上分析處理 (OLAP) Cube。 BizTalk Server 隨附的兩個 Cube 為「訊息事實」與「服務事實」。|  
|hierarchical view (階層檢視)|追蹤設定檔編輯器 (TPE) 的左窗格及報告命名空間和建立 [商務活動] 檢視的區域。 主要目的在於表示追蹤設定檔。|  
|History database (歷程記錄資料庫)|「商務程序管理」實例專用的後端資料庫。|  
|主機|代表一或多個 BizTalk Server 執行階段執行個體的邏輯容器。 這是成品相關資訊駐留的程序空間 (包括所有駐留在主控件內的協調流程、結構描述、接收位置和配接器等成品)。 主控件也做為 Windows 內的安全性網域 - 它代表主控件執行個體在一或多個伺服器上執行的虛擬程序邊界。|  
|host instance (主控件執行個體)|Windows NT 服務。 主控件執行個體是特定伺服器上主控件的實體表示法。|  
|host instance– level setting ( 主控件執行個體層級設定)|BizTalk 系統管理員可以在 [BizTalk 設定儀表板] 中修改的其中一項設定。 其範例包括與協調流程記憶體節流有關的 .NET CLR 設定和屬性。 主控件層級設定為一個主控件執行個體所專屬，基本上用於控管電腦資源 (如 RAM 或 I/O) 的使用。 例如，最大值。 I/O 執行緒。|  
|host-level setting (主控件層級設定)|BizTalk 系統管理員可以在 [BizTalk 設定儀表板] 中修改的其中一項設定。 其範例包括主控件追蹤，以及與資源型節流、速率型節流和協調流程節流相關的屬性。 主控件層級設定可調整主控件的所有執行個體在某個部署中的行為方式。 例如，若 Host1 設定最大值。 引擎執行緒變更為 200，Host1 的所有執行個體將會使用最多 200 個引擎執行緒。|  
|host load balancing (主控件負載平衡)|指將多個執行 BizTalk Server 的伺服器加入至 BizTalk 群組，然後將內含式主控件的多個執行個體設定為在這些伺服器上執行的程序。 這樣可將該主控件中所設定的服務和成品執行作業分散於該主控件的多個執行個體，以提高可用性和擴充性。|  
|host type (主控件類型)|決定主控件是在 BizTalk Server 程序內或外部加以控制的屬性。 主控件類型為「內含式」或「外掛式」。|  
|HTTP 配接器|可以在 BizTalk Server 與任何使用 HTTP 或 HTTPS 通訊協定的應用程式之間交換訊息的配接器。|  
  
## <a name="i"></a>I  
  
|詞彙|定義|  
|----------|----------------|  
|IDE|請參閱 Integrated Development Environment (整合式開發環境)。|  
|Import/export (匯入/匯出)|在 [BizTalk 設定儀表板] 中，用於匯入/匯出設定和繫結。 群組、主控件和主控件執行個體目前的 BizTalk 設定會匯出並儲存為 XML 檔案。 BizTalk 系統管理員會匯入這些設定，以將這些設定套用至其他 BizTalk 環境。|  
|Import Wizard (匯入精靈)|從 BizTalk 管理主控台啟動的精靈，用於從 MSI 檔案匯入資源至 BizTalk 應用程式。 如果指定的應用程式不存在，匯入精靈將自動予以建立。|  
|independent composition (獨立撰寫)|兩個動作的序列，其中第二個動作開始處理商務邏輯前不依靠第一個動作的同步訊息；第二個動作可以立即開始。|  
|infotip|在 Web 檢視中，以及在使用 [詳細資料] 檢視時的 [Windows 檔案總管] 的 [註解] 欄中，用來提供桌面、視窗和 [開始] 功能表命令之說明的工具提示。|  
|inheriting (繼承)|在交易夥伴管理 (TPM) Web 服務中，成員設定檔將繼續其父群組所有喜好設定的概念。 在非繼承群組的情況中，成員設定檔不會從父群組繼承任何喜好設定。 非繼承群組可以變更為繼承群組，但繼承群組不能變更為非繼承群組。|  
|interruptible orchestration (可中斷協調流程)|在程序中途妥善定義的位置點可中斷的協調流程。|  
|In-process host (內含式主控件)|在 BizTalk Server 程序空間內操作的主控件類型。 任何協調流程可以登錄到內含式主控件，也可以由其裝載任何傳送處理常式。 內含式主控件只能裝載內含式主控件的接收處理常式 (FILE 配接器)。|  
|In-process receive adapter (內含式接收配接器)|裝載於 BizTalk Server 程序內的配接器。 它是由伺服器程序建立、控制和摧毀的。|  
|安裝精靈|在匯入精靈的最後步驟啟動的精靈，用於安裝 BizTalk 應用程式到本機電腦。|  
|instance activity (執行個體活動)|一系列連續的處理步驟，其中會有一或多個訊息流程。|  
|instance message (執行個體訊息)|經過 BizTalk Server 的執行階段資料的不連續單位，通常表示特定商務文件 (如訂購單)，而且與定義其結構的 BizTalk Server 結構描述區別。|  
|Integrated Development Environment (IDE) (整合式開發環境)|與 Microsoft Windows 相容的使用者介面 (UI) 工具的結合組集，用來繫結、測試和改善平台及其功能。|  
|interceptor (攔截器)|從正在處理的資料流擷取資料並將資料保存到儲存區的機制。|  
|interchange (交換)|在 EDI 中文件的邏輯結合。 交換預定給單一收件者。 在 BizTalk 傳訊中，交換是由接收管線的解譯階段或傳送管線的組譯階段所處理的資料內文。 交換包含零或多個訊息。 接收管線上的解譯器會從收到的交換中擷取訊息，並進一步傳播這些訊息到接收管線。|  
|interchange header (交換標頭)|在 EDI 中，交換的一部分或邏輯關聯文件的群組，用來指示交換的開頭。|  
|interchange trailer (交換結尾)|在 EDI 中，交換的一部分或邏輯關聯文件的群組，用來指示交換的結束。|  
|intergroup adapter (群組間配接器)|在不需仰賴中繼存放區的情況下，促成兩個 BizTalk Server 群組間內部網路/區域網路通訊的 BizTalk Server 配接器。|  
|internal message format (內部訊息格式)|由 BizTalk Server 處理之後或之前的訊息格式。 例如，BizTalk Server 在接收管線開始時收到的訊息是外部格式。 訊息通過管線後，就成為內部格式。|  
|Isolated host (外掛式主控件)|在 BizTalk Server 安裝外操作的主控件類型。 外掛式主控件不能在其中登錄協調流程、裝載傳送處理常式、使用主控件追蹤，或做為群組的預設主控件。 只有外掛式主控件的接收處理常式 (HTTP、SOAP) 可以由外掛式主控件裝載。|  
|isolated receive adapter (外掛式接收配接器)|裝載在 BizTalk Server 程序之外其他程序中的接收配接器。 此配接器由外部程序建立及控制，而且在執行階段與 BizTalk Server 一起註冊以提交訊息。|  
  
## <a name="k"></a>K  
  
|詞彙|定義|  
|----------|----------------|  
|關鍵效能指標 (KPI)|Analysis Services 提供的可自訂商務計量。 KPI 由相關的屬性以及產生產業標準目標和基準線的關聯計算組成。 KPI 集合包含量值、目標、顯示屬性和變異。 公司使用 KPI 追蹤效能並改善制定決策的能力。|  
  
## <a name="l"></a>L  
  
|詞彙|定義|  
|----------|----------------|  
|late bound port (晚期繫結連接埠)|協調流程中定義的連接埠，其「繫結」屬性設定為「稍後指定」。 晚期繫結連接埠是在繫結到實體連接埠時才設定組態。 使用 BizTalk 管理主控台可以執行繫結。|  
|line-of-business application (商業實務應用程式)|對經營企業很重要的應用程式，如薪水、資源規畫、供應鏈管理和會計。|  
|live data (即時資料)|目前由 BizTalk Server 進行處理的資料。|  
|locally unique identifier (LUID) (本機唯一識別碼)|在 BizTalk 群組中用於唯一識別成品的名稱。 視成品類型而定，LUID 的組成項目將有所不同。 例如，BizTalk 組件的 LUID 包含其名稱、版本、文化特性和公開金鑰 Token，像是 Microsoft.BizTalk.Hws.HwsPromotedProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35。|  
|long-running transaction (長時間執行的交易)|視為一個單位的動作集合，通常以堅固和可預測的形式維護適當狀態。 交易可以在無限期的時間內發生，並包含數個巢狀交易。|  
|looping record (迴圈記錄)|一個執行個體訊息可以有多個相符項目的結構。|  
  
## <a name="m"></a>M  
  
|詞彙|定義|  
|----------|----------------|  
|管理資料庫|儲存組態資訊做為組織資源的 Microsoft SQL Server 資料庫。 每個組織各有一個管理資料庫 (有時稱為組態資料庫)。|  
|地圖 (map)|在一規格中的記錄和欄位以及其他規格中的記錄和欄位之間，定義對應關係的 XML 檔案。 對應包含 Extensible Stylesheet Language (XSL) 樣式表，BizTalk Server 使用此樣式表執行對應中描述的轉換。|  
|mapper grid (對應工具方格)|BizTalk Mapper 主視窗的多層中間區域，介於來源和目的結構描述之間，在其中定義資料對應。|  
|mapper grid page (對應工具格線頁面)|對應工具方格的單一層，用來組織與其他資料對應分開的相關資料對應。|  
|master secret (主要密碼)|在企業單一登入 (SSO) 管理員要求時由主要密碼伺服器產生的金鑰。 此密碼金鑰儲存於登錄，做為主要密碼伺服器上的 Local Security Authority (LSA) 密碼。 只有 SSO 管理員可以存取此密碼金鑰。|  
|master secret server (主要密碼伺服器)|在分散式企業單一登入 (SSO) 環境，登錄中儲存主要密碼金鑰的一台電腦。 可以有許多 SSO 伺服器 (不同電腦) 存取此單一 SSO 資料庫。 其中一個 SSO 伺服器是專門當成主要密碼伺服器。|  
|message|資料的電子執行個體，通常在兩個執行的商務程序或應用程式之間進行交換。|  
|message body part (訊息內文部分)|BizTalk Server 訊息的主要部分，包含實際內容，且大部分時候會包含 XML BLOB。 所有訊息最多只能有一個內文部分。 一般來說，從對應到 BizTalk Server 訊息內文部分讀取的資料會用來升級訊息內容屬性。 因此根據升級屬性的路由、發佈或訂閱通常都是以內文部分來完成的。|  
|message context (訊息內容)|BizTalk Server 處理文件時使用的各種屬性之容器。|  
|訊息內容屬性|與訊息相關的一組屬性。|  
|Message Details view (訊息詳細資料檢視)|在 [群組中樞] 頁面上，MessageBox 中某個訊息的所有已知資訊的詳細檢視。 透過兩種 [作業] 檢視之一，從樞紐分析表欄位清單的快顯功能表可存取此檢視。|  
|message digest (訊息摘要)|請參閱＜其他詞彙：hash (雜湊)＞|  
|Message Facts cube (訊息事實 Cube)|彙總訊息和服務相關資訊的線上分析處理 (OLAP) Cube。 現成提供的兩個 Cube 包括「訊息事實」與「服務事實」。|  
|訊息流程|一系列連續的處理步驟，其中會有一或多個訊息流程。|  
|Message Flow view (訊息流程檢視)|「群組中樞」頁面上的一種檢視，可顯示特定訊息的處理事件歷程記錄。|  
|message header (訊息標頭)|在 EDI 中，用來指示文件開頭的訊息部分，是邏輯結合區段的集結，其中包含一個交易的資訊。 在 ANSI X.12 中，訊息等同於交易集合。|  
|message instance (訊息執行個體)|BizTalk Server 正在處理，或已序列化至 MessageBox 或追蹤資料存放區以分別做進一步處理或追蹤之訊息的執行個體。 在 BizTalk Server 內，這通常是訊息的參考、訊息的升級屬性以及訊息內文。|  
|Message Metrics view (訊息計量檢視)|訊息計量線上分析處理 (OLAP) Cube 的樞紐分析表檢視。|  
|message trailer (訊息結尾)|在 EDI 中，用來指示文件結束的訊息部分，是邏輯結合區段的集結，其中包含一個交易的資訊。 在 ANSI X.12 中，訊息等同於交易集合。|  
|MessageBox binding (MessageBox 繫結)|與 MessageBox 互動的繫結。|  
|MessageBox 資料庫|Microsoft SQL Server 資料庫群組，此群組包含 MessageBox 群組的訂閱與追蹤資訊。|  
|MessageBox node (MessageBox 節點)|在 BizTalk 管理主控台中，用來檢視目前執行 MessageBox 資料庫之清單的節點。|  
|Messages view (訊息檢視)|在「群組中樞」頁面上，MessageBox 中服務使用的訊息執行個體的即時檢視。 此檢視在 [作業] 功能表可以取得。|  
|Messaging (傳訊)|BizTalk Server 的主要功能之一，促成可靠的訊息接收、路由與散佈。|  
|Messaging Instance (傳訊執行個體)|在「群組中樞」頁面上，傳訊執行個體包含傳送埠和接收埠服務執行個體。 傳訊執行個體會參考傳訊服務執行個體。|  
|中繼資料|如位置、時間、訊息大小和 (或) 例外資訊等資訊。|  
|milestone alias (里程碑別名)|在 BAM 中，用於意指 BAM 活動所包含之里程碑或資料項目的名稱。 每個里程碑和資料項目可以有多個別名。|  
|mixed content (混合內容)|特定 XML 項目的內容，同時包含子項目以及不在子項目內的資料。 HTML 的範例是︰ &lt;P&gt;共 &lt;EM&gt;一律&lt;/e m&gt; 日落，增加或減少上升。&lt;/ P&gt;|  
|multi-part message type (Multipart 訊息類型)|訊息結構的定義，包含其項目的資料類型。 Multipart 訊息類型可以包含單一部分或許多部分。|  
  
## <a name="n"></a>N  
  
|詞彙|定義|  
|----------|----------------|  
|native|XML 以外的任何資料格式。|  
|native adapter (原生配接器)|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供的配接器，包括 MQSeries、FILE、FTP、HTTP、SMTP、SOAP 和 SQL 配接器。|  
|native pipeline component (原生管線元件)|Microsoft 所提供隨附於 BizTalk Server 中的管線元件。  例子包括：一般檔案解譯器、XML 解譯器和 S/MIME 解碼器。|  
|node|在 BizTalk 編輯器和 BizTalk 對應工具內，顯示於結構描述樹狀結構中的項目。|  
  
## <a name="o"></a>O  
  
|詞彙|定義|  
|----------|----------------|  
|OLAP|請參閱 online analytical processing (線上分析處理)。|  
|online analytical processing (OLAP) (線上分析處理)|利用多維度結構來提供資料的快速存取以進行分析的技術。 OLAP 的來源資料通常儲存在關聯式資料庫的資料倉儲中。|  
|operation (作業)|連接埠上的要求或要求-回應組，與傳送或接收動作關聯。|  
|Operations views (作業檢視)|在「群組中樞」頁面上，讓使用者檢視但不追蹤即時資料的檢視。|  
|Operations/Message Details view (作業/訊息詳細資料檢視)|MessageBox 中特定訊息的所有已知資訊的詳細檢視。|  
|Operations/Messages view (作業/訊息檢視)|MessageBox 資料庫中服務使用之訊息的即時檢視。|  
|Operations/Service Instance Details view (作業/服務執行個體詳細資料檢視)|MessageBox 中特定服務執行個體的所有已知資訊的詳細檢視。|  
|Operations/Service Instances view (作業/服務執行個體檢視)|MessageBox 資料庫中服務 (作用中或已擱置) 的即時檢視；在 BizTalk Server 2002 中為 WorkQ/SuspendedQ。|  
|orchestration (協調流程)|可執行的商務程序。|  
|orchestration binding (協調流程繫結)|協調流程連接埠，沒有連接到固定結束點，而是直接連接到 MessageBox。|  
|協調流程設計師|用來設計和實作商務程序的圖形使用者介面工具。|  
|orchestration instance (協調流程執行個體)|特定可執行商務程序的執行中執行個體。|  
  
## <a name="p"></a>P  
  
|詞彙|定義|  
|----------|----------------|  
|PAM|請參閱 Partner Agreement Management (PAM) (夥伴協議管理)。|  
|參數 (parameter)|指商務程序的預設參數、每個夥伴的商務程序參數，以及每個夥伴群組的商務程序參數。|  
|夥伴|請參閱＜其他詞彙：trading partner (交易夥伴)＞|  
|Partner Agreement Management (PAM) (夥伴協議管理)|在 BizTalk Server 管理主控台的 [合作對象] 節點中，用來設定合作對象屬性的使用者介面。 您可以設定從事 EDI 文件交換、EDI 批次處理和 AS2 文件傳輸之合作對象的處理屬性，以及當合作對象不存在時所使用的全域屬性。|  
|party (合作對象)|BizTalk Server 外部與協調流程互動的每個實體。 與貴組織合作的所有夥伴皆視為合作對象，而且貴組織可能有數千個合作對象。|  
|party enlistment (合作對象登錄)|繫結合作對象到角色的機制。 您可以在角色中登錄合作對象，因而讓協調流程能夠與合作對象互動。|  
|pass-through (通過)|BizTalk Server 連接埠的組態，在傳送埠上僅使用一個篩選條件運算式，將接收埠直接連接到傳送埠。 篩選條件運算式的格式應該為 BTS.ReceivePortName == "名稱或接收埠"。 在這種組態中，接收埠接收的任何訊息會直接傳送到傳送埠。 BizTalk 2004 中通過執行的意義與 BizTalk Server 2000 或 2002年中通過執行的意義不同。 在 BizTalk Server 2004 中通過執行訊息仍在管線中處理，並可能在連接埠數目也會進行轉換。|  
|效能監視|觀看訊息程序/接收速率、執行協調流程數、快取點擊數、一段時間的記憶使用狀況等的程序。|  
|performance processing rules (效能處理規則)|管理程序效能或容量類型計數器的規則。|  
|周邊網路|位於內部網路與網際網路之間的裝置和子網路的集合，可隔離未獲授權的網際網路使用者，以協助保護內部網路。 也稱為 DMZ (非軍事區域) 以及過濾的子網路。|  
|physical (early) binding (實體早期繫結)|做為組件中一部分的資訊，由部署程序使用來建立傳送埠和接收埠。|  
|pipeline (管線)|定義及連結一或多個處理階段的軟體基礎結構，以指定的順序執行來完成特定工作。 管理將處理分成各個階段，描述工作類別的抽象概念。 它也決定執行每個工作類別的順序。|  
|pipeline component (管線元件)|COM 或 .NET 相容元件，可放置在管線中，在訊息經過該管線時執行一些處理動作。|  
|管線設計師|用來建立和設定 BizTalk Server 中管線的圖形使用者介面工具。|  
|policy (原則)|各種版本的商務規則集合。|  
|port connector line (連接埠連接線)|顯示傳送/接收圖形與連接埠圖形上作業之間的連接線。 連接埠連接線的結束點都不能保持為未連接狀態。|  
|port type (連接埠類型)|定義該結束點允許之訊息互動模式組合 (稱為作業) 的屬性。 作業可以是單向，其中傳送或接收一個訊息，或者可以是要求-回應，其中會傳送 (或接收) 訊息並接收 (或傳送) 回應。|  
|positional flat file (位置一般檔案)|用來表示商務文件的檔案格式類型，其中記錄和欄位有固定長度，因為不需要加隔符號。|  
|private queue (私用佇列)|不是發佈為 Active Directory 物件的佇列。 BizTalk 訊息佇列完全支援在私用佇列中訊息的傳送和接收。|  
|process surface (程序介面)|協調流程設計師中設計介面的中間區域。 這個區域用來設計協調流程。|  
|Project Designer (專案設計師)|組成專案的服務、連接埠和繫結的視覺表示法。 新增和移除服務、建立和移除設計師內服務上相容連接埠之間的繫結，使用者即可在專案設計師中編輯視覺項目。|  
|property promotion (屬性升級)|透過此特定的訊息屬性寫入訊息內容與訊息相關聯，做為屬性欄位機制。 寫入至訊息內容屬性欄位會被視為已提升的屬性的屬性 ( **IsPromoted** 欄位的屬性設定為 **True**)，而且需要相關聯的屬性結構描述。  BizTalk Server 傳訊引擎的文件追蹤的訊息路由的指南，用於評估協調流程中使用屬性欄位。 訊息的訊息內容會儲存在 MessageBox 資料庫的多工緩衝處理表格中，該訊息所在資料列的 imgContext 一欄。|  
|屬性結構描述|與 BizTalk Server 結構描述關聯的結構描述，用於識別文件中即將升級至訊息內容做為屬性欄位的項目欄位。|  
|protocol setting (通訊協定設定)|此設定定義使用特定 B2B 通訊協定來支援商務交易的方式。 每個商務設定檔都會針對夥伴可用於通訊的每個 B2B 通訊協定來定義各種設定，以便處理訊息 (編碼) 或傳送訊息 (傳輸)。 通訊協定設定可適用於編碼通訊協定或傳輸通訊協定。|  
|public queue (公用佇列)|發佈為 Active Directory 物件的佇列。|  
|publication-subscription (發佈-訂閱)|請參閱＜其他詞彙：publish/subscribe architecture (發佈/訂閱架構)＞|  
|publish/subscribe architecture (發佈/訂閱架構)|發佈與訂閱的組合，用於在子系統之間移動訊息。 例如，接收埠接收訊息、處理訊息，然後發佈訊息至 MessageBox。 BizTalk Server 將這些訊息路由至進一步處理文件的訂閱協調流程或傳送埠，然後重新發佈至 MessageBox 或傳送到外部系統。|  
|發行|將訊息執行個體儲存到 MessageBox 資料庫的動作，因此可與取用應用程式中的訂閱比對。|  
  
## <a name="q"></a>Q  
  
|詞彙|定義|  
|----------|----------------|  
|Query Expression (查詢運算式)|[群組中樞] 頁面上的一組查詢子句，您可以用於建立和執行 BizTalk 追蹤資料庫的查詢。|  
  
## <a name="r"></a>R  
  
|詞彙|定義|  
|----------|----------------|  
|range dimension (範圍維度)|在 BAM 中，用來建立準則範圍的維度。 例如，您可以建立「低」(0-100)、「中」(100-500) 和「高」(500-1000) 三種範圍來描述銷售額的數值範圍。|  
|receipt generator (回條產生器)|產生假回條的元件，以從重試佇列移除訊息。  如果傳訊埠設定要使用可靠傳訊，則會使用此元件。|  
|receive handler (接收處理常式)|執行接收配接器的 BizTalk 主控件的執行個體。 接收處理常式是待命程式元件、結束點管理員元件和 MessageAgent 元件的邏輯容器。|  
|receive handler host type (接收處理常式主控件類型)|將主控件類型限制為可以裝載特定接收處理常式的屬性。|  
|receive location (接收位置)|位置 (如 URL) 和配接器類型的實體、設計階段概念。 BizTalk Server 管理主控台中主控台節點的接收位置定義了接收功能。|  
|receive pipeline (接收管線)|配接器收到訊息後發佈至 MessageBox 資料庫前，在訊息上執行的管線。|  
|receive port (接收埠)|相似接收位置的邏輯群組。|  
|redeploy (重新部署)|刪除舊位元並部署新位元，藉以重新部署已經存在於目標環境中的組件之動作。|  
|rehydrate (解除凍結)|在某些事件發生 (如接收訊息) 時，從永久儲存區的記憶體中啟動閒置協調流程。|  
|相關性檢視|BizTalk 對應工具的一種檢視，其中結構描述項目的不相關同層級項目會摺疊起來，以提供更簡潔的結構描述檢視。 這樣可減少捲動需求，而將焦點放在結構描述與對應的實用部分。|  
|Reporting views (報告檢視)|顯示商務程序的檢視階層集。|  
|儲存機制|Analysis Services 使用的中繼資料的儲存區容器。 中繼資料儲存於關聯式資料庫中的資料表，用來定義 Analysis Server 物件的參數和屬性。 XML 工具在讀-寫模式中使用儲存機制，而 BizTalk 總管以唯讀模式存取資料。|  
|request-response adapter (要求-回應配接器)|從用戶端接收要求訊息、將訊息提交到伺服器、等候回應，然後將回應傳送回用戶端的接收配接器。|  
|Return shape (返回圖形)|在協調流程實際結束前用來在某個時間點終止協調流程的圖形。  可能的範例：If (security check passed) continue, else Return.|  
|角色 (role)|使用服務或實作服務的連接埠類型之集合，提供合作對象與協調流程互動的方法。 例如，協調流程可能使用託運商的角色。 託運商可能有一或多個合作對象與它關聯。 協調流程決定要僱用哪家託運公司運送項目時，它會比較託運商角色中合作對象的價格。|  
|role link (角色連結)|角色之間的關係，藉由雙方互動時所使用的連接埠和訊息來定義。|  
|role link type (角色連結類型)|定義關係中每個服務扮演的部分，以及指定每個角色提供的連接埠類型，確定兩個服務或協調流程之間關係特徵的屬性。|  
|root node (根節點)|BizTalk Server 結構描述內的節點，表示結構描述所指定之商務文件中最外層的 XML 項目。|  
|RTA window (RTA 視窗)|定義即時彙總 (RTA) 中資料彙總的時間週期。 例如，如果時間週期是一天，而時間點是現在，您只會看到過去 24 小時的資料彙總。 因為時間點不斷在變更中，所以 RTA 視窗中的時間週期也會變更；因此，它也稱為移動時間視窗。|  
|rule (規則)|條件和動作的配對。|  
|rule set (規則集)|相似規則的邏輯群組。 可做為規則引擎的群組/分割機制。|  
|Rules Engine Framework (規則引擎架構)|應用程式開發人員使用的 .NET 元件庫、API 和服務，用來撰寫以規則為基礎的應用程式。|  
|Rules Engine Update service (規則引擎更新服務)|執行動態原則更新的服務。|  
|Rules store (規則存放區)|保存原則的位置。 SQL Server 資料庫是預設的規則存放區。|  
  
## <a name="s"></a>S  
  
|詞彙|定義|  
|----------|----------------|  
|結構描述|訊息的結構。 結構描述可包含多個子結構描述。|  
|Schema Editor extension (結構描述編輯器延伸模組)|軟體模組延伸 BizTalk 編輯器支援的基本 XML/XSD 功能的機制。 結構描述編輯器延伸模組一般會將補充屬性新增到 BizTalk 結構描述中一或多個節點，以表示其特定語意。|  
|過濾的子網路|請參閱＜其他詞彙：perimeter network (周邊網路)＞|  
|安全通訊端層|通訊協定，藉由使用資料加密、數位憑證和公開金鑰加密的組合提高資料通訊的安全性。 SSL 會啟用驗證並提升網路上的資料完整性與隱私權。 SSL 不提供授權或不可否認性。|  
|segment (區段)|在 EDI 中項目的邏輯結合。 例如，名稱和地址詳細資料會結合到一個區段中。|  
|segment tag (區段標記)|在 EDI 中區段的唯一識別碼。 例如，在 EDIFACT 內，區段標記是三個大寫字母的代碼，做為文件內項目的前置詞。 在 ANSI X.12 中，區段標記是二或三個大寫字母代碼。 區段標記與記錄類型識別項類似。|  
|send handler (傳送處理常式)|與傳送配接器相關聯的 BizTalk 主控件。|  
|send pipeline (傳送管線)|訊息從 BizTalk Server 送出前，在訊息上執行的管線。|  
|send port (傳送埠)|傳送訊息的目標位置或是接收訊息的位置，也是指用來實作通訊動作的技術。 這個位置只會由這個連接埠的名稱唯一識別。|  
|send port group (傳送埠群組)|傳送埠的邏輯群組。 將訊息傳送至傳送埠群組時，該訊息會路由至所有相關的傳送埠。 也稱為通訊群組清單。|  
|服務|執行特定系統功能支援作業系統層級之其他程式 (如 Windows NT 服務) 的程式、常式或程序。 服務是在伺服器上執行的 Windows NT 服務或 COM+ 服務。|  
|service instance (服務執行個體)|通常是指 BizTalk Server 正在處理，或已序列化至 MessageBox 做進一步處理或追蹤之協調流程的執行個體。 這通常是協調流程狀態的序列化表示法，再加上協調流程中使用之任何訊息的參考。 在傳訊過程中，服務執行個體會套用至連接埠的執行個體，例如，接收埠的輸入為接收位置而輸出為發佈至 MessageBox 資料庫，或傳送埠的輸入為 MessageBox 而輸出通常是傳送配接器。|  
|Service Metrics view (服務計量檢視)|服務計量 OLAP Cube 的樞紐分析表檢視。 之前屬於彙總檢視的一部分。|  
|工作階段 (session)|兩個主控件之間建立的邏輯連線，用來交換資料。 一般來說，工作階段使用序列和通知來傳送資料。|  
|shape (圖形)|協調流程中動作或動作群組的圖形表示。|  
|shape connector line (圖形連接線)|用來連結圖形並決定圖形在協調流程中相對順序的線。|  
|Simple shape (簡單圖形)|協調流程中的圖形，不能摺疊也不能包含其他圖形。|  
|單一登入 (SSO)|請參閱＜其他詞彙：Enterprise Single Sign-On system (企業單一登入系統)＞|  
|Single Sign-On administration (單一登入管理)|由管理命令列公用程式 (如 ssomanage 和 ssoconfig) 以及由 Windows Management Instrumentation (WMI) 及 BizTalk 總管存取的物件模型，做為組態存放區實例。 此元件與使用 SSO 伺服器的 SSO 資料庫通訊。|  
|Single Sign-On Administrators group (單一登入管理員群組)|有最高權限而且通常要設定加密金鑰的管理員。|  
|Single Sign-On Affiliate Application Administrators group (單一登入分支機構應用程式管理員群組)|這些管理員可以建立和管理分支機構應用程式，指定每個分支機構應用程式的單一登入應用程式管理員帳戶，執行單一登入應用程式管理員和單一登入應用程式使用者可以執行的所有管理工作。|  
|Single Sign-On Application Administrators group (單一登入應用程式管理員群組)|特別指派給每個分支機構應用程式的管理員。|  
|Single Sign-On client utilities (單一登入用戶端公用程式)|做為管理功能的一部分，一般使用者的公用程式，在 SSO 資料庫內提供他們的認證對應。 由 SSO 伺服器用來與 SSO 資料庫通訊。|  
|單一登入 (SSO) 資料庫|存放企業單一登入 (SSO) 認證的資料庫。 其他資料庫則儲存 URL 和傳送埠；只有一個資料庫可以有密碼子服務。|  
|Single Sign-On server (單一登入伺服器)|安裝企業單一登入 (SSO) 服務的伺服器。|  
|Single Sign-On services (單一登入服務)|存取 SSO 資料庫中的認證而讓配接器可以單一登入的服務。 這些服務可以管理 SSO 資料庫。 這些服務做為組態存放區，可以存取配接器的組態資料。|  
|Smart Tag (智慧標籤)|圖形未設定完全的圖形警告，提供如何繼續的提示。|  
|SMTP adapter (SMTP 配接器)|實作 SMTP 通訊協定 (也就是傳送電子郵件訊息) 以便與商業實務應用程式互動的配接器。 此配接器僅包含傳送處理常式。|  
|SOAP adapter (SOAP 配接器)|此配接器可實作 SOAP 通訊協定與商業實務應用程式互動，將協調流程發佈為 Web 服務，以及取用外部 Web 服務。|  
|SOAP fault (SOAP 錯誤)|由 Web 服務所傳回的錯誤訊息，表示 Web 服務中的應用程式發生例外狀況。|  
|SOAP 標頭|SOAP 訊息的信封內所包含的選擇性項目，其所含資料與 XML Web 服務方法的主要功能未必有直接關聯。|  
|SOAP message (SOAP 訊息)|格式正確的 XML 文件。 此文件應使用 SOAP 信封和 SOAP 編碼命名空間，且包含選擇性 XML 宣告，後面接著由選擇性 SOAP 標頭與 SOAP 訊息內文所構成的 SOAP 信封 (根項目)。|  
|SOAP message tracing (SOAP 訊息追蹤)|在已發佈的 Web 服務中設定中斷點的方法，藉以傳回詳細例外狀況給 Web 用戶端。|  
|solicit-response adapter (請求-回應配接器)|雙向傳送配接器。 請求-回應傳送配接器會從 BizTalk Server 傳送要求訊息至目的地、等候回應訊息，然後將回應訊息提交回 BizTalk Server。|  
|source schema (來源結構描述)|BizTalk Server 對應中使用的結構描述，表示輸出執行個體訊息的結構。|  
|SQL adapter (SQL 配接器)|在 BizTalk Server 與 SQL Server 資料庫之間交換資訊的配接器。|  
|SSO|請參閱 Enterprise Single Sign-On system (企業單一登入系統)。|  
|stage (階段)|專門完成特定工作類別之管線的部分。 階段內的管線元件會完成實際工作。|  
|staging database (臨時資料庫)|測試者使用的資料庫，用來部署組件及其繫結到測試或臨時資料庫。|  
|static adapter (靜態配接器)|使用配接器架構提供的使用者介面的配接器。|  
|static port (靜態連接埠)|有目的位址也有關聯的配接器類型的傳送埠。 與動態傳送埠意義相反，靜態傳送埠在執行階段不能變更其組態，而且永遠只能傳送訊息到一個目的位址。|  
|強式名稱金鑰檔|含有組件識別 - 其簡單文字名稱、版本號碼和文化特性資訊 (如果有提供) - 加上公開金鑰與數位簽章所組成的檔案。 此為使用對應的私密金鑰，從組件檔所產生 (組件檔含有組件資訊清單，後者包含構成組件的所有檔案的名稱與雜湊)。|  
|submit (提交)|在 MessageBox 資料庫的適當資料表中放置訊息和相關屬性，及掃描訂閱目錄以尋找其述詞符合訊息屬性的訂閱之動作。|  
|subscribe|BizTalk 指示 MessageBox 將屬性符合指定參數 (訂閱) 的訊息路由至適當程序的機制。 例如，傳送埠篩選條件在 MessageBox 中建立訂閱。 符合篩選條件規格的訊息一旦發佈至 MessageBox，BizTalk Server 便將訊息路由到訂閱的傳送埠進行處理。|  
|訂閱|將符合特定屬性比較準則的訊息路由到工作佇列的機制。|  
|訂閱資料庫|包含 MessageBox 群組所有訂閱的 MessageBox 資料庫。|  
|suspended instance (擱置的執行個體)|由於系統或訊息中有錯誤，BizTalk Server 已停止處理的訊息或協調流程的執行個體。 一般來說，因系統錯誤而擱置的執行個體會在系統問題獲得解決後繼續。 因訊息有問題而擱置的執行個體則通常無法繼續，且必須修正訊息本身並重新提交至 BizTalk Server 系統。|  
|Suspended queue (訊息擱置佇列)|包含處理時碰到錯誤或失敗之工作項目的佇列。 訊息擱置佇列會儲存訊息直到修正和重新處理或是刪除後為止。|  
  
## <a name="t"></a>T  
  
|詞彙|定義|  
|----------|----------------|  
|target database/environment (目標資料庫/環境)|部署組件及其繫結到目標環境時所識別的。|  
|工作 (task)|動作內的人力碰觸點。 每個動作可以有零或多個工作，每個都指派到不同的目標。 工作與目標之間有一對一對應。|  
|task response (工作回應)|從目標對工作的回應。 每個工作可以有零或多個回應。|  
|TDDS|請參閱 Tracking Data Decode Service (追蹤資料解碼服務)。|  
|Technical Details view (技術詳細資料檢視)|「群組中樞」頁面上的一種檢視，可顯示活動單一執行緒中的技術處理步驟。|  
|term (詞彙)|可以用於述詞和動作、具有值的極小實體。 可以是類別成員 (.NET 類別屬性、方法或欄位；XML 項目；資料庫項目)、規則變數或常數。|  
|time dimension (時間維度)|描述時間 (用於彙總) 的 UI 項目。|  
|timer message (計時器訊息)|插入訊息佇列的計時器訊息，觸發將資料流移回到佇列。|  
|toolbox (工具箱)|可停駐視窗，包含可用於協調流程設計程序的各種項目。|  
|tooltip (工具提示)|當您將滑鼠指標移到項目上的時候，可提供簡短即時線上說明的小型快顯視窗。|  
|TPE|請參閱 Tracking Profile Editor (追蹤設定檔編輯器)。|  
|tracking (追蹤)|能夠追蹤 BizTalk Server 交換和訊息處理。|  
|Tracking Analysis database (追蹤分析資料庫)|相關聯 MessageBox 群組的追蹤分析 (OLAP) 資料庫的名稱。|  
|Tracking Data Decode Service (TDDS) (追蹤資料解碼服務)|將事件資料從 MessageBox 資料庫移至 BAM 主要匯入資料庫的服務。 此服務會處理並保存商務智慧和 BizTalk 狀況監控資料。|  
|追蹤資料庫|儲存 MessageBox 群組之追蹤資訊的 Microsoft SQL Server 資料庫。 每個 MessageBox 群組有一個追蹤資料庫。|  
|Tracking Options view (追蹤選項檢視)|[ 群組中樞] 頁面上可定義追蹤選項的一種檢視 。|  
|tracking profile (追蹤設定檔)|定義商務相關程序且包含特定協調流程與活動定義之間對應的一組特性。  追蹤設定檔的副檔名為 .btt。|  
|Tracking Profile Editor (追蹤設定檔編輯器)|圖形使用者介面工具，用來定義其商務程序有興趣的部分以及有興趣的商務內容資料。|  
|交易夥伴|與貴組織交換電子資料的外部組織或內部組織。 例如，交易夥伴可能是供應商、客戶或內部部門。|  
|交易夥伴協議|兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。 交易夥伴協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。 這完整收集了兩個交易夥伴之間進行商務交易時受制於的所有層面。 交易夥伴協議通常是透過設定每個合作夥伴的設定檔而產生，並可讓人自訂和覆寫必要設定。|  
|trading partner management (交易夥伴管理)|管理及儲存夥伴、其業務和 B2B 關係/協議之相關資訊的動作。 增強的交易夥伴管理 (TPM) 方案可以更直覺地反映出商務實體與關係，而讓組織能夠更妥善地管理與交易夥伴的商務合作關係。|  
|trading party (交易合作對象)|位於交易夥伴管理 (TPM) 方案根層級的實體。 進行中商務關係中的每個參與組織，以及執行 BizTalk Server 並與其他合作對象往來傳送訊息的任何單一商務實體，都屬於交易合作對象。|  
|transactional messaging (交易式傳訊)|依序一次傳送的訊息流，藉由同步化和協調群組中多個 BizTalk 訊息佇列配接器執行個體來完成。|  
|轉換圖形|協調流程中的圖形，用來從一個訊息移動資料到另一個訊息，然後使用 XSLT 對應將它轉換。|  
|轉換|將符合一個結構描述的 XML 文件轉換到符合另一個結構描述的 XML 文件的程序，通常在處理過程中會變更文件結構。|  
|translation (轉譯)|將 XML 文件轉換成原生 (非 XML) 格式、或反之亦然的程序。|  
|transport agreement (傳輸協議)|指兩個交易夥伴的商務設定檔之間，規定要使用特定傳輸通訊協定 (AS2) 來交換訊息的協議。|  
|Transport Layer Security (傳輸層安全性)|一種通訊協定，可提供透過網路進行通訊的兩個應用程式之間的通訊私密性與安全性。 TLS 會將通訊加密，並可讓用戶端驗證伺服器以及 (選擇性) 讓伺服器驗證用戶端。 TLS 是比較安全的安全通訊端層 (SSL) 通訊協定版本。|  
|transport protocol (傳輸通訊協定)|一種通訊協定，可控管用於在兩個夥伴之間往返傳送訊息的傳輸通道。 在交易夥伴管理 (TPM) 方面，則僅支援 AS2 通訊協定。|  
  
## <a name="u"></a>U  
  
|詞彙|定義|  
|----------|----------------|  
|undeploy (解除部署)|從 BizTalk Server 資料庫和管理主控台刪除 BizTalk 應用程式，並從任何已安裝的電腦上移除應用程式的程序。|  
|unenlist (取消登錄)|清除該服務的所有訂閱和執行個體 (執行或擱置) 的動作。|  
|United Nations Trade Data Elements Dictionary (UNTDED)|在 EDI 中，EDIFACT 標準內使用的所有項目的字典。|  
|UNTDED|請參閱 United Nations Trade Data Elements Dictionary。|  
|UNZ segment (UNZ 區段)|在 EDI 中，EDIFACT 文件的交換結尾區段。 它包括項目交換參考和交換中的文件編號。 用來指示交換結束及檢查交換參考及交換中文件編號的區段。|  
  
## <a name="v"></a>V  
  
|詞彙|定義|  
|----------|----------------|  
|版本控制|更新成品的實作並遞增其版本號碼的動作。|  
|virtual node (虛擬節點)|在結構描述中，沒有直接對應到結構描述定義的執行個體訊息中任何 XML 項目或屬性的節點。|  
|vocabulary (詞彙)|規則組合中使用的詞彙項目集合。|  
|vocabulary element (詞彙項目)|事實的可閱讀名稱。|  
  
## <a name="w"></a>W  
  
|詞彙|定義|  
|----------|----------------|  
|Web 服務|應用程式邏輯單元，對其他應用程式提供資料和服務。 應用程式使用標準 Web 通訊協定和資料格式 (如 HTTP、XML 和 SOAP) 存取 XML Web 服務，與每個 XML Web 服務實作的方式無關。 XML Web 服務結合元件基礎開發和 Web 的最佳層面，是 .NET 程式開發模型的基石。|  
|Web Services Description Language (WSDL) (Web 服務描述語言)|一種 XML 格式的語言，可將 Web 服務描述為交換訊息的端點。 可以將它擴充，以允許描述端點和其訊息，而不論訊息格式和網路通訊協定為何。 這是「通用描述、探索與整合」(UDDI) 所使用的語言 (UDDI 是一種以 Web 為基礎的商務名錄)。|  
|Windows Management Instrumentation (WMI)|Microsoft Windows 作業系統的元件之一，也是 Microsoft 實作「以網路為主的企業管理」(WBEM，Web-Based Enterprise Management) 的元件，用來將企業環境中的管理工作自動化。|  
|WMI|請參閱 Windows Management Instrumentation。|  
|work queue (工作佇列)|包含要由 BizTalk Server 處理之訊息的佇列。|  
|WSDL|請參閱 Web Services Description Language (Web 服務描述語言)。|  
  
## <a name="x"></a>X  
  
|詞彙|定義|  
|----------|----------------|  
|X.509 certificate (X.509 憑證)|Windows 憑證程序所採用的標準憑證格式。 X.509 憑證包含憑證核發對象的個人或實體的公開金鑰及相關資訊、憑證的相關資訊，可能還有核發憑證的憑證授權單位 (CA) 的相關資訊。|  
|XDR|請參閱 XML-Data Reduced。|  
|XML Schema definition language (XSD) (XML 結構描述定義語言)|結構描述語言。 XML 結構描述所定義的項目、屬性和資料類型符合「全球資訊網協會 (W3C) XML 結構描述 Part 1：XML 結構描述定義語言的結構推薦」標準。 「W3C XML 結構描述 Part 2：資料類型推薦」則針對定義 XML 結構描述中所使用的資料類型提供建議。 XML 結構描述定義語言讓您定義 XML 訊息的結構和資料類型。|  
|XML-Data Reduced (XDR)|可以描述 XML 文件結構的數種方式之一。  BizTalk Server 可以開啟使用 XDR 所描述的結構描述，但在處理過程中會將其轉換成 XML 結構描述定義語言 (XSD)。|  
|XPath|用來巡覽 XML 文件階層結構的完整語言。 XPath 運算式可以包含 XML 項目和屬性資訊，選取符合特定準則的資料，並在擷取的資料上執行比較。 也稱為節點路徑。|  
|XSD|請參閱 XML Schema Definition language (XML 結構描述定義語言)。|  
|XSLT|請參閱 Extensible Stylesheet Language Transformations (可延伸樣式表語言轉換)。|  
  
## <a name="z"></a>Z  
  
|詞彙|定義|  
|----------|----------------|  
|zombie|協調流程所沒有處理的訊息。 這類訊息不在訊息擱置佇列上，因此永無重試的機會。|  
|zombie resurrector|一種在 MessageBox 資料庫上接聽符合特定準則之 Zombie 和 Resurrect 的協調流程。|