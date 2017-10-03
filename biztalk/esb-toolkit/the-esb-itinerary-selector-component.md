---
title: "ESB 路線的選取器元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cd8a85-e036-4817-9541-3fd720ca04ef
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83cdd0b2022eb7dc4ad78e5702f5c21e4c4f432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-selector-component"></a>ESB 路線的選取器元件
ESB 行程選取器元件可讓沒有 SOAP 標頭來選取適當的伺服器端路線的解析程式的說明訊息通過 ESB 行程的內送訊息。 元件也用於使用 SOAP 標頭定義的名稱和版本的路線，用戶端要求的訊息。  
  
## <a name="installation"></a>安裝  
 自動安裝 ESB 核心安裝**ItinerarySelector**元件的 BizTalk Server 管線元件資料夾中。  
  
## <a name="how-it-works"></a>運作方式  
 ESB 行程選取器元件會接收管線中只可位於 Microsoft BizTalk 管線元件。 元件選取用於伺服器端行程中處理訊息。 當訊息通過接收管線中的元件，元件會讀取其組態，並使用**ResolverConnectionString**呼叫正確的解析程式來查閱適當路線時要使用的屬性處理訊息。 行程選取器元件，然後執行路線管線元件來驗證訊息和升級的屬性以確保訊息會繼續到下個處理階段所需的相同步驟。  
  
## <a name="using-the-esb-itinerary-selector-component"></a>使用 ESB 路線的選取器元件  
 您可以 ESB 行程元件新增至接收管線，然後使用管線，接收位置中。 當此元件設定為 WCF 上手、 名稱和版本的路線 （如 SOAP 標頭中所表示），用戶端要求中的行程靜態解析程式會擷取從訊息內容和用來選取適當路線。  
  
## <a name="component-properties"></a>元件屬性  
 ESB 行程選取器元件會公開三個公用屬性：  
  
-   **IgnoreErrorKey**。 此屬性會定義是否，解析程式所傳回的錯誤時，如果應該處理訊息沒有路線 (當設定為**True**) 或暫止。  
  
-   **ItineraryFactKey**。 這表示，其中包含選取路線的實際 XML 解析程式所傳回之字典中索引鍵。 一般而言， **Resolver.Itinerary**，除非您使用自訂解析程式。  
  
-   **ResolverConnectionString**。 這是解析程式的連接字串，包含名稱 / 值組的解析程式可以用來選取和 （或） 查詢的路線。