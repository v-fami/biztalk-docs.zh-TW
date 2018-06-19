---
title: 何謂追蹤設定檔？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking profiles, about tracking profiles
- tracking profiles, Tracking Profile Editor
- Tracking Profile Editor, tracking profiles
- tracking profiles
ms.assetid: b579bdc4-7c69-4fa0-bbc1-f98170c13d4f
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da032fb6063d81cedca9f21899c5e2bbe6eca947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289702"
---
# <a name="what-is-a-tracking-profile"></a>何謂追蹤設定檔？
設定檔是定義商務程序的一組特性。 追蹤設定檔包含從活動到協調流程和連接埠這些特性的對應。 追蹤設定檔的副檔名為 .btt。  
  
## <a name="using-tracking-profiles-in-the-tpe"></a>在 TPE 中使用追蹤設定檔  
 TPE 的使用者可以在 BAM 活動項目與那些項目的 BizTalk Server 解決方案來源之間建立對應，也就是所謂的追蹤設定檔。 BAM 活動是由構成「可見性期望清單」的里程碑與內容資料所組成，並且定義追蹤設定檔所依循之商務中的工作單位。 如需活動的詳細資訊，請參閱[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md)。  
  
 使用 TPE 建立追蹤設定檔時，您會用到下列物件：  
  
-   BAM 活動  
  
-   已部署組件中的 BizTalk 協調流程  
  
-   接收埠與傳送埠  
  
-   已部署組件中的訊息結構描述  
  
-   內容屬性  
  
-   BAM 主要匯入資料庫  
  
-   BizTalk 管理資料庫  
  
-   BizTalk 追蹤資料庫  
  
 將訊息結構描述、協調流程圖形與內容屬性中的項目拖放到商務里程碑 (事件) 和資料項目資料夾，藉此定義協調流程中的資料擷取。  
  
 舉例來說，假設 BAM 活動包含名為「收到的 PO」的里程碑，並且含有讓訂單連入以初始化處理作業的傳訊連接埠。 開發人員可以將 `PO Received` 里程碑與方案中連接埠的 BizTalk 傳訊屬性 `PortEndTime` 產生關聯。 語意上，這代表只要接收埠結束動作，並填入 `PortEndTime` 屬性，就會成功接收到 PO。 開發人員會讓此關聯與任何其他對應能夠完成追蹤設定檔。 此活動中含有 BizTalk Server 來源的所有項目都會建立對應，但如果資料或事件的來源是來自 BizTalk Server 執行階段環境以外的處理序，則會保留未對應的狀態，以便由 API 呼叫直接填入。  
  
 雖然 TPE 中的每個窗格或檢視都有獨特功能，但所有檢視與資料夾的瀏覽功能都很類似，方便您尋找和處理資訊。  
  
## <a name="who-uses-tracking-profiles-and-the-tpe"></a>誰會用到追蹤設定檔與 TPE？  
 需要進行企業整合開發的使用者可以使用追蹤設定檔與 TPE，將 BizTalk Server 事件來源對應到 BAM 目標活動。 產生的 .btt 檔案會交付給 IT 實作進行部署。  
  
 一般而言，IT 實作使用者會使用命令列工具 (BTTDeploy) 套用追蹤設定檔。 IT 使用者也可以使用 TPE 直接套用追蹤設定檔。  
  
 IT 作業部門的使用者可能要負責定期對追蹤設定檔進行更新 (包括任何必要的資料庫作業，例如備份與還原)，尤其是商務需求有所變更時，更是非做不可。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)