---
title: 何謂事件追蹤？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [HAT tracking], events
- DTA_Services audit table [HAT]
- HAT, events
- events, tracking
- tracking, events
- Tracking database, DTA_Services audit table
- events, HAT
ms.assetid: dd211752-d1af-4287-967a-908b8d067ebb
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42799a084c579cfba7d696c700d887b1ae992db2
ms.sourcegitcommit: ed9590dbcd97c12a1fe5ce2cdf8d826492cccdff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39640082"
---
# <a name="what-is-event-tracking"></a>何謂事件追蹤？
追蹤的訊息事件資料根據事件 （例如，當服務開始或結束，或傳送或接收訊息時）。 訊息事件追蹤處理程序傳回之事件的發生，讓您查看發生的所有項目會根據您設定的追蹤篩選清單。  
  
 當傳送和接收訊息時，您可以追蹤協調流程和連接埠的開始與結束，以及協調流程中每個圖形的執行。  
  
 BizTalk 追蹤 (BizTalkDTADb) 資料庫包含一個 DTA_Services 稽核表格。 此表格包含所有已部署服務的歷程記錄 — 管線、 傳輸和協調流程。 它不會持續追蹤解除部署。  
  
 您可以追蹤訊息的內容以及訊息的升級屬性。 追蹤訊息事件定義為這些動作**訊息內文**追蹤並**訊息屬性**追蹤。 雖然信封會出現在訊息事件追蹤輸出中，但是您不能追蹤信封中的訊息屬性。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 管理主控台設定追蹤](http://msdn.microsoft.com/49b7f9d3-60b5-41bd-ba8b-029253926bef)
