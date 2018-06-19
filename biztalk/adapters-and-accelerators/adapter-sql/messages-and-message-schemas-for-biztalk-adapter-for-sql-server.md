---
title: 訊息與 BizTalk adapter for SQL Server 的訊息結構描述 |Microsoft 文件
description: BizTalk Server 的 SQL Server 配接器使用的訊息和資料類型的 XML 結構
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e95c6342-5420-4fb8-9b41-7c87d27b5b68
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b1e45f0a20500253e2ca831138a21efa24df3c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222374"
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-sql-server"></a><span data-ttu-id="c9fdc-103">訊息與 BizTalk adapter for SQL Server 的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fdc-103">Messages and Message Schemas for BizTalk Adapter for SQL Server</span></span>

## <a name="overview"></a><span data-ttu-id="c9fdc-104">概觀</span><span class="sxs-lookup"><span data-stu-id="c9fdc-104">Overview</span></span>
<span data-ttu-id="c9fdc-105">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-105">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="c9fdc-106">它會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="c9fdc-107">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="c9fdc-108">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="c9fdc-109">做為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開其作業和資料類型的中繼資料，以使用標準[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]機制。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="c9fdc-110">本主題中的各節描述 XML 訊息的結構和資料型別[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="c9fdc-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9fdc-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="c9fdc-111">In This Section</span></span>  
  
-   [<span data-ttu-id="c9fdc-112">基本的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="c9fdc-112">Basic SQL Server Data Types</span></span>](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)  
  
-   [<span data-ttu-id="c9fdc-113">訊息結構描述，插入、 更新、 刪除和選取資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="c9fdc-113">Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [<span data-ttu-id="c9fdc-114">訊息結構描述的程序和函式</span><span class="sxs-lookup"><span data-stu-id="c9fdc-114">Message Schemas for Procedures and Functions</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)  
  
-   [<span data-ttu-id="c9fdc-115">輪詢和 TypedPolling 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fdc-115">Message Schemas for the Polling and TypedPolling Operations</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)  
  
-   [<span data-ttu-id="c9fdc-116">查詢通知的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fdc-116">Message Schemas for Query Notification</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)  
  
-   [<span data-ttu-id="c9fdc-117">複合操作的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fdc-117">Message Schemas for Composite Operations</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)  
  
-   [<span data-ttu-id="c9fdc-118">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fdc-118">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)  
  
