---
title: MessageBox 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, suspended messages
- MessageBox database, messages
- MessageBox database, about MessageBox database
- MessageBox database, suspended messages
- suspended messages
- MessageBox database
- suspended messages, MessageBox database
ms.assetid: f89eb02c-1b83-4127-8a91-e78fb4a1f96e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cec97829d96aa81403a4f4457cb1aebf9c3d9522
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966375"
---
# <a name="the-messagebox-database"></a>MessageBox 資料庫
在 Microsoft BizTalk Server 中發佈/訂閱引擎的中心是 MessageBox 資料庫。 MessageBox 是由兩個元件組成：一或多個 Microsoft SQL Server 資料庫和傳訊代理程式。 SQL Server 資料庫會提供許多項目的持續性存放區，這些項目包括訊息、訊息部分、訊息屬性、訂閱、協調流程狀態、追蹤資料、路由的主控件佇列，以及其他項目。 BizTalk Server 群組可能會有一或多個 MessageBox 資料庫，可讓它發佈訊息到其中，而那些訊息的訂閱者也會從其中擷取訊息。  
  
 資料庫提供與路由訊息及完成訂閱相關的部分邏輯。 不過，訊息代理程式是封裝和抽象化資料庫元件的元件，也是 BizTalk Server 與 MessageBox 互動所使用的介面。 訊息代理程式是提供發佈訊息、訂閱訊息、擷取訊息等介面的「元件物件模型」(COM) 元件。 這個介面是其他 BizTalk Server 元件 (包括配接器架構和協調流程) 用來與 MessageBox 互動的唯一機制。  
  
## <a name="the-messagebox-and-the-message"></a>MessageBox 和訊息  
 MessageBox 資料庫訂閱是一組建立的資訊和服務資訊。 建立的 (或述詞) 資訊是訊息必須符合的準則。 服務資訊是處理符合準則之訊息的方法。 這個資訊的全部都儲存在可呼叫傳訊與協調流程引擎的一組資料表中。  
  
 當 BizTalk Server 接收訊息時，它會在管線中處理訊息，並將訊息存放在 MessageBox 資料庫。 內送訊息有內容。 訊息內容是一組與訊息相關的屬性。 訊息內容屬性有三種類型：  
  
- 簡單寫入屬性  
  
- 升級屬性  
  
- 述詞屬性  
  
  升級與述詞訊息屬性會指出訂閱此訊息的商務程序，以及商務程序是否有接收訊息所需的權限。  
  
  若商務程序訂閱訊息，MessageBox 資料庫會將訊息傳送到商務程序。 當商務程序接收訊息時，它會在可用的主控件執行個體上處理訊息。 處理訊息之後，若商務程序訂閱一個管線或傳送埠，則商務程序會傳送一個回傳訊息到 MessageBox 資料庫。  
  
  對於每個 BizTalk 主控件，相關的 MessageBox 會有一個工作佇列和一個擱置的佇列。 此外，每個 MessageBox 資料庫都會包含一組靜態狀態、動態狀態和執行個體狀態的資料表。 如需 BizTalk 主控件的詳細資訊，請參閱[實體](../core/entities.md)。  
  
> [!IMPORTANT]
>  若主控件變成無法使用 (例如，從該主控件接收訊息的 MessageBox 資料庫變成無法使用)，則所有其他 MessageBox 資料庫都會變成無法使用。  
  
 當您執行「組態精靈」時，就會建立第一個 MessageBox 資料庫。 設定的 MessageBox 資料庫會變成主要 MessageBox 資料庫。 主要 MessageBox 資料庫會評估訂閱，並將其路由至 BizTalk Server 環境中的所有其他 MessageBox 資料庫。 如需改善主要 MessageBox 資料庫的效能資訊，請參閱[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)。  
  
> [!IMPORTANT]
>  您必須使用 SQL Server 叢集，來提供 MessageBox 資料庫的容錯移轉保護。  
  
## <a name="suspended-messages-in-the-messagebox-database"></a>MessageBox 資料庫中擱置的訊息  
 BizTalk Server 會儲存與 MessageBox 資料庫中擱置管線相關的訊息。 若管線中發生容錯轉移，BizTalk Server 會擱置訊息的執行個體。 擱置的服務執行個體有兩種類型：  
  
- 您可以繼續的擱置執行個體。  
  
- 您無法繼續的擱置執行個體。 例如，若一個執行個體已損毀。  
  
  視擱置的原因而定，您或許可以繼續 BizTalk Server 擱置的服務，例如，若協調流程叫用「擱置」圖形，或是傳輸無法遞送訊息。BizTalk Server 不會自動移除您無法從 MessageBox 資料庫繼續的擱置執行個體。 在從擱置的佇列移除服務執行個體之前，您可以選擇將該服務執行個體儲存至磁碟。  
  
  如需備份 MessageBox 資料庫的詳細資訊，請參閱 <<c0> [ 備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [傳訊引擎](../core/the-messaging-engine.md)