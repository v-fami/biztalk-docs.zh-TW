---
title: 以路線為基礎的路由 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28028721-798c-4302-a532-d863ed8ea88b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13be8ab9078a2c12e110c5d80b65b2930d805952
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970879"
---
# <a name="itinerary-based-routing"></a>以路線為基礎的路由
核心功能的其中一個[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是佈建的路線為基礎的路由，來簡化開發企業級傳訊應用程式，並降低成本的維護大量的靜態傳送埠和接收位置。  
  
 路線是由執行的服務清單 （其中可以包含路由、 轉換和自訂的服務） 和解決每項服務的執行時所需的中繼資料所需的組態資訊所組成。 例如，一個階段的路線可能路由的服務;此服務相關聯的解決方法指示可能指示來執行通用描述、 探索與整合 (UDDI) 或商務規則引擎 (BRE) 查閱特定的目標端點，它會將路由的相關資訊的服務訊息。  
  
 路線可以附加至輸入訊息，以下列方式：  
  
- 用戶端提交的訊息不包含任何行程相關的資料。 接收管線會解析、 擷取，並會附加適當的路線，根據訊息內容或內容。  
  
- 用戶端所提交的郵件可以包含 SOAP 標頭，以定義路線的參考資料，其中包含路線的名稱和版本，以及商務活動監控 (BAM) 追蹤的唯一識別碼。 接收管線會評估這項資訊，並從 ESBItineraryDb 資料庫擷取適當的路線。  
  
- 用戶端提交的訊息可以有路線 SOAP 標頭，包含路線的整個內容。 這項設計不建議，並應僅用於測試目的。  
  
  路線解析用於輸入訊息之後，接收管線會升級至訊息內容，因此可用的屬性來存取此訊息會訂閱任何 Microsoft BizTalk Server 元件的路線資料。 BizTalk Server 元件可以取得目前的路線步驟的詳細資料，完成必要的處理，及/或前進至下一個步驟的路線。 這將導致下一個服務來處理訊息，路線根據發行-訂閱的 BizTalk Server 的功能。  
  
  ESB 動態解析機制、 轉換、 路線的處理和訊息建立的相關資訊，請參閱[重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)。