---
title: 如何定義 BAM 彙總 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, BAM
- aggregations [BAM], creating
- Excel add-in [BAM], security
- Excel add-in [BAM], creating aggregations
- managing [BAM], creating aggregations
ms.assetid: a5ef3a15-b1de-4099-8e94-64af4b5ec746
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1b5b377611eb8e28088cb2d0c2f2ed6f829de8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249510"
---
# <a name="how-to-define-bam-aggregations"></a>如何定義 BAM 彙總
BAM 支援兩種資料彙總：  
  
-   線上分析處理 (OLAP) 彙總  
  
-   即時彙總 (RTA)  
  
 BAM 使用 Microsoft SQL Server Analysis Services，實作 OLAP 彙總。  
  
 您必須在 BAM 主要匯入資料庫上設定定義 RTA 的觸發程序。  
  
### <a name="to-define-olap-aggregations"></a>定義 OLAP 彙總  
  
1.  在 BAM Excel 活頁簿中，建立檢視，並至少在樞紐分析表中新增一個維度和一個量值，清除 RTA 工具列按鈕，然後儲存此活頁簿。  
  
    -   如需開啟 BAM 活頁簿，建立檢視，以及新增維度和量值，請參閱[定義 BAM 檢視](../core/defining-a-bam-view.md)。  
  
2.  部署活頁簿。  
  
    -   若要部署活頁簿，請依照下列中的指示[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。  
  
3.  方案開發人員使用**DirectEventStream**類別將事件匯入 BAM 主要匯入資料庫。  
  
    -   如需有關資訊**DirectEventStream**類別，請參閱[DirectEventStream 類別](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx)。  
  
4.  執行更新 Cube Data Transformation Services (DTS) 封裝。  
  
    -   如需執行更新 cube DTS 封裝的詳細資訊，請參閱[BAM DTS 封裝](../core/bam-dts-packages.md)。  
  
5.  開啟此活頁簿最近的即時資料複本，以檢視 OLAP 彙總。  
  
    > [!IMPORTANT]
    >  基於安全性理由，BAM 不會刪除活頁簿現有的即時資料複本， 而是遞增即時資料複本的檔案名稱。  
  
### <a name="to-define-the-rta"></a>定義 RTA  
  
1.  在 BAM Excel 活頁簿中，建立檢視，並至少在樞紐分析表中新增一個維度和一個量值，選取 RTA 工具列按鈕，然後儲存此活頁簿。  
  
    > [!WARNING]
    >  請勿定義多個使用相同 BAM 活動的 RTA。 若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。  
  
    -   如需開啟 BAM 活頁簿，建立檢視，以及新增維度和量值，請參閱 < 定義商務活動檢視 > 和 < 定義彙總 」 中*資訊工作者使用者手冊 》*。  
  
2.  部署活頁簿。  
  
    -   若要部署活頁簿，請依照下列中的指示[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。  
  
3.  方案開發人員使用**DirectEventStream**類別將事件匯入 BAM 主要匯入資料庫。  

  
4.  開啟此活頁簿最近的即時資料複本，以檢視 RTA。  
  
    > [!IMPORTANT]
    >  基於安全性理由，BAM 不會刪除活頁簿現有的即時資料複本， 而是遞增即時資料複本的檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [BAM DTS 封裝](../core/bam-dts-packages.md)   
 [如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)   
 [更新 OLAP 和 RTA 連接字串屬性](../core/updating-olap-and-rta-connection-string-properties.md)   
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)