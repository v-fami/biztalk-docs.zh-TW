---
title: 在 SQL 中使用 BizTalk Server 接收查詢通知之後接收位置解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e70fa4c2-d81b-4eb0-a23d-871b64c881e6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f7bf6026ebd9bf506dd84b1a8c309760c38f8d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975455"
---
# <a name="receive-query-notifications-after-a-receive-location-breakdown-in-sql-using-biztalk-server"></a>在 SQL 中使用 BizTalk Server 接收查詢通知之後接收位置細目
假設您有 EMPLOYEE 資料表受到變更時，接收資料庫變更通知訊息的 BizTalk 應用程式的位置。 如果接收位置設定為一部分的 BizTalk 應用程式細分，同時新增到員工資料表的記錄，您不會收到通知的最近新增的記錄。 您也不會知道接收位置再次可用時。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開繫結屬性， **NotifyOnListenerStart**，您可以設定為會收到通知，接收位置已復原。 您可以指定下列值**NotifyOnListenerStart**繫結屬性：  
  
- 將此屬性設定為 **，則為 True**，以接收通知，通知的接收位置的話，只要接收位置復原。  
  
- 將此屬性設定為**False**，而不會收到通知，通知的接收位置已復原，接收位置復原後。  
  
  預設值是 **，則為 True**。  
  
## <a name="configuring-the-sql-adapter-behavior"></a>設定 SQL 配接器行為  
 針對任一種方法，您不需要產生中繼資料時，或在設定 BizTalk 應用程式時，執行任何特定的工作。 您只需要設定**NotifyOnListenerStart**屬性繫結據以 Wcf-custom 或 WCF SQL 接收位置。 若要建立的 BizTalk 應用程式，您必須執行同一組工作中所述[接收查詢通知以累加方式從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)。 不過，設定 BizTalk 應用程式使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以嘗試變更的值**NotifyOnListenerStart**屬性繫結，並查看兩個組態的差異。  
  
 下圖示範如何在收到通知後根據的值**NotifyOnListenerStart**繫結屬性。  
  
 ![設定 SQL 配接器的通知](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")  
  
 請注意，在第一個案例中，當**NotifyOnListenerStart**設為 **，則為 true**並記錄插入資料庫資料表向下接收位置時，配接器只會傳送給您當接收位置恢復運作時，就會通知訊息。 配接器不會執行任何作業來處理已插入向下接收位置時的記錄。 配接器用戶端必須實作相關的邏輯來處理已插入向下接收位置時記錄其應用程式中。  
  
## <a name="see-also"></a>另請參閱  
 [接收使用 BizTalk Server 的 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)