---
title: "追蹤資料庫中記錄大小 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: be7a891b-2674-49a3-a8e0-6aa11a918bf2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1f4d09d1af92ce4777f5036885d81ea7bf3e648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="record-size-in-tracking-databases"></a>追蹤資料庫中的記錄大小
為了協助您規劃 BizTalk 的硬體需求，下表會顯示追蹤資料庫中不同事件記錄的預期記錄大小。  
  
|動作類型|大小|注意|  
|-----------------|----------|-----------|  
|部署服務|1864 + 符號資訊大小|符號資訊會根據協調流程的大小而定。 例如，接收一個訊息並將訊息以兩個圖形傳送出的協調流程大約需要 4000 個位元組。|  
|已啟動及已成功完成的服務執行個體|通常需要 252 個位元組。<br /><br /> 特別狀況下可達到 735 個位元組。||  
|已啟動及遇到失敗/例外狀況的服務執行個體|通常需要 252 個位元組 + 錯誤資訊。<br /><br /> 特別狀況下可達到 735 個位元組 + 錯誤資訊。|錯誤資訊是由 BizTalk 或使用者元件傳回的文字資料。 範圍從 100 個位元組到 2 KB。|  
|協調流程中的圖形開始/結束|每個 120 個位元組。||  
|訊息進/出事件|最小需要 162 個位元組。<br /><br /> 第一次看見訊息時為 202 個位元組 + 訊息屬性 (若進行追蹤)<br /><br /> 特別狀況下可達到 2930 個位元組。|若沒有訊息屬性追蹤，您可安全地假設平均為 182 個位元組。|  
|訊息屬性大小|40 至 288 個位元組 (若 DTA 可識別此追蹤屬性)。<br /><br /> 第一次追蹤屬性時最大為 268 個位元組。||  
  
## <a name="see-also"></a>另請參閱  
 [什麼是訊息追蹤？](../core/what-is-message-tracking.md)   
 [管理與追蹤架構](../core/management-and-tracking-architecture.md)