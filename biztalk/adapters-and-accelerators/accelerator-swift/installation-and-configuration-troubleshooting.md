---
title: 安裝和組態疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, troubleshooting
- configuring, troubleshooting
- troubleshooting, configuring
- troubleshooting, installing
ms.assetid: 25a2f6c5-c049-4042-8e38-4f7a2556e066
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10c0816508d2efb05dbac14797f80ffef12765fa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967175"
---
# <a name="installation-and-configuration-troubleshooting"></a>安裝和組態疑難排解
## <a name="setup-is-unable-to-deploy-the-runtimeschemas-assembly"></a>安裝程式無法部署 RuntimeSchemas 組件  
  
### <a name="symptom"></a>徵兆  
 A4SWIFT 安裝程式無法部署 RuntimeSchemas.dll。 如果組件不會在安裝之後以手動方式部署，[A4SWIFT 組態精靈] 將會失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 在下列情況的其中一個存在：  
  
- 當您嘗試執行 A4SWIFT 的初始安裝時已部署的執行階段結構描述組件。  
  
- Microsoft[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]您嘗試安裝 A4SWIFT 的電腦上未啟動。  
  
- 執行階段結構描述組件已部署，當您嘗試升級 A4SWIFT，且另一個組件所參考。 這導致解除部署 A4SWIFT 執行階段結構描述組升級計劃。  
  
### <a name="solution"></a>方案  
 請繼續進行，如下所示，取決於問題的本質而定：  
  
- 如果已部署的執行階段結構描述組件，當您嘗試執行 A4SWIFT 的初始安裝時，開啟 在 Microsoft BizTalk 總管[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]，以滑鼠右鍵按一下 Microsoft 組件。Solutions.FinancialServices.SWIFT.RuntimeSchemas，，然後按一下 解除部署。 使用 BizTalk 部署精靈部署最新版的從 RuntimeSchemas.dll *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Assemblies。  
  
- 如果[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]是未啟動，啟動[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]Service Manager。 使用 BizTalk 部署精靈部署最新版的從 RuntimeSchemas.dll *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Assemblies。  
  
- 如果已部署的執行階段結構描述組件，當您嘗試升級 A4SWIFT，且所參考另一個組件，就會解除部署在 BizTalk 總管 中，參考的組件，並解除部署 BizTalk 總管 中的 RuntimeSchemas.dll。 使用 BizTalk 部署精靈部署最新版的從 RuntimeSchemas.dll *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Assemblies。  
  
## <a name="after-the-web-components-feature-is-removed-message-repair-and-reconciliation-is-incorrectly-shown-as-uninstalled"></a>移除網路元件功能之後，訊息修復和重新調整不正確地顯示為解除安裝  
  
### <a name="symptom"></a>徵兆  
 移除 Web 元件，A4SWIFT Message Repair 和 New Submission 功能之後，您無法解除安裝、 安裝，或設定訊息修復和重新調整功能 （或 A4SWIFT 元件）。 如果安裝了訊息修復和重新調整，A4SWIFT 無法辨識為安裝的功能。 如果您嘗試安裝、 修改或移除訊息修復和從內 （從控制台中顯示） 的新增/移除程式的重新調整，新增/移除程式會指出未安裝此功能。  
  
### <a name="possible-cause"></a>可能的原因  
 您已從移除[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員群組之後，您已安裝 Web 元件，Message Repair 和 New Submission 的功能和訊息修復和重新調整功能。 如果您接著移除網路元件功能 (可執行的成員，而[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組)、 A4SWIFT 安裝程式將會移除檔案的訊息修復和重新調整功能具有相依性。 這些檔案包括 ConfigFramework.exe。  
  
### <a name="solution"></a>方案  
 如果您遇到此問題，請繼續，如下所示：  
  
1. 在 [電腦管理] 視窗中，加入您自己回[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]登出電腦，系統管理員群組，並再登入。  
  
2. 重新安裝 Web 元件，Message Repair 和 New Submission 的功能。  
  
   > [!NOTE]
   >  步驟 2 新增 ConfigFramework.exe 回 A4SWIFT 安裝。  
  
3. 重新安裝 MRSR 功能。  
  
4. 如果您仍然不想 Web 元件 Message Repair 和 New Submission 功能，請將它移除。  
  
## <a name="repairing-a4swift-to-add-the-service-folder-can-result-in-improper-access-permissions-for-that-folder"></a>修復 A4SWIFT 加入服務資料夾可能會導致該資料夾不適當的存取權限  
  
### <a name="symptom"></a>徵兆  
 如果您刪除資料夾 *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Service 與已正確設定的 A4SWIFT 安裝，然後執行 A4SWIFT 回到 A4SWIFT 安裝程式來新增伺服器資料夾的修復功能安裝 [服務] 資料夾的存取權限不是正確的狀態。 正確的權限是具有完整控制權 A4SWIFT 系統管理員] 及 [讀取 & 執行 A4SWIFT 使用者。  
  
 如果服務資料夾已存在時，會執行 A4SWIFT 安裝的修復功能，這也會發生。 存取權限，由 [A4SWIFT 組態精靈] 中，設定會覆寫不正確的值。  
  
### <a name="possible-cause"></a>可能的原因  
 Message Repair 和 New Submission 安裝 Web 元件功能加入服務資料夾。 如果您刪除資料夾，然後執行 A4SWIFT 安裝的修復選項，Message Repair 和 New Submission 中新增 Web 元件，A4SWIFT 安裝程式不會執行設定精靈 (ConfigFramework.exe) 來設定資料夾的權限。 因為已經執行 「 組態精靈 」，就很難執行精靈，再次以重設組態。 如此一來，[修復] 選項將重新建立所有已刪除的檔案和資料夾，但它將不會正確地設定存取權限。  
  
 如果資料夾存在時執行修復，修復程序也覆寫服務資料夾的權限。 如同之前執行修復，刪除 [服務] 資料夾的情況下它將會很難執行組態程式設定權限。 在這種情況，權限可能會不正確，您就必須手動設定它們。  
  
### <a name="solution"></a>方案  
 如果您遇到這個問題，以手動方式設定下列服務資料夾的存取權限：  
  
|群組或使用者名稱|權限|  
|------------------------|----------------|  
|A4SWIFT 系統管理員|完整控制|  
|A4SWIFT 使用者|閱讀及執行|  
  
 若要設定這些權限，請繼續進行，如下所示：  
  
 在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Service。  
  
1.  以滑鼠右鍵按一下 服務 資料夾中，按一下**屬性**，然後按一下**安全性** 索引標籤。  
  
2.  在 群組或使用者名稱 窗格的 服務內容 對話方塊中，按一下**新增**，輸入 ***\<伺服器名稱\>* \A4SWIFT 管理員**，然後按一下  **確定**.  
  
    > [!NOTE]
    >  如果 A4SWIFT Administrators 群組的網域群組，請輸入 ***\<網域名稱\>* \A4SWIFT 管理員**。  
  
3.  重複步驟 2 ***\<伺服器名稱\>* \A4SWIFT 使用者**，或 **\<*網域名稱*\>\A4SWIFT 使用者**如果A4SWIFT 使用者群組是網域群組。  
  
4.  在 [群組或使用者名稱] 窗格中，選取**A4SWIFT 管理員**。 在 [權限] 窗格中，選取**允許**for**完全控制**。  
  
5.  在 [群組或使用者名稱] 窗格中，選取**A4SWIFT 使用者**。 在 權限 窗格中，按一下 **允許**如**讀取與執行**，**列出資料夾內容**，以及**讀取**。  
  
6.  按一下 [確定] 。  
  
## <a name="upgrade-results-in-a-side-by-side-installation-of-two-versions-of-a4swift"></a>在並排顯示兩個版本的 A4SWIFT 安裝的升級結果  
  
### <a name="symptom"></a>徵兆  
 當您嘗試升級至[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，A4SWIFT 的先前版本可能不會完全移除。 如果您是從控制台中執行新增/移除程式，目前和先前版本，可能會顯示目前已安裝的程式清單。  
  
### <a name="possible-cause"></a>可能的原因  
 下列任一條件可能會導致上述的發生：  
  
- 嘗試升級的使用者不是成員的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
- [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] (MSSQLSERVER) 服務已停止。  
  
- 您使用來執行無訊息升級**setup.exe /addlocal**命令。  
  
### <a name="solution"></a>方案  
 若要避免的並排顯示安裝[!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)]並[!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)]在升級期間發生，請確定您 （登入的使用者） 所隸屬[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組， [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] (MSSQLSERVER) 服務已啟動。  
  
 如果您得到的並排顯示安裝[!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)]或是[!INCLUDE[btaA4SWIFT2.1abbrev](../../includes/btaa4swift2-1abbrev-md.md)]和[!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)]，繼續進行，如下所示：  
  
1. 備份 [SWIFT Messages] 資料夾中的資料。  
  
2. 登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]BTS Administrators 的成員群組，並確定 MSSQLSERVER 服務正在執行。  
  
3. 移除 A4SWIFT 的先前版本。  
  
4. 一次升級至最新版的 A4SWIFT。 這次升級將會運作，且沒有並排顯示安裝將會建立。  
  
5. 使用 「 BizTalk 部署公用程式，手動解除部署 Microsoft。Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll，並重新部署將它從 [A4SWIFT 安裝位置的組件] 資料夾。 如需有關這項工具的詳細資訊，請參閱 < [BRE 部署公用程式](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)。  
  
## <a name="the-uninstall-or-upgrade-process-may-not-complete-correctly-if-you-do-not-restart-when-prompted"></a>在解除安裝或升級程序可能不正確地完成若未重新出現提示時  
  
### <a name="symptom"></a>徵兆  
 解除安裝或升級程序不正確地完成。  
  
### <a name="possible-cause"></a>可能的原因  
 如果您不解除部署的專案參考現有的已部署組件，您可能會收到提示，指出您必須重新啟動系統，A4SWIFT 組態變更才會生效。 如果您沒有按一下**是**立即重新啟動，有些在全域組件快取中移除已指派的組件可能不會移除，導致額外的解除安裝或升級的程序，以不正確地完成。  
  
### <a name="solution"></a>方案  
 解除部署任何參考現有的已部署組件的專案，然後再次執行解除安裝或升級程序。  
  
## <a name="if-the-iis-admin-service-is-stopped-during-setup-you-must-reconfigure-the-webservice-feature"></a>如果在安裝期間停止 IIS 管理服務，您必須重新設定 web 服務功能  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈 不會正確設定 web 服務功能。 您會收到下列錯誤：  
  
 「 無法建立 MRSR 成品： 無法連接到遠端伺服器。 」  
  
### <a name="possible-cause"></a>可能的原因  
 IIS Admin Service 已停止執行時[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈。  
  
### <a name="solution"></a>方案  
 若要成功完成設定程序，請繼續進行，如下所示：  
  
1. 關閉[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]設定 主控台。  
  
2. 重新啟動 IIS 管理服務。  
  
3. 執行 *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Configuration.exe。  
  
4. 在 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，選取**取消設定功能**，然後選取**WebService**。  
  
5. 請確定在 設定 主控台中的 WebService 功能的狀態，會顯示為 尚未設定。  
  
6. 選取 **套用設定**。  
  
   > [!NOTE]
   >  [A4SWIFT 組態精靈] 現在會正確設定 web 服務功能。  
  
## <a name="a4swift-configuration-will-fail-if-the-biztalkserverapplication-host-was-not-created-in-biztalk-server-configuration"></a>如果 biztalkserverapplication 主控件不是在 BizTalk Server 組態，A4SWIFT 組態將會失敗  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈 不會正確設定 web 服務功能。 您會收到下列錯誤：  
  
 「 無法建立 MRSR 成品： 物件參考未設定為物件的執行個體。 」  
  
### <a name="possible-cause"></a>可能的原因  
 BizTalk Server 執行階段組態期間未建立內含式主控件和主控件執行個體。  
  
### <a name="solution"></a>方案  
 若要修復 A4SWIFT 組態，請繼續進行，如下所示：  
  
- 在 [BizTalk Server 管理] 中建立的主機。 沒有需要現在擁有執行中執行個體。  
  
- 在中執行 RepairBAS 工具 *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\SDK\Tools 資料夾的 A4SWIFT 安裝。  
  
  若要這樣做，請繼續進行，如下所示：  
  
1.  開始**BizTalk Server 管理**主控台。  
  
2.  在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**，然後展開**BizTalk 群組**，然後展開**平台設定。**  
  
3.  以滑鼠右鍵按一下**主機**，指向**新增**，然後選取**主機**。  
  
4.  在 [主機屬性] 畫面中，在 [一般] 窗格中，輸入下列內容：  
  
    -   主機名稱： **BizTalkServerApplication**  
  
    -   類型：**同處理序**  
  
    -   Windows 群組：  **\<*網域*\>\BizTalk 應用程式使用者**（或您在執行 BizTalk 內含式 BizTalk Server 組態期間設定的帳戶應用程式）  
  
    -   在 選項 區段中，選取 兩者**允許主控件追蹤**並**將此預設主機群組中**。  
  
5.  按一下 [確定] 。  
  
6.  按一下 **啟動**然後按一下 執行。 型別**cmd** ，然後按一下**確定**。  
  
7.  在命令提示字元中，瀏覽至 * %programfiles%***\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools**。  
  
8.  型別**RepairBAS.exe** ，然後按**Enter**。  
  
## <a name="you-must-change-the-bre-deployment-configuration-file-when-running-the-bre-deployment-utility-on-a-64-bit-computer"></a>在 64 位元電腦上執行 BRE 部署公用程式時，您必須變更 BRE 部署設定檔  
  
### <a name="symptom"></a>徵兆  
 BRE 部署公用程式無法正常運作時您它在 64 位元電腦上或在非預設以外的目錄 （C:\Program Files\Microsoft BizTalk Accelerator for SWIFT) 中的電腦上執行 32 位元。  
  
### <a name="possible-cause"></a>可能的原因  
 BRE 部署公用程式將無法正常運作直到您變更內 BREDeployment.exe.config 檔案中的路徑\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools 資料夾。  
  
### <a name="solution"></a>方案  
 在 [記事本] 中開啟過的 BREDeployment.exe.config 並變更詞彙目錄、 結構描述，以及基底原則資料夾中更新公用程式的組態。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解：問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)