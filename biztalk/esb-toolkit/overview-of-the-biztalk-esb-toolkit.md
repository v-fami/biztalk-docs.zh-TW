---
title: 在 BizTalk Server 中的 ESB 工具組的概觀 |Microsoft Docs
description: ESB 工具組和它會在 BizTalk Server 中的說明
caps.latest.revision: 6
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: mandia
ms.openlocfilehash: 404e93739d45cbca0235990dc7d2014bf38e0a84
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008783"
---
# <a name="what-is-the-biztalk-esb-toolkit"></a>什麼是 BizTalk ESB 工具組

## <a name="overview"></a>概觀
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk server 功能，以支援鬆散偶合的傳訊架構。 大部分的開發人員熟悉程式碼導向、 程序，或物件導向的開發架構。 不過，當開始來開發 BizTalk 解決方案時，開發人員會嘗試尋找 BizTalk Server 的訊息導向功能。  
  
 BizTalk Server 包含功能強大的發佈/訂閱機制的運作方式是建立並填入訂用帳戶。 當新的訊息抵達 BizTalk Message Box 資料庫中時，訊息代理程式會識別訂閱者，並將訊息傳送至任何有訂用帳戶的端點。 訂用帳戶可以建立數種方式，包括繫結至接收埠，讓等待的訊息，或建立傳送埠與篩選條件，符合的屬性 （例如類型、 接收訊息的相互關聯的接收的協調流程點或路由傳送的屬性的值）。  
  
 藉此有效率且可調整的方法，BizTalk Server 可讓開發人員若要建立一系列的不連續的子處理序，定義其引動過程，觸發程序，而不必擔心有關順序的訊息類型。 處理程序起始訊息到達的訊息; 上執行其處理它會處理訊息之後，它可以提供這個或另一個訊息至 Messagebox 資料庫，這反而可能會啟動一個以上的子處理序。  
  
 Microsoft 會提供所需的建置完整的服務導向基礎結構，包括 Windows Server、.NET Framework，以及 BizTalk Server 的主要建置組塊。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]因為它提供的最常見的 ESB 服務，包括下列的基礎，根據 BizTalk Server:  
  
-   訊息路由  
  
-   訊息驗證  
  
-   訊息轉換  
  
-   連線的可延伸的配接器架構  
  
-   服務協調流程  
  
-   商務規則引擎  
  
-   商務活動監控  
  
-   Web 服務和 WS-* 整合 （WCF 配接器）  

## <a name="core-capabilities"></a>核心功能  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 提供各種新功能，著重於建置強固、 連結、 服務導向應用程式的功能。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]視為個別可以連線的工作單位中的 BizTalk Server 元件所需，以形成鬆散結合的解決方案。 以下是一些核心功能，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供增強的 BizTalk Server 功能：  
  
- **原則導向的中繼。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
  - 它提供以路線為基礎的路由支援輕量服務組合，發行當時的訊息。 這個方法可動態探索的服務端點和中繼需求使用服務登錄或商務規則原則路由傳送的訊息。  
  
  - 針對所收到的路線為基礎的路由使用伺服器端路線動態解析和訊息後加入至訊息內容時，它會新增原則集中化的支援。 管理在中央位置的路線，可讓來自完全不會察覺的方式會路由傳送其要求的用戶端的訊息處理。  
  
  - 它會使用一個增強型的版本[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，可使用動態端點解析和轉換需求; 如此有效即可減少來自服務的取用者。  
  
- **將系統的連線。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
  -   它提供標準化 XML 訊息的命名空間的管線元件。  
  
  -   它整合了 JMS 透過 WebSphere MQ 配接器的 BizTalk Server。  
  
  -   它可協助啟用動態服務彙總、 訊息路由、 訊息驗證和訊息轉換的訊息交換模式。  
  
  -   它支援從登錄和使用 UDDI 3.0 的存放庫整合的服務端點探索。  
  
  -   它支援訊息路由透過特定業務 (LOB) 配接器使用 WCF 自訂 BizTalk 配接器的 BizTalk Server。  
  
- **管理和監視。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
  -   它提供例外狀況管理架構和工具。  
  
  -   它有助於訊息修復和重新提交使用管理入口網站中，隨附的範例應用程式。 此 Web 應用程式特定的錯誤發生時，也支援可自訂的電子郵件通知。  
  
  -   它可讓 BizTalk Server 端點及登錄整合、 管理和發行集。  
  
  -   它提供設定版本的伺服器端路線的集中存放的庫。  
  
  -   它支援報告和分析用於 BizTalk Server 應用程式。  
  
  -   它包含商務活動監控元件，可追蹤路線服務的執行，包括開始時間、 結束時間和服務中繼序列。  
  
- **SOA 控管。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
  -   它整合了第三方 SOA 控管解決方案，包括內嵌的管理代理程式，以便讓 BizTalk Server 從 AmberPoint 和 SOA 軟體。  

> [!TIP]
> [了解 BizTalk Server](../core/understanding-biztalk-server.md)等等，傳訊引擎，提供更多詳細資料。

## <a name="get-some-help"></a>取得相關協助
取得相關協助，以及可協助其他人在[BizTalk ESB Toolkit 論壇](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409)。

## <a name="next-steps"></a>後續的步驟
[BizTalk ESB 工具組內容](contents-of-the-biztalk-esb-toolkit.md)  
