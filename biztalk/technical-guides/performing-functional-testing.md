---
title: "執行功能測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b9c8c95-5a25-4255-a4c2-e26c67b7a620
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17c2701d6aa90393b8839bafc933bea2fba5746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performing-functional-testing"></a>執行功能測試
若要測試特定的端對端案例或指定的使用案例特定的 BizTalk 應用程式的內容中使用的功能測試。 功能測試應該涵蓋所有可能的途徑給定的狀況中，包括失敗路徑。 應該評估失敗的路徑，以確保應用程式適當地處理失敗的狀況。  
  
 應叫用 （例如協調流程、 自訂管線元件，以及自訂組件） 的所有成品，並透過這些物件的所有程式碼分支應該經過測試，以及。 應該執行訊息的所有可能組合，以確保訊息正確地通過系統。 也應該測試無效的訊息，請確定應用程式中發生錯誤時的預期方式會做出反應，及測試包含協調流程和自訂元件的所有例外狀況區塊中的程式碼。  
  
## <a name="automating-functional-testing"></a>自動化功能測試  
 您應該自動化功能測試，使它快，以便可以重複，且，好讓它將會避免的人為錯誤。 **BizUnit**是宣告式的測試架構，可讓開發人員快速設計測試案例所設計。 事實上，XML 組態檔稱為 BizUnit XML 測試案例即已足夠定義應該如何執行測試。 若要執行測試您可以建立您自己自訂的驅動程式或更輕鬆地利用**Visual Studio 單元測試**或**NUnit**裝載和執行測試。  
  
 每個 XML BizUnit 測試案例包含三個階段： **TestSetup**， **TestExecution**，和**TestCleanup**。 每一個階段可以包含零或多個測試步驟。 每個步驟代表工作單位，並實作為.NET 類別，設計用來執行特定工作。 這個架構會提供一組豐富的元件。 如果您需要了解特定的元件，以符合特定需求，不過，您可以撰寫自己的自訂測試步驟的元件。 如需有關這些工具的詳細資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 測試操作整備](../technical-guides/checklist-testing-operational-readiness.md)