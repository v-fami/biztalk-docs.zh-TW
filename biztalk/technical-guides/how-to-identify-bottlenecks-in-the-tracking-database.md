---
title: 如何識別追蹤資料庫中的瓶頸 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b72e726-6225-47a0-8e1d-0f5a9cf745d3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc63ae8f673b25c4acbd2f7c066c38f2cb58d914
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011015"
---
# <a name="how-to-identify-bottlenecks-in-the-tracking-database"></a>如何識別追蹤資料庫中的瓶頸
若要識別 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的瓶頸，請執行下列步驟：  
  
1. 確認 SQL-Agent 服務正在執行。  
  
2. 確定「封存/清除作業」服務正在執行而且即將順利完成。  
  
3. 請確定 TrackedMessages_Copy_BizTalkMsgBoxDB 作業正在執行，而且無法順利完成。  
  
4. 確認是否有足夠的可用磁碟空間可以容納 DTADb 封存和資料庫成長。  
  
5. 用於追蹤專用的主機，並測量在負載下的主控件佇列長度效能計數器。  
  
6. 經過一段時間檢查遞增趨勢的多工緩衝處理表格 size 效能計數器。  
  
7. 檢查長時間執行的封存/清除作業執行持續時間。  
  
8. 在裝載 「 BizTalk 追蹤資料庫的磁碟，請檢查磁碟回應性 （Read/Write 效能計數器每次磁碟秒）。  
  
   我們強烈建議微調 dtasp_BackupAndPurgeTrackingDatabase 或 dtasp_PurgeTrackingDatabase DTA 清除與封存工作所叫用的下列參數的值：  
  
- @nLiveHours tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 預設值為 0 小時。  
  
- @nLiveDays tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 預設間隔是 1 天。  
  
- @nHardDeleteDays tinyint — （即使未完成） 所有的資料超過這將會被刪除。 為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。 資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。 早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。 預設值為 30 天。  
  
  這些參數都應該根據資料保留原則，在生產環境中，設定，而在效能實驗室測試，我們建議您使用的值，如下所示：  
  
  宣告@dtLastBackup日期時間組@dtLastBackup= getutcdate （）  
  exec dtasp_PurgeTrackingDatabase 1，0，1， @dtLastBackup  
  
## <a name="see-also"></a>另請參閱  
 [資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)