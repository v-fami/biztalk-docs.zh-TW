---
title: "BizTalk Server 設定的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf1f89ced33be6f10ceaae37ccb2c899c4e01eac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-biztalk-server-settings"></a>BizTalk Server 設定的最佳做法
本主題列出當您執行操作的整備的程序，您應該遵循的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 **設定訊息批次處理以增進配接器效能**  
  
-   執行配接器藉由結合到單一批次中的多個作業的交易數目降到最低。  
  
-   限制的總位元組數的批次中除了訊息計數為基礎的批次大小。 如需限制批次大小的詳細資訊，請參閱[設定批次處理，以改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。  
  
 **調整大型訊息閾值**  
  
-   若要改善輸送量，增加的大型訊息閾值，這會降低大型緩衝處理的訊息數目在對應的磁碟。  
  
 **判斷您需要在計劃期間追蹤的資訊**  
  
-   您需要追蹤哪些資訊，您應該決定在規劃階段中。如此一來，您部署專案之後, 您可以設定追蹤選項和限制，讓您所需的資訊的追蹤資料數量。  
  
    > [!NOTE]  
    >  如需與追蹤相關的最佳作法的詳細資訊，請參閱[規劃追蹤](../technical-guides/planning-for-tracking.md)本指南中和[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/p/?LinkId=154187)(http://go.microsoft.com/fwlink/p/?LinkId=154187)。  
  
 **不要追蹤所有訊息**  
  
-   我們建議您在不追蹤所有訊息。 這是因為每次觸及訊息時，BizTalk Server 將訊息的另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於將您的系統效能最大化，並保持資料庫的整齊。  
  
 **設定追蹤傳送埠和接收埠而不是在管線**  
  
-   如果您設定管線的追蹤選項，您也會設定每個管線所使用的連接埠全域追蹤選項。 這又可能會導致更多正在追蹤資料比您想要這會拖慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。  
  
 **調整節流根據資源使用量**  
  
-   在 節流[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供完善保護系統的預設設定。 監視瞭解節流狀態，請參閱是否節流正在進行中的效能計數器。 然後量測計自行如果依據上節流的資源 （例如，資料庫大小或記憶體使用量） 下方或上方利用。 接下來，調整 節流閾值會啟動，或據以關閉。 如需詳細資訊，請參閱[調整節流閾值： 時間和原因](http://go.microsoft.com/fwlink/p/?LinkId=154188)(http://go.microsoft.com/fwlink/p/?LinkId=154188)。  
  
 **盡可能使用 PassThruTransmit 管線**  
  
-   如果沒有任何文件處理需要傳送訊息至其目的地之前，使用 PassThruTransmit 管線，而不是 XML 傳送管線。  
  
 **最小化的協調流程 」 圖形開始與結束 「 使用方式追蹤事件**  
  
-   當追蹤的協調流程圖形有明顯的好處，協調流程偵錯時，其效能和延展性的含意。 **圖形開始和結束**追蹤事件可能會造成顯著的額外負荷。 您最好在實際執行環境，其中需要高輸送量是其使用情形降至最低。  
  
    > [!NOTE]  
    >  **圖形開始和結束**所有協調流程上預設會啟用追蹤事件。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)