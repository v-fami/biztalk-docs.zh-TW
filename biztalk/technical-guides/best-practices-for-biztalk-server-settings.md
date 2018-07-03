---
title: 如需 BizTalk Server 設定的最佳做法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 461e2e1a4256d79112e4eec94047c25df34a4511
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001114"
---
# <a name="best-practices-for-biztalk-server-settings"></a>如需 BizTalk Server 設定的最佳作法
本主題列出當您執行作業整備的程序，您應該遵循的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 **設定訊息批次處理以增進配接器效能**  
  
- 由配接器藉由結合成單一批次的多個作業執行的交易數目降至最低。  
  
- 限制的總位元組數的批次中除了訊息計數為基礎的批次大小。 如需有關限制的批次大小的詳細資訊，請參閱 <<c0> [ 設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。  
  
  **調整大型訊息閾值**  
  
- 若要改善輸送量，增加 大型訊息閾值，這麼做可降低大型會進行緩衝處理的訊息數目在對應期間的磁碟。  
  
  **判斷您要追蹤計劃期間所需的資訊**  
  
- 您需要追蹤哪些資訊，您應該決定在規劃階段中。如此一來，您部署專案之後, 您可以設定追蹤選項和限制，讓您只將所需的資訊的追蹤資料數量。  
  
  > [!NOTE]  
  >  如需與追蹤相關的最佳作法的詳細資訊，請參閱[規劃追蹤](../technical-guides/planning-for-tracking.md)本指南中並[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/p/?LinkId=154187)(http://go.microsoft.com/fwlink/p/?LinkId=154187)。  
  
  **不會追蹤所有訊息**  
  
- 我們建議您不追蹤所有訊息。 這是因為每次觸及訊息時，BizTalk Server 將訊息的另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於您系統的效能最大化，並保持資料庫的整齊。  
  
  **設定追蹤傳送埠和接收埠而不是在管線**  
  
- 如果您設定在管線的追蹤選項時，您也會設定每個管線所使用的連接埠的全域追蹤選項。 這接著可能會導致更多正在追蹤資料比您想，這將會變慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。  
  
  **調整節流根據資源使用量**  
  
- 中的節流[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供完善的保護系統的預設設定。 監視效能計數器來瞭解節流狀態，看看是否正在進行節流。 然後自行測量節流的資源為基礎 （例如，資料庫大小或記憶體使用量） 底下或透過使用。 接下來，調整 節流閾值增加或減少時隨之。 如需詳細資訊，請參閱 <<c0> [ 調整節流閾值： 何時和為何](http://go.microsoft.com/fwlink/p/?LinkId=154188)(<http://go.microsoft.com/fwlink/p/?LinkId=154188>)。  
  
  **如果可能，請使用 PassThruTransmit 管線**  
  
- 如果任何文件處理不需要傳送訊息至其目的地之前，請使用 PassThruTransmit 管線，而不是 XML 傳送管線。  
  
  **最小化協調流程 」 圖形開始與結束 」 的使用狀況追蹤事件**  
  
- 雖然追蹤的協調流程圖形會有明顯的好處，協調流程偵錯，它會具有效能和延展性的影響。 **流程化開始與結束**追蹤事件可能會造成相當大的負擔。 最好的方式是其其中高輸送量是必要的生產環境中的使用量降到最低。  
  
  > [!NOTE]  
  >  **圖形開始和結束**上所有的協調流程的預設會啟用追蹤事件。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)