---
title: 使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21cf4875-1c04-41cf-98f5-d1307987ca55
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be084ca9e0a90813a541563bf6f600ea277aec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223958"
---
# <a name="receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk-server"></a><span data-ttu-id="67b90-102">使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠</span><span class="sxs-lookup"><span data-stu-id="67b90-102">Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server</span></span>
<span data-ttu-id="67b90-103">假設您要建立 BizTalk 應用程式，其中包含兩個輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="67b90-103">Consider a scenario where you want to create a BizTalk application that includes two polling operations.</span></span> <span data-ttu-id="67b90-104">每個輪詢作業就會以不同的資料表，員工和客戶，從相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="67b90-104">Each polling operation polls separate tables, Employee and Customer, from the same database.</span></span> <span data-ttu-id="67b90-105">當您部署中的這類的應用程式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須建立兩個接收埠。</span><span class="sxs-lookup"><span data-stu-id="67b90-105">When you deploy such an application in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you will need to create two receive ports.</span></span> <span data-ttu-id="67b90-106">連線 URI 為每個接收埠將會：</span><span class="sxs-lookup"><span data-stu-id="67b90-106">The connection URI for each receive port will be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>  
```  
  
 <span data-ttu-id="67b90-107">由於兩種接收連接埠會接收來自相同的伺服器上相同的資料庫的輪詢訊息，兩者的連線 URI 將會相同。</span><span class="sxs-lookup"><span data-stu-id="67b90-107">Because both receive ports are receiving polling messages from the same database on the same server, the connection URI for both will be the same.</span></span> <span data-ttu-id="67b90-108">不過，BizTalk 應用程式不能有兩個接收埠具有相同的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="67b90-108">However, a BizTalk application cannot have two receive ports with the same connection URI.</span></span>  
  
 <span data-ttu-id="67b90-109">若要讓配接器用戶端有兩個 BizTalk 應用程式中收到輪詢相同的資料庫 （或甚至在資料庫中的相同資料表） 的連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]提供連接屬性， **InboundID**。</span><span class="sxs-lookup"><span data-stu-id="67b90-109">To enable adapter clients to have two receive ports that poll the same database (or even the same table in a database) in a BizTalk application, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides a connection property, **InboundID**.</span></span> <span data-ttu-id="67b90-110">您可以指定任何連接屬性的值。</span><span class="sxs-lookup"><span data-stu-id="67b90-110">You can specify any value for this connection property.</span></span> <span data-ttu-id="67b90-111">藉由加入的輸入的識別碼，連線 URI 成為唯一。</span><span class="sxs-lookup"><span data-stu-id="67b90-111">By adding the inbound ID, a connection URI becomes unique.</span></span> <span data-ttu-id="67b90-112">例如：</span><span class="sxs-lookup"><span data-stu-id="67b90-112">For example:</span></span>  
  
 <span data-ttu-id="67b90-113">接收 Employee 資料表的輪詢訊息的連接埠的連線 URI 可以是：</span><span class="sxs-lookup"><span data-stu-id="67b90-113">The connection URI for the port receiving polling messages for the Employee table can be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Employee  
```  
  
 <span data-ttu-id="67b90-114">同樣地，接收 Customer 資料表中的輪詢訊息的連接埠的連線 URI 可以是：</span><span class="sxs-lookup"><span data-stu-id="67b90-114">Similarly, the connection URI for the port receiving polling messages for the Customer table can be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Customer  
```  
  
 <span data-ttu-id="67b90-115">因為連線 Uri 成為唯一，藉由新增**InboundID**屬性，您現在可以有多個接收埠輪詢相同的資料庫或單一的 BizTalk 應用程式中的資料表。</span><span class="sxs-lookup"><span data-stu-id="67b90-115">Because the connection URIs become unique by adding the **InboundID** property, you can now have multiple receive ports polling the same database or table in a single BizTalk application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67b90-116">您可以選擇指定**InboundID**兩者的連接屬性**輪詢**和**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="67b90-116">You can choose to specify the **InboundID** connection property for both the **Polling** and **TypedPolling** operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b90-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67b90-117">See Also</span></span>  
 [<span data-ttu-id="67b90-118">與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="67b90-118">Poll SQL Server using the SQL Adapter with BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)