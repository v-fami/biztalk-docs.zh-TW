---
title: 教學課程 2： 員工-訂單程序使用 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eeb4dd1e-209a-47eb-9c0e-a138e02f0ff2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d14008611bfb22bf39e446e72ecb3bba4571761
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010775"
---
# <a name="tutorial-2-employee---purchase-order-process-using-the-sql-adapter"></a><span data-ttu-id="09341-102">教學課程 2： 員工-訂單程序使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="09341-102">Tutorial 2: Employee - Purchase Order Process using the SQL adapter</span></span>
<span data-ttu-id="09341-103">在本教學課程中，您就會自動將設備的採購部門位置順序每次新的員工加入組織的程序。</span><span class="sxs-lookup"><span data-stu-id="09341-103">In this tutorial, you are automating the process where the Purchases department that places an equipment order every time a new employee joins the organization.</span></span> <span data-ttu-id="09341-104">員工詳細資料和採購單詳細資料保存在**員工**並**為 Purchase_Order**資料表分別在 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="09341-104">Both employee details and purchase order details are maintained in **Employee** and **Purchase_Order** tables respectively, in a SQL Server database.</span></span> <span data-ttu-id="09341-105">採購部門獲知更新為 Purchase_Order 資料表中的 SQL Server 資料庫，以及傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="09341-105">The Purchases department is informed by updating the Purchase_Order table in the SQL Server database and by sending an e-mail.</span></span> <span data-ttu-id="09341-106">在處理序中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="09341-106">Within the process, the following actions occur:</span></span>  
  
1. <span data-ttu-id="09341-107">配接器接收的通知每次**員工**會更新資料表。</span><span class="sxs-lookup"><span data-stu-id="09341-107">The adapter receives a notification each time the **Employee** table is updated.</span></span> <span data-ttu-id="09341-108">然後，配接器會傳送通知給 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="09341-108">The adapter then sends a notification to the BizTalk orchestration.</span></span>  
  
2. <span data-ttu-id="09341-109">BizTalk 協調流程會找出通知是否為新記錄插入至**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="09341-109">The BizTalk orchestration figures out whether the notification is for a new record inserted into the **Employee** table.</span></span> <span data-ttu-id="09341-110">如果通知是任何其他作業上**員工**資料表中，協調流程不會執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="09341-110">If the notification is for any other operation on the **Employee** table, the orchestration does not perform any operation.</span></span>  
  
3. <span data-ttu-id="09341-111">如果通知是在插入作業**員工**通知，已加入新的員工資料錄，協調流程使用的資料表[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讀取新的記錄詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09341-111">If the notification is for an Insert operation on the **Employee** table, notifying that a new employee record was added, the orchestration uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to read the details of the new record.</span></span>  
  
4. <span data-ttu-id="09341-112">協調流程收到回應，其中包含新加入的員工記錄的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09341-112">The orchestration receives a response that contains the details of the new added employee record.</span></span> <span data-ttu-id="09341-113">協調流程對應**Employee_ID**並**指定**欄位以回應插入作業的要求訊息上**為 Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="09341-113">The orchestration maps the **Employee_ID** and **Designation** fields in the response to the request message for the Insert operation on the **Purchase_Order** table.</span></span>  
  
5. <span data-ttu-id="09341-114">協調流程接著會使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上執行插入作業**為 Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="09341-114">The orchestration then uses the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform an Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="09341-115">插入作業的回應會傳送至採購部門中，以電子郵件。</span><span class="sxs-lookup"><span data-stu-id="09341-115">The response for the Insert operation is sent to the Purchases department as an e-mail.</span></span>  
  
## <a name="about-the-database-objects-used-in-this-sample"></a><span data-ttu-id="09341-116">此範例中使用的資料庫物件的相關</span><span class="sxs-lookup"><span data-stu-id="09341-116">About the Database Objects Used in this Sample</span></span>  
 <span data-ttu-id="09341-117">本教學課程會使用隨附於範例 SQL 指令碼所建立的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="09341-117">This tutorial uses the database objects created by the SQL script shipped with the samples.</span></span> <span data-ttu-id="09341-118">如需有關此指令碼和範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="09341-118">For more information about the script and the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="09341-119">您將在本教學課程中使用的資料庫物件如下：</span><span class="sxs-lookup"><span data-stu-id="09341-119">The database objects that you will use in this tutorial are:</span></span>  
  
- <span data-ttu-id="09341-120">**ADAPTER_SAMPLES**資料庫。</span><span class="sxs-lookup"><span data-stu-id="09341-120">**ADAPTER_SAMPLES** database.</span></span>  
  
- <span data-ttu-id="09341-121">**員工**並**為 Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="09341-121">**Employee** and **Purchase_Order** tables.</span></span>  
  
- <span data-ttu-id="09341-122">**UPDATE_EMPLOYEE**預存程序。</span><span class="sxs-lookup"><span data-stu-id="09341-122">**UPDATE_EMPLOYEE** stored procedure.</span></span>  
  
  <span data-ttu-id="09341-123">當您執行範例所提供的 SQL 指令碼時，會建立所有這些資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="09341-123">All these database objects are created when you run the SQL script provided with the sample.</span></span> <span data-ttu-id="09341-124">請確定在開始本教學課程之前，執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="09341-124">Make sure you run the script before you start with the tutorial.</span></span>  
  
## <a name="sample-based-on-this-tutorial"></a><span data-ttu-id="09341-125">根據此教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="09341-125">Sample Based on This Tutorial</span></span>  
 <span data-ttu-id="09341-126">範例中， **Employee_PurchaseOrder**，根據本教學課程也會提供與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="09341-126">A sample, **Employee_PurchaseOrder**, which is based on this tutorial is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="09341-127">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="09341-127">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
 <span data-ttu-id="09341-128">我們建議您瀏覽本教學課程完全了解如何建立使用配接器的 BizTalk 專案，並再看看此範例做為參考。</span><span class="sxs-lookup"><span data-stu-id="09341-128">We recommend that you go through the tutorial completely to understand how to create BizTalk projects using the adapter, and then look at the sample as a reference.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09341-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="09341-129">In This Section</span></span>  
  
-   [<span data-ttu-id="09341-130">第 1 課：產生結構描述和建立訊息</span><span class="sxs-lookup"><span data-stu-id="09341-130">Lesson 1: Generate Schemas and Create Messages</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [<span data-ttu-id="09341-131">第 2 課：接收和篩選通知</span><span class="sxs-lookup"><span data-stu-id="09341-131">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [<span data-ttu-id="09341-132">第 3 課：執行預存程序以選取新增的員工</span><span class="sxs-lookup"><span data-stu-id="09341-132">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [<span data-ttu-id="09341-133">第 4 課：在訂單資料表上執行插入作業</span><span class="sxs-lookup"><span data-stu-id="09341-133">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [<span data-ttu-id="09341-134">第 5 課：部署方案</span><span class="sxs-lookup"><span data-stu-id="09341-134">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)