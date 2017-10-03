---
title: "在 BizTalk Server ESB toolkit 的概觀 |Microsoft 文件"
description: "ESB 工具組，以及它沒有 BizTalk Server 中的說明"
caps.latest.revision: "6"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: mandia
ms.openlocfilehash: 9ce0bbe3710530a63127701447db87b0a3135b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-biztalk-esb-toolkit"></a>什麼是 BizTalk ESB Toolkit

## <a name="overview"></a>概觀
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 以支援鬆散偶合的傳訊架構的功能。 大部分的開發人員皆熟悉程式碼導向，程序，或物件導向的開發架構。 不過，當開始開發 BizTalk 解決方案時，開發人員通常會忽略了訊息導向的 BizTalk Server 功能。  
  
 BizTalk Server 包含的運作方式是建立及填入訂用帳戶的功能強大的發佈/訂閱機制。 當新的訊息抵達 BizTalk Messagebox 資料庫中時，訊息代理程式識別 「 訂閱者 」，並將訊息傳送至擁有訂用帳戶的任何端點。 有數種，包括繫結至接收埠，讓等候訊息時，或建立傳送埠篩選條件符合的屬性 （例如型別，接收訊息的相互關聯的接收的協調流程可以建立訂閱點或路由屬性的值）。  
  
 藉由提供這個有效率且可延展的方法，BizTalk Server 可讓開發人員建立一系列的不連續的子處理序，請定義觸發其引動過程，和不必擔心序列訊息的型別。 處理程序起始訊息到達的訊息; 上執行其處理它會處理訊息之後，它可以將這個或其他訊息傳遞至 Messagebox 資料庫，其中，可能會啟用一個以上的子處理序。  
  
 Microsoft 提供索引鍵所需的建置完整 Service-Oriented 基礎結構，包括 Windows Server、.NET Framework 和 BizTalk Server 的建置組塊。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]因為它提供最常見的 ESB 服務，包括下列的基礎，根據 BizTalk Server:  
  
-   訊息路由  
  
-   訊息驗證  
  
-   訊息轉換  
  
-   連線的可延伸的配接器架構  
  
-   服務協調流程  
  
-   商務規則引擎  
  
-   商務活動監控  
  
-   Web 服務和 WS-* 整合 （WCF 配接器）  

## <a name="core-capabilities"></a>核心功能  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 提供的新功能，專注於建置穩固、 連線、 服務導向應用程式範圍的功能。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]視為個別的可以連接的工作單位中的 BizTalk Server 元件所需，形成鬆散結合的解決方案。 以下是一些核心功能，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供增強的 BizTalk Server 功能：  
  
-   **原則導向中繼。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
    -   它提供行程為基礎的路由支援在發行訊息時的輕量級服務組合。 這個方法可讓您動態探索的服務端點和使用服務登錄或商務規則原則路由傳送的訊息中繼需求。  
  
    -   它會加入支援原則集中化行程為基礎的路由使用伺服器端旅，能夠動態解析並加入至訊息內容的訊息之後收到。 管理儲存在集中位置的行程，可讓來自完全不會察覺的方式會路由傳送其要求的用戶端的訊息處理。  
  
    -   它會使用一個增強型的版本[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，可讓動態解析的端點和轉換的需求; 這有效地以減少從服務取用者。  
  
-   **系統的連線。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
    -   它提供標準化 XML 訊息的命名空間的管線元件。  
  
    -   它可以整合與 JMS 透過 WebSphere MQ 配接器的 BizTalk Server。  
  
    -   它能啟用動態服務彙總、 訊息路由、 訊息驗證和訊息轉換的訊息交換模式。  
  
    -   它支援從登錄和使用 UDDI 3.0 的儲存機制整合的服務端點探索。  
  
    -   它支援透過 Wcf-custom BizTalk 配接器的 BizTalk Server 的特定業務 (LOB) 配接器透過訊息路由。  
  
-   **管理和監視。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
    -   它提供例外狀況管理架構和工具。  
  
    -   它有助於進行訊息修復和重新送出使用管理入口網站中，隨附的範例應用程式。 此 Web 應用程式特定錯誤發生時，也支援可自訂的電子郵件通知。  
  
    -   它可讓 BizTalk Server 端點和登錄的整合、 管理和發行集。  
  
    -   它會提供已建立版本的伺服器端旅的集中式儲存機制。  
  
    -   它支援報告和分析 BizTalk Server 應用程式。  
  
    -   它包含商務活動監控元件，可追蹤路線服務執行，包括開始時間、 結束時間，以及服務的中繼順序。  
  
-   **SOA 控管。** [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：  
  
    -   它與第三方 SOA 控管解決方案，包括內嵌的管理代理程式從 AmberPoint 軟 SOA BizTalk Server 的整合。  

> [!TIP]
> [了解 BizTalk Server](../core/understanding-biztalk-server.md)傳訊引擎，以及其他更多資訊提供更多詳細資料。

## <a name="get-some-help"></a>取得相關協助
取得相關協助，並幫助其他人在[BizTalk ESB Toolkit 論壇](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409)。

## <a name="next-steps"></a>後續的步驟
[BizTalk ESB 工具組的內容](contents-of-the-biztalk-esb-toolkit.md)  
