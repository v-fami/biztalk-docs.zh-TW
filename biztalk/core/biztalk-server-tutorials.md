---
title: BizTalk Server 教學課程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials, getting started
- getting started, tutorials
ms.assetid: 58019f98-e91a-4705-b689-c269174d6bae
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f13a5d74d0957a208600653823e7604680296f4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232070"
---
# <a name="biztalk-server-tutorials"></a>BizTalk Server 教學課程
教學課程，了解如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。

BizTalk Server 教學課程包含簡單的實例，讓新使用者在建立已編譯、可測試的整合方案時，體驗使用不同的 BizTalk 工具。 對於進階的使用者或設計 BizTalk 方案的使用者，請參閱[商務解決方案的實例](../core/scenarios-for-business-solutions.md)。  
  
## <a name="enterprise-application-integration"></a>企業應用程式整合
  
[教學課程： 企業應用程式整合](../core/tutorial-1-enterprise-application-integration.md) 

實作接收倉儲的庫存補充要求訊息和評估要求訊息的 BizTalk 解決方案。 如果方案拒絕要求，然後會傳送拒絕訊息給倉儲。 如果方案核准要求時，會轉送至企業資源規劃 (ERP) 系統訊息。  

## <a name="create-a-hybrid-application"></a>建立混合式應用程式
[教學課程： 建立使用 BizTalk Server 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)  

設定使用 EDI，來產生通知，接收訊息，服務匯流排的端對端應用程式，然後再將資料插入 SQL。 

## <a name="invoke-a-rest-interface"></a>叫用 REST 介面
[教學課程： 叫用 REST 介面使用 BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)  

使用 Wcf-webhttp 配接器，即可使用 REST URL，並傳送回應訊息。 

## <a name="integrate-biztalk-with-salesforce"></a>將 BizTalk 與 Salesforce 的整合
[教學課程： 將與 Salesforce 整合 BizTalk Server](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)  

每當在 Salesforce 系統中建立了商機時，Northwind 會希望其在內部部署系統，例如 BizTalk Server 中，若要收到通知，讓其他下游系統可以挑選該資料，並啟動其他相關的處理序。 

## <a name="process-json-messages"></a>處理 JSON 訊息
[使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)  

設定 BizTalk 應用程式接收 JSON 訂單。 在接收管線中，JSON 解碼器元件來轉換 XML 訊息之 JSON 訊息。 然後，會使用對應將 XML 訂單轉換為 XML 發票。 傳送管線將 XML 發票轉換為 JSON 發票，使用 JSON 編碼器，並接著傳送訊息。

## <a name="edi-interface-developer"></a>EDI 介面開發人員
  [教學課程： EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md)
  
交易夥伴傳送訂單使用 ANSI X12 4010 850 交易集 （850 訊息）。 內部訂單系統的處理程序採購訂單。

身為介面開發人員負責設計 850 訊息之間的介面中，您會收到來自交易夥伴和公司內部訂單系統。 您的交易夥伴要求其每傳送一個 850 訊息都要收到功能通知 (997)。


## <a name="as2"></a>AS2  
[教學課程： AS2 教學課程](../core/tutorial-3-as2-tutorial.md)

設定接收和傳送 EDIINT/AS2 編碼訊息透過 HTTP 傳輸的解決方案。    


## <a name="do-more"></a>執行其他動作  
 若要了解有關 BizTalk Server 的概念與架構的詳細資訊，請考慮下列各項：  
  
[開始使用](../core/getting-started-with-biztalk-server.md)
  
[規劃和設計 BizTalk Server 解決方案架構](../core/plan-and-architect-your-biztalk-server-solution.md)