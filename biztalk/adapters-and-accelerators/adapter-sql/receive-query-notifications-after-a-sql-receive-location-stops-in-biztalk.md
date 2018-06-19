---
title: 在 SQL 中使用 BizTalk Server 接收查詢通知之後接收位置分解 |Microsoft 文件
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
ms.openlocfilehash: 070285dbd435160af818b1077dafb35cd9e1e545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223014"
---
# <a name="receive-query-notifications-after-a-receive-location-breakdown-in-sql-using-biztalk-server"></a><span data-ttu-id="ee738-102">在 SQL 中使用 BizTalk Server 接收查詢通知之後接收位置分解</span><span class="sxs-lookup"><span data-stu-id="ee738-102">Receive query notifications After a Receive Location Breakdown in SQL using BizTalk Server</span></span>
<span data-ttu-id="ee738-103">假設您尚未員工資料表進行變更時收到資料庫變更的通知訊息的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee738-103">Consider a scenario where you have a BizTalk application that receives database change notification messages when changes are made to the EMPLOYEE table.</span></span> <span data-ttu-id="ee738-104">如果接收位置設定的一部分的 BizTalk 應用程式細分，同時新增到員工資料表的記錄，您將不會收到最近新增的記錄的通知。</span><span class="sxs-lookup"><span data-stu-id="ee738-104">If the receive location configured as part of the BizTalk application breaks down, and simultaneously records are added into the EMPLOYEE table, you will not receive notifications for the recently added records.</span></span> <span data-ttu-id="ee738-105">您也不會知道接收位置再次可用時。</span><span class="sxs-lookup"><span data-stu-id="ee738-105">You will also not know when the receive location is available again.</span></span> <span data-ttu-id="ee738-106">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開繫結屬性， **NotifyOnListenerStart**，您可以設定要取得的接收位置已復原的通知。</span><span class="sxs-lookup"><span data-stu-id="ee738-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes a binding property, **NotifyOnListenerStart**, that you can configure to get a notification that the receive location has recovered.</span></span> <span data-ttu-id="ee738-107">您可以指定下列值**NotifyOnListenerStart**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="ee738-107">You can specify the following values for the **NotifyOnListenerStart** binding property:</span></span>  
  
-   <span data-ttu-id="ee738-108">將此屬性設定為**True**中接收通知，通知的接收位置的話，只要接收位置復原。</span><span class="sxs-lookup"><span data-stu-id="ee738-108">Set this property to **True**, to receive a notification informing that the receive location is available, as soon as the receive location recovers.</span></span>  
  
-   <span data-ttu-id="ee738-109">將此屬性設定為**False**，而不會收到已復原的接收位置，接收位置復原後通知告知。</span><span class="sxs-lookup"><span data-stu-id="ee738-109">Set this property to **False**, to not receive a notification informing that the receive location has recovered, after the receive location recovers.</span></span>  
  
 <span data-ttu-id="ee738-110">預設值是**True**。</span><span class="sxs-lookup"><span data-stu-id="ee738-110">Default is **True**.</span></span>  
  
## <a name="configuring-the-sql-adapter-behavior"></a><span data-ttu-id="ee738-111">設定 SQL 配接器行為</span><span class="sxs-lookup"><span data-stu-id="ee738-111">Configuring the SQL Adapter Behavior</span></span>  
 <span data-ttu-id="ee738-112">其中一個方法，您不需要執行任何特定的工作，產生中繼資料時，或在設定 BizTalk 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="ee738-112">For either of the approaches, you do not need to perform any specific tasks while generating metadata or while configuring the BizTalk application.</span></span> <span data-ttu-id="ee738-113">您只需要設定**NotifyOnListenerStart**繫結屬性據此在 WCF 自訂或 WCF SQL 接收位置。</span><span class="sxs-lookup"><span data-stu-id="ee738-113">You only need to set the **NotifyOnListenerStart** binding property accordingly on the WCF-Custom or WCF-SQL receive location.</span></span> <span data-ttu-id="ee738-114">若要建立 BizTalk 應用程式，您必須執行相同的一組工作中所述[接收查詢通知以累加方式使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee738-114">To create the BizTalk application, you must perform the same set of tasks as described in [Receive Query Notifications Incrementally from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md).</span></span> <span data-ttu-id="ee738-115">不過，設定 BizTalk 應用程式使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以嘗試的值變更**NotifyOnListenerStart**繫結屬性和查看兩個設定的差異。</span><span class="sxs-lookup"><span data-stu-id="ee738-115">However, when configuring the BizTalk application using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can try changing the value of the **NotifyOnListenerStart** binding property and see the difference in the two configurations.</span></span>  
  
 <span data-ttu-id="ee738-116">下圖示範如何收到通知的值根據**NotifyOnListenerStart**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ee738-116">The following figure demonstrates how the notifications are received based on the value of the **NotifyOnListenerStart** binding property.</span></span>  
  
 <span data-ttu-id="ee738-117">![設定通知的 SQL 配接器](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")</span><span class="sxs-lookup"><span data-stu-id="ee738-117">![Configure SQL Adapter for notifications](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")</span></span>  
  
 <span data-ttu-id="ee738-118">請注意，在第一個案例中，當**NotifyOnListenerStart**設**true**並記錄插入資料庫資料表向下接收位置時，配接器只會傳送給您當接收位置再次開啟時，就會通知訊息。</span><span class="sxs-lookup"><span data-stu-id="ee738-118">Note that in the first scenario, when the **NotifyOnListenerStart** is set to **true** and records are inserted into the database table while the receive location was down, the adapter only sends you a notification message when the receive location comes back up.</span></span> <span data-ttu-id="ee738-119">配接器不會執行任何作業可以處理的接收位置已關閉時插入記錄。</span><span class="sxs-lookup"><span data-stu-id="ee738-119">The adapter does not perform any operation to process the records that were inserted while the receive location was down.</span></span> <span data-ttu-id="ee738-120">配接器用戶端必須實作相關的邏輯來處理的接收位置已關閉時插入記錄在應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ee738-120">The adapter client must implement the relevant logic in their application to process the records that were inserted while the receive location was down.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee738-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee738-121">See Also</span></span>  
 [<span data-ttu-id="ee738-122">接收使用 BizTalk Server 的 SQL 查詢通知</span><span class="sxs-lookup"><span data-stu-id="ee738-122">Receive SQL Query Notifications using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)