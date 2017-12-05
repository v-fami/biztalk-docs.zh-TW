---
title: "新增主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ba10a6-c5e7-4dec-98f1-4e6ba44c2851
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4c2e029e9599143c52577771a313d9810ca6f12
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="add-a-host-instance"></a>新增主控件執行個體

## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI) 來新增主控件執行個體。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您一次只能新增一個主控件執行個體到一個伺服器。 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。 如需使用 WMI 新增主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 新增主控件執行個體會將指定主控件的執行個體對應至 BizTalk Server 的執行個體。 如果您有必須修復的現有主控件執行個體，您可以更新主控件執行個體屬性。 您必須停止現有的主控件執行個體，才能再次新增它。 如需停止主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。  
  
> [!NOTE]
>  如果您想要建立更多 26 主控件執行個體，您必須依照知識庫文件 184802"User32.dll 或 Kernel32.dll 無法初始化，」，可在[http://go.microsoft.com/fwlink/?LinkId=26176](http://go.microsoft.com/fwlink/?LinkId=26176)。 當您套用該「知識庫」文件中的建議之後，若需要其他主控件執行個體，您可以嘗試減少 BTSNTSvc 服務的每個執行個體之可用記憶體量。 這將提供額外的必要記憶體，供建立更多執行個體之用。  
  
> [!NOTE]
>  服務帳戶將會在安裝主控件執行個體的伺服器上自動被授與「登入為服務」權限。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。  
  
 此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：  
  
-   BAM 主要匯入 (BAMPrimaryImport)  
  
-   BizTalk 管理 (BizTalkMgmtDb)  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) (全部)  
  
-   BizTalk 追蹤 (BizTalk DTADb)  
  
-   規則引擎 (BizTalkRuleEngineDb)  
  
> [!CAUTION]
>  建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。 這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。  
  
## <a name="steps"></a>步驟
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 [BizTalk 群組]，然後按一下**平台設定**。  
  
3.  以滑鼠右鍵按一下**主控件執行個體**，按一下 **新增**，然後按一下 **主控件執行個體**。  
  
4.  在**主控件執行個體屬性**對話方塊中，執行下列命令，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主機名稱**|顯示和所選取的伺服器相關聯的主控件名稱。|  
    |**Server**|顯示與所選取的主控件相關聯的伺服器。|  
    |**登入**|顯示將執行主控件執行個體的新服務帳戶之帳戶名稱。|  
    |**設定**|按一下即可顯示**登入認證**對話方塊中，您可以在此輸入的帳戶名稱和密碼將執行主控件執行個體的帳戶。|  
    |**停用主控件執行個體無法啟動**|選取此核取方塊將選取主控件的狀態由啟用變更為停用。 若您不要主控件執行個體啟動，但是要保留其設定時，停用主控件執行個體就非常有用。|  
  
 在您安裝主控件執行個體之後，必須啟動它，這樣它才能將訊息路由至 MessageBox 資料庫。 如需啟動主控件執行個體的相關資訊，請參閱[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="a-biztalk-host-instance-is-created-with-a-status-of-uninstall-failed-if-the-designated-biztalk-server-runtime-computer-is-not-available-during-host-instance-creation"></a>如果在主控件執行個體建立期間無法使用指定的 BizTalk Server 執行階段電腦，則會建立狀態為「解除安裝失敗」的 BizTalk 主控件執行個體  
  
##### <a name="problem"></a>問題  
 如果在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦的遠端電腦上安裝 BizTalk 管理主控台，則即使無法使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，仍然可能會在遠端 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上嘗試建立主控件執行個體。  
  
 如果您嘗試在無法使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上建立 BizTalk 主控件執行個體，則會出現一個對話方塊，其中包含下列錯誤訊息：  
  
 安裝主控件 instace \<*主機名稱*\>伺服器上\<*伺服器名稱*\>失敗。  
  
 其他資訊：  
  
 RPC 伺服器無法使用。 (WinMgmt)  
  
 當您按一下 [確定] 關閉此對話方塊時，會顯示一個對話方塊，其中包含下列錯誤訊息：  
  
 清除已完成中止的主機安裝\<*主機名稱*\>伺服器上\<*伺服器名稱*\>失敗。  
  
 其他資訊：  
  
 發生失敗時刪除 Windows NT 服務 BTSSvc {*\<GUID\>*}。 (WinMgmt)  
  
 當您按一下**確定**若要關閉此對話方塊中，BizTalk 主控件執行個體便會顯示在 BizTalk 管理主控台與**狀態**的**Uninstall 失敗**.  
  
##### <a name="cause"></a>原因  
 當建立主控件執行個體時，會在 BizTalk 管理資料庫中產生一個項目，然後才會將此主控件執行個體安裝到指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上。 如果在指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上安裝此主控件執行個體失敗，則 BizTalk 管理程式將會嘗試解除安裝此主控件執行個體，但是因為無法使用指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，所以解除安裝也會失敗。  
  
##### <a name="resolution"></a>解決方案  
 如果狀態為 「 BizTalk 管理主控台中建立 BizTalk 主控件執行個體**Uninstall 失敗**、 刪除主控件執行個體和指定的 BizTalk Server 電腦變成可用之後重新建立主控件執行個體。  
  
> [!NOTE]
>  如果使用 BizTalk 管理主控台中建立 BizTalk 主控件執行個體**狀態**的**Uninstall 失敗**主控件執行個體將無法正常運作即使指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦再次變為無法使用。  
  
## <a name="see-also"></a>請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [啟動主控件執行個體](../core/how-to-start-a-host-instance.md)   
 [停止主控件執行個體](../core/how-to-stop-a-host-instance.md)   
 [刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)   
 [修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)