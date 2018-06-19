---
title: FileAct 配接器檔案和傳輸識別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a9aaff1-8816-42cf-b100-fedf964caaf5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5340f9ad739009ff1cb1257365ceeeb7459511a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223150"
---
# <a name="fileact-adapter-file-and-transfer-identification"></a>FileAct 配接器檔案和傳輸識別碼
A4SWIFT FileAct 配接器可讓開發人員提供在執行階段的檔案和傳輸識別特性。 這些參數包括：  
  
-   **實體檔案名稱**– 完整路徑和要讀取或寫入檔案的名稱。 這個參數絕不會傳遞，並為本機檔案處理常式元件。  
  
-   **邏輯檔案名稱**– SWIFTNet 之間傳遞從傳送至接收應用程式的應用程式的檔案名稱。 這是選擇性，而且，如果未提供，會使用不含路徑的實體檔案名稱。  
  
-   **檔案傳輸事件端點**– 基本訂閱事件中指定應用程式處理的檔案傳輸事件的名稱。 這個參數會連結至應用程式，用於接收事件報告的檔案傳輸。  
  
-   **檔案傳輸參考**– 語彙基元字串所建立和使用的傳輸的控制代碼之 FileAct 子系統本身。 FileAct 配接器是而言，這是只將此傳輸，唯一字串。  
  
-   **將金鑰傳輸**– 應用程式識別為傳輸時所指派的字串中止用途。 如果未提供應用程式，這是與檔案相關聯的 GUID。  
  
-   **傳送資料分割**– 用來與多項傳輸的字串。 如果未提供開發人員的呼叫中，這將會是"Application Name"指定當定義相關的傳送或接收位置。  
  
-   **使用者參考**– 來唯一識別傳送不可否認性的應用程式所定義的字串。 如果未提供應用程式，這會是與檔案相關聯的 GUID。  
  
-   **訊息識別碼**– 唯一定義的初始要求或回應的識別項。 這是適當的要求或回應訊息相關聯的 GUID 和傳送配接器所產生。 因此，用戶端產生要求的訊息識別碼，伺服器會回應。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)