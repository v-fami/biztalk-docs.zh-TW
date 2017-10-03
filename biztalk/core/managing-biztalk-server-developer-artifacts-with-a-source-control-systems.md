---
title: "管理 BizTalk Server 開發人員成品來源控制系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce25b112-38c9-40c8-9a5f-a2855572aabb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 829749911bd4f3ca6aee1da42578a1aac28db7ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-server-developer-artifacts-with-a-source-control-systems"></a>管理原始檔控制系統與 BizTalk Server 開發人員成品
保護您的 BizTalk 專案免於發生未預期的系統失敗，應做為第一優先的事項。 保護專案檔案的一個方式是使用原始程式碼控制系統，例如 Team Foundation Server Source Control 與 Microsoft Visual SourceSafe。 本主題說明一些基本策略，可將專案組織成與任何原始檔控制系統搭配使用時都能發揮最佳效果，並提供有關使用 Visual SourceSafe 的特定建議。  
  
## <a name="basic-organization-strategies"></a>基本的組織策略  
 無論您最終會使用何種原始檔控制系統，都可以遵循一些基本組織策略。 這些策略可確保您的 BizTalk 專案檔案結構組織成適用於開發和原始程式碼控制。  
  
### <a name="use-a-consistent-folder-structure-for-solutions-and-projects"></a>讓解決方案和專案使用一致的資料夾結構  
 如果小組間使用一樣的結構來儲存 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 解決方案和專案，會比較容易管理小組環境中的開發。 特別是在每個 BizTalk 專案都會產生和使用如建置、測試和部署小組所需的繫結檔案時，更是如此。  
  
 如果不花時間將資料庫結構標準化，通常可以很輕鬆地開始進行開發。 但是日後不可避免地必須花費更多的時間，因為隨著解決方案的開發，專案連結和測試控管都需要被「修補」。  
  
### <a name="keep-source-control-and-file-system-structures-identical"></a>保持原始檔控制和檔案系統的結構相同  
 為了簡化多位開發人員環境的管理方式，請在原始檔控制系統內設定符合您本機檔案結構的資料夾結構。 這有助於確保開發人員可以直接取得最新版本，並且確保磁碟上的結構符合小組的標準。  
  
### <a name="define-and-use-a-common-root-folder"></a>定義並使用相同的根資料夾  
 建議您將所有的專案代碼和完成品都保存單一資料夾根目錄中，該資料夾根目錄可以在所有開發人員電腦上建立。 當所有開發人員使用相同的根目錄時，會簡化管理開發成品及維護一致組態的工作。 例如，在 Visual SourceSafe 內建立 $/SysInteg2009 根資料夾，如此一來，所有開發人員便可在自己的本機檔案系統上建立 C:\SysInteg2009。  
  
### <a name="create-a-master-solution-that-will-hold-all-projects"></a>建立保存所有專案的主要解決方案  
 主要解決方案通常可做為主建置方案。 這項建議適用於中高複雜度的 BizTalk 專案。  
  
### <a name="store-all-biztalk-projects-under-the-master-solution"></a>將所有 BizTalk 專案儲存在主要解決方案之下  
 這個策略對於組織主要解決方案之下所有相關的 BizTalk 專案十分有用。 原始檔控制系統中的結構應該會鏡像這個階層。  
  
### <a name="divide-the-folder-structure-into-shared-and-process-specific-sections"></a>將資料夾結構分割為共用和特定程序的區段  
 當您建立檔案結構時，通常會分割資料夾結構，區隔共用實體與商務特定程序實體。 共用實體通用於多個專案，並且可能包含協助程式類別。  
  
 舉例來說，下列清單中的前三個資料夾是由共用實體所組織，而最後兩個資料夾則由商務程序組織：  
  
 C:\SysInteg2009\\_Master_Solution\Shared\  
  
 C:\SysInteg2009\\_Master_Solution\Shared\EmailHelper  
  
 C:\SysInteg2009\\_Master_Solution\Shared\SharedSchema  
  
 C:\SysInteg2009\\_Master_Solution\AccountRequest\  
  
 C:\SysInteg2009\\_Master_Solution\AccountValidate\  
  
### <a name="separate-pipeline-projects-into-distinct-projects"></a>將管線專案分割成不同專案  
 在開發管線元件的期間，通常需要獨立於其餘解決方案之外，單獨修改和重新測試管線。 基於這個原因，將管線解決方案當做個別的 BizTalk 專案有助於產生可移除和重新部署的個別管線組件，而不需要重新繫結其餘的解決方案。  
  
 此外，將實作實際管線介面的程式碼以及管線處理邏輯保存個別專案中，該專案具有從 BizTalk 專案 (包括 .btp 檔) 到 [!INCLUDE[btsCSharp](../includes/btscsharp-md.md)] 或 Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)] 專案的參考，也是常見的做法。  
  
### <a name="keep-deployment-and-test-scripts-with-their-projects"></a>將部署指令碼和測試指令碼和專案一起保存  
 為了開發統一的建置和開發程序，建置和安裝指令碼應該由個別開發人員建置，不過應視為完整解決方案的可重複使用部分。 如果將指令碼寫入為可重複使用，那麼如部署完整解決方案套件的工作就可以重複使用指令碼。 舉例來說，如果部署指令碼和解除部署指令碼接受參數以指定 DLL 和用於繫結檔案資料夾位置的路徑，則當編譯的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件位於不同的位置時，可以重複使用指令碼。  
  
 開發人員可以使用這個方法，將特定程序的安裝指令碼新增至資料夾，接著便可輕鬆地寫入單一程序，為所有程序執行完整部署。  
  
### <a name="use-unique-strong-name-keys-when-appropriate"></a>在適當時使用唯一強式名稱金鑰  
 一般而言，單一 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 解決方案使用單一金鑰檔案。 這是因為解決方案會被當做單一實體，並依照同樣的方式加以管理。 如果要開發的商務解決方案實際是由兩個以上不同的部分所組成，請考慮是否應該使用兩個金鑰檔案。 這個狀況中的多個金鑰在將來會允許每個部分都被視為獨立實體，例如使用不同的升級途徑。  
  
 在考慮使用協助程式專案時，請採用相同的考量。 如果協助程式專案是 (或將是) 個別的實體，請使用不同的強式名稱金鑰來建置。  
  
### <a name="put-dependent-dlls-into-a-separate-folder"></a>將相依 DLL 放入不同的資料夾  
 建立資料夾結構時，建立通用資料夾來存放做為檔案相依性參考的 DLL 會很有用。 確認所有開發人員都遵循相同的資料夾結構後，當解決方案在開發人員或工作站之間移動時，將不會破壞檔案參考。  
  
### <a name="keep-test-messages-in-a-msgs-folder"></a>將測試訊息存放在 "Msgs" 資料夾中  
 開發結構描述並使用訊息時，通常要花費相當多的精力對 XML 結構描述和協調流程程序測試各種不同範例訊息。  
  
 在實際的解決方案中，範例訊息是非常重要的資產，因為範例訊息包含的資訊對商務解決方案而言意義重大。 相同訊息中的隨機值或空值，通常會造成程序失敗。 因此，應該和重視解決方案的程式碼一樣重視範例訊息。  
  
 為了協助管理訊息檔案，請將測試訊息保存在名為 "msgs" 的特定資料夾中。 如果同時存在「產生的執行個體」和「範例訊息」(例如來自現有系統的訊息)，區隔這些訊息有助於比較開發的結構描述和實際資料。  
  
 整合專案通常有多種版本的結構描述，因此也有多種版本的訊息檔案。 為了區分範例訊息，請使用版本編號來命名檔案。  
  
### <a name="managing-other-files"></a>管理其他檔案  
 有些類型的檔案可以以群組的方式儲存在不同的資料夾中，有些檔案則可以和其他檔案儲存在通用資料夾中。 請制定如何處理每種檔案類型的原則，然後一貫地遵循該原則。  
  
## <a name="working-with-biztalk-server-and-visual-sourcesafe"></a>使用 BizTalk Server 和 Visual SourceSafe  
 本節說明使用 Visual SourceSafe 時應注意的特定考量，包括處理 Unicode、使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 進行原始檔控制、存回的時機、版本控制和其他問題。  
  
### <a name="solution-character-sets"></a>解決方案字元集  
 Visual SourceSafe 存在與處理 Unicode 檔案有關的已知限制。 使用 BizTalk 解決方案時，必須防止 Visual SourceSafe 損毀 BizTalk Server Unicode 檔案。  
  
##### <a name="to-enable-visual-sourcesafe-to-work-with-biztalk-server-unicode-files"></a>將 Visual SourceSafe 與 BizTalk Server Unicode 檔案搭配使用  
  
1.  啟動 Visual SourceSafe 8.0 Admin。  
  
2.  選取要使用的 SourceSafe 資料庫。  
  
3.  在 **[工具]** 功能表上，按一下 **[選項]**。  
  
4.  按一下**檔案類型** 索引標籤。  
  
5.  將下列項目新增至二進位檔案清單的末端。 請確認以分號分隔每種檔案類型：  
  
     *.btm;\*.btp;\*.xsd;\*.odx  
  
6.  按一下 **[確定]**。  
  
 現在，Visual SourceSafe 不會檢查 BizTalk Server 檔案並嘗試變更檔案的格式。  
  
### <a name="use-visual-studio-for-source-control-operations"></a>使用 Visual Studio 進行原始檔控制作業  
 Visual SourceSafe 內所有專案的建立和操作都應該使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中整合的 Visual SourceSafe 支援功能表的方式來執行。 請勿使用 Visual SourceSafe Explorer 執行這些作業。  
  
### <a name="when-to-check-in-biztalk-server-projects"></a>存回 BizTalk Server 專案的時機  
 使用 Visual SourceSafe 的建議方式是，只在程式碼順利通過功能測試，以及開發人員確定程式碼將成功建置且不會破壞任何相關程式碼的時候，才存回程式碼。 將這個模式套用至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時有下列指導方針：  
  
-   除非結構描述已順利測試過各種不同的範例訊息，否則不存回只包含訊息結構描述的 BizTalk 專案。  
  
-   除非解決方案已經使用適當的輸入和輸出訊息以及正確的傳送埠和接收埠測試成功，否則不存回包含商務程序的 BizTalk 專案。  
  
-   除非 Web 服務已經在初始化系統中進行測試，或者已使用測試控管測試過，否則不存回 .ASP.NET Web 服務專案。  
  
 如果遵循這個模式，Visual SourceSafe 儲存機制將永遠保存可成功建置並通過測試的建置。 如果要遵守「夜間建置」的方法，這個原則非常重要。  
  
### <a name="checking-in-intermediate-versions"></a>存回中繼版本  
 另一個存回檔案的方法是存回「中繼」版本。 在這個方法中，中繼版本尚未順利通過功能測試，可以視為「介於建置之間」。 一般並不建議使用這個方法，因為它違反了原始檔控制系統內只能有可建置版本的原則。 然而有些小組偏好這個方法，因為它讓開發人員可以使用原始檔控制系統存回並回復版本，而不需遵守存回正式建置的準則。  
  
 如果需要使用存回中繼版本的方法，您不能假設原始檔控制系統包含「可建置」版本。 而是必須區別中繼版本和建置版本。 使用 Visual SourceSafe，您可以以各種不同的方式 (自動或程序) 來做區別。 例如：  
  
-   開發人員依照程序通知建置管理員何時將「可建置」版本新增至 Visual SourceSafe。  
  
-   開發人員在 Visual SourceSafe 中將已測試的版本 (可進行建置) 存回至「升級區域」。 然後，這個升級區域可做為主要建置所依據的來源。  
  
-   程式碼或指令碼可寫入為使用 Visual SourceSafe COM 介面。 舉例來說，特定標籤可以用來代表可進行建置的程式碼，指令碼會搜尋這個標籤，然後將這個原始檔 Pin 到個別 Visual SourceSafe 分支。 接著，這個分支將做為主要建置的來源。  
  
### <a name="comparing-files"></a>比較檔案  
 您可以使用 Visual SourceSafe 找出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來源檔案兩個不同版本之間的差異。 這項操作可以利用成品來完成，包括對應、結構描述，以及測試訊息之類的相關檔案，甚至包括匯出的組態檔。  
  
> [!NOTE]
>  比較對應時，您必須先編輯對應後再將它簽入，否則Visual SourceSafe 便會在尋找此對應與下一版的差異時，執行二進位檔比較。 這是因為必須等到您完成編輯之後，編碼資訊才會加入到對應 XML 公用程式。  
  
### <a name="version-controlling-non-biztalk-server-project-files"></a>對非 BizTalk Server 的專案檔案進行版本控制  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用有益於建立版本並儲存在 Visual SourceSafe 中的額外檔案。 下列是範例檔案：  
  
-   繫結檔案 (開發和測試)  
  
-   自訂管線組件  
  
-   測試資料 (例如測試訊息)  
  
-   測試控管 (在專案存留期間可能會改變)  
  
-   建置、部署以及啟動和停止指令碼可能需要在開發小組和建置小組間共用  
  
 如果這些檔案關聯至特定 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 專案，這些檔案可以包含在 BizTalk 專案中，並使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 整合原始檔控制功能進行管理。  
  
##### <a name="to-include-a-file-or-folder-into-an-existing-visual-studio-project"></a>若要將檔案或資料夾加入現有 Visual Studio 專案  
  
1.  在 方案總管 中，按一下 **顯示所有檔案**。  
  
2.  選取要加入解決方案的資料夾或檔案。  
  
3.  以滑鼠右鍵按一下資料夾或檔案，然後**包含在專案**。  
  
> [!NOTE]
>  Visual SourceSafe Explorer「不應該」用來管理原始檔控制下 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案中的任何項目。  
  
### <a name="checking-the-visual-sourcesafe-database"></a>檢查 Visual SourceSafe 資料庫  
 如果 Visual SourceSafe 資料庫容量很大、使用量龐大或正由許多使用者存取，建議您定期執行 Visual SourceSafe 功能表中的 "Analyze VSS DB" 指令。 如果分析偵測到錯誤，即可使用 "Analyze and Fix VSS DB" 指令來修正錯誤。 這兩種指令都需要鎖定 Visual SourceSafe 資料庫，因此，必須要求所有人中斷與 Visual SourceSafe 的連線。