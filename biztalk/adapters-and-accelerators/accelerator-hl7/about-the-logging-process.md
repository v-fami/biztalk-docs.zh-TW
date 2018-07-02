---
title: 關於記錄處理程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logging, about logging
- auditing, about auditing
- logging
- auditing
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110c7d4505e6518836fa481ed268771aef72d4c4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981055"
---
# <a name="about-the-logging-process"></a>關於記錄處理程序
您的應用程式處理重要，因為時間敏感和貨幣資料，稽核會成為應用程式的重要部分。 若要啟用企業層級的管理能力和可用性，Microsoft[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]依賴下列共用執行的階段和系統管理的元件：  
  
- **記錄**： 收集和路由傳送所有記錄以受管理的方式，來指定資料庫事件  
  
- **事件監控及偵錯服務**： 若要設定記錄行為，以及調查/管理所收集的資訊，讓系統管理員和其他 IT 專業人員  
  
  增強稽核功能[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]，您可以最佳化您的營運效率、 安全性和效能，以確保 HL7 法規的合規性。  
  
## <a name="types-of-data"></a>資料類型  
 本主題說明不同類型的使用記錄功能，並儲存此資料的記錄資料：  
  
- 設定資料： 記錄組態資料會儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫），並包含稽核資訊和稽核資料的 SQL ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件檢視器、 集中式資料庫 WMI) 的位置。  
  
- 封存資料： SQL 記錄檔中的事件記錄檔資料表會儲存 '記錄' 的資料。  
  
## <a name="how-logging-works"></a>記錄的運作方式  
 本主題說明三種類型的事件記錄的軟體，以及您可以在其中儲存記錄的資料的三個位置。  
  
|元件|目的|  
|---------------|-------------|  
|組態編輯器|若要指定要儲存的記錄資料的位置。 BTAHL7 支援記錄到以下的任何組合： 事件檢視器、 WMI 及 SQL Server 的記錄。|  
|事件訊息代理程式|若要接收記錄檔事件由其他元件所引發並將其根據記錄組態資料記錄。|  
|記錄 API|記錄所有 BTAHL7 組件所呼叫的介面。|  
  
### <a name="types-of-logging"></a>類型的記錄  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 記錄錯誤的三種：  
  
- 參考事件、 服務啟動或停止或事件失敗。  
  
- 警告事件，例如中非關鍵錯誤和警告[!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件記錄檔。 比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為資料驗證失敗。  
  
- 在元件中的嚴重失敗的錯誤事件。 比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為剖析器失敗。  
  
  系統可以記錄[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]事件加入下列可設定的位置：  
  
- [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] 事件檢視器  
  
- WMI 事件  
  
- 集中式的資料庫 （SQL 記錄資料庫）  
  
  事件代理程式接收所有[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄事件，根據組態資訊、 將它們傳送到適當的位置。  
  
### <a name="overview-of-features"></a>功能概觀  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供記錄功能：  
  
-   統一的方式記錄所有錯誤訊息  
  
-   集中存放庫來儲存所有事件詳細資料  
  
-   用於記錄訊息流向離散的特定業務應用程式一致的物件模型  
  
-   記錄和追蹤，協助的系統管理員將相互關聯的組合會記錄錯誤的文件  
  
## <a name="event-log-data"></a>事件記錄檔資料  
 本主題描述的格式和內容的事件記錄檔資料。  
  
 下表顯示適用於合作夥伴的一般記錄的資料。  
  
|data|描述|  
|----------|-----------------|  
|LogData|將資料記錄檔|  
|CategoryNumber|類別目錄數目|  
|EntryType|事件的類型|  
|EventId|事件識別碼|  
|MachineName|電腦名稱|  
|訊息|訊息詳細資料|  
|來源|建立、 更新、 讀取、 刪除、 部署或封存資料|  
|TimeGenerated|成功或失敗|  
|UserName|[使用者名稱]|  
|MsgGuid|訊息的 GUID|  
|SvcGuid|服務 GUID|  
|作業|作業詳細資料|  
  
## <a name="see-also"></a>另請參閱  
 [設定記錄](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)