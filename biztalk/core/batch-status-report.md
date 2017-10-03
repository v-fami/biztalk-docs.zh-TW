---
title: "批次狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dad016-e7bb-45cd-b36a-a9c83d073501
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c033f58432c8ae5a2d87b87b56223b8f64a7201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-status-report"></a>批次狀態報告
這份報告會顯示批次協調流程的執行個體活動。 報告中的每一列表示批次協調流程單一執行個體所處理的批次狀態。  
  
 保留批次的狀態不會在「批次狀態報告」中提供，但「交換/通知狀態」報告中有提供其報告資料。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 「批次狀態報告」會顯示批次交換的下列資訊：  
  
-   批次狀態  
  
-   批次名稱  
  
-   目的合作對象名稱  
  
-   啟動時間  
  
-   批次發生次數  
  
-   EDI 編碼類型  
  
-   批次類型  
  
-   批次目標  
  
-   批次項目計數： 批次項目數目已經累積的批次處理協調流程執行個體  
  
-   已拒絕元素計數  
  
-   批次已啟動、 排程釋放、 計數式釋放、 手動覆寫釋放、 批次終止/停止釋放、 新增項目，或外部釋放，可以是最新動作：  
  
-   交換控制編號  
  
-   交換日期時間  
  
-   批次大小 (以字元為單位) (預設情況下不顯示)  
  
## <a name="view-related-interchanges-status-reports"></a>檢視相關的交換狀態報告  
 如果您以滑鼠右鍵按一下的交換或批次狀態報告中所列的通知，您可以顯示的批次相關之交換的詳細資料。  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂「批次狀態報告」，藉由變更查詢運算式中的欄位，來決定要顯示的資料。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|批次狀態|是 (必要)|  
|批次狀態|等於<br /><br /> 不等於|定義： 批次的執行個體已設定但開始日期時間晚於目前日期時間。<br /><br /> 作用中 （預設值）： 批次執行個體已設定且正在收集批次的交易集。 開始日期時間早於目前日期時間。<br /><br /> 發行日期： 已符合釋放準則，並傳送批次，或批次協調流程已停止處理任何訊息之前。<br /><br /> 完成： 已符合釋放準則，但尚未傳送批次。<br /><br /> All： 顯示狀態為上述其中任何批次執行個體。|是|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|啟動日期時間|小於或等於<br /><br /> 大於或等於|日期時間<br /><br /> 今天<br /><br /> 今天-5|否<br /><br /> 附註： 可以包含超過一次在查詢運算式中。|  
|批次名稱|等於|全部 (預設)<br /><br /> 特定批次名稱|否|  
|目的合作對象|等於|全部 (預設)<br /><br /> 特定合作對象名稱|否|  
|EDI 編碼類型|等於|X12<br /><br /> EDIFACT<br /><br /> 全部 (預設)|否|  
  
