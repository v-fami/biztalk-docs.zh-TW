---
title: "秘訣和訣竅尋找 MST 的 DTA 追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d72e4ac-d952-4cff-9a65-491e20945d40
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9faaaf7ebb47ac7ec18d8df6d8cb7c6ebd48d7f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tips-and-tricks-for-finding-mst-of-dta-tracking"></a>尋找 DTA 追蹤之 MST 的秘訣和訣竅
根據定義，MST 是以重現方式使用固定負載來測量系統效能的基準。 在下列情況中，瞭解 MST 將特別有用。  
  
1.  **當您需要從系統的最低延遲**。 超過 MST 會在系統中產生積存，因此增加訊息延遲情況。 即使積存只是暫時性，但這會對延遲造成立即且不利的影響。 因此，瞭解系統的 MST 會顯示在個別訊息處理延遲暴增 (視組態而定，從數秒到數分鐘) 之前，可預期達到的絕對最大輸送量。  
  
2.  **比較與其他系統時**。 例如，相較於另一個系統 (例如本主題中的案例、案例研究或環境中的另一個系統)，若要驗證是否達到預期的 MST，則透過穩定輸入測量 MST，會提供可重現、明確的比較標準。  
  
 不用說，測量 MST 很耗時。 因此，在開始冗長的測量練習之前，您應該評估優點。 大部分實際執行的系統不會經歷 MST 所測量的穩定輸入，而是隨時間變動的負載。 負載設定檔就是最終必要的測試項目，才能將系統付諸實際執行。 所幸，您可以用測量 MST 的相同技巧來評估實際執行負載設定檔的持續性。 只要執行負載設定檔夠久，可以包含一或多個 BizTalkDTADb 資料庫資料保留時間，並觀察關鍵效能指標 (KPI) 即可。  
  
 重要的是，使用空白 BizTalkDTADb 資料庫啟動測試回合 (不論是 MST 還是負載設定檔)。 BizTalkDTADb 資料庫中儲存的資料具時效性，如果每個測試回合未重新取得空白資料庫，則會扭曲測試結果。 根據資料保留時間，尋找 MST 的所需時間可能會大為增加。 若要緩和這個問題，請在測試回合期間即時調整負載，有助於更快速尋找 MST。  
  
 例如，如果已傳遞第一個保留時間，而且 KPI 指出輸送量還有成長空間 (例如，磁碟閒置時間仍然高於零)，您就可以遞增負載並觀察結果。 用這個方式調整 MST 預估值之後，請務必使用空白 BizTalkDTADb 資料庫重新執行測試回合，驗證此預估值。  
  
## <a name="recommendations"></a>建議  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的追蹤系統架構能夠追蹤廣泛的資訊，必須進行周密管理和監控。 MST 指出，對系統效能造成最大影響的因素如下：  
  
-   所需的系統輸送量。  
  
-   針對系統中每個訊息和服務執行個體所追蹤的資訊量。 這會決定 BizTalkDTADb 資料庫大小增加的速度，以及最終 BizTalkDTADb 資料庫多久必須清除以避免延遲。  
  
-   您希望在 BizTalkDTADb 資料庫中保留資料多久，即資料保留時間。 保留時間越久，BizTalkDTADb 資料庫會變得越大，因此會影響輸送量。  
  
-   您要同時進行 BizTalkDTADb 資料庫資料封存與清除，還是為了維護 BizTalkDTADb 資料庫大小，只進行清除。  
  
 尋找最大持續性輸送量，以便在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中進行追蹤的程序，包含三個關鍵效能指標：  
  
-   DTAdb 資料檔案磁碟子系統的「實體磁碟閒置時間」  
  
-   多工緩衝處理深度  
  
-   BizTalkDTADbData 深度  
  
 藉由監控這三個關鍵效能指標並尋找下列項目，來尋找系統的 MST 或驗證實際執行設定檔輸送量：  
  
-   穩定的多工緩衝處理和追蹤資料表深度。  
  
-   接近零 (但不持續固定在零) 的 BizTalkDTADb 資料庫資料檔案磁碟實體閒置時間。  
  
 使用 DTA 追蹤功能有關聯的效能影響。  預設追蹤在解決方案付諸實際執行後可能會大於需要，但由於它提供充分的問題解決資訊，會讓開發、初始測試和偵錯更加輕鬆。 因此，建議在開發和初始測試期間啟動預設追蹤。 一旦在 BizTalk 部署的解決方案穩定並準備實際執行驗證 (包括效能測試) 時，建議您仔細檢查在實際執行中必須追蹤的資訊量，以及在 BizTalkDTADb 資料庫中必須保留資訊的時間長度，並適當進行調整。  
  
 例如，如果不需為了不可否認性與問題解決目的而追蹤訊息內文，請勿開啟訊息內文追蹤。 為了說明這點，在此案例中所述[測量 MST 的 DTA 追蹤測試案例](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)時的訊息內文追蹤的追蹤組態元件已被排除，MST 會加倍為 40訊息/秒。  
  
 此外，請記住，即使發生問題，在許多狀況下 (但非全部)，訊息會擱置在 MessageBox 資料庫中，不需追蹤訊息內文即可擷取和檢查訊息。  
  
 集中於系統的負載持續性：  
  
-   即使在一般維護活動的同時，系統是否能無限期地持續實際執行負載設定檔？  
  
-   如果發生狀況 (例如計劃與非計劃的 BizTalkDTADb 資料庫中斷) 而導致系統產生積存？  
  
 最好根據最壞案例設定目標，並針對這些目標進行測試。 例如，如果您知道定期計劃性的維護週期必須讓 BizTalkDTADb 資料庫離線，則可以在測試回合期間模擬此中斷狀況，評估系統從產生的積存復原的能力。  
  
## <a name="see-also"></a>另請參閱  
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [瞭解 DTA 追蹤效能行為](../core/understanding-dta-tracking-performance-behavior.md)   
 [測量 MST 的 DTA 追蹤測試案例](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [調整追蹤資料庫大小的指導方針](../core/tracking-database-sizing-guidelines.md)