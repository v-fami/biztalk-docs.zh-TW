---
title: 接收使用 BizTalk Server 的 Oracle 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495a29bc-72f6-4140-8160-0b917d935503
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8bd67791e56d941d58cb0b221bf7ad63bb3778f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985039"
---
# <a name="receive-oracle-database-change-notifications-using-biztalk-server"></a><span data-ttu-id="78d80-102">接收使用 BizTalk Server 的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="78d80-102">Receive Oracle Database Change Notifications Using BizTalk Server</span></span>
<span data-ttu-id="78d80-103">您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收資料庫變更通知訊息。</span><span class="sxs-lookup"><span data-stu-id="78d80-103">You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive database change notification messages from the Oracle database.</span></span> <span data-ttu-id="78d80-104">您可以指定配接器用來註冊通知與 Oracle 資料庫的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="78d80-104">You can specify a SELECT statement that the adapter uses to register for notifications with the Oracle database.</span></span> <span data-ttu-id="78d80-105">結果集的 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="78d80-105">The adapter receives a notification message when the result set for the SELECT statement, registered for notification, changes.</span></span> <span data-ttu-id="78d80-106">如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="78d80-106">For more information about how the adapter supports notification, see [Considerations for Receiving Database Change Notifications using the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).</span></span>  
  
 <span data-ttu-id="78d80-107">以下是一些您可以設定的案例[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 資料庫接收通知：</span><span class="sxs-lookup"><span data-stu-id="78d80-107">Following are some scenarios in which you can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from the Oracle database:</span></span>  
  
- <span data-ttu-id="78d80-108">配接器用戶端取得 「 增量 」 通知，比方說，只有這些上次告知以來對資料庫資料表所做的變更。</span><span class="sxs-lookup"><span data-stu-id="78d80-108">Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.</span></span>  
  
- <span data-ttu-id="78d80-109">如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置，以進行負載平衡接收通知。</span><span class="sxs-lookup"><span data-stu-id="78d80-109">If large number of rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.</span></span>  
  
  <span data-ttu-id="78d80-110">一旦配接器用戶端會收到通知訊息，他們可以執行特定工作，根據接收到通知的類型。</span><span class="sxs-lookup"><span data-stu-id="78d80-110">Once the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received.</span></span> <span data-ttu-id="78d80-111">例如，BizTalk 協調流程可以設計的方式收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作。</span><span class="sxs-lookup"><span data-stu-id="78d80-111">For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="78d80-112">針對在網路中斷期間在 Oracle 資料庫上所做的變更，將通知 Oracle 資料庫與配接器用戶端之間的網路中斷時，將不傳送給配接器用戶端，之後。</span><span class="sxs-lookup"><span data-stu-id="78d80-112">If there is a network outage between the Oracle database and the adapter client, the notifications will not be sent to the adapter clients for the changes done on the Oracle database during the period of network outage, and thereafter.</span></span> <span data-ttu-id="78d80-113">因此，您必須使用輪詢作業，而非通知作業的重要案例。</span><span class="sxs-lookup"><span data-stu-id="78d80-113">Therefore, you must use the Polling operation instead of the Notification operation for critical scenarios.</span></span>  
  
 <span data-ttu-id="78d80-114">在本節中的主題提供有關如何設定每個案例的配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="78d80-114">The topics in this section provide information on how to configure the adapter for each of these scenarios.</span></span> <span data-ttu-id="78d80-115">若要開始從 Oracle 資料庫使用中取得通知[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="78d80-115">To start getting notifications from the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must specify certain binding properties.</span></span> <span data-ttu-id="78d80-116">如需有關繫結屬性與通知相關的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="78d80-116">For more information about the binding properties related to notifications, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span> <span data-ttu-id="78d80-117">如需通知訊息的結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)。</span><span class="sxs-lookup"><span data-stu-id="78d80-117">For more information about structure of notification messages, see [Message Schemas for the Notification Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md).</span></span>  
  
 <span data-ttu-id="78d80-118">從 Oracle 資料庫中接收通知，請確定：</span><span class="sxs-lookup"><span data-stu-id="78d80-118">For receiving notifications from the Oracle database, make sure:</span></span>  
  
-   <span data-ttu-id="78d80-119">您可以使用配接器連線到 Oracle 資料庫版本 10.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="78d80-119">You use the adapter to connect to Oracle database version 10.2 or later.</span></span> <span data-ttu-id="78d80-120">10.2 之前的 oracle 資料庫版本不支援通知。</span><span class="sxs-lookup"><span data-stu-id="78d80-120">Oracle database versions prior to 10.2 do not support notifications.</span></span>  
  
-   <span data-ttu-id="78d80-121">您用來連接到 Oracle，通知的認證具有`change notification`權限。</span><span class="sxs-lookup"><span data-stu-id="78d80-121">The credentials you use to connect to Oracle for notifications has `change notification` privilege.</span></span> <span data-ttu-id="78d80-122">此權限，才能接收資料庫變更通知。</span><span class="sxs-lookup"><span data-stu-id="78d80-122">This privilege is required for receiving database change notifications.</span></span> <span data-ttu-id="78d80-123">若要這樣做，請連接到 Oracle 資料庫使用系統管理權限，然後在 SQL 提示字元上輸入下列命令。</span><span class="sxs-lookup"><span data-stu-id="78d80-123">To do so, connect to Oracle database using administrative privileges and then type the following command on the SQL prompt.</span></span>  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   <span data-ttu-id="78d80-124">決定您想要用來從 Oracle 資料庫接收資料庫變更通知 ODP.NET TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="78d80-124">Decide on a TCP port you want ODP.NET to use for receiving database change notifications from Oracle database.</span></span> <span data-ttu-id="78d80-125">將該連接埠新增至 Windows 防火牆例外清單中。</span><span class="sxs-lookup"><span data-stu-id="78d80-125">Add that port to Windows Firewall exceptions list.</span></span> <span data-ttu-id="78d80-126">如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。</span><span class="sxs-lookup"><span data-stu-id="78d80-126">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span> <span data-ttu-id="78d80-127">您必須提供的相同連接埠號碼**NotificationPort**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="78d80-127">You must provide the same port number for the **NotificationPort** binding property.</span></span> <span data-ttu-id="78d80-128">如需有關繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="78d80-128">For more information about the binding property, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78d80-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="78d80-129">In This Section</span></span>  
  
-   [<span data-ttu-id="78d80-130">接收資料庫變更通知使用 Oracle 資料庫配接器的考量</span><span class="sxs-lookup"><span data-stu-id="78d80-130">Considerations for Receiving Database Change Notifications Using the Oracle Database Adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [<span data-ttu-id="78d80-131">處理通知訊息，以使用 BizTalk Server 的 Oracle 資料庫中完成特定工作</span><span class="sxs-lookup"><span data-stu-id="78d80-131">Processing Notification Messages to Complete Specific Tasks in Oracle Database using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)  
  
-   [<span data-ttu-id="78d80-132">以累加方式使用 BizTalk Server 接收的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="78d80-132">Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [<span data-ttu-id="78d80-133">接收 Oracle 資料庫變更通知，在多個接收位置</span><span class="sxs-lookup"><span data-stu-id="78d80-133">Receiving Oracle Database Change Notifications On Multiple Receive Locations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [<span data-ttu-id="78d80-134">接收之後的 Oracle 資料庫變更通知接收位置細目</span><span class="sxs-lookup"><span data-stu-id="78d80-134">Receiving Oracle Database Change Notifications After a Receive Location Breakdown</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)  
  
## <a name="see-also"></a><span data-ttu-id="78d80-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78d80-135">See Also</span></span>  
[<span data-ttu-id="78d80-136">若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="78d80-136">Building Blocks to Develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)