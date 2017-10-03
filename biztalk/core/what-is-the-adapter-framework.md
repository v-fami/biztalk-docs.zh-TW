---
title: "何謂配接器架構？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd1e2fd7-4e77-49c4-839d-c2bf16b10ba2
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 648c22a52e543b24458daa73146836e1e3a5463e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-adapter-framework"></a>何謂配接器架構？
BizTalk 配接器架構提供穩定、開放的機制，讓所有的配接器都能從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳訊引擎實作或存取工作。 中描述的介面**Microsoft.BizTalk.Adapter.Framework**命名空間啟用配接器能夠提供方法來修改組態屬性頁。 這種方法也可以將服務和結構描述匯入到 BizTalk 專案中。  
  
 下圖顯示配接器和配接器架構如何共同運作，以便將應用程式連線至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 ![配接器架構](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")  
  
 下列步驟說明圖中顯示的一連串步驟：  
  
1.  資料是從接收位置接收，該位置在指定的位址聆聽特定通訊協定的訊息。 接收位置與配接器和接收管線相關聯。 您可以設定配接器和管線元件，對已預先決定通訊協定的訊息執行特定邏輯。  
  
2.  接收位置收到訊息後，便會將訊息傳送至配接器，再由配接器建立新的 BizTalk 訊息，將資料流附加到訊息 (通常在訊息的內文部分)，新增與接收資料的結束點相關的任何中繼資料，然後將該訊息提交至傳訊引擎。  
  
3.  傳訊引擎將訊息傳送到接收管線，讓資料在此轉換成 XML，並在此驗證訊息傳送者、解密訊息及驗證 XML。  
  
4.  傳訊引擎將訊息發佈至 MessageBox 資料庫。 MessageBox 是 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料表，其中包含要處理的訊息。 協調流程和傳送埠兩者都可以訂閱 MessageBox。  
  
5.  傳訊引擎根據符合訂閱者在篩選條件中設定之規格的訊息內容屬性，將訊息傳送到協調流程或傳送埠訂閱者。  
  
6.  若協調流程為訂閱者，協調流程會處理訊息並透過傳送埠將訊息傳送出去。 如果訂閱者是傳送管線，則在傳輸之前，訊息會先通過傳送管線進入傳送配接器。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用配接器架構工具](../core/using-the-adapter-framework-tools.md)  
  
-   [配接器訊息交換模式](../core/adapter-message-exchange-patterns.md)  
  
-   [配接器架構元件](../core/adapter-framework-components.md)  
  
-   [配接器裝載模型](../core/adapter-hosting-model.md)  
  
-   [配接器元件](../core/adapter-components.md)