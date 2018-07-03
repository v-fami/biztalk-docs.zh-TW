---
title: Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e92520cf-c552-4225-abba-8e03f73ecf70
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6381e2c429763596e3aa5c1fd70619cae588b68d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991423"
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-using-biztalk-server"></a><span data-ttu-id="1cdb8-102">Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1cdb8-102">Receive Oracle E-Business Suite database change notifications using BizTalk Server</span></span>
<span data-ttu-id="1cdb8-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle E-business Suite 接收資料庫變更通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive database change notification messages from Oracle E-Business Suite.</span></span> <span data-ttu-id="1cdb8-104">您可以指定配接器用來註冊通知 Oracle E-business Suite 的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-104">You can specify a SELECT statement that the adapter uses to register for notifications with Oracle E-Business Suite.</span></span> <span data-ttu-id="1cdb8-105">結果集的 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-105">The adapter receives a notification message when the result set for the SELECT statement, registered for notification, changes.</span></span> <span data-ttu-id="1cdb8-106">如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle E-business Suite 配接器的考量](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-106">For more information about how the adapter supports notification, see [Considerations for Receiving Database Change Notifications using the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md).</span></span>  
  
 <span data-ttu-id="1cdb8-107">以下是一些您可以設定的案例[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]要從 Oracle E-business Suite 接收通知：</span><span class="sxs-lookup"><span data-stu-id="1cdb8-107">Following are some scenarios in which you can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from Oracle E-Business Suite:</span></span>  
  
- <span data-ttu-id="1cdb8-108">配接器用戶端取得 「 增量 」 通知，比方說，只有這些上次告知以來對資料庫資料表所做的變更。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-108">Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.</span></span>  
  
- <span data-ttu-id="1cdb8-109">如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置，以進行負載平衡接收通知。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-109">If a large number of rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.</span></span>  
  
  <span data-ttu-id="1cdb8-110">配接器用戶端會收到通知訊息之後，他們可以執行的收到的通知類型為基礎的特定工作。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-110">After the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received.</span></span> <span data-ttu-id="1cdb8-111">例如，BizTalk 協調流程可以設計的方式收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-111">For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1cdb8-112">針對在網路中斷期間在 Oracle 資料庫上所做的變更，將通知 Oracle 資料庫與配接器用戶端之間的網路中斷時，將不傳送給配接器用戶端，之後。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-112">If there is a network outage between the Oracle database and the adapter client, the notifications will not be sent to the adapter clients for the changes done on the Oracle database during the period of network outage, and thereafter.</span></span> <span data-ttu-id="1cdb8-113">因此，您必須使用輪詢作業，而非通知作業的重要案例。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-113">Therefore, you must use the Polling operation instead of the Notification operation for critical scenarios.</span></span>  
  
 <span data-ttu-id="1cdb8-114">在本節中的主題提供有關如何設定每個案例的配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-114">The topics in this section provide information on how to configure the adapter for each of these scenarios.</span></span> <span data-ttu-id="1cdb8-115">若要開始通知 Oracle E-business Suite 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-115">To start getting notifications from Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must specify certain binding properties.</span></span> <span data-ttu-id="1cdb8-116">如需有關繫結屬性與通知相關的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-116">For more information about the binding properties related to notifications, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="1cdb8-117">如需通知訊息的結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-117">For more information about structure of notification messages, see [Message Schemas for the Notification Operation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md).</span></span>  
  
 <span data-ttu-id="1cdb8-118">從 Oracle E-business Suite 中接收通知，請確定：</span><span class="sxs-lookup"><span data-stu-id="1cdb8-118">For receiving notifications from Oracle E-Business Suite, make sure:</span></span>  
  
-   <span data-ttu-id="1cdb8-119">您可以使用配接器連線到支援的 Oracle 資料庫版本。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-119">You use the adapter to connect to a supported Oracle database version.</span></span> <span data-ttu-id="1cdb8-120">10.2 之前的 oracle 資料庫版本不支援通知。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-120">Oracle database versions prior to 10.2 do not support notifications.</span></span>  
  
-   <span data-ttu-id="1cdb8-121">**變更通知**權限，才能接收資料庫變更通知。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-121">The **change notification** privilege is required for receiving database change notifications.</span></span>  <span data-ttu-id="1cdb8-122">若要設定此權限，連接到 Oracle 資料庫使用系統管理權限，然後輸入下列命令在 SQL 提示字元上。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-122">To configure this privilege, connect to Oracle database using administrative privileges and then type the following command on the SQL prompt.</span></span>  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   <span data-ttu-id="1cdb8-123">決定您想要用來從 Oracle 資料庫接收資料庫變更通知 ODP.NET TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-123">Decide on a TCP port you want ODP.NET to use for receiving database change notifications from Oracle database.</span></span> <span data-ttu-id="1cdb8-124">將該連接埠新增至 Windows 防火牆例外清單中。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-124">Add that port to Windows Firewall exceptions list.</span></span> <span data-ttu-id="1cdb8-125">如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-125">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span> <span data-ttu-id="1cdb8-126">您必須提供的相同連接埠號碼**NotificationPort**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-126">You must provide the same port number for the **NotificationPort** binding property.</span></span> <span data-ttu-id="1cdb8-127">如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1cdb8-127">For more information about the binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cdb8-128">本節內容</span><span class="sxs-lookup"><span data-stu-id="1cdb8-128">In This Section</span></span>  
  
-   [<span data-ttu-id="1cdb8-129">接收資料庫變更通知使用 Oracle E-business Suite 配接器的考量</span><span class="sxs-lookup"><span data-stu-id="1cdb8-129">Considerations for Receiving Database Change Notifications using the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)  
  
-   [<span data-ttu-id="1cdb8-130">若要完成 Oracle E-business Suite 中的特定工作的程序通知訊息</span><span class="sxs-lookup"><span data-stu-id="1cdb8-130">Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)  
  
-   [<span data-ttu-id="1cdb8-131">接收以累加方式使用 BizTalk Server 的 Oracle E-business Suite 變更通知</span><span class="sxs-lookup"><span data-stu-id="1cdb8-131">Receive Oracle E-Business Suite Change Notifications Incrementally Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [<span data-ttu-id="1cdb8-132">接收 Oracle E-business Suite 資料庫變更通知上多個接收位置</span><span class="sxs-lookup"><span data-stu-id="1cdb8-132">Receive Oracle E-Business Suite database Change Notifications On Multiple Receive Locations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [<span data-ttu-id="1cdb8-133">接收 Oracle E-business Suite 資料庫後的變更通知接收位置細目</span><span class="sxs-lookup"><span data-stu-id="1cdb8-133">Receive Oracle E-Business Suite Database Change Notifications After a Receive Location Breakdown</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)  
  
## <a name="see-also"></a><span data-ttu-id="1cdb8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cdb8-134">See Also</span></span>  
[<span data-ttu-id="1cdb8-135">開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器</span><span class="sxs-lookup"><span data-stu-id="1cdb8-135">Develop BizTalk applications using the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)