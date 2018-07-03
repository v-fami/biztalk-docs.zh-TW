---
title: 第 3 課： 執行預存程序以選取 加入新員工 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec7897e9-0c77-41b2-8cc2-61745bd3b028
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3021a5e3ead821a0f3c8d0372d48ae469a834c1c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001855"
---
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a><span data-ttu-id="a3fd7-102">第 3 課： 執行預存程序來選取新增的員工</span><span class="sxs-lookup"><span data-stu-id="a3fd7-102">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>
<span data-ttu-id="a3fd7-103">在這一課中了解工作執行之前，您必須先了解為何需要這些工作。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-103">Before understanding the tasks performed in this lesson, you must first understand why these tasks are required.</span></span> <span data-ttu-id="a3fd7-104">**員工**以新增新進員工插入記錄的資料表定義的方式可**狀態**每次將新員工新增 always 資料行設定為"0"。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-104">The **Employee** table to which the records are inserted to add a new employee is defined in such a way that a **Status** column is always set to “0” every time a new employee is added.</span></span> <span data-ttu-id="a3fd7-105">這麼做是為了讓您可以使用此資料行來查詢新加入的員工，並也收到通知。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-105">This is done so that you can use this column to query for newly added employees and also get notifications.</span></span> <span data-ttu-id="a3fd7-106">在 SQL Server 中，您會將此查詢執行下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a3fd7-106">In SQL Server, you would query this by running the following SQL statement:</span></span>  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 <span data-ttu-id="a3fd7-107">新接收的清單加入員工之後，您也必須更新**狀態**為"1"(因此，下一次加入新的員工和您執行相同查詢的資料行，您無法取得記錄的舊的員工。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-107">After receiving the list of newly added employees, you must also update the **Status** column to “1” so that the next time new employees are added and you run the same query, you do not get records for old employees as well.</span></span> <span data-ttu-id="a3fd7-108">若要確定上述的 Select 陳述式可讓新加入的員工，您將會更新**員工**資料表使用下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a3fd7-108">To make sure that the above Select statement gives only the newly added employees, you will update the **Employee** table using the following SQL statement:</span></span>  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 <span data-ttu-id="a3fd7-109">因此，**狀態**舊員工的資料行設為"1"的新員工永遠是"0"。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-109">So, the **Status** column for the old employees is set to “1” while new employees will always be “0.”</span></span>  
  
 <span data-ttu-id="a3fd7-110">在這一課，您將執行預存程序中， **UPDATE_EMPLOYEE**，它會依序執行的 Select 和 Update 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-110">In this lesson, you will execute a stored procedure, **UPDATE_EMPLOYEE**, which in turn executes the Select and Update statements.</span></span> <span data-ttu-id="a3fd7-111">完成本課程之後，您的協調流程會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a3fd7-111">After you have finished this lesson, your orchestration will do the following:</span></span>  
  
1. <span data-ttu-id="a3fd7-112">收到的任何變更的通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-112">Receives notification for any changes to the **Employee** table.</span></span>  
  
2. <span data-ttu-id="a3fd7-113">擷取收到的通知訊息的通知類型。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-113">Extracts the type of notification from the notification message received.</span></span>  
  
3. <span data-ttu-id="a3fd7-114">如果通知訊息是插入作業，協調流程便會執行**UPDATE_EMPLOYEE**預存程序。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-114">If the notification message is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure.</span></span>  
  
4. <span data-ttu-id="a3fd7-115">預存程序會讀取中的新輸入資料錄**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-115">The stored procedure reads the newly entered records in the **Employee** table.</span></span> <span data-ttu-id="a3fd7-116">閱讀後的新記錄，預存程序也會設定**狀態**"1"。 這些記錄的資料行</span><span class="sxs-lookup"><span data-stu-id="a3fd7-116">After reading the new records, the stored procedure also sets the **Status** column for those records to “1.”</span></span>  
  
   <span data-ttu-id="a3fd7-117">現在您知道您需要執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-117">Now you know why you need to execute the stored procedure.</span></span> <span data-ttu-id="a3fd7-118">您現在需要思考如何執行此協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-118">You now need to think about how to execute this as part of the orchestration.</span></span> <span data-ttu-id="a3fd7-119">協調流程需要的要求訊息**UPDATE_EMPLOYEE**預存程序。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-119">The orchestration needs a request message for the **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="a3fd7-120">在本教學課程中，您將建立會動態建立訊息並再將它提供給協調流程的自訂類別庫。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-120">In this tutorial, you will create a custom class library that will create the message on the fly and then provide it to the orchestration.</span></span> <span data-ttu-id="a3fd7-121">協調流程收到訊息之後，它會將訊息傳送至 SQL Server 使用 SQL 配接器，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-121">After the orchestration receives the message, it will send the message to the SQL Server using the SQL adapter and receive the response.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3fd7-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="a3fd7-122">In This Section</span></span>  
  
-   [<span data-ttu-id="a3fd7-123">步驟 1：為 UPDATE_EMPLOYEE 預存程序建立要求訊息</span><span class="sxs-lookup"><span data-stu-id="a3fd7-123">Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [<span data-ttu-id="a3fd7-124">步驟 2：將要求訊息傳送到 SQL Server 並接收回應</span><span class="sxs-lookup"><span data-stu-id="a3fd7-124">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)