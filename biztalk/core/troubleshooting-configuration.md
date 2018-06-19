---
title: 疑難排解設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 902e591a-4ff4-4053-b329-0c022f44999a
caps.latest.revision: 37
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e523c5c992ea422e6fe81f3c0d948db7007bcdb1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975988"
---
# <a name="troubleshooting-configuration"></a>組態疑難排解
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式會在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的一或多部電腦上建立資料庫、將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所使用的資料表、角色和預存程序填入資料庫中，然後將執行階段所使用的 .NET 組件部署到 BizTalk 管理資料庫。  
  
 本章節將討論解決組態錯誤的疑難排解技術。 此外，也將列出一些常見的組態問題以及解決這些問題的方式。  
  
## <a name="configuration-logging"></a>組態記錄  
 組態程式會將詳細資訊寫入組態記錄檔中，此記錄檔預設是位於執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之電腦的暫存目錄中。 若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：  
  
 **echo %TEMP%**  
  
 此組態記錄檔含有已執行之組態步驟的摘要，以及組態程序中可能發生之任何失敗的相關診斷資訊。 如果發生組態錯誤，請在文字編輯器 (如 [記事本]) 中開啟此組態記錄檔，然後檢查此記錄檔，找出錯誤的可能原因。  
  
## <a name="troubleshooting-tools"></a>疑難排解工具  
 使用 SQL Server Profiler、Filemon 或 Regmon 可蒐集有關組態失敗的其他資訊。 如需有關這些工具的詳細資訊，請參閱[工具和公用程式，以供疑難排解使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="configuration-fails-when-biztalk-server-and-sql-server-are-installed-on-separate-computers"></a>當 BizTalk Server 和 SQL Server 安裝在不同電腦上時，會發生組態失敗  
  
##### <a name="problem"></a>問題  
 當您嘗試設定企業單一登入 (SSO) 元件時，組態會發生失敗，其錯誤與底下類似：  
  
 嘗試存取 SSO 資料庫時發生錯誤。  
  
 函式： FieldInfoCreate  
  
 -或-  
  
 無法啟用單一登入 (SSO) 服務 （錯誤碼 0X800706BA）  
  
##### <a name="cause"></a>原因  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同電腦上，則會在「分散式交易協調器」(MSDTC) 交易的內容底下執行組態作業，而且這兩部電腦之間必須可透過網路使用 MSDTC 功能。 如果無法在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦之間透過網路使用 MSDTC 功能，則可能會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 請依照[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)以確保能透過網路執行的電腦之間的 MSDTC 功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
#### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a>防毒軟體干擾組態，並造成組態失敗  
  
##### <a name="problem"></a>問題  
 當防毒軟體錯誤判斷出組態程式為病毒時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態會發生失敗。  
  
##### <a name="cause"></a>原因  
 防毒軟體沒有更新成包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態程式當做合法 （非病毒） 程式。  
  
##### <a name="resolution"></a>解決方案  
 設定此防毒程式，使其將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式辨識為合法 (非病毒) 程式，或是在組態程式執行時，暫時停用此防毒軟體。  
  
#### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a>組態失敗，其錯誤為「找不到檔案或組件名稱 FileName.dll 或其相依性的其中之一」。  
  
##### <a name="problem"></a>問題  
 在組態程序期間，出現了類似以下的錯誤：  
  
 無法部署 BizTalk 系統組件 "C:\Program Files\Microsoft\  
  
 BizTalk Server 2009\Microsoft.BizTalk.DefaultPipelines.dll。 [未指定]  
  
 例外狀況： 檔案或組件名稱 FileName.dll，或其中一個它  
  
 相依性，找不到。 檔案或組件名稱 FileName.dll，或  
  
 其中一個相依性，找不到。 」  
  
##### <a name="cause"></a>原因  
 如果 Network Service 帳戶在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上沒有暫存資料夾的寫入權限，可能會發生這個錯誤。 在組態進行期間，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態會使用 Windows Management Instrumentation (WMI)，將 .NET 組件部署到 BizTalk 管理資料庫。 WMI 在將這些組件部署到 BizTalk 管理資料庫時，會模擬 Network Service 帳戶，因此，Network Service 帳戶在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上必須有暫存資料夾的寫入權限。  
  
##### <a name="resolution"></a>解決方案  
 將執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之電腦上的暫存資料夾寫入權限授與給 Network Service 帳戶，然後再次執行組態程式。 若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：  
  
```  
echo %TEMP%  
```  
  
#### <a name="configuration-of-the-group-fails-if-the-netbios-name-of-the-computer-running-sql-server-exceeds-15-characters"></a>如果執行 SQL Server 之電腦的 NetBIOS 名稱超過 15 個字元，群組的組態會失敗  
  
##### <a name="problem"></a>問題  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組組態失敗，而且在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態記錄檔中出現與下列類似的錯誤：  
  
 2006-08-29 23:54:00:0902 [警告] AdminLib GetBTSMessage: hrErr = 80070547;  
  
 Msg = 無法從網域讀取資訊的組態  
  
 控制站，可能是因為該機器已無法使用，或存取有  
  
 已拒絕。;  
  
##### <a name="cause"></a>原因  
 如果執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 NetBIOS 名稱長度超過 15 個字元，會發生這個問題。 如果 NetBIOS 名稱超過 15 個字元，Windows 就會將此 NetBIOS 名稱截斷為 15 個字元，而此 NetBIOS 名稱就不再符合這部電腦的完整格式網域名稱 (FQDN) 或 DNS 名稱的第一個部分。 如果此 NetBIOS 名稱不符合電腦 FQDN 的第一個部分，群組組態將會失敗。  
  
##### <a name="resolution"></a>解決方案  
 變更執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 NetBIOS 名稱，使其不超過 15 個字元，然後再次執行組態。  
  
> [!NOTE]
>  如果您為電腦重新命名，則必須重新啟動電腦。  
  
#### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a>如果 SQL Server 資料庫檔案與 SQL Server 資料夾中已經存在的指定資料庫同名，組態會發生失敗  
  
##### <a name="problem"></a>問題  
 組態發生失敗，其錯誤與以下類似：  
  
 無法安裝 BAM 資料庫  
  
 無法開啟登入 'BAMPrimaryImport' 中要求的資料庫  
  
 登入失敗。 使用者登入失敗 '*BizTalk\BizTalkUser*'  
  
##### <a name="cause"></a>原因  
 如果執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 \MSSQL\data 資料夾中已經有 .mdf 檔案或 .ldf 檔案與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式嘗試建立的 .mdf 檔案或 .ldf 檔案同名，就會發生這個錯誤。 針對資料庫建立的 .mdf 檔案和 .ldf 檔案名稱是衍生自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式中所指定的資料庫名稱，但是附加了 .mdf 和 .ldf 副檔名。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個行為，請使用下列其中一種方法：  
  
-   刪除與您要建立之任何資料庫名稱同名的任何 .mdf 檔案或 .ldf 檔案。  
  
-   選擇使用與 SQL Server 之 \Program Files\Microsoft SQL Server\MSSQL\data 資料夾中已經存在的任何 .mdf 檔案或 .ldf 檔案不同名的資料庫名稱。  
  
#### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a>指定本機帳戶時，網域控制站上的組態發生失敗  
  
##### <a name="problem"></a>問題  
 當執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態程式的網域控制站，如果您指定的 biztalkserverapplication 主控件或 BizTalkIsolatedHost 主機的本機群組 （例如，BizTalk 主控件使用者群組） 的組態會失敗。  
  
##### <a name="cause"></a>原因  
 網域控制站會自動將本機 Windows 群組視為網域 Windows 群組 (也就是說，網域控制站上不會有本機 Windows 群組)。 如果您在執行組態程式時，為主控件指定了本機 Windows 群組，則當您嘗試為此群組建立 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 登入時，組態會發生失敗。 當伺服器是網域控制站時，組態程式不會停用本機 Windows 群組選項。  
  
##### <a name="resolution"></a>解決方案  
 針對組態進行期間建立的主控件指定網域群組。  
  
#### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a>如果 SQL Server 已經重新命名，則組態程式將無法建立 SQL Server 分析資料庫  
  
##### <a name="problem"></a>問題  
 若您將安裝 SQL Server Analysis Server 的電腦重新命名，組態程式就無法建立新的 SQL Server 分析資料庫，而且會產生類似以下的錯誤：  
  
 無法連線到儲存機制。  
  
 Analysis server:\<機器名稱\>  
  
 Error:  
  
 '\\\\< 機器名稱\>\MsOLAPRepository$\msmdrep.mdb' 不是有效的路徑。  
  
 請確定您正確拼寫的路徑名稱，而且是  
  
 連接到檔案所在的伺服器。  
  
##### <a name="cause"></a>原因  
 組態程式無法判斷安裝 SQL Server Analysis Server 之電腦的新名稱。  
  
##### <a name="resolution"></a>解決方案  
 請以手動方式執行以下步驟，將 Analysis Server 更新為新的電腦名稱：  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server**，指向  **Analysis Services**，然後按一下  **Analysis Manager**。  
  
2.  在**Analysis Manager**導覽面板中按兩下**Analysis Servers**節點來展開它。  
  
3.  以滑鼠右鍵按一下您想要編輯，然後選取 儲存機制連線字串伺服器**編輯儲存機制連線字串**。  
  
4.  在**編輯儲存機制連線字串**對話方塊，確認伺服器名稱，這個字串中的，將其更新為新的電腦名稱是否正確。  
  
5.  瀏覽至下列位置： \<*安裝目錄*\>\Program Files\Microsoft Analysis Services\Bin。  
  
6.  以滑鼠右鍵按一下**Bin**資料夾，然後再按一下**共用和安全性**。 **Bin 屬性** 對話方塊隨即出現。  
  
7.  在**Bin 屬性**對話方塊中，按一下 **共用**索引標籤，以確認所有的線上分析處理 (OLAP) 系統管理員具有完整權限，此資料夾。  
  
#### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a>從 Visual Studio 重新部署組件時，成品從組態資料庫中消失  
  
##### <a name="problem"></a>問題  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 內的專案層級上重新部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案時，此專案中參考重新部署之專案的所有成品似乎會在重新整理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MMC 後消失。  
  
##### <a name="cause"></a>原因  
 為了說明這個問題的原因，假設以下範例是根據範例 BizTalk Server 解決方案，而使用者想要在其中重新部署 Maps 專案。 請注意，編譯專案會產生個別的組件。 下圖指示使用者執行重新部署之前的解決方案狀態， 成品之間的關係如下：  
  
-   Orch1、Orch2、Maps、Pipelines 和 Schemas 都是專案。  
  
-   Orch1 參考 Maps，而 Maps 則參考 Schemas。  
  
-   Orch2 參考 Schemas。  
  
-   Pipelines 參考 Schemas。  
  
 ![](../core/media/bcd-existingbiztalkserversolutionc.gif "bcd_ExistingBizTalkServerSolutionc")  
  
 如果使用者使用預設 Visual Studio 專案設定來重新部署 Maps 專案，則 Orch1、Orch2 和 Pipeline 成品會消失，如下圖所示。  
  
 ![](../core/media/bcd-biztalksolutionwlostartifactsc.gif "bcd_BizTalkSolutionWLostArtifactsc")  
  
 重新部署 Maps 是一個兩個步驟的程序，要先解除部署目前已部署的 Maps.dll 組件，然後部署新的 Maps.dll 檔案。 Visual Studio 重新部署程序的一部分，請以自動執行這些步驟。  
  
> [!NOTE]
>  上一個句子嚴格來說並不正確，因為 Visual Studio 一定會執行這些步驟，所以它不會意識到這是適當的作法。  
  
 關鍵的地方是，為了要解除部署 BizTalk Server 組件，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 也必須解除部署相依於該組件 (已設定部署旗標) 的所有組件。 在這個範例中，若要執行重新部署的第一個解除部署步驟，BizTalk Server 需要解除部署 Orch1.dll (它相依於 Maps.dll)。 在解除部署 Maps.dll 時，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 也會解除部署 Schemas.dll (假設它已設定部署旗標)。 為了要解除部署 Schemas.dll，Visual Studio 需要解除部署 Orch2.dll 和 Pipelines.dll (這兩者都相依於 Schemas.dll)。  
  
 問題在於，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]甲重新部署只有 Maps.dll 和它所依據的組件： 在此情況下，Schemas.dll。 讓使用者重新整理 BizTalk Server MMC 時，Orch1、 Orch2 和 Pipeline 組件似乎已消失，但是 Maps.dll 和 Schemas.dll 仍然可見。  
  
##### <a name="resolution"></a>解決方案  
 如果是主要專案 (它會參考其他專案)，請執行以下作業：  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下方案節點。  
  
2.  按一下**屬性**開啟**方案屬性頁** 對話方塊。  
  
3.  按一下**組態屬性**，然後按一下 **組態**。  
  
4.  清除**部署**參考之專案的核取方塊。  
  
5.  在 [方案總管] 中，執行新的方案層級部署。 若要這樣做，以滑鼠右鍵按一下方案節點，然後按一下 **部署方案**。  
  
#### <a name="supported-virtual-directory-types"></a>支援的虛擬目錄類型  
 匯出作業時參考 Web 服務從協調流程，並嘗試進行 MSI 匯出，將會成功，相關聯的虛擬目錄為型別時，才**IIsWebVirtualDir**或**IIsWebDirectory**. **IIsWebVirtualDir**和**IIsWebDirectory**會出現在 IIS metabase 中的節點型別。 **IIsWebVirtualDir**是使用的虛擬目錄**路徑**指向絕對檔案資料夾的屬性。 **IIsWebDirectory**而不是虛擬目錄**路徑**屬性，因此是指相對檔案資料夾，通常是另一個子資料夾**IIsWebVirtualDir**或**IIsWebDirectory**節點。 在 Metabase 階層中，經常會看到用來描述資料夾的這兩個類型。  
  
 類型的虛擬目錄**IIsConfigObject**不支援 MSI 匯出會在此情況下失敗。 **IIsConfigObject**非預期的 metabase 節點類型可以是 BizTalk Server 未適當處理的有效節點類型，或未適當建立的 （並因此它是無效的） metabase 項目的指示。 在此情況下，BizTalk Server 將會顯示類似下列的錯誤訊息： 類型 IIsConfigObject 的未預期的目錄項目"Iis: //lm/w3svc/1/root/badvdir/"。  
  
#### <a name="unable-to-view-group-information-after-removing-stale-logons"></a>在移除過時的登入之後，無法檢視群組資訊  
  
##### <a name="problem"></a>問題  
 如果在組態進行期間，您發現了過時的登入並將它刪除，您可能就無法檢視群組資訊。  
  
##### <a name="cause"></a>原因  
 這是已知的組態問題。  
  
##### <a name="resolution"></a>解決方案  
 刪除主控件 Windows 群組登入，然後再重新設定可能會有幫助。 如果仍然無法使用群組資訊，請連絡 Microsoft 產品支援中心。  
  
##### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a>BizTalk Server 安裝之後，無法變更電腦名稱  
  
###### <a name="problem"></a>問題  
 當您變更執行的電腦上的電腦名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而且您重新啟動 （重新開機） 的電腦，錯誤訊息可能會發生。  
  
###### <a name="cause"></a>原因  
 SQL Server 不支援變更電腦名稱，因此[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援一次變更電腦名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝和設定。  
  
###### <a name="resolution"></a>解決方案  
 我們建議您不要變更電腦名稱之後您安裝 BizTalk Server。