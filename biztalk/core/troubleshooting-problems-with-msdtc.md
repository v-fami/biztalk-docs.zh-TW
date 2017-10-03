---
title: "MSDTC 問題疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f39cde52-da8f-4cc1-bdc5-e4b828891a79
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c244ec27cd3e584f7fb22a34effeaf0033c3e78a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-problems-with-msdtc"></a>MSDTC 問題疑難排解
大部分 BizTalk Server 執行階段作業都需要 Microsoft 分散式交易協調器 (MSDTC) 支援，以確保作業在交易上的一致。 如果沒有 MSDTC 交易支援，則關聯的 BizTalk Server 執行階段作業將無法繼續。 未正確設定 MSDTC 交易支援時，通常會受到影響的 BizTalk 元件包括 (但不限於) 單一登入服務、BizTalk 主控件執行個體，以及任何經由 BizTalk Server 所連接的 SQL Server 執行個體。 本節包含描述 MSDTC 相關錯誤的資訊，以及可供遵循以診斷和解決 MSDTC 問題的步驟。  
  
## <a name="errors-that-can-occur-if-msdtc-transaction-support-is-not-configured-correctly"></a>未正確設定 MSDTC 交易支援時可能發生的錯誤  
 當 BizTalk 環境中之電腦上的 MSDTC 交易支援設定不正確時，可能會發生類似下列的錯誤：  
  
-   「Microsoft 分散式交易協調器 (DTC) 的問題導致無法連線到組態資料庫。 交易管理員已停用對遠端/網路交易的支援」。  
  
-   「Microsoft 分散式交易協調器 (DTC) 的問題導致無法連線到組態資料庫。 已隱含或明確地認可或中止交易」。  
  
-   「錯誤碼：0x8004d00a - 無法在指定的異動協調器中編列異動」。  
  
-   「無法從組態存放區擷取接收位置 'MySample ReceiveLocation' 的傳輸類型資料。 主要 SSO Server 'MyServer' 失敗。 RPC 伺服器無法使用」。  
  
-   「錯誤碼：0x8004d025，協力電腦異動管理員已經停用了對遠端/網路異動的支援」。  
  
-   「錯誤碼：0xc0002a24，無法匯入 DTC 交易。 請檢查 MSDTC 是否已正確設定為支援遠端作業」。  
  
-   「0x8004d01c  
  
     [0x1705] 建立內部工作項目時發生失敗。  
  
     請確定 SQL Server 正在執行」。  
  
 若要解決 MSDTC 組態錯誤，請遵循下列步驟。  
  
## <a name="ensure-netbios-name-resolution-between-the-biztalk-server-and-remote-servers-is-successful"></a>確定 BizTalk Server 與遠端伺服器之間的 NetBIOS 名稱解析成功  
 用戶端電腦必須能夠將伺服器電腦的 NetBIOS 名稱解析為正確的 IP 位址，而且伺服器電腦也能夠將用戶端電腦的 NetBIOS 名稱解析為正確的 IP 位址，電腦之間的 MSDTC 交易才會成功。 若要確認 NetBIOS 名稱解析在兩個方向 (用戶端至伺服器以及伺服器至用戶端) 上都運作正常，請依照下列步驟：  
  
> [!NOTE]
>  NetBIOS 名稱又常稱為 **網路** 名稱。  
  
1.  判斷每一台電腦的 NetBIOS 名稱：  
  
    1.  在 **[我的電腦]** 上按一下滑鼠右鍵顯示 **[系統內容]** 對話方塊，再按一下 **[電腦名稱]** 索引標籤檢視指派給電腦的 **[完整電腦名稱]** 。  
  
    2.  NetBIOS 名稱是指派為 **[完整電腦名稱]** 的第一個部分；例如，如果 **[完整電腦名稱]** 列出的是 myserver.company.domain.com，則電腦的 NetBIOS 名稱就是 **myserver**。  
  
2.  判斷 IP 位址或與每台電腦關聯的位址：  
  
    1.  在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ipconfig /all  
        ```  
  
    2.  命令提示字元視窗會列出 IP 位址或與每台電腦關聯的位址。  
  
    3.  在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ipconfig /all  
        ```  
  
    4.  命令提示字元視窗會列出 IP 位址或與伺服器電腦關聯的位址。  
  
3.  確認每一台電腦的 NetBIOS 名稱已解析為其中一個與電腦關聯的 IP 位址：  
  
    1.  在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ping <NetBIOS name of server computer>  
        ```  
  
         ping 命令的結果應該會傳回與伺服器電腦關聯的 IP 位址。  
  
    2.  在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ping <NetBIOS name of client computer>  
        ```  
  
         ping 命令的結果應該會傳回與用戶端電腦關聯的 IP 位址。  
  
4.  確認與每一台電腦的 NetBIOS 名稱相關聯的反向名稱查詢都會解析為正確的電腦名稱。  
  
    1.  在用戶端電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ping -a <IP Address associated with client computer NetBIOS name>  
        ```  
  
         ping 命令的結果會傳回 NetBIOS 名稱，或與用於步驟 3a 中的 NetBIOS 名稱相對應的完整格式網域名稱。 如果傳回的名稱與步驟 3a 中使用的 NetBIOS 名稱不符合或與該名稱不對應，則 IP 位址的反向查詢會失敗，而這可能導致 MSDTC 交易失敗。  
  
    2.  在伺服器電腦上啟動命令提示字元，輸入下列命令後按 ENTER：  
  
        ```  
        ping -a <IP Address associated with server computer NetBIOS name>  
        ```  
  
         ping 命令的結果會傳回 NetBIOS 名稱，或與用於步驟 3b 中的 NetBIOS 名稱相對應的完整格式網域名稱。 如果傳回的名稱與步驟 3b 中使用的 NetBIOS 名稱不符合或與該名稱不對應，則 IP 位址的反向查詢會失敗，而這可能導致 MSDTC 交易失敗。  
  
 如果 NetBIOS 名稱解析在兩個方向上都不成功，或者如果反向名稱查詢失敗，請在 DNS 伺服器、NetBIOS 名稱伺服器、HOSTS 檔案或 LMHOSTS 檔案中輸入適當的項目以修正問題。  
  
> [!NOTE]
>  電腦使用的名稱解析方法因電腦的 NetBIOS 節點類型而有所不同。 如需 NetBIOS 節點類型的詳細資訊，請參閱 [NetBIOS 名稱解析](http://go.microsoft.com/fwlink/?LinkId=201638)。  
  
## <a name="ensure-that-a-firewall-between-the-biztalk-server-and-remote-servers-is-not-blocking-ports-required-for-rpc-dynamic-port-allocation"></a>確定 BizTalk Server 和遠端伺服器之間的防火牆沒有封鎖 RPC 動態連接埠配置所需的連接埠  
 網路上的 MSDTC 功能依存於網路上的 RPC 功能。 您必須開啟特定連接埠以配合 RPC 動態連接埠配置，才能透過防火牆使用 RPC 功能。 如果防火牆位於 BizTalk Server 和遠端伺服器之間，請依照 [如何設定 RPC 動態連接埠配置以使用防火牆](http://go.microsoft.com/fwlink/?LinkId=66831) 中的步驟來配合 RPC 動態連接埠配置。  
  
## <a name="set-the-appropriate-msdtc-security-configuration-options"></a>設定適當的 MSDTC 安全性組態選項  
 Windows 提供安全性增強功能來控管如何透過網路存取 MSDTC。 您可以藉由修改 MSDTC 安全性設定，控制遠端電腦在網路上與 MSDTC 的通訊方式。 下表列出進行 MSDTC 安全性設定時，針對可用選項的建議值：  
  
|組態選項|預設值|建議值|  
|--------------------------|-------------------|-----------------------|  
|網路 DTC 存取|Disabled|已啟用|  
|**用戶端和管理**|||  
|允許遠端用戶端|Disabled|Disabled|  
|允許遠端系統管理|Disabled|已停用|  
|**交易管理員通訊**|||  
|允許輸入|Disabled|已啟用|  
|允許輸出|Disabled|已啟用|  
|需要相互驗證|已啟用|如果所有的遠端電腦都在執行 Windows Server 2003 SP1、Windows XP SP2 或更新版本，並且設定為「需要相互驗證」，則為已啟用。|  
|要求對連入呼叫者驗證|Disabled|如果在叢集上執行 MSDTC，則啟用此項。|  
|不需要驗證|Disabled|如果遠端電腦是 Windows Server 2003 SP1 之前的版本或 Windows XP SP2 之前的版本，則啟用此項。|  
|啟用 TIP|Disabled|如果執行 BAM 入口網站，則啟用此項。|  
|啟用 XA 交易|Disabled|如果是與使用 MQSeries 配接器的 XA 交易系統進行通訊 (例如與 IBM WebSphere MQ 通訊時)，則啟用此項。|  
  
 在套用這些變更後，MSDTC 服務就會重新啟動。  
  
 若要存取 MSDTC 安全性組態選項，請依照下列步驟執行：  
  
1.  依序按一下 [開始] 與 [執行] ，然後輸入 **dcomcnfg** ，以啟動 [元件服務] 管理主控台。  
  
2.  按一下以展開 **[元件服務]** ，然後再按一下以展開 **[電腦]**。  
  
3.  依按一下 [我的電腦] 與 [分散式交易協調器] 加以展開，再於 [本機 DTC] 上按一下滑鼠右鍵，然後按一下 [屬性] 。  
  
4.  按一下 [本機 DTC 內容]  對話方塊中的 [安全性]  索引標籤。  
  
> [!NOTE]
>  依照所做的變更，您可能需要重新啟動電腦以使變更生效。 如果在套用變更及重新啟動 MSDTC 服務之後仍遭遇問題，請將其上進行了變更的電腦重新啟動，以確保這些變更生效。  
  
 如果啟用 **[要求相互驗證]** 或 **[要求對連入呼叫者驗證]** 組態選項，則必須對用戶端電腦帳戶授與 **[從網路存取這台電腦]** 使用者權限。 如果並未對用戶端電腦的電腦帳戶授與 **[從網路存取這台電腦]** 使用者權限，或者該帳戶是包含在 **[拒絕從網路存取這台電腦]** 使用者權限中，則用戶端和伺服器電腦之間的 DTC 通訊會失敗。  
  
 預設設定是對 Everyone 群組授與 **[從網路存取這台電腦]** 使用者權限。 因此，這個使用者權限不需變更，除非預設設定已經修改。 如果已啟用 **[不需要驗證]** 組態選項，則 **[從網路存取這台電腦]** 使用者權限就不會套用至用戶端電腦帳戶。  
  
 若要變更被授與 [從網路存取這台電腦] 使用者權限的使用者或群組，請依照下列步驟進行：  
  
1.  依序按一下 **[開始]**、 **[執行]**，然後輸入 **Gpedit.msc**，再按一下 **[確定]**。  
  
2.  展開 [本機電腦原則] 清單中的下列項目：  
  
    -   電腦組態  
  
    -   Windows 設定  
  
    -   安全性設定  
  
    -   本機原則  
  
3.  按一下 **[使用者權限指派]**。  
  
4.  按兩下 **[從網路存取這台電腦]**，然後按一下 **[新增使用者或群組]**。  
  
5.  按一下 **[物件類型]**，選取 **[電腦]** ，然後按一下 **[確定]**。  
  
6.  在 **[輸入物件名稱來選取]** 區域中，輸入電腦名稱或群組名稱。  
  
7.  按一下 **[檢查名稱]** 來確認項目。  
  
8.  按兩次 **[確定]** 。  
  
 若要變更包含在 **[拒絕從網路存取這台電腦]** 使用者權限中的使用者或群組，請依照下列步驟進行：  
  
1.  展開 [本機電腦原則] 清單中的下列項目：  
  
    -   電腦組態  
  
    -   Windows 設定  
  
    -   安全性設定  
  
    -   本機原則  
  
2.  按一下 **[使用者權限指派]**。  
  
3.  按兩下 **[拒絕從網路存取這台電腦]**，然後按一下以選取要從這個使用者權限移除的電腦名稱或群組。  
  
4.  按一下 **[移除]** ，然後按一下 **[確定]**。  
  
## <a name="set-the-appropriate-values-for-the-enableauthepresolution-and-restrictremoteclients-options"></a>設定 EnableAuthEpResolution 和 RestrictRemoteClients 選項的適當值  
 Windows 要求在對 RPC 介面進行呼叫時需要驗證，大大增加了安全性。 透過 **EnableAuthEpResolution** 和 **RestrictRemoteClients** 登錄機碼，可設定這項功能。 為確保遠端電腦能夠存取 RPC 介面，請遵循下列步驟：  
  
> [!WARNING]
>  不正確使用登錄編輯程式可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 如需有關如何備份、還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文件＜Microsoft Windows 登錄說明＞，位在 [Microsoft Windows 登錄說明](http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
1.  按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
     瀏覽至 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT**  
  
2.  在 **RPC** 機碼下，以指示的值建立下列 DWORD 項目。 如果 **RPC** 機碼不存在，則必須建立它。  
  
    |DWORD 項目|預設值|建議值|  
    |-----------------|-------------------|-----------------------|  
    |EnableAuthEpResolution|0 (停用)|1|  
    |RestrictRemoteClients|1 (啟用)|0|  
  
3.  關閉 [登錄編輯程式]。  
  
4.  重新啟動 MSDTC 服務。  
  
> [!NOTE]
>  依照所做的變更，您可能需要重新啟動電腦以使變更生效。 如果在套用變更及重新啟動 MSDTC 服務之後仍遭遇問題，請將其上進行了變更的電腦重新啟動，以確保這些變更生效。  
  
## <a name="if-windows-firewall-is-running-add-an-exception-for-the-msdtc-service"></a>如果 Windows 防火牆正在執行，請為 MSDTC 服務新增例外。  
 Windows 防火牆服務可以封鎖電腦之間的 MSDTC 通訊。 為了確保電腦之間的 MSDTC 通訊不會封鎖，請將 msdtc.exe 新增至 Windows 防火牆的例外清單 (如果 Windows 防火牆服務正在執行)。  
  
1.  依序按一下 **[開始]**和 **[執行]**，輸入 **firewall.cpl**，再按一下 **[確定]** 顯示 **[Windows 防火牆]** 對話方塊。  
  
2.  按一下 [允許程式通過 Windows 防火牆]  ，以顯示 [Windows 防火牆設定]  對話方塊。  
  
3.  按一下 [Windows 防火牆]  對話方塊中的 [例外]  索引標籤。  
  
4.  按一下 **[新增程式]** ，顯示 **[新增程式]** 對話方塊。  
  
5.  按一下 **[瀏覽]** ，並瀏覽到 *%system32%*\msdtc.exe。  
  
    > [!NOTE]
    >  啟動命令提示字元，輸入 **echo %system32%** ，然後按 **ENTER** 以判斷此電腦上的 \System32 目錄位置。  
  
6.  按一下以選取 **msdtc.exe** ，然後按一下 **[開啟]**。  
  
7.  按一下 **[變更領域]** ，以指定應該允許 MSDTC 通訊的電腦集，然後按一下 **[確定]**。  
  
8.  在 [新增程式]  對話方塊中按一下 [確定]  ，然後再按一下 [Windows 防火牆]  對話方塊中的 [確定]  。  
  
9. 關閉 [Windows 防火牆]  對話方塊。  
  
10. 停止分散式交易協調器服務，然後再重新啟動。  
  
    -   啟動命令提示字元，輸入 **net stop msdtc** ，然後按 **ENTER**。  
  
    -   在分散式交易協調器服務停止之後，輸入 **net start msdtc** ，然後按 **ENTER**。  
  
## <a name="use-dtctester-or-dtcping-to-verify-msdtc-functionality-over-the-network"></a>使用 DTCTester 或 DTCPing 以驗證網路上的 MSDTC 功能  
 如果 SQL Server 安裝在兩台電腦中的任一台，使用 DTCTester 公用程式來驗證這兩台電腦之間的交易支援。 DTCTester 公用程式使用 ODBC 來驗證對 SQL Server 資料庫的交易支援。 如需 DTCTester 的詳細資訊，請參閱 [如何使用 DTCTester 工具](http://go.microsoft.com/fwlink/?LinkId=66232)。  
  
 如果 SQL Server 安裝在兩台電腦中的任一台，使用 DTCPing 公用程式來驗證這兩台電腦之間的交易支援。 當用戶端及伺服器電腦都沒有 SQL Server 時，這兩台電腦都必須執行 DTCPing 工具，而這也是 DTCTester 公用程式的良好替代工具。 如需有關 DTCPing 的詳細資訊，請參閱[如何疑難排解 MS DTC 防火牆問題](http://go.microsoft.com/fwlink/?LinkId=61915)。  
  
> [!IMPORTANT]
>  如果 DTCPing 傳回「警告：兩部測試機器的 CID 值相同」警告，請遵循 **「確定 MSDTC 獲派唯一的 CID 值」** 一節中的步驟，讓測試機器之間能正常執行 MSDTC 功能。  
  
## <a name="ensure-that-msdtc-is-assigned-a-unique-cid-value"></a>「確定 MSDTC 獲派唯一的 CID 值」  
 Windows 作業系統的 MSDTC 功能需要有唯一的 CID 值，才能確保電腦之間的 MSDTC 功能運作正常。 Windows 安裝的磁碟複製影像必須有唯一的 CID 值，否則 MSDTC 功能可能無法正常執行。 使用虛擬硬碟將作業系統部署到虛擬電腦時，可能會發生這種情況。  
  
 若要判斷執行 Windows 作業系統之電腦的 MSDTC CID 值是否為唯一的，請檢查兩部電腦上 HKEY_CLASSES_ROOT\CID 登錄機碼底下項目的值。 如果每部電腦上的這些值不是唯一的，請遵循 **「如果其他疑難排解步驟均無法成功解決問題，請考慮重新安裝分散式交易協調器服務」** 一節的步驟，在其中一部電腦上重新安裝 MSDTC，這樣就會針對該電腦產生唯一的 MSDTC CID 值，因而讓 MSDTC 作業能夠正常執行。  
  
## <a name="error-new-transaction-cannot-enlist-in-the-specified-transaction-coordinator-0x8004d00a-occurs-if-the-msdtc-connection-between-a-client-computer-and-a-server-computer-is-closed"></a>如果用戶端電腦和伺服器電腦之間的連線已關閉，即會發生「無法在指定的異動協調器中編列異動 (0x8004d00a)」錯誤。  
 在某些情況下，可能會關閉現有 MSDTC 連線用戶端與伺服器之間，並使用此連接的後續嘗試會導致下列錯誤訊息：  
新的交易無法登錄於指定的交易協調器 (0x8004d00a)  
如需詳細資訊，請參閱[當您嘗試在 MS DTC 中啟動交易時的錯誤訊息: 「 新的交易無法登錄於指定的交易協調器 」](http://support.microsoft.com/kb/922430)。  
  
## <a name="consider-reinstalling-the-distributed-transaction-coordinator-service-if-other-troubleshooting-steps-are-not-successful"></a>「如果其他疑難排解步驟均無法成功解決問題，請考慮重新安裝分散式交易協調器服務」  
 若其他嘗試疑難排解 MSDTC 問題的措施也不成功，請考慮解除安裝再重新安裝 MSDTC。 請遵循下列步驟來解除安裝再重新安裝 MSDTC：  
  
1.  以系統管理員身分開啟命令提示字元。  
  
2.  在命令提示字元中輸入如下，以解除安裝分散式交易協調器服務：  
    `msdtc -uninstall`  
  
3.  在命令提示字元中輸入如下，以安裝分散式交易協調器服務：  
    `msdtc –install`  
  
> [!IMPORTANT]
>  重新安裝 MSDTC 可能會變更分散式交易協調器服務的預設行為。 重新安裝 MSDTC 之後，請遵循下列步驟，以確保分散式交易協調器服務能夠正常運作：  
>   
>  -   重新安裝 MSDTC 可能會將 MSDTC 安全性組態選項重設為預設值。 請確認 MSDTC 安全性組態選項值的設定在重新安裝 MSDTC 之後仍然正確。  
> -   重新安裝 MSDTC 可能會變更分散式交易協調器服務的 **啟動類型** 值。 確認重新安裝 MSDTC 之後，分散式交易協調器服務的 **啟動類型** 值設定為 **自動** 。  
> -   重新安裝 MSDTC 之後，電腦可能需要重新開機。 為確保分散式交易協調器服務能夠正常運作，重新安裝 MSDTC 之後，請將電腦重新開機。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來進行疑難排解的使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [疑難排解 Windows Server 叢集](../core/troubleshooting-a-windows-server-cluster.md)