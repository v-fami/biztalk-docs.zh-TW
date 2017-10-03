---
title: "記錄程序的相關 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logging, about logging
- auditing, about auditing
- logging
- auditing
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07dba617358d6ad451c53eeb75dbe5d1986f9066
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-logging-process"></a>關於記錄處理程序
您的應用程式處理重要，因為時間敏感資料和貨幣資料，稽核會變成應用程式很重要的一部分。 若要啟用企業層級的管理性和可用性， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]依賴下列共用的執行的階段和管理元件：  
  
-   **記錄**： 來收集和傳送的所有記錄事件中指定之資料庫的 managed 方法  
  
-   **事件監視及服務偵錯**： 若要設定記錄行為，以及調查/管理系統管理員和其他 IT 專業人員所收集的資訊  
  
 使用增強稽核功能[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]，您可以最佳化您的營運效率、 安全性和效能，以確保相容性與 HL7 法規。  
  
## <a name="types-of-data"></a>資料類型  
 本主題說明不同類型的使用記錄功能，以及這項資料的儲存位置的記錄資料：  
  
-   設定資料： 記錄組態資料會儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫），並包含稽核資訊和稽核資料的 SQL ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件檢視器，集中式資料庫 WMI) 的位置。  
  
-   封存資料： SQL 記錄檔中的事件記錄檔資料表會儲存 '記錄' 的資料。  
  
## <a name="how-logging-works"></a>記錄的運作方式  
 本主題說明三種事件軟體記錄檔，以及三個位置，您可以在其中儲存記錄的資料類型。  
  
|元件|目的|  
|---------------|-------------|  
|組態編輯器|若要指定儲存記錄資料的位置。 BTAHL7 支援記錄功能，下列的任何組合： 事件檢視器、 WMI 和 SQL Server 記錄。|  
|事件 Broker|要接收記錄事件的其他元件所引發並將其根據記錄組態資料記錄。|  
|記錄應用程式開發介面|記錄所有 BTAHL7 組件所呼叫介面。|  
  
### <a name="types-of-logging"></a>類型的記錄  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄錯誤的三種：  
  
-   參考事件、 服務啟動或停止或事件失敗。  
  
-   警告事件，例如非重大錯誤和警告中的[!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件記錄檔。 例如，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為資料驗證失敗。  
  
-   在元件中的嚴重失敗的錯誤事件。 例如，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為剖析器發生失敗。  
  
 系統可以記錄[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]事件加入下列可設定的位置：  
  
-   [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件檢視器  
  
-   WMI 事件  
  
-   集中式的資料庫 （SQL 記錄資料庫）  
  
 事件 broker 接收所有[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄的事件，根據組態資訊、 將它們傳送到適當的位置。  
  
### <a name="overview-of-features"></a>功能概觀  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供記錄功能：  
  
-   統一的方式，記錄所有錯誤訊息  
  
-   集中式的儲存機制來儲存所有的事件詳細資料  
  
-   記錄訊息在離散的特定業務應用程式一致的物件模型  
  
-   組合的記錄和追蹤，以協助的系統管理員將相互關聯的文件已記錄錯誤  
  
## <a name="event-log-data"></a>事件記錄檔資料  
 本主題描述的格式和內容的事件記錄檔資料。  
  
 下表顯示為夥伴的一般記錄的資料。  
  
|data|Description|  
|----------|-----------------|  
|LogData|資料記錄|  
|CategoryNumber|類別目錄數目|  
|EntryType|事件的類型|  
|EventId|事件識別碼|  
|MachineName|電腦名稱|  
|訊息|訊息詳細資料|  
|Source|建立、 更新、 讀取、 刪除、 部署，或將資料封存|  
|TimeGenerated|成功或失敗|  
|UserName|使用者名稱|  
|MsgGuid|訊息的 GUID|  
|SvcGuid|服務 GUID|  
|作業|作業詳細資料|  
  
## <a name="see-also"></a>另請參閱  
 [設定記錄](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)