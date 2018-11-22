---
title: 疑難排解： 問題與 Resolutions3 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 40f59f54-183e-43db-afb5-0a45b437697f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab1f869d8d7c06260a1f7f8388991a0e18a2ff09
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50758693"
---
# <a name="troubleshooting-issues-and-resolutions"></a>疑難排解： 問題與解決方式
本主題說明執行 Microsoft® 相關的問題[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。 每個問題的說明都會詳細描述其特殊徵狀、可能的原因以及解決方式。  
  
## <a name="error-publishing-a-batch-of-n-messages"></a>發佈 n 個訊息的批次作業時發生錯誤  
  
### <a name="symptom"></a>徵兆  
 您在事件日誌中收到下列或類似的錯誤：  
  
 為傳輸配接器「BizTalk HTTP 接收者」發佈 n 個訊息的批次作業至 MessageBox 資料庫時，傳訊引擎發生錯誤。 如需有關此失敗的詳細資訊，請參考「狀況與活動追蹤」工具，並檢查是否已正確設定結束點繫結。  
  
### <a name="possible-cause"></a>可能的原因  
 此錯誤可能是由下列其中一項原因所造成：  
  
- 遺失解密憑證  
  
- 未正確加密的訊息  
  
- 未授權的訊息 (來源無法辨識為有效的夥伴)  
  
- 訊息的任何標頭部分驗證失敗：前序、傳遞標頭或服務標頭。  
  
  此訊息之前可能有另一錯誤訊息，詳細說明原因。  
  
### <a name="solution"></a>方案  
 請檢閱錯誤訊息所提供的詳細資訊，可取得額外的協助。 正在重新啟動 Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ 可能可以解決此問題。  
  
## <a name="you-cannot-unenlist-all-artifacts"></a>無法取消登錄所有成品  
  
### <a name="symptom"></a>徵兆  
 執行 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean 公用程式並未取消登錄所有成品。  
  
### <a name="possible-cause"></a>可能的原因  
 如果您執行[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]之前刪除協議與夥伴從 Microsoft® Management Console (MMC) 的 Clean 公用程式，BtarnClean 公用程式將無法取消登錄所有成品，因為仍在使用。  
  
### <a name="solution"></a>方案  
  
##### <a name="to-remove-artifacts-using-the-loopback-utility"></a>用回送公用程式移除成品  
  
1.  在命令提示字元中，輸入：  
  
    ```  
    lookback.exe /disable <home org or partner>  
    ```  
  
2.  執行 BtarnClean.exe 檔案。  
  
3.  在 [BizTalk 總管] 中刪除合作對象。  
  
## <a name="installing-btarn-on-a-computer-without-biztalk-server-causes-missing-files"></a>沒有 BizTalk Server 的電腦上安裝 BTARN 會導致檔案遺失  
  
### <a name="symptom"></a>徵兆  
 執行 ConfigFramework.exe 檔案會產生任何結果，並沒有 MicrosoftBizTalk Server 或 Microsoft 的電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]安裝。 這個 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態只能當作 HTTP 用戶端使用。  
  
### <a name="possible-cause"></a>可能的原因  
 在安裝中遺失兩個 DLL 檔案。  
  
### <a name="solution"></a>方案  
 在電腦上安裝 SQLXML，然後手動將 Msxml4.dll 與 Atl71.dll 檔案複製到 [System] 資料夾。  
  
## <a name="you-receive-an-access-error-when-attempting-to-change-the-btarn-configuration"></a>要變更 BTARN 組態時收到存取錯誤  
  
### <a name="symptom"></a>徵兆  
 當您使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台匯入組態檔案時，收到下列錯誤訊息：  
  
 無法將「傳送埠」'RNSTT.Async' 的「主要傳輸」之傳輸類型資料存放至組態存放區。 存取遭到拒絕。  
  
 當您嘗試變更組態 (例如要建立新的夥伴) 時，也可能會收到這種錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 目前使用者並非「BizTalk 系統管理員」群組中的成員。  
  
### <a name="solution"></a>方案  
 請確認目前使用者為「BizTalk 系統管理員」群組中的成員。  
  
## <a name="you-receive-bam-errors"></a>收到 BAM 錯誤  
  
### <a name="symptom"></a>徵兆  
 「事件檢視器」中出現以下錯誤訊息：  
  
 在追蹤「訊息」活動中發生錯誤。 錯誤訊息為「預存程序不存在」。  
  
 -或-  
  
 終止 BAM 訊息活動識別碼的錯誤 *\<ID 編號\>*。  
  
### <a name="possible-cause"></a>可能的原因  
 未安裝商務活動監控 (BAM) 追蹤工具。  
  
### <a name="solution"></a>方案  
 安裝追蹤工具使用 BAM **Custom Installation**選項。 如果您不需要 BAM 功能，可以忽略這些訊息，或利用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台停用追蹤功能。 停用追蹤功能之後，必須重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 與 Internet Information Services (IIS)。  
  
## <a name="your-xsd-schema-does-not-display-properly-in-biztalk-editor"></a>您的 XSD 結構描述無法正確顯示在 BizTalk 編輯器中  
  
### <a name="symptom"></a>徵兆  
 無法用 BizTalk 編輯器正確檢視結構描述的內容。  
  
### <a name="possible-cause"></a>可能的原因  
 結構描述缺少 `displayroot_reference` 項目的 `schemaInfo` 屬性。  
  
### <a name="solution"></a>方案  
 使用 [記事本] 或其他文字編輯器開啟這個結構描述，並將 `displayroot_reference` 屬性加入至 `schemaInfo` 項目內。 `displayroot_reference` 屬性的值應該與 `root_reference` 屬性相同。  
  
 例如：  
  
 \<schemaInfo document_type ="4A1"版本 ="V02_00"xmlns ="<http://schemas.microsoft.com/BizTalk/2003>」 *displayroot_reference ="Pip4A1StrategicForecastNotification"* root_reference ="Pip4A1StrategicForecastNotification 」 \>  
  
## <a name="404-not-found-error-when-sending-a-http-request"></a>發出 HTTP 要求卻收到「404 找不到」(404 Not Found) 錯誤  
  
### <a name="symptom"></a>徵兆  
 當傳送 HTTP 要求時，收到下列或類似的錯誤：  
  
 遠端伺服器傳回錯誤：(404) 找不到。  
  
 訊息無法傳送至 ../BTSHttpReceive.dll。  
  
### <a name="possible-cause"></a>可能的原因  
 Internet Information Services (IIS) 中的 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 網際網路伺服器 API (ISAPI) 擴充程式 DLL (BTSHttpReceive.dll) 尚未設定好。 如果 HwsMessages HttpReceive Web 服務延伸模組未設定，或這個 Web 服務延伸模組已設定但不被允許，就會發生這個問題。  
  
### <a name="solution"></a>方案  
 請執行下列程序，判斷 HwsMessages HttpReceive Web 服務延伸模組是否已設定為允許 (或尚未設定)。  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a>在 IIS 中設定 BizTalk ISAPI 擴充程式 DLL  
  
1. 按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2. 依序展開 **\<電腦名稱\>（本機電腦)**，然後按一下 **網頁服務延伸** 。  
  
3. 在 [ **Web 服務延伸模組**] 窗格中，確認是否允許 HwsMessages HttpReceive 的狀態。 如果沒有，請以滑鼠右鍵按一下**HwsMessages HttpReceive**，然後按一下**允許**。  
  
   如果 HwsMessages HttpReceive Web 服務延伸模組未設定 (未包含於 IIS 管理員的 Web 服務延伸模組清單中)，請執行下列程序。  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a>在 IIS 中設定 BizTalk ISAPI 擴充程式 DLL  
  
1.  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2.  依序展開**\<電腦名稱\>（本機電腦）**，以滑鼠右鍵按一下**網頁服務延伸**，然後按一下**新增新的 Web 服務延伸**.  
  
3.  中**新增網頁服務延伸**對話方塊中，於**延伸模組名稱**方塊中，輸入**BizTalk ISAPI 擴充程式**，然後按一下**新增**。  
  
4.  在  **Add File**對話方塊的 **檔案路徑** 方塊中，輸入 **\<磁碟機\>: \Program Files\Microsoft BizTalk Server\<版本\>\HttpReceive\BTSHttpReceive.dll** ，然後按一下 **確定** 。  
  
5.  在 **新增網頁服務延伸**對話方塊中，選取**設定延伸狀態成允許**，然後按一下  **確定**。  
  
## <a name="an-access-violation-occurs-when-running-the-configuration-wizard"></a>執行組態精靈時發生違規存取  
  
### <a name="symptom"></a>徵兆  
 您在事件日誌中收到下列或類似的錯誤：  
  
 設定成使用者帳戶 \HostSvc 身分的 BizTalk 外掛式主控件執行個體並未執行，或不在這台電腦上。 請用 BizTalk 管理主控台建立一個新的外掛式主控件，或將已經設定好的外掛式主控件重新設定成以 \hostsvc 身分執行。  
  
### <a name="possible-cause"></a>可能的原因  
 若要執行 「 組態精靈 」，使用者應該設定為\<*電腦名稱*\>\hostsvc'，不是 '\hostsvc'。  
  
### <a name="solution"></a>方案  
 開啟 BizTalk 管理主控台中，並變更 '\hostsvc'，在帳戶下執行的主機，使他們的帳戶下執行 '\<*電腦名稱*\>\hostsvc'。  
  
## <a name="you-receive-an-error-when-importing-and-compiling-a-rosettanet-next-generation-pip-schema"></a>匯入編譯 RosettaNet 下一代 PIP 結構描述時收到錯誤  
  
### <a name="symptom"></a>徵兆  
 您在事件日誌中收到下列或類似的錯誤：  
  
 錯誤 CS0234： 類型或命名空間名稱 'SerializableAttribute' 不存在於類別或命名空間 'RosettaNet.Schemas.System' （您是否遺漏了組件參考？）。  
  
### <a name="possible-cause"></a>可能的原因  
 您的其中一個結構描述 (例如 StandardDocumentHeader.xsd) 擁有 RosettaNet.Schemas.System 的 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 命名空間。  
  
### <a name="solution"></a>方案  
 將該結構描述 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 命名空間中的 System 移除，使該命名空間變成 RosettaNet.Schemas。  
  
## <a name="you-receive-an-error-when-trying-to-manually-deploy-the-bam-package"></a>嘗試手動部署 BAM 封裝時收到錯誤  
  
### <a name="symptom"></a>徵兆  
 當您嘗試手動部署 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] BAM 封裝時，收到您不能部署該封裝的錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 您的系統上已安裝了 BAM_DM_Process 和 BAM_DM_Message 這兩個 DTS 封裝，導致您無法部署 BAM 封裝。  
  
### <a name="solution"></a>方案  
  
##### <a name="to-recover-from-the-error-condition-and-deploy-the-bam-package"></a>修正此錯誤狀況並部署 BAM 封裝  
  
1.  按一下 **開始**，指向**所有程式**，指向**Microsoft SQL Server**，然後按一下**Enterprise Manager**。  
  
2.  在 Enterprise Manager 中，展開**Microsoft SQL Servers**， **SQL Server 群組**， **（本機） (Windows NT)**，和**Data Transformation Services**.  
  
3.  按一下 **本機封裝**，以滑鼠右鍵按一下**bam_dm_message 這兩個**，然後按一下**刪除**。  
  
4.  以滑鼠右鍵按一下**BAM_DM_Process**，然後按一下**刪除**。  
  
5.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
6.  在命令提示字元中，輸入下列的程式碼來部署此追蹤檔案，然後再按一下**確定**。  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server <version>\Tracking  
    bm deploy all  "%ProgramFiles%\Microsoft BizTalk <version> Accelerator for RosettaNet\BAMTracking\tracking.xml"  
    ```  
  
## <a name="you-receive-an-error-when-adding-a-new-pip"></a>新增 PIP 時收到錯誤  
  
### <a name="symptom"></a>徵兆  
 您在事件日誌中收到下列或類似的錯誤：  
  
 UNP.SCON.VALERR：驗證服務內容時發生錯誤。  
  
 詳細資料：依據訊息類型尋找文件規格失敗。 請確認已正確部署結構描述。  
  
### <a name="possible-cause"></a>可能的原因  
 Pip4A5NotifyofForecastReply 執行個體已部署的結構描述中，文件命名空間或根節點屬性不正確。  
  
### <a name="solution"></a>方案  
 請檢查 Pip4A5NotifyofForecastReply 執行個體已部署結構描述的文件命名空間與根節點屬性是否正確。  
  
## <a name="error-during-the-configuration-of-btarn-at-installation-time-caused-by-presumed-network-connectivity-issues"></a>安裝過程中設定 BTARN 組態時發生錯誤，系統推測原因可能是網路連線問題  
  
### <a name="symptom"></a>徵兆  
 在設定組態的過程中收到錯誤對話方塊，指出電腦並未正確連上網路，但事實上電腦已正確連上網路了。  
  
### <a name="possible-cause"></a>可能的原因  
 此錯誤可能是因為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態程式錯誤解譯 IP 位址而造成的。 C:\Windows\system32\drivers\etc 中的 Hosts 檔案內含有一個項目，會將 localhost 主機名稱對應成 IP 位址 127.0.0.1。 此組態程式可能把這個值和回送位址混淆了，所以才認為電腦並未正確連上網路。  
  
### <a name="solution"></a>方案  
  
##### <a name="to-avoid-this-error-and-complete-the-configuration-process"></a>避免此種錯誤並完成組態程序  
  
1. 在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 總管] 中，移到 C:\Windows\system32\drivers\etc，用「記事本」開啟 Hosts 檔案。  
  
2. 行註解 「 127.0.0.1 localhost 」 藉由將"#"放在一行的開頭。 將變更後的 Hosts 檔案存檔。  
  
3. 按一下 **重試**錯誤 對話方塊中。  
  
4. 等組態設定成功完成後，再用「記事本」開啟 Hosts 檔案，把對應 localhost 那一行開頭的註解標記刪除，然後再將 Hosts 檔案存檔。  
  
## <a name="you-receive-an-error-regarding-incorrect-signature-length"></a>收到簽章長度不正確的錯誤  
  
### <a name="symptom"></a>徵兆  
 您在事件日誌中收到下列或類似的錯誤：  
  
 執行接收管線失敗: "Microsoft.Solutions.BTARN.Pipelines.Receive" 來源: "MIME/SMIME decoder" 接收位置: "/BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async" 原因: 簽章長度不正確，值 = 1935897193。  
  
### <a name="possible-cause"></a>可能的原因  
 此錯誤訊息表示簽章的長度不正確。 除了以上的原因之外，標頭內容長度不正確或不完整，導致讀取的簽章長度位元組數不正確，也可能是造成此錯誤的原因。  
  
### <a name="solution"></a>方案  
 檢查簽章長度與標頭內容長度是否正確。  
  
## <a name="you-receive-503-service-unavailable-from-internet-explorer-on-64-bit-machine"></a>您會從 64 位元電腦上的 Internet Explorer 收到「503：服務無法使用」  
  
### <a name="symptom"></a>徵兆  
 在後[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]完成組態設定，當您嘗試存取[ http://localhost ](http://localhost/)或是[ http://localhost/BtarnApp/RnifSend.aspx ](http://localhost/BtarnApp/RnifSend.aspx)，可能會收到下列或類似的錯誤：  
  
 503：服務無法使用  
  
### <a name="possible-cause"></a>可能的原因  
 此錯誤可能是由於 IIS 網站設定 C:\windows\system32\rpcproxy\rpcproxy.dll 底下的 ISAPI 篩選常式所造成的。  
  
### <a name="solution"></a>方案  
  
##### <a name="to-remove-rpcproxy-filter-entry-in-iis"></a>移除 IIS 中的 RpcProxy 篩選常式項目  
  
1.  按一下 **開始**，指向 **系統管理工具**，然後按一下 **Internet Information Services (IIS) 管理員**。  
  
2.  依序展開**\<電腦名稱\>（本機電腦）**，以滑鼠右鍵按一下**網站**，然後按一下**屬性**。  
  
3.  選取 [ **ISAPI 篩選器**] 索引標籤。  
  
4.  選取 [ **RpcProxy 篩選常式]**，然後按一下**移除**。  
  
5.  按一下 [確定] 。  
  
6.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
7.  在命令提示字元下，輸入下列程式碼以重設 IIS。  
  
    ```  
    iisreset  
    ```  
  
> [!NOTE]
>  如果您嘗試存取 http://localhost 或 http://localhost/BtarnApp/RnifSend.aspx 再次執行上述步驟之後，您會收到 HTTP 400 訊息從 Internet Explorer，這表示，IIS 已經正常運作。  
  
## <a name="the-hubscenario-sample-will-not-be-installed-correctly-if-the-assembly-key-files-are-not-entered-for-the-projects"></a>如果沒有輸入專案的組件金鑰檔，HubScenario 範例就不會正確安裝  
  
### <a name="symptom"></a>徵兆  
 當您執行 setup.bat *\<磁碟機\>*: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\HubScenario 設定HubScenario 範例中，作業會失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 HubScenario 和 HubHelper 組件未正確部署，因為未在專案中設定組件金鑰檔。  
  
### <a name="solution"></a>方案  
 對 HubScenario 和 HubHelper 專案設定組件金鑰檔。 如需詳細資訊，請參閱 < [HubScenario 範例](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md)。  
  
## <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample-on-sql-server-2008-r22008-sp1"></a>執行 setupx64.bat，以設定 SQL Server 2008 R2/2008 SP1 中的雙向動作 PIPAutomation 協調流程範例  
  
### <a name="symptom"></a>徵兆  
 執行 setup.bat 以建置和初始化設定「雙向動作 PIPAutomation 協調流程」範例時，BTARNData 資料庫中的 PipAutomationGetAction 預存程序未建立。  
  
### <a name="possible-cause"></a>可能的原因  
 在 64 位元電腦上或在 SQL Server 2008 R2/2008 SP1 執行的 BizTalk Server 安裝上，執行 setup.bat。 這兩個執行個體都需要您執行 setupx64.bat。  
  
### <a name="solution"></a>方案  
 請執行 setupx64.bat 以建立預存程序。 如需詳細資訊，請參閱 <<c0> [ 雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)。  
  
## <a name="enable-the-btarn-application-pools-for-32-bit-on-windows-server-2008-64-bit-windows-operating-system-os"></a>啟用 Windows Server 2008 64 位元 Windows 作業系統 (OS) 上的 32 位元的 BTARN 應用程式集區  
 在 Windows Server 2008、64 位元的 Windows 作業系統 (OS)、Internet Information Services Manager 7.5/7.0 上執行 BTARN 端對端實例。  
  
 1. 啟用 32 位元的 BTARN 應用程式集區。  
  
 2. 新增的 HTTP 處理常式\*.dll 參考 IsapiModule 篩選器。  
  
## <a name="see-also"></a>另請參閱  
 [BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md)   
 [回送](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)
