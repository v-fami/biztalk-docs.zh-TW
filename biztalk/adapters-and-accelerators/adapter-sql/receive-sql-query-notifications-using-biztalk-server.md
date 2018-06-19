---
title: 接收 SQL 查詢通知使用 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69444df7-f2ae-4d1a-9b49-817b437517d8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1632bde50a0daf9df22b9c1cfb7aaca8d59fbce7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223814"
---
# <a name="receive-sql-query-notifications-using-biztalk-server"></a><span data-ttu-id="c2e16-102">接收使用 BizTalk Server 的 SQL 查詢通知</span><span class="sxs-lookup"><span data-stu-id="c2e16-102">Receive SQL Query Notifications using BizTalk Server</span></span>
<span data-ttu-id="c2e16-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來接收通知訊息的 SQL Server 資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="c2e16-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notification messages for SQL Server tables or views.</span></span> <span data-ttu-id="c2e16-104">您可以指定配接器用來註冊通知的 SQL Server 的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2e16-104">You can specify a SQL statement that the adapter uses to register for notifications with SQL Server.</span></span> <span data-ttu-id="c2e16-105">在 notification 陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="c2e16-105">The notification statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="c2e16-106">查詢通知的詳細資訊，請參閱 「 使用查詢通知 」，網址[http://go.microsoft.com/fwlink/?LinkId=122159](http://go.microsoft.com/fwlink/?LinkId=122159)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-106">For more information about query notifications, see “Using Query Notifications” at  [http://go.microsoft.com/fwlink/?LinkId=122159](http://go.microsoft.com/fwlink/?LinkId=122159).</span></span> <span data-ttu-id="c2e16-107">可用於查詢通知的查詢的相關資訊，請參閱 「 建立查詢的通知 」，在[http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-107">For information about queries that can be used for query notifications, see “Creating a Query for Notification” at [http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160).</span></span>  
  
 <span data-ttu-id="c2e16-108">從 SQL Server 接收查詢通知是類似輪詢 SQL Server，但有一些主要差異。</span><span class="sxs-lookup"><span data-stu-id="c2e16-108">Receiving query notifications from SQL Server is similar to polling SQL Server, with a few key differences.</span></span> <span data-ttu-id="c2e16-109">如需差異的清單，請參閱[考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-109">For the list of differences, see [Considerations Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="c2e16-110">以下是一些案例，您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]要從 SQL Server 接收通知：</span><span class="sxs-lookup"><span data-stu-id="c2e16-110">Following are some scenarios in which you can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from SQL Server:</span></span>  
  
-   <span data-ttu-id="c2e16-111">配接器用戶端取得 「 增量 」 通知，例如，僅至資料庫資料表的最後一個通知之後進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="c2e16-111">Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.</span></span>  
  
-   <span data-ttu-id="c2e16-112">如果多個資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置的負載平衡接收通知。</span><span class="sxs-lookup"><span data-stu-id="c2e16-112">If many rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.</span></span>  
  
-   <span data-ttu-id="c2e16-113">如果配接器用戶端會在其接收通知的接收位置關閉時，配接器用戶端可以設定配接器接收通知，因為接收位置已啟動一次。</span><span class="sxs-lookup"><span data-stu-id="c2e16-113">If the receive location on which the adapter clients are receiving notifications goes down, the adapter clients can configure the adapter to receive a notification as soon as the receive location is up again.</span></span> <span data-ttu-id="c2e16-114">用戶端也必須實作的邏輯來處理，可能有已插入、 更新或刪除接收位置已關閉時記錄在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c2e16-114">The clients must also implement the logic in their application to process the records that may have been inserted, updated, or deleted while the receive location was down.</span></span>  
  
 <span data-ttu-id="c2e16-115">一旦配接器用戶端會收到通知訊息，他們可以執行特定工作，根據收到的通知類型。</span><span class="sxs-lookup"><span data-stu-id="c2e16-115">Once the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received.</span></span> <span data-ttu-id="c2e16-116">例如，BizTalk 協調流程可以設計收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作的方式。</span><span class="sxs-lookup"><span data-stu-id="c2e16-116">For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.</span></span>  
  
 <span data-ttu-id="c2e16-117">本節中的主題提供有關如何設定配接器的每個案例的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2e16-117">The topics in this section provide information about how to configure the adapter for each of these scenarios.</span></span> <span data-ttu-id="c2e16-118">若要開始使用 SQL Server 取得通知[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c2e16-118">To start getting notifications from SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must specify certain binding properties.</span></span> <span data-ttu-id="c2e16-119">如需配接器支援接收訊息的詳細資訊，請參閱[考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-119">For more information about how the adapter supports receiving messages, see [Considerations Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).</span></span> <span data-ttu-id="c2e16-120">如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-120">For more information about the binding properties related to notifications, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="c2e16-121">如需結構的通知訊息的詳細資訊，請參閱[查詢通知的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-121">For more information about the structure of notification messages, see [Message Schemas for Query Notification](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md).</span></span>  
  
 <span data-ttu-id="c2e16-122">您也必須啟用查詢通知的 SQL Server 上執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="c2e16-122">You must also perform the following tasks on SQL Server to enable query notifications.</span></span>  
  
-   <span data-ttu-id="c2e16-123">您必須啟用 SQL Server 資料庫的 Service Broker。</span><span class="sxs-lookup"><span data-stu-id="c2e16-123">You must enable Service Broker for the SQL Server database.</span></span>  
  
-   <span data-ttu-id="c2e16-124">您必須確定配接器用戶端已執行命令要求通知的必要權限。</span><span class="sxs-lookup"><span data-stu-id="c2e16-124">You must ensure that the adapter client has the necessary permissions to execute commands to request notification.</span></span>  
  
 <span data-ttu-id="c2e16-125">如需這些工作的詳細資訊，請參閱 「 啟用查詢通知 」 在[http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323)。</span><span class="sxs-lookup"><span data-stu-id="c2e16-125">For more information about these tasks, see “Enabling Query Notifications” at [http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2e16-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="c2e16-126">In This Section</span></span>  
  
-   [<span data-ttu-id="c2e16-127">考量接收查詢通知使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="c2e16-127">Considerations Receiving Query Notifications Using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="c2e16-128">處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL</span><span class="sxs-lookup"><span data-stu-id="c2e16-128">Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)  
  
-   [<span data-ttu-id="c2e16-129">使用 BizTalk Server 的 sql 查詢通知以累加的方式接收</span><span class="sxs-lookup"><span data-stu-id="c2e16-129">Receive Query Notifications Incrementally from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2e16-130">使用 BizTalk Server sql 接收查詢通知上的多個接收位置</span><span class="sxs-lookup"><span data-stu-id="c2e16-130">Receive Query Notifications On Multiple Receive Locations from SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-on-receive-locations-from-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="c2e16-131">在 SQL 中使用 BizTalk Server 接收查詢通知之後接收位置分解</span><span class="sxs-lookup"><span data-stu-id="c2e16-131">Receive Query Notifications After a Receive Location Breakdown in SQL using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2e16-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e16-132">See Also</span></span>  
[<span data-ttu-id="c2e16-133">開發 BizTalk 應用程式使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="c2e16-133">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)