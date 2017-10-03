---
title: "工具和公用程式進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b0946a-56de-47cd-95d9-365722cdbaed
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086c7144d39b459a342e3c4f6c5c87f669fffedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tools-and-utilities-for-troubleshooting"></a>工具和公用程式進行疑難排解
本主題描述數個工具和公用程式，可用於診斷 microsoft 問題的根本原因[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]元件或相依性。  
  
|疑難排解|工具|使用|  
|---------------------|----------|---------|  
|**SQL Server 疑難排解**|SQL 活動監視器|SQL Server 2008 活動監視器提供 SQL Server 處理序以及這些處理序如何影響目前的 SQL Server 執行個體的相關資訊。 如需有關 SQL Server 2008 活動監視器的詳細資訊，請參閱[活動監視器](http://go.microsoft.com/fwlink/?LinkId=146355)(http://go.microsoft.com/fwlink/?LinkId=146355) 中的 SQL Server 文件。 如需如何從 SQL Server Management Studio 中開啟活動監視器資訊，請參閱[如何： 開啟活動監視器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) 中的 SQL Server 文件。|  
||SQL Server 2008 資料收集|SQL Server 2008 提供您可以使用來取得及儲存從數個來源蒐集資料的資料收集器。 資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 2008 的電腦上的資料收集的頻率。 如需有關實作 SQL Server 2008 資料收集的詳細資訊，請參閱[資料收集](http://go.microsoft.com/fwlink/?LinkId=146356)(http://go.microsoft.com/fwlink/?LinkId=146356) 中的 SQL Server 文件。|  
||**效能相關之疑難排解**|重新記錄公用程式會用來擷取效能計數器的效能監視所建立的記錄檔，並將資料轉換成其他格式，例如 tab 鍵分隔文字檔案 (TSV 文字)、 逗號分隔的文字檔案 (CSV 文字)、 二進位檔案和 SQL 資料庫。 這項資料分析，而且查詢使用其他工具，例如記錄檔剖析器，來產生統計資料的關鍵效能指標 (Kpi)。 Windows Server 2003 和後續版本中提供重新記錄公用程式。|  
|Windows 效能分析工具||Windows 效能工具分析的各種不同的效能問題，包括應用程式啟動時間，開機問題延遲程序呼叫的設計和插斷活動 （Dpc 及 Isr） 系統的回應性問題，應用程式資源使用方式和插斷的衝擊。 如需詳細資訊，請參閱[Windows 效能分析開發人員中心](http://go.microsoft.com/fwlink/?LinkId=139763)(http://go.microsoft.com/fwlink/?LinkId=139763)。|  
|Pathping||Pathping 提供的目標主機的方式，就可能發生資料遺失，在一或多個路由器躍點的相關資訊。 若要這樣做，pathping 會將網際網路控制訊息通訊協定 (ICMP) 封包傳送至路徑中的每個路由器。 自 Windows 2000 Server，Pathping.exe 是適用於所有 Windows 版本。|  
|IOMeter||IOMeter 是開放原始碼工具，可用來測量磁碟 I/O 效能。 如需詳細資訊，請參閱[IOMeter](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412)。 **重要事項：**使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。|  
|**一般疑難排解**|事件檢視器<br />網路監視器<br />SQL Server Profiler<br />SQL Server 查詢編輯器<br />-DTCTester<br />-DTCPing<br />效能主控台<br />-RegMon<br />-FileMon<br />-Debug Diagnostics Tool IIS Diagnostics toolkit|請參閱[工具和公用程式用於疑難排解](http://go.microsoft.com/fwlink/?LinkId=154416)(http://go.microsoft.com/fwlink/?LinkId=154416)。|  
  
## <a name="see-also"></a>另請參閱  
 [測試的工具](../technical-guides/tools-for-testing.md)   
 [檢查清單： 設定 BizTalk Server](~/technical-guides/checklist-configuring-biztalk-server.md)