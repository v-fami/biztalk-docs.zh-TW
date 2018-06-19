---
title: 監視的健全狀況和效能，使用內建的工具 |Microsoft 文件
description: 可用性、 健全狀況和效能監視在 BizTalk Server 和監視 SQL Agent 工作
ms.custom: ''
ms.date: 01/14/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96e244dc-b826-4a9f-a4e1-6dabc41eb144
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6652c962d8ef522128dfb4c9febeca55ce42669
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22265358"
---
# <a name="monitoring-biztalk-server"></a>監控 BizTalk Server
定期監控 BizTalk Server 應用程式和基礎結構並解決所發現的任何問題，有助於維持您的 BizTalk Server 應用程式讓使用者存取。 監控的目標是要讓例外情形未獲得偵測 (亦即未解決) 的時間減至最少。 此外，您也可以使用監控來偵測可能造成例外情形的狀況。  
  
 當您監控 BizTalk Server 時，您應該尋找任何非預期或異常的行為。 監控可以是手動或自動程序。 您可以監視使用 BizTalk Server 基礎結構使用 BizTalk Server 管理主控台的健全狀況。 您可以使用 BizTalk Server 管理主控台來監視 BizTalk Server 應用程式的健全狀況和執行根本原因分析，以識別任何問題的根本原因。 。 當監控 BizTalk Server 時，請牢記下列幾個要點：  
  
-   您的基礎結構可能狀況良好，但應用程式可能不是 (例如，應用程式收到無效的訊息，而且無法處理這些訊息)。  
  
-   您的基礎結構可能狀況不好，但應用程式可能正常運作 (例如，如果某部伺服器停機，但是有指派足夠的伺服器給主控件來接管負載)。  
  
-   基礎結構問題可能會以應用程式問題的形式出現 (例如，由於伺服器停機，造成訊息的處理速度不夠快)。  
  
 BizTalk Server 和應用程式的監控分成三個主要類別：  
  
-   可用性監控  
  
-   健康情況監控  
  
-   效能監控  
  
## <a name="availability-monitoring"></a>可用性監控  
 可用性監控會解答以下問題：「無法使用某項系統或應用程式資源是否會讓 BizTalk Server 應用程式無法以最佳方式執行？」 這些問題大多是系統層級所特有，例如服務和連接的可用性。 例如，如果因為企業單一登入服務停止而造成配接器失敗，這就是可用性問題。 如果指派給主控件的其中一部伺服器失敗了，而應用程式在處理訊息上發生落後，這也是可用性問題。 同樣地，如果應用程式已停止且無法處理訊息，這也是可用性問題。 下表列出可用性監控工具。  
  
|工具|工作|  
|----------|----------|  
|BizTalk Server 管理主控台|您應該在 BizTalk Server 管理主控台中查看 [群組中樞] 頁面，以瞭解應用程式或其元件 (連接埠/協調流程) 是否停止。|  
|事件檢視器|尋找配接器連接問題、停止的服務等等。|  
  
## <a name="health-monitoring"></a>健全狀況監視  
 健康情況監控可解答以下問題：「有任何應用程式或資源處於不良健康情況嗎？」 例如，目前有任何應用程式或其構成成品遇到例外狀況嗎？ 或者，是否因為訊息內容中的無效資料造成訊息擱置？ 下表列出健康情況監控工具。  
  
|工具|工作|  
|----------|----------|  
|BizTalk 健全狀況監視工具 (BHM)|MMC 嵌入式管理單元的使用者來監視 BizTalk Server 環境的健全狀況偵測重大和非重大問題，並執行維護工作。  [下載 BizTalk 健全狀況監視器](https://www.microsoft.com/download/details.aspx?id=43716)。|  
|BizTalk Server 管理主控台|您將會在 BizTalk Server 管理主控台中使用 [群組中樞] 頁面和 [查詢] 頁面，以識別應用程式健康情況問題，並分析其原因。|  
|事件檢視器|偵測訊息和協調流程的處理期間所發生的問題。|  
  
## <a name="performance-monitoring"></a>效能監控  
 效能監控會解答以下問題：「系統執行工作的效率如何？」 這種監控主要著重於實體資源 (如資料庫和磁碟) 的負載。 例如，如果 CPU 使用率持續維持在百分之 90 和 100，而且形成了訊息的積存，這就是電腦層級的效能問題。 下表列出效能監控工具。  
  
|工具|工作|  
|----------|----------|  
|SQL Query Analyzer|監控資料庫大小及內容，以診斷系統問題。|  
|BizTalk Server 管理主控台|[群組中樞] 頁面會顯示 BizTalk Server 應用程式中的重要效能度量，例如目前使用中、已凍結、準備要執行、已排程、已擱置等情況的服務執行個體數目。|  
|商務活動監控 (BAM)|您可以在商務程序中指定特定的階段，而您想要針對這些階段來追蹤與商務應用程式有關的關鍵效能指標。|  
  
## <a name="biztalk-server-monitoring"></a>BizTalk Server 監控  
 您可以執行 **監控 BizTalk Server** SQL Agent 工作來識別管理、 訊息方塊或 DTA 資料庫中的任何已知的問題。 當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。  
  
 [監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：  
  
> [!NOTE]
>  [監控 BizTalk Server] 工作只會掃描問題。 並不會修正找到的問題。  
  
-   不具任何參考的訊息  
  
-   不具參考計數的訊息  
  
-   參考計數小於 0 的訊息  
  
-   不具多工緩衝處理列的訊息參考  
  
-   不具執行個體的訊息參考  
  
-   不具執行個體的執行個體狀態  
  
-   不具對應執行個體的執行個體訂閱  
  
-   被遺棄的 DTA 服務執行個體  
  
-   被遺棄的 DTA 服務執行個體例外狀況  
  
-   啟用全域追蹤選項時，TDDS 沒有在任何主控件執行個體上執行。  
  
 已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。 因為工作會進行密集計算，所以建議您排程它在關閉/低流量期間進行。  
  
 工作只要發生任何問題就會失敗；錯誤字串會包含找到的問題數。 否則表示已順利執行。 您可以在工作記錄中查看詳細資料。 如果您使用系統管理員權限執行工作，則也會將錯誤字串記錄至 [事件檢視器] \(和工作記錄)。  
  
## <a name="troubleshooting"></a>疑難排解  
 一旦您察覺 BizTalk Server 應用程式 (而不是基礎結構) 有健康情況問題時，您可以在 BizTalk Server 管理主控台中使用 [群組中樞] 頁面和 [查詢] 頁面來分析問題。 BizTalk Server 管理主控台會提供整合式組態、部署和疑難排解體驗，而且當您指出組態和部署相關的問題之後，可以在管理主控台中加以修正。 一般來說，大多數的應用程式問題都是因為未得到預期的訊息 (這可以呈現為擱置的服務執行個體或重試連接埠，或是尚未重新啟動的已凍結執行個體等等)。  
  
 您可以使用 [群組中樞] 頁面和查詢頁面將您的服務執行個體 (不論其狀態為︰ 執行暫止、 已凍結，等) 由應用程式錯誤類型，服務類型、 主機等，以找出不同的錯誤、 調查它們一一加以修正。 您也可以從 BizTalk Server 管理主控台監控追蹤資料，以調查訊息流程的記錄或是協調流程或規則集的執行記錄。 這個追蹤資料包含有關 BizTalk Server 應用程式的歷程記錄資料。  
  
 如果您已啟用追蹤，在 BizTalk 管理主控台中，您可以使用追蹤來找出訊息流程和服務執行個體使用的查詢。 當您想要尋找訊息，而且只知道訊息類型 (結構描述)、屬性和它的值 (如客戶名稱) 等資料時，這樣的處理方式會很有用處。  
  
 下列主題將討論使用 BizTalk Server 管理主控台、[群組中樞] 頁面和 [查詢] 頁面進行監控和疑難排解的相關內容。 本章節也討論追蹤，您可以使用它來協助疑難排解和根本原因分析。  
  
## <a name="more-good-stuff"></a>其他不錯的工具  
  
-   [使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)  
  
-   [檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)  
  
-   [追蹤 BizTalk Server 應用程式中成品之間的依存性](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md)

- [效能計數器](performance-counters.md)