---
title: "避免 DBNETLIB 例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fbee0cf-d249-4d98-8d16-168ded32f9f1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decd258c5f4c965c79d9821c82671c6997ac9e3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="avoiding-dbnetlib-exceptions"></a>避免 DBNETLIB 例外狀況
當 BizTalk Server 執行階段無法與 MessageBox 或「管理」資料庫通訊時，會發生 DBNetLib (資料庫網路程式庫) 錯誤。 發生此錯誤時，攔截例外狀況的 BizTalk Server 執行階段執行個體會關閉，然後每分鐘循環查看資料庫是否可以使用。  
  
 造成 DBNetLib 錯誤最常見的原因是：當其中一個 (可能有多個) MessageBox 資料庫伺服器變得非常忙碌，又嘗試與它通訊時發生逾時，因此造成 DBNetLib 例外狀況。  
  
 除了 MessageBox 資料庫所在只需非常忙碌的情況下，DBNetLib 錯誤可能在生產環境中裝載多個 MessageBox 資料庫的其中一個 BizTalk 資料庫伺服器變成 I/O （輸入/輸出） 繫結。  
  
 本主題描述可能導致 DBNetLib 錯誤的情況，以及避免這些錯誤的建議。  
  
## <a name="cause-and-resolution-for-the-dbnetlib-error"></a>DBNetLib 錯誤的原因和解決方案  
  
### <a name="symptoms-of-a-dbnetlib-error"></a>DBNetLib 錯誤的徵狀  
 Microsoft BizTalk Server 主控件執行個體會終止，然後自行重新啟動，並將類似下列的錯誤寫入 BizTalk Server 應用程式記錄檔：  
  
```  
Event Type:Warning  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:5410  
Computer:BIZTALKSERVER  
Description:  
An error occurred that requires the BizTalk service to terminate. The most common causes are the following:  
 1) An unexpected out of memory error.  
 OR  
 2) An inability to connect or a loss of connectivity to one of the BizTalk databases.   
 The service will shutdown and auto-restart in 1 minute. If the problematic database remains unavailable, this cycle will repeat.  
  
 Error message: [DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation.  
 Error source:    
  
 BizTalk host name: BizTalkHost  
 Windows service name: BTSSvc$BizTalkHost   
  
---------------------------------------------------------  
Event Type:Error  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:6913  
Computer:BIZTALKSERVER  
Description:  
An attempt to connect to "BizTalkMsgBoxDb" SQL Server database on server "SQLSERVER " failed.  
 Error: "[DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation."  
```  
  
### <a name="biztalk-database-servers-hosting-messagebox-databases-becoming-io-bound"></a>裝載 MessageBox 資料庫的 BizTalk 資料庫伺服器變成 I/O 繫結  
 BizTalk Server 會直接與裝載 MessageBox 資料庫的資料庫伺服器通訊並作用。 若有任何裝載 MessageBox 資料庫的資料庫伺服器過度使用，並進入 I/O 繫結狀況，則資料庫伺服器可能變成反應遲緩。 接著，其中一個 BizTalk Server 可能與這些資料庫伺服器失去連線，會發生 DBNetLib 錯誤。  
  
 我們的測試顯示，高度使用的資料庫伺服器會在其實體磁碟的「閒置時間百分比」持續下降到 10% 以下時，變成 I/O 繫結。 若「閒置時間百分比」持續下降到該層級以下，這表示您的資料庫伺服器可能會變成反應遲緩。  
  
#### <a name="cause"></a>原因  
 有幾個原因可能造成裝載 MessageBox 資料庫的資料庫伺服器變成 I/O 繫結，下列為其中部分原因：  
  
-   如果裝載 MessageBox 資料庫的資料庫電腦受限於硬體規格不足，例如，記憶體不足、處理器的數目和速度等等  
  
-   若裝載 MessageBox 資料庫之資料庫電腦上的實體磁碟正由其他高度使用的資料庫共用。 在數個資料庫 (包括 MessageBox) 正在同時高度使用的情況下，實體磁碟可能會陷入 I/O 繫結狀況。  
  
     這類狀況的範例如下：  
  
     我們的測試顯示，裝載 BizTalkDTADb 和/或 BAM 資料庫的資料庫伺服器有時會使用高百分比的實體磁碟之「磁碟讀取和寫入次數百分比」。 當裝載 MessageBox 資料庫的資料庫伺服器磁碟由另一個高度使用的資料庫 (如 BizTalkDTADb 或 BAM) 共用，而這兩個資料庫同時高度使用時，它們可能造成資料庫伺服器實體磁碟變成 I/O 繫結，然後變成反應遲緩。  
  
-   若 BizTalkDTADb 和一或多個 MessageBox 資料庫正在共用資料庫伺服器上的相同實體磁碟，而封存與清除不常執行時，則磁碟可能變成 I/O 繫結。  
  
#### <a name="resolution"></a>解決方案  
 確定裝載 BizTalk MessageBox 的資料庫伺服器不會陷入高度使用和可能反應遲緩的狀況。  
  
 以下列出造成伺服器磁碟變成高度使用的部分主要原因以及如何減輕此問題的建議。  
  
##### <a name="low-hardware-specs"></a>硬體規格不足  
 我們的測試顯示，當伺服器的硬體規格趕不上它所嘗試處理的負載量時，就會開始增加伺服器的使用。 若硬體規格不足，系統很快就會因為發生在資料庫上的活動量而超過負荷。 這可能造成伺服器的「磁碟讀取和寫入次數百分比」持續增加而不穩定，而且磁碟的「閒置時間百分比」也持續降低到 10% 以下，這可能造成資料庫伺服器變成反應遲緩。  
  
 視 BizTalk 部署上的活動量與負載的不同，若您在高負載期間發現資料庫伺服器反應遲緩，應該考慮將資料庫伺服器中的下列部分升級：CPU 數目、記憶體以及連接到 SAN。 當然，您應該進行適當的診斷，以找出硬體中哪個部分 (記憶體、CPU 數目等) 是需要升級的瓶頸。  
  
##### <a name="sharing-one-server-or-disk-for-more-than-one-group-of-biztalk-databases"></a>讓一個以上的 BizTalk 資料庫群組共用一個伺服器或磁碟  
 如先前所提及，MessageBoxes 以外的資料庫 (如 BizTalk 追蹤 (BizTalkDTADb) 資料庫與 BAM 資料庫) 可能高度循環使用伺服器的實體磁碟。 因此，若這些資料庫正好與 MessageBox 資料庫共用相同的實體磁碟，它們就可能阻礙磁碟並使它反應遲緩，這也同樣可能造成 BizTalk Server 與 MessageBox 資料庫失去連線，並因此造成 DBNetLib。  
  
 強烈建議您將任何預期會高度使用伺服器之實體磁碟的資料庫與 BizTalk MessageBox 分開，如此，它們可以共用不同的實體磁碟 (或是將它們分隔在不同的伺服器)。 建議您將 BizTalkDTADb 和 BAM 資料庫分隔在 MessageBox 以外的個別磁碟/伺服器上，同時也建議您將每個 MessageBox 資料庫 (在擁有一個以上的 MessageBox 資料庫情形下) 放在其本身的磁碟上。  
  
##### <a name="archiving-and-purging"></a>封存與清除  
 在 BizTalkDTADb 和 MessageBox 資料庫共用相同伺服器的相同磁碟的情況下，您必須定期封存與清除 BizTalkDTADb 資料庫，否則它們將會無限成長。  
  
 測試指出，定期封存與清除是較好的作法，不過，若您執行比一般更高的負載，可能要考慮更頻繁地封存與清除。 若沒有定期維護 BizTalkDTADb 資料庫的成長，在最後執行這些動作時，可能會花費相當長的時間，並在執行這些動作時使用大部分可用的資料庫伺服器資源。