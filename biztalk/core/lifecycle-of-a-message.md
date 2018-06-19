---
title: 訊息的生命週期 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, orchestrations
- messages, host instances
- messages, receive locations
- send ports, about send ports
- processing, messages
- messages, processing
- host instances, about host instances
- receive locations, about receive locations
- hosts, about hosts
- messages, lifecycle
- MessageBox database, about MessageBox database
- receive ports, about receive ports
- send port groups, about send port groups
- messages, hosts
- messages, send port groups
- messages, receive ports
- orchestrations, about orchestrations
- messages, send ports
ms.assetid: d2374f86-9b5f-404f-ba7b-9cab69873fa8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e05aca3ec819fb8615552c5ed57114032d7ea60b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262822"
---
# <a name="lifecycle-of-a-message"></a>訊息的生命週期
下圖提供從傳訊觀點來看的 BizTalk Server 架構之概要簡介。  
  
 ![BizTalk Server 傳訊架構](../core/media/arch-messaging-01.gif "arch_messaging_01")  
  
 在此簡化的檢視中，訊息是透過指定接收埠所定義的接收位置來接收。 此訊息是由接收位置所處理，然後發佈到 MessageBox 資料庫，這是 BizTalk Server 的主要保存與路由機制。 MessageBox 會評估作用中的訂閱，並將訊息路由至具有符合訂閱的協調流程與傳送埠。 協調流程可能會透過 MessageBox 處理訊息並將訊息發佈到傳送埠，在此傳送埠上會將訊息推出至其最終目的地。  
  
 下列是 BizTalk Server 訊息處理所需的主要元件。  
  
## <a name="receive-ports-and-receive-locations"></a>接收埠與接收位置  
 A*接收埠*是集合的一個或多個接收到 BizTalk Server 定義特定的進入點的位置。 A*接收位置*是單一的端點 (URL) 的組態來接收訊息。 此位置包含接收配接器與接收管線的組態資訊。 *配接器*負責接收訊息的傳輸與通訊部分。 像這樣的範例有 FILE 配接器與 SOAP 配接器，每一個配接器都從不同類型的來源接收訊息。 接收管線負責準備要發佈到 MessageBox 的訊息。 A*管線*是一系列的順序，每個提供特定處理的訊息，例如解密/加密、 剖析或驗證來執行的元件。 如需管線的詳細資訊，接收埠和接收位置，請參閱[成品](../core/artifacts.md)。  
  
## <a name="send-ports-and-send-port-groups"></a>傳送埠與傳送埠群組  
 A*傳送埠*是傳送管線和傳送配接器的組合。 傳送埠群組是傳送埠的集合，與電子郵件通訊群組清單的運作方式非常相似。 傳送到傳送埠群組的訊息將會傳送到該群組的所有傳送埠。 傳送管線是用來準備將源自 BizTalk Server 的訊息傳輸到另一個服務。 傳送配接器負責使用特定通訊協定 (如 SOAP 或 FTP) 來實際傳送訊息。 如需有關傳送埠與傳送埠群組的詳細資訊，請參閱[成品](../core/artifacts.md)。  
  
## <a name="orchestrations"></a>協調流程  
 協調流程可以透過 MessageBox 訂閱 (接收) 和發佈 (傳送) 訊息。 此外，協調流程可以建構新的訊息。 我們已經討論過藉由使用訂閱與路由機制來接收訊息。 若已為協調流程填入訂閱，則會啟動新的執行個體並傳送訊息，或者，在執行個體訂閱的狀況下，若有需要，執行個體會解除凍結，然後會傳送訊息。 當訊息從協調流程傳送時，會以訊息到達接收位置的相同方式來將它們發佈至 MessageBox，並將適當的屬性插入資料庫以供路由使用。 如需協調流程的詳細資訊，請參閱[成品](../core/artifacts.md)。  
  
## <a name="messagebox-database"></a>MessageBox 資料庫  
 BizTalk Server 中發佈/訂閱引擎的核心為 MessageBox 資料庫。 MessageBox 是由兩個元件所組成：一或多個 Microsoft SQL Server 資料庫以及訊息代理程式。 SQL Server 資料庫為許多項目提供持續的存放區，包括訊息、訊息屬性、訂閱、協調流程狀態、追蹤資料以及要路由的主控件佇列。 如需 MessageBox 資料庫的詳細資訊，請參閱[MessageBox 資料庫](../core/the-messagebox-database.md)。  
  
## <a name="hosts-and-host-instances"></a>主控件與主控件執行個體  
 A*主機*是執行 BizTalk Server 成品，例如 Microsoft Windows 處理序的邏輯表示法傳送埠和協調流程。 A*主控件執行個體*是特定伺服器上的主機的實體表示法。 主控件可以是內含式主控件，這表示它是由 BizTalk Server 所擁有和管理，或者是外掛式主控件，這表示 BizTalk Server 程式碼是在不受 BizTalk Server 控制的程序中執行。 外掛式主控件最好的範例就是 Internet Information Services (IIS)，它裝載 HTTP 與 SOAP 配接器的接收功能。 主控件是為整個 BizTalk Server 群組所定義；是共用組態、MessageBox、連接埠等等的 BizTalk Server 集合。 如需主控件和主控件執行個體的詳細資訊，請參閱[實體](../core/entities.md)。  
  
## <a name="saving-a-message-body"></a>儲存訊息內文  
 有三種方法可以儲存訊息內文。  
  
### <a name="from-the-admin-mmc-group-hub-page-queries"></a>從 [管理] MMC 群組中樞頁面查詢  
 此方法僅適用於 MessageBox 資料庫中的訊息。  
  
-   檢視服務執行個體。  
  
-   開啟**服務執行個體詳細資料** 對話方塊。  
  
-   按一下**訊息索引標籤**若要檢視與此執行個體相關聯的訊息清單。  
  
-   請以滑鼠右鍵按一下訊息，然後按一下**儲存**。  
  
     -或-  
  
-   按兩下要開啟中的訊息**訊息檢視器**，然後按一下**儲存**。  
  
### <a name="from-the-operations-om"></a>從作業 OM  
  
-   使用**GetInstance**擷取服務執行個體物件。  
  
-   使用**Instance.Messages []** 列舉服務執行個體目前參考的所有訊息。  
  
-   訊息物件上使用方法，例如**Message.BodyPart []** 和**Message.Context []** 存取並儲存它。  
  
### <a name="from-the-dta"></a>從 DTA  
  
-   從使用 DTA 擷取訊息**GetTrackedInstance**和**GetTrackedmessage** API 呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段架構](../core/runtime-architecture.md)