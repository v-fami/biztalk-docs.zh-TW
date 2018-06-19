---
title: 步驟 5： 測試方案 |Microsoft 文件
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
ms.openlocfilehash: 7ce7edd1c1f1f8a063e2787cc2acecb3b57cca2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276886"
---
# <a name="step-5-test-the-solution"></a><span data-ttu-id="fdff1-102">步驟 5： 測試方案</span><span class="sxs-lookup"><span data-stu-id="fdff1-102">Step 5: Test the Solution</span></span>
<span data-ttu-id="fdff1-103">此解決方案旨在自動化程序傳送通知給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每當在 Salesforce 中關閉新商機的設定當做商機的階段**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="fdff1-103">This solution aims at automating the process of sending notifications to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], every time a new opportunity is closed in Salesforce by setting the stage of the opportunity as **Closed Won**.</span></span> <span data-ttu-id="fdff1-104">在收到通知之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送查詢到 Salesforce 擷取與商機相關的產品詳細資料，然後將回應從 Salesforce 插入呼叫的 SQL Server 資料庫資料表**OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="fdff1-104">After the notification is received [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a query to Salesforce to retrieve product details related to the opportunity, and then inserts the response from Salesforce into a SQL Server database table called **OrderDetails**.</span></span> <span data-ttu-id="fdff1-105">因此，若要測試此解決方案，我們將更新的機會階段**Closed Won** ，如此一來，您必須取得相關的記錄插入 OrderDetails 資料表中 「 訂單 」 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fdff1-105">So, to test this solution, we will update the stage of an opportunity to **Closed Won** and as a result, relevant records must get inserted in the OrderDetails table in the Orders database.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="fdff1-106">測試方案</span><span class="sxs-lookup"><span data-stu-id="fdff1-106">To test the solution</span></span>  
  
1.  <span data-ttu-id="fdff1-107">登入`https://login.salesforce.com/?lt=de`，使用 Salesforce 開發人員的登入認證。</span><span class="sxs-lookup"><span data-stu-id="fdff1-107">Log in to `https://login.salesforce.com/?lt=de`, using the Salesforce developer login credentials.</span></span>  
  
2.  <span data-ttu-id="fdff1-108">在導覽列中，按一下**機會**，然後按一下 **客戶 1 的機會**。</span><span class="sxs-lookup"><span data-stu-id="fdff1-108">In the navigation bar, click **Opportunities**, and then click **Opportunity with Customer 1**.</span></span> <span data-ttu-id="fdff1-109">您建立這個機會在[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。</span><span class="sxs-lookup"><span data-stu-id="fdff1-109">You had created this opportunity in [Step 2: Set up the Salesforce System](../core/step-2-set-up-the-salesforce-system.md).</span></span>  
  
3.  <span data-ttu-id="fdff1-110">在**機會詳細**區段中，記下中相關聯的產品的**產品 （標準）** > 一節。</span><span class="sxs-lookup"><span data-stu-id="fdff1-110">In the **Opportunity Detail** section, take a note of the associated products in the **Products (Standard)** section.</span></span> <span data-ttu-id="fdff1-111">您在這一節下最後取得插入的 SQL Server 資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="fdff1-111">The values you under this section will finally get inserted into the SQL Server database.</span></span> <span data-ttu-id="fdff1-112">在下**機會詳細**區段中，按一下**編輯**按鈕，然後將值變更**階段**欄位設為**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="fdff1-112">Under the **Opportunity Detail** section click the **Edit** button and change the value of **Stage** field to **Closed Won**.</span></span> <span data-ttu-id="fdff1-113">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="fdff1-113">Click **Save**.</span></span>  
  
     <span data-ttu-id="fdff1-114">![編輯現有的機會](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span><span class="sxs-lookup"><span data-stu-id="fdff1-114">![Edit an existing opportunity](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span></span>  
  
4.  <span data-ttu-id="fdff1-115">SQL Server Management Studio，在上執行的查詢**OrderDetails**来選取所有資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="fdff1-115">In SQL Server Management Studio, run a query on the **OrderDetails** table to select all rows.</span></span>  
  
     <span data-ttu-id="fdff1-116">![SQL 查詢的輸出](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span><span class="sxs-lookup"><span data-stu-id="fdff1-116">![SQL Query output](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span></span>  
  
     <span data-ttu-id="fdff1-117">請注意，它會列出有機會在您變更此階段中所列的產品。</span><span class="sxs-lookup"><span data-stu-id="fdff1-117">Notice that it lists the products that are listed in the opportunity for which you changed the stage.</span></span>  
  
     <span data-ttu-id="fdff1-118">![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="fdff1-118">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
 <span data-ttu-id="fdff1-119">您可以看到在其中輸入記錄**OrderDetails**資料表對應至在 Salesforce 中建立一組指定的產品銷售的機會。</span><span class="sxs-lookup"><span data-stu-id="fdff1-119">You can see that the records entered in the **OrderDetails** table correspond to the sales opportunity created in Salesforce for a given set of products.</span></span> <span data-ttu-id="fdff1-120">您可以藉由建立新的機會，並將新的產品產生關聯的機會，重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="fdff1-120">You can repeat these steps by creating new opportunities and associating new products with the opportunity.</span></span>