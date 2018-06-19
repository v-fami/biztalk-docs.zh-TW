---
title: 封存主要匯入資料庫資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Primary Import database [BAM], archiving data
- archived data, BAM
- managing [BAM], archiving data
- data, archiving [BAM]
ms.assetid: 4a014a59-0578-41fa-9441-8b582f54bbe8
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0fdfd55681fabd1b6cfc72f68b7e33150a121f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230414"
---
# <a name="archiving-primary-import-database-data"></a>封存主要匯入資料庫資料
系統管理員可以指定主要匯入資料庫中，活動執行個體資料的封存時間間隔。 請使用 BAMPrimaryImport 資料庫 BAM_Metadata_Activities 資料表中的 OnlineWindowTimeUnit 和 OnlineWindowTimeLength 屬性。  
  
 若商務使用者已部署多個活動，您可以針對每個活動指定不同的時間間隔。 如需部署活動的相關資訊，請參閱 「 定義商務活動 」*資訊工作者使用者手冊 》*。  
  
 下表說明 OnlineWindowTimeUnit 和 OnlineWindowTimeLength 可用的值。  
  
|屬性|值|  
|--------------|-----------|  
|OnlineWindowTimeUnit|這個屬性可以是： 月、 日、 小時或分鐘。 此屬性的預設值是月。|  
|OnlineWindowTimeLength|此屬性必須是整數。 這個屬性的預設值為 6。|  
  
 當分割比線上視窗還要舊時 (目前時間 - OnlineWindowTimeLength 個 OnlineWindowTimeUnit)，BAM 會將分割所代表的資料移出 BAM 主要匯入資料庫。 例如，假設 OnlineWindowTimeLength = 5 且 OnlineWindowTimeUnit = 日，便會移除 5 天前的分割。  
  
 BAM 會將封存的活動執行個體資料移至 BAM 封存資料庫。 BAM 封存資料庫是在設定 BizTalk BAM 組態期間指定的。 如需 BizTalk BAM 組態資訊，請參閱[BAM 組態結構描述](../core/bam-configuration-schema.md)。  
  
 若您並未執行將執行個體資料處理至活動 Cube 中的 BAM Cube 更新「資料轉換服務」(DTS) 封裝，則 BAM 不會封存活動執行個體資料。  
  
 如需執行 BAM 資料維護 DTS 封裝的詳細資訊，請參閱[BAM DTS 封裝](../core/bam-dts-packages.md)。  
  
 經過一段時間 BAMArchive 資料庫會成長的大小增加活動執行個體資料。 雖然沒有直接的方式截斷整個資料庫，您可以定期截斷資料庫交易記錄，以減少儲存需求，並定期備份和封存整個 BAMArchive 資料庫。 「 截斷交易記錄檔 」，請參閱 SQL Server 線上叢書 》 中的詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [定義時間間隔和時間配量屬性](../core/defining-the-time-window-and-time-slice-properties.md)   
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)