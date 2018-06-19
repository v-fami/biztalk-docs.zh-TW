---
title: 已知的安裝問題 |Microsoft 文件
description: 已知的問題和常見問題與安裝和設定 BizTalk Server 時的解決方式
ms.custom: ''
ms.date: 11/30/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4d0e707-6b9e-49e1-9f17-19b3bac1229e
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90217a4e80df6f017b451dd7c40f6a1dfe3898ac
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26011031"
---
# <a name="troubleshoot-biztalk-server-setup"></a>疑難排解 BizTalk Server 安裝程式

## <a name="introduction"></a>簡介  
 此疑難排解指南 》 列出已知的問題，以及最常見的問題，您可能會遇到安裝 BizTalk Server 時。 本指南還包括自訂動作來提供有關 Windows Server logo program BizTalk 伺服器憑證的詳細資料。  它提供安裝 BizTalk Server 期間可能會執行的自訂動作清單。  
  
## <a name="review-install-steps"></a>檢閱安裝步驟  
大部分 BizTalk Server 安裝程式問題的發生是因為 BizTalk Server 的電腦未正確地準備之前已安裝 BizTalk Server，或先前安裝的 BizTalk Server 未完全解除安裝之前嘗試新的安裝。  
  
檢閱兩個檢查清單，您也可以在 BizTalk Server 安裝指南，以確保您的電腦上已正確設定以支援 BizTalk Server 中找到。 如果檢閱此資訊之後，您的設定仍不成功，則這份文件的其餘部分中的疑難排解提示可能很有用。  
  
1. 安裝先決條件軟體和程式：

    * [BizTalk Server 2016](set-up-and-install-prerequisites-for-biztalk-server-2016.md)
    * [BizTalk Server 2013 R2 & 2013](prepare-your-computer-for-installation.md)

2. 安裝和設定 BizTalk Server:  

    1. 安裝 BizTalk Server: [BizTalk 2016](install-biztalk-server-2016.md) ， [BizTalk 2013 R2 / 2013年](install-biztalk-server-2013-and-2013-r2.md)  
    2. [設定](configure-biztalk-server.md)BizTalk Server
    3. [設定的後續作業步驟](post-configuration-steps-to-optimize-your-environment.md)
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a>取消設定後一些 EDI/AS2 成品仍然使用中  
  
**問題**  
 之後您取消設定 BizTalk Server 中，某些與 EDI 的 BizTalk Server 成品的 BizTalk EDI/AS2 功能和 AS2 處理，仍然可以在 BizTalk 群組組態的內容中。 這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。 因此，即使取消設定 BizTalk EDI/AS2 功能，您仍然可以執行基本的 EDI 和 AS2 處理。  
  
**可能的原因**   
 這時有存在與 EDI 和 AS2 處理相關聯的使用中連接埠。 有些成品會在這些連接埠保持使用狀態時繼續運作。  
  
**解決方式**  
 若要停用所有的 EDI/AS2 成品，您應該停用、停止或刪除與 EDI 和 AS2 處理相關聯的連接埠。  
  
## <a name="after-renaming-biztalk-or-sql-server-computer-the-configuration-wizard-fails"></a>在之後重新命名 BizTalk 或 SQL Server 的電腦，設定精靈會失敗  
  
**問題**  
 這個問題可能會以數種方式出現：  
  
-   Configuration manager 正確地載入 [概觀] 頁面，但是當嘗試設定某項功能，功能選項並未出現在螢幕上。  
  
-   組態精靈無法連接到 SQL Server。  
  
-   嘗試取消設定所有功能會取消設定部分功能，而非全部功能。  
  
**可能的原因**   
 BizTalk Server 組態會儲存電腦網路名稱。 重新命名電腦時，組態管理員 」 和 「 組態精靈找不到 BizTalk Server。 如果在設定 BizTalk Server 後重新命名 SQL Server 電腦，也會發生相似的問題。  
  
**解決方式**  
 請勿重新命名 BizTalk Server 電腦或 SQL Server 電腦。 如果您必須重新命名伺服器，取消設定所有 BizTalk 功能，然後再重新命名電腦。 接著，在重新命名電腦後，重新設定 BizTalk Server 功能。  
  
## <a name="business-rules-configuration-wizard-fails"></a>商務規則組態精靈失敗  
  
**問題**  
  
-   商務規則組態精靈失敗，發生錯誤 「 一些元件的組態失敗和不套用任何設定到那些元件 」。  
  
-   在已順利設定商務規則引擎的 BizTalk Server 電腦上，無法啟動並且無法手動啟動規則引擎更新服務。  
  
發生這個問題時，BizTalk Server 電腦應用程式記錄檔中可能會產生與下例類似的錯誤：  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
**可能的原因**   
 從 Microsoft 惡意程式碼防護中心發行更新的簽章檔案，在 2010 年 3 月 9 日解決潛在威脅從 SettingsModifier:Win32 / PossibleHostsFileHijack。 這個更新過的簽章檔案可能會讓 Microsoft 惡意程式碼偵測軟體 (例如 Windows Defender) 更新本機 HOSTS 檔案，以減輕來自 SettingsModifier:Win32/PossibleHostsFileHijack 的威脅。 基於這些變更，可能無法啟動 BizTalk Server 規則引擎更新服務。  
  
**解決方式**  
 更新本機 HOSTS 檔案，以加入下行︰  
  
```  
127.0.0.1         localhost  
```  
  
 HOSTS 檔案位於 %systemroot%\drivers\etc\ 目錄中。  
  
> [!NOTE]
> 請參閱 Microsoft 惡意程式碼防護中心簽章更新的位址可能威脅從[SettingsModifier:Win32 / PossibleHostsFileHijack](http://go.microsoft.com/fwlink/?LinkId=146221)。  
  
## <a name="configuration-logging"></a>組態記錄  
 「 組態 」 程式寫入組態記錄檔中的預設位於執行 BizTalk Server 之電腦的暫存目錄的詳細的資訊。 若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：  
  
 **echo %TEMP%**  
  
 此組態記錄檔含有已執行之組態步驟的摘要，以及組態程序中可能發生之任何失敗的相關診斷資訊。 如果發生組態錯誤，請在文字編輯器 (如 [記事本]) 中開啟此組態記錄檔，然後檢查此記錄檔，找出錯誤的可能原因。  
  
## <a name="troubleshooting-tools"></a>疑難排解工具  
 使用 SQL Server Profiler、Filemon 或 Regmon 可蒐集有關組態失敗的其他資訊。 請參閱[用於疑難排解的工具和公用程式](../core/tools-and-utilities-to-use-for-troubleshooting.md)。  
  
### <a name="configuration-fails-when-biztalk-and-sql-are-installed-on-separate-computers"></a>BizTalk 和 SQL 安裝在不同電腦時，設定失敗  
  
**問題**  
 當您嘗試設定企業單一登入 (SSO) 元件時，組態會發生失敗，其錯誤與底下類似：  
  
```
An error occurred while attempting to access the SSO database.  
Function: FieldInfoCreate  
```
  
 -或-  
  
```Failed to enable the Single Sign-On (SSO) Service (error code 0X800706BA)```  
  
**可能的原因**    
 如果不同的電腦上安裝 BizTalk Server 和 SQL Server 則組態作業將會在 Microsoft Distributed Transaction Coordinator (MSDTC) 交易的內容下，而且必須透過使用 MSDTC 功能這些電腦之間的網路。 如果無法透過執行 BizTalk Server 和 SQL Server 的電腦之間網路使用 MSDTC 功能，會發生此錯誤。  
  
**解決方式**    
使用[疑難排解 MSDTC 問題的](https://support.microsoft.com/help/306843/how-to-troubleshoot-ms-dtc-firewall-issues)以確保執行 BizTalk Server 和 SQL Server 的電腦之間網路上的 MSDTC 功能。  
  
### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a>防毒軟體干擾組態，並造成組態失敗  
  
**問題**   
 當防毒軟體錯誤判斷組態程式為病毒時，BizTalk Server 組態就會失敗。  
  
**原因**  
 包含 BizTalk Server 組態程式當做合法 （非病毒） 程式尚未更新防毒軟體。  
  
**解決方式**  
 設定防毒程式將 BizTalk Server 組態程式辨識為合法 （非病毒） 程式，否則執行組態程式時，暫時停用防毒軟體。  
  
### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a>組態失敗，其錯誤為「找不到檔案或組件名稱 FileName.dll 或其相依性的其中之一」。  
  
**問題**  
 在組態程序期間，出現了類似以下的錯誤：  
  
 無法部署 BizTalk 系統組件"C:\Program Files\Microsoft\BizTalk Server 20xx\Microsoft.BizTalk.DefaultPipelines.dll。 未指定例外狀況： 找不到檔案或組件名稱 FileName.dll，或其相依性的其中一個。 」  
  
**原因**  
 如果網路服務帳戶未具備執行 BizTalk Server 的電腦上的暫存資料夾寫入權限，就會發生此錯誤。 在設定期間，BizTalk Server 組態會使用 Windows Management Instrumentation (WMI)，將.NET 組件部署至 BizTalk 管理資料庫。 WMI 會模擬 Network Service 帳戶同時將這些組件部署到 BizTalk 管理資料庫，因此網路服務帳戶必須具有寫入存取權執行 BizTalk Server 的電腦上的暫存資料夾。  
  
**解決方式**  
 授與 Network Service 帳戶寫入到暫存資料夾執行 BizTalk Server 的電腦上，然後再次執行組態程式。 若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：  
  
```  
echo %TEMP%  
```  
  
### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a>如果 SQL Server 資料庫檔案與 SQL Server 資料夾中已經存在的指定資料庫同名，組態會發生失敗  
  
#### <a name="problem"></a>問題  
 組態發生失敗，其錯誤與以下類似：  
  
```
Failed to set up BAM database(s)  
  
Cannot open database requested in login 'BAMPrimaryImport'  
  
Logon fails. Logon failed for user '*BizTalk\BizTalkUser*'  
```
  
**原因**  
 會發生此錯誤，如果.mdf 檔案或.ldf 檔案已經存在具有相同名稱的.mdf 檔案或.ldf 檔案的 BizTalk Server 組態程式嘗試建立的 SQL Server 執行電腦的 \MSSQL\data 資料夾中。 針對資料庫所建立的.mdf 檔案和.ldf 檔案的名稱被衍生自指定了.mdf 和.ldf 副檔名附加 「 BizTalk Server 組態 」 程式中的資料庫名稱。  
  
**解決方式**  
 若要解決這個行為，請使用下列其中一種方法：  
  
-   刪除與您要建立之任何資料庫名稱同名的任何 .mdf 檔案或 .ldf 檔案。  
  
-   選擇使用與 SQL Server 之 \Program Files\Microsoft SQL Server\MSSQL\data 資料夾中已經存在的任何 .mdf 檔案或 .ldf 檔案不同名的資料庫名稱。  
  
### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a>指定本機帳戶時，網域控制站上的組態發生失敗  
  
**問題**  
 當網域控制站上執行 BizTalk Server 組態程式，組態就會失敗 biztalkserverapplication 主控件或 BizTalkIsolatedHost 主機如果指定的本機群組 （例如，BizTalk 主控件使用者群組）。  
  
**原因**  
 網域控制站會自動將本機 Windows 群組視為網域 Windows 群組 (也就是說，網域控制站上不會有本機 Windows 群組)。 如果您指定主機的本機 Windows 群組組態程式執行時，設定會在嘗試建立 SQL Server 登入群組時失敗。 當伺服器是網域控制站時，組態程式不會停用本機 Windows 群組選項。  
  
**解決方式**  
 針對組態進行期間建立的主控件指定網域群組。  
  
### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a>如果 SQL Server 已經重新命名，則組態程式將無法建立 SQL Server 分析資料庫  
  
**問題**  
 若您將安裝 SQL Server Analysis Server 的電腦重新命名，組態程式就無法建立新的 SQL Server 分析資料庫，而且會產生類似以下的錯誤：  

```  
 Cannot connect to the repository.  
  
 Analysis server: <machine name\>  
  
 Error:  
  
 '\\\\<machine name\>\MsOLAPRepository$\msmdrep.mdb' is not a valid path.  
  
 Make sure that you correctly spell the path name and that you are  
  
 connected to the server on which the file resides.  
```
  
**原因**  
 組態程式無法判斷安裝 SQL Server Analysis Server 之電腦的新名稱。  
  
**解決方式**  
 請以手動方式執行以下步驟，將 Analysis Server 更新為新的電腦名稱：  
  
1.  SQL Server 上開啟**Microsoft SQL Server**，選取**Analysis Services**，然後按一下  **Analysis Manager**。  
  
2.  在 **分析管理員** 導覽面板中按兩下 **Analysis Server** 節點來展開它。  
  
3.  以滑鼠右鍵按一下您想要編輯，然後選取的儲存機制連接字串伺服器 **編輯儲存機制連接字串**。  
  
4.  在 **編輯儲存機制連接字串**  對話方塊，確認這個字串中的伺服器名稱，其更新為新的電腦名稱，如果密碼不正確。  
  
5.  瀏覽至下列位置︰ <*安裝目錄*> files\microsoft Analysis Services\Bin。  
  
6.  以滑鼠右鍵按一下 **Bin** 資料夾，然後再按一下 **共用和安全性**。 **紙匣內容**  對話方塊隨即出現。  
  
7.  在 **紙匣內容** 對話方塊中，按一下  **共用** 標籤，確認所有的線上分析處理 (OLAP) 系統管理員具有完整權限，此資料夾。  
  
### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a>重新部署組件從 Visual Studio 的成品會消失從組態資料庫  
  
**問題**  
 當 BizTalk Server 專案上重新部署專案內的層級 Visual Studio 中，參考重新部署專案，將會消失，重新整理 BizTalk Server MMC 時出現在專案內所包含的所有成品。  
  
**原因**  
 為了說明這個問題的原因，假設以下範例是根據範例 BizTalk Server 解決方案，而使用者想要在其中重新部署 Maps 專案。 請注意，編譯專案會產生個別的組件。 下圖指示使用者執行重新部署之前的解決方案狀態， 成品之間的關係如下：  
  
-   Orch1、Orch2、Maps、Pipelines 和 Schemas 都是專案。  
  
-   Orch1 參考 Maps，而 Maps 則參考 Schemas。  
  
-   Orch2 參考 Schemas。  
  
-   Pipelines 參考 Schemas。  
  
![bcd_ExistingBizTalkServerSolutionc](../install-and-config-guides/media/bcd_ExistingBizTalkServerSolutionc.gif)  
  
如果使用者使用預設 Visual Studio 專案設定來重新部署 Maps 專案，則 Orch1、Orch2 和 Pipeline 成品會消失，如下圖所示。  
  
![bcd_BizTalkSolutionWLostArtifactsc](../install-and-config-guides/media/bcd_BizTalkSolutionWLostArtifactsc.gif)  
  
 重新部署 Maps 是一個兩個步驟的程序，要先解除部署目前已部署的 Maps.dll 組件，然後部署新的 Maps.dll 檔案。 Visual Studio 會自動執行下列步驟重新部署程序的一部分。  
  
> [!NOTE]
>  上一個句子嚴格來說並不正確，因為 Visual Studio 一定會執行這些步驟，所以它不會意識到這是適當的作法。  
  
 重點，是為了要解除部署 BizTalk Server 組件，Visual Studio 解除部署所有組件相依於該組件包含設定部署旗標。 在這個範例中，若要執行重新部署的第一個解除部署步驟，BizTalk Server 需要解除部署 Orch1.dll (它相依於 Maps.dll)。 在 解除部署 maps.dll 時，Visual Studio 也會解除部署 Schemas.dll （假設它已設定部署旗標）。 為了要解除部署 Schemas.dll，Visual Studio 需要解除部署 Orch2.dll 和 Pipelines.dll (這兩者都相依於 Schemas.dll)。  
  
 有問題存在，Visual Studio 重新部署，只有 Maps.dll 和它所依據的組件： 在此情況下，Schemas.dll。 因此當使用者重新整理 BizTalk Server MMC 時，Orch1、 Orch2 和 Pipeline 組件似乎消失了，但 Maps.dll 和 Schemas.dll 仍然可見。  
  
**解決方式**  
 如果是主要專案 (它會參考其他專案)，請執行以下作業：  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下方案節點。  
  
2.  按一下  **屬性** 開啟 **方案屬性頁** 對話方塊。  
  
3.  按一下  **組態屬性**, ，然後按一下  **組態**。  
  
4.  清除 **部署** 參考之專案的核取方塊。  
  
5.  在 [方案總管] 中，執行新的方案層級部署。 若要這樣做，請以滑鼠右鍵按一下方案節點，然後按一下  **部署方案**。  
  
### <a name="supported-virtual-directory-types"></a>支援的虛擬目錄類型  
 匯出作業時參考 Web 服務從協調流程，並嘗試進行 MSI 匯出時，將會成功相關聯的虛擬目錄都屬於型別時，才 **IIsWebVirtualDir** 或 **IIsWebDirectory**。 **IIsWebVirtualDir** 和 **IIsWebDirectory** 出現在 IIS metabase 中的節點型別。 **IIsWebVirtualDir** 是使用的虛擬目錄 **路徑** 指向絕對檔案資料夾的屬性。 **IIsWebDirectory** 而不是虛擬目錄 **路徑** 屬性，並因此參考相對檔案資料夾，通常是另一個子資料夾 **IIsWebVirtualDir** 或 **IIsWebDirectory** 節點。 在 Metabase 階層中，經常會看到用來描述資料夾的這兩個類型。  
  
 類型的虛擬目錄 **IIsConfigObject** 不支援的 MSI 匯出會在此情況下失敗。 **IIsConfigObject** 的非預期的 metabase 節點類型，而 BizTalk Server 未適當處理可能是無效節點型別或未適當建立 （並因此無效） metabase 項目表示。 在此情況下，BizTalk Server 將會顯示如下所示的錯誤訊息︰ 類型 IIsConfigObject 的未預期的目錄項目"IIS://LM/W3SVC/1/ROOT/BadVdir/"。  
  
### <a name="unable-to-view-group-information-after-removing-stale-logons"></a>在移除過時的登入之後，無法檢視群組資訊  
  
**問題**  
 如果在組態進行期間，您發現了過時的登入並將它刪除，您可能就無法檢視群組資訊。  
  
**原因**  
 這是已知的組態問題。  
  
**解決方式**  
 刪除主控件 Windows 群組登入，然後再重新設定可能會有幫助。 如果仍然無法使用群組資訊，請連絡 Microsoft 產品支援中心。  
  
### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a>BizTalk Server 安裝之後，無法變更電腦名稱  
  
**問題**  
 當您變更執行 BizTalk Server 的電腦上的電腦名稱，而且您重新啟動 （） 將電腦重新開機，錯誤訊息可能會發生。  
  
**原因**  
 SQL Server 不支援變更電腦名稱，因此 BizTalk Server 不支援 BizTalk Server 會安裝和設定後變更電腦名稱。  
  
**解決方式**  
 我們建議您不要變更電腦名稱之後您安裝 BizTalk Server。  
  
### <a name="known-issues-with-enterprise-single-sign-on"></a>企業單一登入的已知的問題  
 本章節描述可能相關以企業單一登入 (SSO) 的安裝和組態問題。  
  
##### <a name="entsso-service-fails-to-start"></a>ENTSSO 服務無法啟動  
  
**問題**  
 ENTSSO 服務無法啟動。  
  
**原因**  
 如果 ENTSSO 服務不是以有效的 SSO 系統管理員帳戶執行，便無法啟動。  
  
**解決方式**  
 為 ENTSSO 服務指定有效的 SSO 系統管理員帳戶，並從服務控制管理員 (SCM) 嵌入式管理單元重新啟動服務。  
  
##### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a>BizTalk 服務相依於企業單一登入服務 (ENTSSO) 無法在重新開機後啟動  
  
**問題**  
 BTSSvc$BizTalkServerApplication 相依於企業單一登入服務 (ENTSSO)，重新開機後可能會在啟動時發生逾時。  
  
**原因**  
 企業單一登入服務可能需要約 3 分鐘的時間才能啟動。  
  
**解決方式**  
 將 “BizTalk Service BizTalk Group：BizTalkServerApplication” 服務的啟動類型選項設定為 [自動 (延遲開始)]。 這會在所有自動服務皆完成啟動程序後，再啟動該服務。  
  
##### <a name="cannot-access-an-affiliate-application"></a>無法存取分支機構應用程式  
  
**問題**  
 如果與分支機構應用程式相關聯的應用程式系統管理員帳戶無效，企業單一登入服務就會停用該分支機構應用程式。  
  
**原因**  
 SSO 應用程式系統管理員帳戶無效。  
  
**解決方式**  
 建立分支機構應用程式之前，請先確定 SSO 應用程式系統管理員帳戶是否有效。 接著，您必須啟用分支機構應用程式，才能使用該應用程式。  
  
##### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a>連接到用戶端電腦時，就會發生 RPC 錯誤  
  
**問題**  
 當您執行命令，例如**ssomanage-displayapp** *< applicationname\>*，其中電腦嘗試連線到遠端 SSO 伺服器以擷取資訊，您會收到下列錯誤： 錯誤： 0x800706BA: RPC 伺服器不存在。  
  
**原因**  
 當您指定錯誤的伺服器資訊，或無法使用遠端伺服器上的 SSO 服務時，就會發生這個錯誤。  
  
**解決方式**  
  
-   請依照[設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)來確認您已連接到正確的 SSO 伺服器。  
  
-   確定 SSO 服務已在您所連接的 SSO 伺服器上啟用及執行。  
  
##### <a name="master-secret-is-missing-or-corrupt"></a>主要密碼已遺失或損毀  
  
**問題**  
 主要密碼遺漏或損毀。 這個密碼通常會在設定組態時產生。 若遺漏此密碼，則企業單一登入服務啟動時，事件記錄中就會出現下列其中一則訊息。  
  
```
MessageId=10520  
Severity=Warning  
SSO_WARN_NO_SECRETS  
MessageId=10565  
Severity=Error  
SSO_ERROR_SECRET_VALIDATE_FAILED  
MessageId=10521  
Severity=Error  
SSO_ERROR_SECRETS_NOT_LOADED  
```

**原因**  
 如果密碼是在企業單一登入服務 (SSO) 使用某個服務帳戶執行時產生，但後來服務帳戶發生變更，就有可能發生這個問題。 此密碼是以加密的形式儲存在登錄中，加密時則是使用依據服務帳戶 (用來執行 ENTSSO 者) 的識別所產生的金鑰。  
  
**解決方式**  
 將 ENTSSO 執行時所用的服務帳戶變更為建立主要密碼時的原始服務帳戶。  
  
1.  備份主要密碼。 請參閱[備份主要密碼](../core/how-to-back-up-the-master-secret.md)。  
  
2.  停止企業單一登入服務。  
  
3.  變更服務帳戶。  
  
4.  重新啟動 SSO，並忽略任何與密碼損毀有關的事件記錄錯誤。  
  
5.  還原主要密碼。 請參閱[還原主要密碼](../core/how-to-restore-the-master-secret.md)。  
  
### <a name="custom-action"></a>自訂動作  
 本主題提供有關 Windows Server logo program BizTalk 伺服器憑證的詳細資料。 BizTalk Server 安裝程式作業期間，可能會執行下列自訂動作。  
  
|自訂動作|Description|  
|-------------------|-----------------|  
|ReadComplusData|讀取自訂 COM + 資料表，建立 XML 文件，並將它儲存在 Complus_XML_Data 屬性。|  
|SchedXmlConfig|用於設定 RFID 資料的電腦。|  
|CheckBaseEDI|檢查是否有舊版 EDI 存在|  
|CheckMQSeries|檢查是否有 MQSeries 存在|  
|CheckNET30Vista|檢查是否有 WCF 存在|  
|CheckWSSV3SP1|檢查是否有 Windows SharePoint Services 3.0 SP1 存在。|  
|CheckWSSV4|檢查 Windows SharePoint Services 4 存在|  
|GetFrameworkPath|Microsoft.Net framework 4 和 2.0 會保留安裝路徑，安裝程式在設定安裝程式屬性。|  
|Set_BAMClientExcelDir|建立 Excel 應用程式物件的屬性設定為在安裝程式中保留的 Microsoft Office 文件庫的路徑。|  
|Set_CurrentUser|設定目前使用者的網域 \ 使用者名稱資訊|  
|ViewInstallGuide|啟動 BizTalk Server 安裝指南，從安裝來源目錄。|  
|CA_CheckSTSLanguage|WSS 和 BizTalk 設定的語言相同時，請設定 STS_Language_Property 屬性。|  
|CA_CleanupRegistry|當您解除安裝 BizTalk Server 時，它會清除 BizTalk Server 組態期間所建立的登錄項目。|  
|CA_CleanupRegistry_OldProducts|會清除屬於較舊版本的 BizTalk Server，而且不需要的 BizTalk Server 的全新安裝的登錄項目。|  
|CA_RemovePatches|當您解除安裝 BizTalk Server 時，請移除 Microsoft BizTalk Server 更新。|  
|CA_ResolveWellKnownNames|建立安裝程式的屬性與已知的名稱，並將它們指派對應 SID。|  
|CA_SaveTargetVSVersionToRegistry|將 TargetVSVersion_Property 屬性設定為支援的 Visual Studio 版本的值。|  
|CA_StopServices|停止 IISAdmin、 規則引擎更新，以及 EDI 子系統服務。|  
|CleanupUsersKeys|移除 BizTalk Server 從 HKEY_CURRENT_USER 登錄機碼相關項目。|  
|DevEnvRunning|檢查是否正在執行 Visual Studio|  
|ValidateINSTALLDIR|驗證 BizTalk Server 安裝目錄的格式|  
|StartHostInstances|啟動 BizTalk Server 主控件執行個體。|  
|StopHostInstances|停止 BizTalk Server 主控件執行個體。|  
|MQSUnConfig|啟動 MQSeries 組態精靈，如未設定 MQSeries 代理程式。|  
|LaunchConfigFmk|啟動 BizTalk Server 組態精靈|  
|CHKASPNET|會檢查 ASP.NET 的安裝狀態|  
|CHKIIS|檢查 IIS 的安裝狀態|  
|TBExpired|檢查是否已過期 BizTalk Server 使用期限時發生|  
|BrandSKU|更新 BizTalk Server 使用期限時發生的 SKU 安裝而定的值。|  
|CA_ERROR|傳回安裝失敗|  
|InstallComplus|安裝 Complus 應用程式和元件。|  
|BAM_Add_Perf_Silent|安裝 BAM 的效能計數器|  
|RegsvcsApplicationDeployment|在 BizTalk 部署 COM + 應用程式 Dll 上執行 Regsvcs.exe （.NET 服務安裝工具）|  
|RegsvcsDeployment|在 Dll 上執行 Regsvcs.exe|  
|RegsvcsMQSAdapter|在 Dll 上執行 Regsvcs.exe|  
|RegsvcsSQLAdapter|在 Dll 上執行 Regsvcs.exe|  
|WMI_Add_MSBTS_Silent|註冊 BizTalk 伺服器命名空間和 WMI 類別。|  
|LaunchConfigFmk_SlashUP|取消設定 BizTalk Server|  
|CleanupComplus|Complus 應用程式和元件，會解除安裝。|  
|RemoveSKU|移除 BizTalk Server 使用期限時發生資料。|  
|BAM_Remove_Perf|Bam 會解除安裝效能計數器。|  
|LoadBTSCounters|載入 BizTalk Server 效能計數器。|  
|RegisterBtprojExtn|註冊 BizTalk 專案檔 (.btproj) 延伸模組。|  
|UnRegisterBtprojExtn|取消註冊 BizTalk 專案檔 (.btproj) 擴充功能。|  
|UnRegsvcsApplicationDeployment|當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll|  
|UnRegsvcsDeployment|當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll|  
|UnRegsvcsMQSAdapter|當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll|  
|UnRegsvcsSQLAdapter|當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll|  
|UnloadBTSCounters|卸載 BizTalk Server 效能計數器。|  
|WMI_Remove_MSBTS|從 WMI 移除 BizTalk Server 的命名空間。|  
|RegisterComsvcs|以無訊息模式執行 regsvr32.exe comsvcs.dll 上。|  
|DevenvSetupUninstall|執行 DevEnv.exe/安裝//resetskippkgs。|  
|RollbackComplus|回復 Complus 應用程式和元件的安裝。|  
|ResRegsvcsMQSAdapter|在指定的二進位檔上執行 regsvcs.exe|  
|ResRegsvcsSQLAdapter|在指定的二進位檔上執行 regsvcs.exe|  
|RestoreRegsvcsApplicationDeployment|將附加 framework Microsoft.BizTalk.ApplicationDeployment.Engine.dll 的路徑。|  
|RestoreRegsvcsDeployment|將附加 framework Microsoft.BizTalk.ApplicationDeployment.Engine.dll 的路徑。|  
|BrandSKURollback|如果發生安裝失敗，復原會註冊 SKU 資訊。|  
|CA_RestartServices_rollback|重新啟動已停止的服務。|  
|RemoveSKURollback|更新登錄中的 SKU 值。|  
|BAM_Res_Perf_Silent|在無訊息安裝期間，以做為 BAM 效能計數器的 Dll 註冊 Microsoft.BizTalk.Bam.EventObservation.dll。|  
|BAM_Rollback_Perf|取消 Microsoft.BizTalk.Bam.EventObservation.dll 登錄做 BAM 效能計數器 DLL|  
|RBKRegsvcsMQSAdapter|執行給定二進位 regsvcs.exe。|  
|RBKRegsvcsSQLAdapter|執行給定二進位 regsvcs.exe。|  
|RestoreBTSCounters|還原效能計數器.ini 檔案名稱與屬性。|  
|RollbackBTSCounters|執行命令 unlodctr BTSSvc.3.0。|  
|RollbackRegsvcsApplicationDeployment|設定 [FrameworkPath]&#124;[INSTALLDIR]Microsoft.BizTalk.ApplicationDeployment.Engine.dll 失敗的安裝案例。|  
|RollbackRegsvcsDeployment|在解除安裝/rollback 案例來叫用 regsvcs.exe。|  
|WMI_Restore_MSBTS_Silent|呼叫 mofcomp 註冊 WMI 結構描述|  
|WMI_Rollback_MSBTS|從 WMI 移除 BizTalk Server 的命名空間。|  
|CA_RestartServices_commit|重新啟動已停止的服務|  
|DevenvSetup|執行 DevEnv.exe /Setup /resetskippkgs 期間 BizTalk Server 安裝/解除安裝程序。|  
|ExecXmlConfig|用來進行組態變更 machine.config RFID 相關資料。|  
|ExecXmlConfigRollback|用來進行組態變更 machine.config RFID 相關資料。|  
  
#### <a name="running-biztalk-components"></a>執行 BizTalk 元件  
 下表列出必須使用系統管理權限或最高可用權限執行的 BizTalk 元件。  
  
|資料夾路徑|檔案名稱|使用者權限|  
|-----------------|---------------|---------------------|  
|\Program Files (x86)\Common Files\Microsoft shared\Help 9\Microsoft Document Explorer 2008|Install.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|BTSHatApp.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|BTSMMCLauncher.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|BtsWcfServicePublishingWizard.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|BTSWebSvcWiz.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|Configuration.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|REDeployWiz.exe|高可用權限|  
|\Program files (x86) \Microsoft BizTalk Server*您的版本*|Setup.exe|系統管理權限|  
|\Program files (x86) \Microsoft BizTalk Server*版本*\XSD Schema\EDI|MicrosoftEdiXSDTemplates.exe|自我解壓縮 .exe 檔案。|  
|\Program Files (x86)\Microsoft UDDI Services\config|組態 .exe|系統管理權限|  
|\Program Files\ Microsoft BizTalk RFID\bin|BTSMMCLauncher.exe|高可用權限|  
|\Program Files\Microsoft BizTalk RFID\BREConfi guration|組態 .exe|系統管理權限|  
