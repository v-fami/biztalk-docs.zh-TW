---
title: 步驟 5： 測試解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5ca5301-2ee4-4024-a90a-396ed681d12a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33a51cda93a1c2cdd6f5a70ebd62bf1d9ce05a7e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020849"
---
# <a name="step-5-test-the-solution"></a><span data-ttu-id="9715a-102">步驟 5： 測試方案</span><span class="sxs-lookup"><span data-stu-id="9715a-102">Step 5: Test the Solution</span></span>
<span data-ttu-id="9715a-103">此解決方案的目標是在自動化程序傳送通知給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每次在 Salesforce 中關閉新的商機藉由設定為商機的階段**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="9715a-103">This solution aims at automating the process of sending notifications to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], every time a new opportunity is closed in Salesforce by setting the stage of the opportunity as **Closed Won**.</span></span> <span data-ttu-id="9715a-104">收到通知後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將查詢傳送到 Salesforce 擷取機會，相關的產品詳細資料，然後插入回應從 Salesforce 呼叫的 SQL Server 資料庫資料表**OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="9715a-104">After the notification is received [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a query to Salesforce to retrieve product details related to the opportunity, and then inserts the response from Salesforce into a SQL Server database table called **OrderDetails**.</span></span> <span data-ttu-id="9715a-105">因此，若要測試此解決方案，我們將更新的階段有機會**Closed Won** ，如此一來，您必須取得相關的記錄插入訂單資料庫中的 [OrderDetails] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="9715a-105">So, to test this solution, we will update the stage of an opportunity to **Closed Won** and as a result, relevant records must get inserted in the OrderDetails table in the Orders database.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="9715a-106">測試方案</span><span class="sxs-lookup"><span data-stu-id="9715a-106">To test the solution</span></span>  
  
1. <span data-ttu-id="9715a-107">登入`https://login.salesforce.com/?lt=de`，使用 Salesforce 開發人員登入認證。</span><span class="sxs-lookup"><span data-stu-id="9715a-107">Log in to `https://login.salesforce.com/?lt=de`, using the Salesforce developer login credentials.</span></span>  
  
2. <span data-ttu-id="9715a-108">在導覽列中，按一下**機會**，然後按一下**客戶 1 的機會**。</span><span class="sxs-lookup"><span data-stu-id="9715a-108">In the navigation bar, click **Opportunities**, and then click **Opportunity with Customer 1**.</span></span> <span data-ttu-id="9715a-109">您已建立在這個機會[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。</span><span class="sxs-lookup"><span data-stu-id="9715a-109">You had created this opportunity in [Step 2: Set up the Salesforce System](../core/step-2-set-up-the-salesforce-system.md).</span></span>  
  
3. <span data-ttu-id="9715a-110">在 **機會詳細資料**區段中，記下中相關聯的產品**產品 （標準）** 一節。</span><span class="sxs-lookup"><span data-stu-id="9715a-110">In the **Opportunity Detail** section, take a note of the associated products in the **Products (Standard)** section.</span></span> <span data-ttu-id="9715a-111">此區段下您最後會插入至 SQL Server 資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="9715a-111">The values you under this section will finally get inserted into the SQL Server database.</span></span> <span data-ttu-id="9715a-112">底下**機會詳細資料**區段中，按一下**編輯**按鈕，然後將值變更**階段**欄位**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="9715a-112">Under the **Opportunity Detail** section click the **Edit** button and change the value of **Stage** field to **Closed Won**.</span></span> <span data-ttu-id="9715a-113">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="9715a-113">Click **Save**.</span></span>  
  
    <span data-ttu-id="9715a-114">![編輯現有的機會](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span><span class="sxs-lookup"><span data-stu-id="9715a-114">![Edit an existing opportunity](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span></span>  
  
4. <span data-ttu-id="9715a-115">在 SQL Server Management Studio 上執行查詢**OrderDetails**来選取所有資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="9715a-115">In SQL Server Management Studio, run a query on the **OrderDetails** table to select all rows.</span></span>  
  
    <span data-ttu-id="9715a-116">![SQL 查詢的輸出](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span><span class="sxs-lookup"><span data-stu-id="9715a-116">![SQL Query output](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span></span>  
  
    <span data-ttu-id="9715a-117">請注意，它會列出有機會在您變更階段中所列的產品。</span><span class="sxs-lookup"><span data-stu-id="9715a-117">Notice that it lists the products that are listed in the opportunity for which you changed the stage.</span></span>  
  
    <span data-ttu-id="9715a-118">![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="9715a-118">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
   <span data-ttu-id="9715a-119">您可以看到在其中輸入資料錄**OrderDetails**資料表對應到 Salesforce 中建立的一組指定的產品銷售良機。</span><span class="sxs-lookup"><span data-stu-id="9715a-119">You can see that the records entered in the **OrderDetails** table correspond to the sales opportunity created in Salesforce for a given set of products.</span></span> <span data-ttu-id="9715a-120">您可以藉由建立新的商機，並將新的產品產生關聯的機會，重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9715a-120">You can repeat these steps by creating new opportunities and associating new products with the opportunity.</span></span>