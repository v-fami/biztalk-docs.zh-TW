---
title: SQL 配接器支援哪些作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8f4099-df19-48c4-a135-1ec264af3513
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e61230ed2244bc4bb7c79f87c18879c3c83f7f95
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011271"
---
# <a name="what-operations-are-supported-by-the-sql-adapter"></a><span data-ttu-id="7301a-102">SQL 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="7301a-102">What operations are supported by the SQL adapter</span></span>
<span data-ttu-id="7301a-103">您可以使用配接器用戶端上的 SQL Server 資料庫所執行作業：</span><span class="sxs-lookup"><span data-stu-id="7301a-103">You can use the adapter clients to perform operations on the SQL Server database by:</span></span>  
  
- <span data-ttu-id="7301a-104">建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="7301a-104">Creating BizTalk projects</span></span>  
  
- <span data-ttu-id="7301a-105">使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="7301a-105">Using the WCF service model</span></span>  
  
- <span data-ttu-id="7301a-106">使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="7301a-106">Using the WCF channel model</span></span>  
  
  <span data-ttu-id="7301a-107">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會公開應用程式，可以在其上叫用並，它可以依次叫用應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="7301a-107">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="7301a-108">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="7301a-108">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="7301a-109">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="7301a-109">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="7301a-110">訊息結構和每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7301a-110">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>  
  
  <span data-ttu-id="7301a-111">本節提供有關 SQL Server 資料庫使用支援的作業的相關資訊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7301a-111">This section provides information about the operations supported on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="7301a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7301a-112">See Also</span></span>  
 [<span data-ttu-id="7301a-113">BizTalk Adapter for SQL Server 概觀</span><span class="sxs-lookup"><span data-stu-id="7301a-113">Overview of BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)