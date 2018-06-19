---
title: 步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4da3333-e430-4caf-bc29-44a60ebac385
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 402434ec74327b55f243fecd9d1c347ce4ff0390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278014"
---
# <a name="step-3-create-the-biztalk-server-solution-in-visual-studio"></a><span data-ttu-id="18815-102">步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="18815-102">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>
<span data-ttu-id="18815-103">在本節中，我們查看建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用於接收來自 Salesforce 的商機通知、 查詢 Salesforce 以取得更多有關機會，以及最後將該資訊插入在內部部署 SQL 方案伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="18815-103">In this section, we look at creating the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution for receiving opportunity notifications from Salesforce, querying Salesforce to get additional information about the opportunity, and finally inserting that information into an on-premise SQL Server database.</span></span> <span data-ttu-id="18815-104">本節會進一步分類根據每一個更廣泛的步驟。</span><span class="sxs-lookup"><span data-stu-id="18815-104">This section is further categorized according to each of these broader steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18815-105">能夠將訊息傳送至 Salesforce 並接收來自 Salesforce 到訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，我們需要將我們的方案包含一些自訂元件。</span><span class="sxs-lookup"><span data-stu-id="18815-105">To be able to send messages to Salesforce and to receive messages from Salesforce into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], we need to include some custom components into our solution.</span></span> <span data-ttu-id="18815-106">我們會建立這些自訂元件中的[步驟 3d： 啟用 BizTalk Server 傳送和接收的訊息，從 Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md)。</span><span class="sxs-lookup"><span data-stu-id="18815-106">We create those custom components in [Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18815-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="18815-107">In This Section</span></span>  
  
-   [<span data-ttu-id="18815-108">步驟 3a: Salesforce 接收機會通知到 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="18815-108">Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server</span></span>](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md)  
  
-   [<span data-ttu-id="18815-109">步驟 3b： 擷取來自 Salesforce 使用 Wcf-webhttp 配接器的機會詳細資料</span><span class="sxs-lookup"><span data-stu-id="18815-109">Step 3b: Retrieve Opportunity Details from Salesforce using the WCF-WebHttp Adapter</span></span>](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md)  
  
-   [<span data-ttu-id="18815-110">步驟 3c： 機會詳細資料插入 SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="18815-110">Step 3c: Insert Opportunity Details into a SQL Server Database</span></span>](../core/step-3c-insert-opportunity-details-into-a-sql-server-database.md)  
  
-   [<span data-ttu-id="18815-111">步驟 3d： 啟用 BizTalk Server 傳送和接收來自 Salesforce 的訊息</span><span class="sxs-lookup"><span data-stu-id="18815-111">Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce</span></span>](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md)  
  
-   [<span data-ttu-id="18815-112">步驟 3e： 建置和部署 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="18815-112">Step 3e: Build and Deploy the BizTalk Server Solution</span></span>](../core/step-3e-build-and-deploy-the-biztalk-server-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="18815-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18815-113">See Also</span></span>  
 [<span data-ttu-id="18815-114">教學課程 6： 與 Salesforce 整合 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="18815-114">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)