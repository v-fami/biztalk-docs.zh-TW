---
title: 何謂活動檢視？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], Activity view [Tracking Profile Editor]
- activities [BAM], definitions
- Tracking Profile Editor, Activity view
- Activity view [Tracking Profile Editor]
ms.assetid: ae6bcdc8-e426-4148-b83d-08a1a5e99ca3
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48cbf2419f1d3ab0939ed1607df7c17e1ea3f8d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997943"
---
# <a name="what-is-an-activity-view"></a>何謂活動檢視？
活動檢視含有匯入的 BAM 活動定義，這是您使用 Excel 的 BAM 增益集所建立的。 BAM 活動定義是對於商務程序之追蹤需求的抽象概念。 活動可以跨越多個協調流程與連接埠。 您可以匯入一次活動定義，然後將活動定義對應至每個符合部分定義的協調流程或傳訊成品。  
  
 [活動檢視] 連結位於追蹤設定檔編輯器 (TPE) 使用者介面的左窗格中。  
  
## <a name="activity-view-elements"></a>活動檢視項目  
 活動檢視會以樹狀檢視顯示追蹤設定檔的整體結構，並且包含下列項目：  
  
- 里程碑  
  
- 活動的資料項目  
  
- 事件來源  
  
- 資料來源  
  
  **里程碑**： 里程碑是指定的處理序中定義某個點的物件。 可以用下列其中一種方式來存取：  
  
- 您可以從協調流程排程拖曳圖形，並且該圖形的執行結束時間會由 BAM 回報做為里程碑的值。  
  
- 您可以從右側結構描述表示法拖曳傳訊屬性至目標里程碑。  
  
- 您可以拖曳含有里程碑值的訊息內容結構描述節點。  
  
  > [!NOTE]
  >  DATETIME ONLY 類型結構描述節點是在執行階段評估的。 執行階段發生的任何轉換問題 (Conversion 或 Casting) 都會造成事件日誌中出現追蹤錯誤。  
  
  **資料項目**： 資料的項目會定義特定訊息執行個體、 系統或升級的屬性的 XML 結構描述項目的物件。 展開結構描述，找出並選取您想要的項目，然後將該項目拖曳到正確的資料項目類型資料夾，即可存取資料項目。 關於資料項目 (例如 XPath) 的詳細資訊會儲存在設定檔中。  
  
> [!NOTE]
>  TPE 僅支援擁有零對一表示法的資料項目，其表示法如特定資料欄位的訊息結構描述中所定義。 如果有一對多表示法的資料項目，協調流程追蹤可能會發生錯誤。 在這些情況中，不會將任何資料儲存在 BAM 主要匯入資料庫中。 如果沒有發生錯誤，也無法確保追蹤的是哪個資料項目。  
  
> [!NOTE]
>  BAM 開發人員必須注意到，屬性是根據 BizTalk Server 程序規則填入的，而不是 BAM。  
>   
>  例如，在 SMTP 配接器中，內容屬性 (例如 SMTPServer、CC 和 From) 在明確填入之前，並不會含有任何值。 一旦填入之後，它們的值就會出現在 BAM 主要匯入資料庫中，並且也可以用來進行追蹤。  
  
## <a name="activity-view-context-menus"></a>活動檢視快顯功能表  
 活動檢視可用動作的快顯功能表，會依在 [協調流程檢視] 中選取的節點而動態地變更。 例如，如果您選取活動資料夾節點，快速鍵功能表將會包含該活動資料夾的快速鍵功能表項目。  
  
 將右側來源事件窗格中的事件和資料拖曳到 [活動] 檢視的事件或資料節點，即可將事件和資料與商務活動中的項目產生關聯。  
  
 以滑鼠右鍵按一下活動檢視樹狀結構中的節點，即可在該視窗中看到節點的快顯功能表。 下列畫面顯示活動檢視的根節點。 下表說明活動檢視中不同節點快顯功能表中的項目。  
  
 **活動定義樹狀結構根節點**  
  
 ![](../core/media/activityviewcontextmenu.gif "activityviewcontextmenu")  
  
|功能表項目|使用方式|  
|---------------|-----------|  
|新接續|在 [活動] 樹狀結構中插入新的 [Continuation] 資料夾。 您對應此資料夾從接續的來源區段的值。<br /><br /> 與 [ContinuationID] 資料夾搭配使用，提供一種方式讓填入相同活動的多個元件彼此互相轉手處理工作。 BizTalk 協調流程、連接埠、BufferedEventStreams 和 DirectEventStreams 都是這些元件的例子。 **注意：** continuation 資料夾可以包含 127 個字元的最大值。|  
|新 ContinuationID|在 [活動] 樹狀結構中插入 [ContinuationID] 資料夾。 您可以將這個資料夾對應到接續的 continued-to 區段。 例如，如果協調流程 A 接續到協調流程 B，這個資料夾就必須對應到協調流程 B 中的項目。<br /><br /> 與 [Continuation] 資料夾搭配使用，提供一種方式讓填入相同活動的多個元件彼此互相轉手處理工作。 BizTalk 協調流程、連接埠、BufferedEventStreams 和 DirectEventStreams 都是這些元件的例子。 **注意：** continuationid 資料夾可以包含 127 個字元的最大值。|  
|新增關聯性|在 [活動] 樹狀結構中插入新的關係資料夾。 用於發佈組成檢視之各個活動之間的關係。 **注意：** 關聯性的資料夾名稱可以包含最多 128 個字元。 這包括了伺服器名稱和 BizTalk 管理資料庫名稱。|  
|新 Document Reference URL|在 [活動] 樹狀結構中插入新的 [Document Reference URL] 資料夾。 用於將參考 URL 設定為含有此活動相關文件的位置。 **注意：** Document Reference URL 的資料夾名稱可以包含最多 128 個字元。|  
  
 **屬性節點**  
  
|功能表項目|使用方式|  
|---------------|-----------|  
|與所選資料產生關聯|用於在訊息內容或內容屬性資料項目與 BAM 活動資料項目資料夾之間建立關聯。|  
  
 **事件節點**  
  
|功能表項目|使用方式|  
|---------------|-----------|  
|與所選動作的結尾產生關聯|用來建立協調流程圖形、 DateTime 訊息內容或 DateTime 內容屬性資料項目與 BAM 活動里程碑資料夾之間的關聯。|  
  
## <a name="see-also"></a>另請參閱  
 [使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md)   
 [在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md)   
 [TPE 的元件](../core/components-of-the-tpe.md)