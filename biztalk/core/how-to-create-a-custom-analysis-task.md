---
title: "如何建立自訂的分析工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, DTS tasks
- DTS tasks
- DTS packages, tasks
- BAM, processing
ms.assetid: 6046c113-fb58-4e72-8f48-5470e52be9a8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3566e40deaa05886ead701e1871634cf6fb94e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-a-custom-analysis-task"></a>如何建立自訂分析工作
建立自訂 DTS 工作處理 BAM 資料最簡單的方式，就是從 BAM 自動產生的封裝開始，取代所有實際的資料處理。  
  
### <a name="to-create-a-custom-dts-task"></a>建立自訂 DTS 工作  
  
1.  建立需要 OLAP Cube 的 BAM 定義。 例如，請使用 Excel 精靈，將一份 PivotTable® 報告保留為非 RTA 檢視。  
  
2.  開啟 BAM 所建立的 DTS 封裝，進行 Cube 處理。 BAM 會建立一個這類封裝針對每個檢視，又稱為 BAM_AN_\<*檢視名稱*\>。  
  
3.  在 DTS 設計師中開啟這個封裝，然後將前兩個和最後一個步驟之外的所有步驟全部移除。 此外，您需要保持與主要匯入資料庫的連接。  
  
4.  編輯第一個 ActiveX® 工作的屬性。 移除包含 DTSGlobalVariables.Parent.Steps 的所有指令碼行，因為它們參考到已刪除的步驟。 指令碼的開頭如下：  
  
    ```  
    serverName = "<your server here>"   
    databaseName = "<your analysis database here>"  
    cubeName = "<your cube name here>"  
    ```  
  
    > [!NOTE]
    >  「開始資料分析」工作 (封裝中的第二個工作) 非常重要，因為它為您的封裝提供：  
    >   
    >  -   移動的視窗，可進行已完成活動的累加處理 (名稱為 bam_(BamView)_View(Activity)_CompletedInstancesWindow 的動態 SQL 檢視)。  
    > -   正在進行中的資料表，名為 bam 活動的快照集\_(BamView) _View (Activity) _ActiveInstancesSnapshot。  
  
5.  在簡短的交易中取得檢視和資料表，在這段交易期間您不會插入任何資料，所以這份資料就代表主要匯入資料庫的即時快照集。 請根據檢視和資料表做為輸入資料，執行一或多個步驟來完成實際的資料轉換。 如果您分析工作的目的不是要填滿 OLAP Cube，請記得保存最後一次執行工作的時間戳記，並以將此時間戳記指派給 "CompletedCubeLastProcessTime" 全域變數的程式碼取代第一個 ActiveX 工作。 第二個工作就會使用此變數確保不會遺失任何資料，以及在 DTS 封裝損毀和重新啟動時，不會有任何資料處理兩次的情形。  
  
6.  最後，您必須呼叫最後一個工作，也就是「結束資料分析」。 這個工作會釋放處理過的已完成活動，當它們一離開線上視窗時就會予以封存並從主要匯入中移除。  
  
## <a name="see-also"></a>請參閱  
 [使用商務活動監控](../core/using-business-activity-monitoring.md)