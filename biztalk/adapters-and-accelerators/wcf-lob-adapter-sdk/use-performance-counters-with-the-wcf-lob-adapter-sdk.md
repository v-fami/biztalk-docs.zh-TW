---
title: "使用效能計數器，與 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b928eaf-2ab6-40a6-a1dd-804d4e89541e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bfff208920b25ee1a22aa2c3c74feeba42f4b43
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-wcf-lob-adapter-sdk"></a>使用效能計數器，與 WCF LOB 配接器 SDK
您可以使用 [效能] 工具會自動收集效能資料，從本機或遠端電腦執行[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 您可以定義開始和停止時間，來自動產生記錄檔，從單一主控台視窗中，管理多個記錄工作階段，然後設定可讓要傳送訊息的電腦上的記錄檔，以符合您的準則時啟動的警示。 本主題討論的效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
## <a name="performance-objects-and-counters"></a>效能物件和計數器  
 當您安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，已安裝名為"ServiceModel 配接器 」 的單一效能物件。 效能物件包含許多不同的效能計數器。 效能物件會測量特定的資源、 應用程式或服務的活動。 效能物件和計數器取得計數器的效能資料[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]、 功能、 和服務電腦上相同的方式。 此效能資料通常會命名為元件所產生的資料。 效能計數器可用來收集特定資訊或指定的效能物件的資料。  
  
 當選取計數器的 ServiceModel 配接器效能物件中，您可以選擇只從選取的執行個體清單中選取執行個體來監視資訊的特定配接器執行個體。 每個配接器執行個體將會列在格式\<ProcessId\>@\<ConnectionString\>。 比方說， 115@echo:&#124; &#124; 主機 &#124; temp？ echoprefix = 前表示回應配接器執行個體處理序 115 中執行。  
  
 在 WCF 中的效能計數器的相關資訊，請參閱[WCF 效能計數器](https://msdn.microsoft.com/library/ms735098.aspx)。
  
### <a name="servicemodel-adapters-metadata-cache-performance-counters"></a>ServiceModel 配接器中繼資料快取效能計數器  
 下表摘要說明可用來監視快取效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
|計數器|Description|  
|-------------|-----------------|  
|%快取讀取的叫用|讀取配接器快取點擊的中繼資料的百分比。|  
|判斷已解決的中繼資料|配接器所解析的中繼資料項目的數目。|  
|%完整快取|使用中的快取大小限制的百分比。|  
  
### <a name="servicemodel-adapters-connection-performance-counters"></a>ServiceModel 介面卡連線效能計數器  
 下表摘要說明用於監視的連線效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
|計數器|Description|  
|-------------|-----------------|  
|已中止的連線|已中止的目標系統的連線數目。|  
|使用中連接|目前使用中的目標系統的連線數目。|  
|開啟的連接|目前開啟的目標系統的連線數目。|  
|準備好的連線|可用的目標系統的連線數目。|  
|暫止的連接要求|數字的暫止的目標系統的連線要求。|  
  
### <a name="servicemodel-adapters-message-exchange-performance-counters"></a>ServiceModel 配接器訊息交換的效能計數器  
 下表摘要說明用於監視的訊息交換效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
|計數器|Description|  
|-------------|-----------------|  
|傳出呼叫|從配接器到目標系統進行傳出呼叫的數目。|  
|輸出 Calls/sec|傳出呼叫每秒從配接器到目標系統的數目。|  
  
## <a name="see-also"></a>請參閱  
 [使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)