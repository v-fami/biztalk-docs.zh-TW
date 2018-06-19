---
title: 後續安裝步驟，BizTalk Server 2013 和 2013 R2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3b47843-9da5-4144-8b84-135494b8ab43
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b86d8c4c1e1a22dad349c2cc8c2be5ca4b206b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299902"
---
# <a name="post-installation-steps-for-biztalk-server-2013-and-2013-r2"></a>BizTalk Server 2013 和 2013 R2 的後續安裝步驟
  
##  <a name="BKMK_NamedPipes"></a> 啟用 TCP/IP 和具名管道  
  
1.  開啟 **SQL Server 組態管理員**。  
  
2.  展開 [SQL Server 網路組態]，然後選取 [MSSQLSERVER 的通訊協定]。  
  
4.  確認同時啟用 [TCP/IP] 和 [具名管道]。 如果啟用，請繼續下一個步驟。  
  
     如果未啟用：  
  
    -   以滑鼠右鍵按一下通訊協定，然後按一下 [啟用]。  
  
    -   必要時，重複執行以啟用其他通訊協定。  
  
    -   在左窗格中，按一下 [SQL Server 服務]。  
  
    -   在右窗格中，以滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後按一下 [停止]。  
  
    -   停止服務時，以滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後按一下 [啟動]。  
  
    > [!IMPORTANT]
    >  如果您要使用 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]，可能會停止 **NS$BAMAlerts** 服務。 重新啟動服務。  
  
5.  關閉 [組態管理員]。  
  
##  <a name="BKMK_DTC"></a> 在本機主機伺服器上啟用 DTC  
  
1.  開啟 [元件服務]：  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**︰選取 [Windows] 按鈕，然後輸入**元件服務**。 在 [結果] 視窗中，選取 [元件服務]。  
  
     **Windows 8.1**︰選取 [Windows] 按鈕，然後輸入**系統管理工具**。 在 [搜尋] 視窗中，選取 [設定]。 在 [結果] 視窗中，按一下 [系統管理工具]。 按兩下 [元件服務]。  
  
     **Windows 7 SP1**︰選取 [啟動]。 在 [搜尋] 文字方塊中，輸入**元件服務**，然後按一下以開啟該項目。  
  
2.  在主控台樹狀目錄中，依序展開 [元件服務]、[電腦]、[我的電腦]和 [分散式交易協調器]，然後按一下 [本機 DTC]。  
  
3.  以滑鼠右鍵按一下 [本機 DTC]，然後選取 [內容] 以開啟 [本機 DTC 內容]。  
  
4.  選取 [安全性] 索引標籤。  
  
5.  確認已核取下列選項：  
  
    -   **網路 DTC 存取**  
  
    -   **允許輸入**  
  
    -   **允許輸出**  
  
    -   **不需要驗證**  
  
     如需可能需要的其他設定，請參閱 [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。  
  
6.  選取 [確定]，關閉 [本機 DTC 內容] 對話方塊。 系統提示時，請重新啟動 MSDTC 服務。  
  
7.  關閉 [元件服務]。  
  
##  <a name="BKMK_Firewall"></a> 設定 Windows 防火牆啟用 DTC  
  
1.  開啟 [Windows 防火牆]：  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：按一下 [Windows] 按鈕，然後輸入 **Windows 防火牆**。 在 [結果] 視窗中，按一下 [Windows 防火牆]。  
  
     **Windows 8.1**：按一下 [Windows] 按鈕，然後輸入 **Windows 防火牆**。 在 [搜尋] 視窗中，按一下 [設定]。 在 [結果] 視窗中，按一下 [Windows 防火牆]。  
  
     **Windows 7 SP1**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入 **Windows 防火牆**，然後按一下以開啟該項目。  
  
2.  按一下 [進階設定]，然後按一下 [輸入規則]。  
  
3.  在 [輸入規則] 窗格中，以滑鼠右鍵按一下 [分散式交易協調器] \* (適合的話)，然後按一下 [啟用規則]。  
  
4.  按一下 [輸出規則]。  
  
5.  在 [輸出規則] 窗格中，以滑鼠右鍵按一下 [分散式交易協調器] \* (適合的話)，然後按一下 [啟用規則]。  
  
6.  在 [控制台] 上，將檢視變更為依圖示列出，然後按兩下 [系統管理工具]。  
  
7.  按兩下 [服務]。  
  
8.  以滑鼠右鍵按一下 [COM + 系統應用程式]，並按一下 [重新啟動]，然後等待服務重新啟動。  
  
9. 以滑鼠右鍵按一下**分散式交易協調器**服務，再重新啟動。  
  
10. 以滑鼠右鍵按一下 **SQL Server (MSSQLSERVER)** 服務，再重新啟動。  
  
11. 關閉 [服務 (本機)]，然後關閉 [系統管理工具]。  
  
##  <a name="BKMK_SQLAgent"></a> 設定 SQL Agent 作業  
  
|作業|描述|設定原因|  
|---------|-----------------|-------------------|  
|**備份 BizTalk Server**|這個 SQL Agent 作業會備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫和記錄檔。 設定作業時，您可以決定頻率和檔案位置等參數。<br /><br /> 下列連結會說明 SQL Agent 作業和其參數︰<br /><br /> [備份和還原 BizTalk Server 資料庫](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)<br /><br /> [如何設定備份 BizTalk Server 作業](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)|這個 SQL Agent 作業也會截斷交易記錄檔，有利改善效能。<br /><br /> **備份 BizTalk Server** 作業不會移除或刪除備份檔案，包括較舊的檔案。 若要刪除備份檔案，請參閱 [Microsoft BizTalk Server 資料庫伺服器與時俱增的備份檔案中失敗的「備份 BizTalk Server」作業](http://support.microsoft.com/kb/982546)。|  
|**DTA 清除與封存**|這個 SQL Agent 作業會截斷和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫 (BizTalkDTADb)。 設定作業時，您可以決定已完成執行個體的保留天數以及所有資料的保留天數等參數。<br /><br /> 下列連結會說明 SQL Agent 作業和其參數︰<br /><br /> [封存和清除 BizTalk 追蹤資料庫](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)<br /><br /> [如何設定 DTA 清除與封存作業](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)|此 SQL Agent 工作維護追蹤主機以及清除追蹤事件，而直接影響效能。<br /><br /> 效能主題包括：<br /><br /> [如何維護和疑難排解 BizTalk Server 資料庫](http://support.microsoft.com/kb/952555)<br /><br /> [調整追蹤資料庫大小的指導方針](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)|  
  
 **其他**  
  
-   安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，會自動建立數個 SQL Agent 作業 (如下列連結所述)：  
  
     [BizTalk Server 中的 SQL Server Agent 作業描述](http://support.microsoft.com/kb/919776)  
  
     [資料庫結構和作業](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)  
  
##  <a name="BKMK_InstallCU"></a> 安裝累積更新  
 安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後，請安裝 Windows Updates 中列出的任何 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 累積更新。 [知識庫文章 2555976](http://support.microsoft.com/kb/2555976) 列出可用的 Service Pack 和累積更新。  
  
## <a name="next"></a>下一個  
[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)
  
## <a name="see-also"></a>另請參閱  
 [附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md) 
 
[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)  

[附錄 C：可轉散發封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md)  

[附錄 D︰建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[將 BizTalk Server 解除安裝並取消設定以將其移除](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
