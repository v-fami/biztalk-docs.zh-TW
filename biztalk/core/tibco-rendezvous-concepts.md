---
title: "TIBCO Rendezvous 概念 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36060091-57dc-4125-8dca-23058d813deb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9969ff652791e551f8603c0ec890704bccb12c37
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-rendezvous-concepts"></a>TIBCO Rendezvous 概念

## <a name="concepts-explained"></a>說明的概念
下表說明 TIBCO Rendezvous 中的部分功能與概念。  
  
|概念|定義|  
|-------------|----------------|  
|**訊息**|攜帶處理程序或執行緒之間的資料。 訊息包含自我描述的資料欄位。 程式可以操作訊息欄位、傳送訊息以及接收訊息。|  
|**事件**|建立事件物件以監控重要狀況。 例如，分派待命程式事件會通知程式訊息已到達；分派計時器事件會通知程式它的時間間隔已過。<br /><br /> 程式會定義事件回呼函數以處理事件。|  
|**主題**|訊息會與一個邏輯名稱 (主旨) 關聯。 程式會接聽特定主旨，或以特定主旨發佈訊息。|  
|**傳輸**|定義傳遞範圍、機制與通訊協定的物件。|  
|**批次模式**|TIBCO Rendezvous 傳輸物件支援以批次模式發佈訊息。 <br />預設模式是： 儘速傳送訊息。 計時器批次模式是： 累積訊息，並傳送當緩衝區已滿或計時器時間間隔。|  
|**佇列**|程式會建立事件佇列以組織事件。 佇列是待處理之事件物件的序列。|  
|**佇列群組**|合併佇列以自訂事件處理 (使用不同的優先順序)。|  
|**保證的訊息傳遞**|確認傳遞每個訊息到每個註冊的收件者。 儘管程序終止並重新啟動，仍使用以檔案為基礎的分類帳傳遞訊息。<br /><br /> 保證傳遞可向程式確保每個保證訊息均會依照傳送順序到達每個預定的收件者。 當無法傳遞時，傳送與接聽程式均會收到每個無法傳遞之訊息的明確資訊。<br /><br /> 程式會決定每個訊息的明確時間限制。<br /><br /> 在程式傳送保證訊息後，TIBCO Rendezvous 軟體會繼續嘗試傳遞直到成功傳遞為止，或直到超過訊息時間限制為止。<br /><br /> TIBCO Rendezvous 保證傳遞軟體會提供通報訊息，以通知程式和傳遞有關的每個重要事件。<br /><br /> TIBCO Rendezvous 保證傳遞軟體會在分類帳中記錄每個訊息的狀態。 只有程式處理程序期間需要保證的程式，才應使用以處理程序為基礎的分類帳。 需要的保證超出處理程序終止和程式重新啟動界限的程式則使用以檔案為基礎的分類帳。<br /><br /> 當不允許保證傳遞時，傳遞條件會降為標準 TIBCO Rendezvous 可靠傳遞語意。|  
|**分散式的佇列精靈**|在數個處理程序間分散服務。<br /><br /> TIBCO Rendezvous 精靈會完成網路中 TIBCOTIBCO 程式處理程序之間的資訊路徑。 程式會嘗試連線至 TIBCO Rendezvous 精靈處理程序。 如果本機精靈處理程序尚未執行，程式會自動啟動一個精靈處理程序並與它連線。 TIBCO Rendezvous 精靈會排列資料傳輸的詳細資訊、封包順序、回條確認、重新傳輸要求，並分派資訊到正確的程式處理程序。 精靈會對 TIBCO Rendezvous 程式隱藏前述所有詳細資訊。 TIBCO Rendezvous 精靈對依賴它的程式而言幾乎是無形的。 程式使用 TIBCO Rendezvous 通訊呼叫傳送與接收資訊，TIBCO Rendezvous 精靈則負責將資訊送到適當的位置。<br /><br /> 精靈會執行下列工作：<br /><br /> -將傳送到網路的輸出訊息從程式處理程序。<br />-輸入訊息傳遞從網路到程式處理程序。<br />-篩選主旨確定的訊息。<br />-保護不受影響作業系統特性，例如低層級的通訊端程式。|  
|**安全性**|TIBCO Rendezvous 支援以憑證或使用者與密碼為基礎的驗證。|  
|**虛擬電路**|經由專用與連續監控連線在兩個終端機之間進行 Rendezvous 通訊。|  
|**直接通訊**|不經過中繼 Rendezvous 精靈處理程序的點對點通訊。|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for TIBCO Rendezvous 中的訊息](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)