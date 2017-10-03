---
title: "使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21cf4875-1c04-41cf-98f5-d1307987ca55
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be084ca9e0a90813a541563bf6f600ea277aec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk-server"></a>使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠
假設您要建立 BizTalk 應用程式，其中包含兩個輪詢作業。 每個輪詢作業就會以不同的資料表，員工和客戶，從相同的資料庫。 當您部署中的這類的應用程式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須建立兩個接收埠。 連線 URI 為每個接收埠將會：  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>  
```  
  
 由於兩種接收連接埠會接收來自相同的伺服器上相同的資料庫的輪詢訊息，兩者的連線 URI 將會相同。 不過，BizTalk 應用程式不能有兩個接收埠具有相同的連線 URI。  
  
 若要讓配接器用戶端有兩個 BizTalk 應用程式中收到輪詢相同的資料庫 （或甚至在資料庫中的相同資料表） 的連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]提供連接屬性， **InboundID**。 您可以指定任何連接屬性的值。 藉由加入的輸入的識別碼，連線 URI 成為唯一。 例如：  
  
 接收 Employee 資料表的輪詢訊息的連接埠的連線 URI 可以是：  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Employee  
```  
  
 同樣地，接收 Customer 資料表中的輪詢訊息的連接埠的連線 URI 可以是：  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Customer  
```  
  
 因為連線 Uri 成為唯一，藉由新增**InboundID**屬性，您現在可以有多個接收埠輪詢相同的資料庫或單一的 BizTalk 應用程式中的資料表。  
  
> [!IMPORTANT]
>  您可以選擇指定**InboundID**兩者的連接屬性**輪詢**和**TypedPolling**作業。  
  
## <a name="see-also"></a>另請參閱  
 [與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)