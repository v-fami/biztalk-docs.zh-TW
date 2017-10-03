---
title: "OrderBroker 與 OrderManager 之間的通訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, publishing [MessageBox database]
- MessageBox database, publishing
ms.assetid: 1b77dcd2-f7a5-4013-b9a2-c06ace161792
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f438b0dfe744aae5867943f4b1493bb163994f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="communication-between-orderbroker-and-ordermanager"></a>OrderBroker 與 OrderManager 之間的通訊
訂單仲介和訂單管理員協調流程 (**OrderBroker**， **OrderManager**) 透過 MessageBox 資料庫，而不是正在直接夥伴繫結進行通訊。 這樣可確保仲介及管理員鬆散組合，如此一來，他們可以位於不同的 BizTalk 群組及不同地域位置 (如有必要)。 以這種方式分隔協調流程僅需要管理組態，而不需要變更任何程式碼。  
  
 在目前設定的解決方案中，訂單仲介會為特定訂單管理員標記訊息，然後將訊息傳送給 MessageBox。 接著，訂單管理員篩選所用的訊息，並從 MessageBox 取出這些訊息。 這種迂迴方式，亦即透過 MessageBox 進行通訊而不是直接繫結，易於將仲介和管理員移到不同的群組。  
  
 若是有不同的群組負責維護仲介及管理員，或若是這些人必須在不同的地域位置，這種設計就很容易配合這種情形。 您只需要將協調流程移到不同的 BizTalk 群組即可。 協調流程位於不同的群組後，重新連接只需建立連接埠即可。 在訂單仲介群組中，您必須建立傳送埠，其篩選條件與訂單管理員相同，但會將訊息轉寄到新的群組。 在訂單管理員群組中，則是必須建立接收埠來接收訊息並將訊息放到 MessageBox 資料庫中。  
  
 匯出應用程式可以移動應用程式，以針對仲介和管理員各建立一個 MSI 檔案。 如需有關匯出應用程式的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)