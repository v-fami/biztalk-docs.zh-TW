---
title: BizTalk Server 傳訊引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0c8d3e6-953d-4a04-adfc-b77ef7173464
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f8e0f4fa694699e2dfbc499b6f2fd3440656935
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279262"
---
# <a name="the-biztalk-server-messaging-engine"></a>BizTalk Server 傳訊引擎
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳訊引擎可以讓使用者建立跨越多個應用程式藉由提供兩個主要動作的商務程序：  
  
-   一個是可指定並實作驅動商務程序的邏輯  
  
-   一個是在商務程序使用的應用程式間通訊的機制  
  
 下圖說明可解決這兩個問題的引擎主要元件。  
  
 ![](../core/media/understandingbts-04-engine4.gif "UnderstandingBTS_04_Engine4")  
  
 如圖所示，透過接收到訊息**接收配接器**。 不同的配接器提供不同的通訊機制，如此訊息可以透過存取 Web 服務、從檔案讀取或以其他方法取得。 訊息接著會處理透過**接收管線**。 此管線可以包含各種元件，執行像是將訊息從原生格式轉換成 XML 文件，以及驗證其數位簽章等等的工作。 然後訊息傳遞到呼叫資料庫**MessageBox**，這使用 Microsoft SQL Server 來實作。  
  
 驅動商務程序的邏輯會實作為一或多個**協調流程**，其中每個可執行程式碼所組成。 但這些協調流程不是使用 C# 這類語言撰寫程式碼所建立的。 而是商務分析師或 (更可能是) 開發人員使用適當的工具，以圖形化方式組織已定義的圖形組以表示條件、迴圈及其他行為。 協調流程可以選擇性地使用**商務規則引擎**以提供更簡單且更輕鬆地修改方法以表達複雜的商務程序中的規則集。  
  
 每個協調流程建立**訂閱**來指示它要接收的訊息類型。 當適當的訊息送達 MessageBox 時，就被分派到它的目標協調流程，然後進行商務程序需要的動作。 此處理的結果通常是另外一個訊息，它是由協調流程產生並儲存在 MessageBox 中。 此訊息，請依次處理**傳送管線**，這可能會將它轉換所使用的內部 XML 格式從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]其目的地所需的格式，來新增 數位簽章，以及其他等等。 然後會將訊息傳出使用**傳送配接器**，使用適當的機制與此訊息目的地應用程式通訊。  
  
 完整**方案**上建置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎可以包含不同的部分 （有時稱為 「 成品 」）： 協調流程、 管線、 訊息結構描述，以及更多。 這些部分或成品可以當作一個單位，稱為**BizTalk 應用程式**。 BizTalk 應用程式會將解決方案所需的所有部分包裝為一個邏輯單位，讓它成為管理及部署的基礎概念。  
  
 不同類型的人執行不同的功能使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎。 A**商務分析師**，例如，可能會定義規則和商務程序的行為。 商務分析師也會判斷商務程序的流程、定義傳送到每個應用程式的訊息及商務文件如何互相對應。 商務分析師定義此程序之後,**開發人員**可以建立 BizTalk 應用程式實作它。 這包括為將使用的商務文件定義 XML 結構描述、指定它們之間的詳細對應，以及建立必要的協調流程來實作程序等等的工作。 **管理員**也扮演重要角色設定這些部分間的通訊、 適當調整的方法，在部署 BizTalk 應用程式，並執行其他工作。 這三個角色，商務分析師、 開發人員和系統管理員，建立和維護所需[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [系統連線](../core/connecting-systems.md)  
  
-   [定義商務程序](../core/defining-business-processes.md)  
  
-   [管理和監視](../core/management-and-monitoring.md)  
  
-   [企業單一登入](../core/enterprise-single-sign-on-sso.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 架構](../core/biztalk-server-architecture.md)   
 [執行階段架構](../core/runtime-architecture.md)