---
title: 第 3 課： 執行預存程序選取 加入新的員工 |Microsoft 文件
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
ms.openlocfilehash: 7af49c026b443fb1ca6a0fb7f35b64cdf1e377f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222622"
---
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a><span data-ttu-id="8f747-102">第 3 課： 執行預存程序選取 加入新的員工</span><span class="sxs-lookup"><span data-stu-id="8f747-102">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>
<span data-ttu-id="8f747-103">了解工作執行在這一課之前，您必須先了解為什麼這些工作所需。</span><span class="sxs-lookup"><span data-stu-id="8f747-103">Before understanding the tasks performed in this lesson, you must first understand why these tasks are required.</span></span> <span data-ttu-id="8f747-104">**員工**要新增為新員工插入記錄的資料表中的方式進行定義，**狀態**資料行永遠為"0"每次加入新的員工。</span><span class="sxs-lookup"><span data-stu-id="8f747-104">The **Employee** table to which the records are inserted to add a new employee is defined in such a way that a **Status** column is always set to “0” every time a new employee is added.</span></span> <span data-ttu-id="8f747-105">這是好讓您可以使用此資料行查詢新加入的員工，並也會取得通知。</span><span class="sxs-lookup"><span data-stu-id="8f747-105">This is done so that you can use this column to query for newly added employees and also get notifications.</span></span> <span data-ttu-id="8f747-106">在 SQL Server 中，您會將此查詢執行下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="8f747-106">In SQL Server, you would query this by running the following SQL statement:</span></span>  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 <span data-ttu-id="8f747-107">新接收的清單加入員工之後，您也必須更新**狀態**為"1"下, 一次加入新的員工，而且您會執行相同的查詢的資料行，則不會收到記錄的舊的員工。</span><span class="sxs-lookup"><span data-stu-id="8f747-107">After receiving the list of newly added employees, you must also update the **Status** column to “1” so that the next time new employees are added and you run the same query, you do not get records for old employees as well.</span></span> <span data-ttu-id="8f747-108">若要確定上述 Select 陳述式可讓新加入的員工，將會更新**員工**資料表使用下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="8f747-108">To make sure that the above Select statement gives only the newly added employees, you will update the **Employee** table using the following SQL statement:</span></span>  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 <span data-ttu-id="8f747-109">因此，**狀態**舊員工的資料行設定為"1"時新員工一律為"0"。</span><span class="sxs-lookup"><span data-stu-id="8f747-109">So, the **Status** column for the old employees is set to “1” while new employees will always be “0.”</span></span>  
  
 <span data-ttu-id="8f747-110">在這一課，您將會執行預存程序， **UPDATE_EMPLOYEE**，它接著會執行 Select 和 Update 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8f747-110">In this lesson, you will execute a stored procedure, **UPDATE_EMPLOYEE**, which in turn executes the Select and Update statements.</span></span> <span data-ttu-id="8f747-111">當您完成本課程之後，您的協調流程會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8f747-111">After you have finished this lesson, your orchestration will do the following:</span></span>  
  
1.  <span data-ttu-id="8f747-112">收到的任何變更的通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="8f747-112">Receives notification for any changes to the **Employee** table.</span></span>  
  
2.  <span data-ttu-id="8f747-113">從接收的通知訊息中擷取通知的類型。</span><span class="sxs-lookup"><span data-stu-id="8f747-113">Extracts the type of notification from the notification message received.</span></span>  
  
3.  <span data-ttu-id="8f747-114">如果插入作業的通知訊息，協調流程執行**UPDATE_EMPLOYEE**預存程序。</span><span class="sxs-lookup"><span data-stu-id="8f747-114">If the notification message is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure.</span></span>  
  
4.  <span data-ttu-id="8f747-115">預存程序讀取新輸入資料錄中的**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="8f747-115">The stored procedure reads the newly entered records in the **Employee** table.</span></span> <span data-ttu-id="8f747-116">閱讀後新的記錄，預存程序也會設定**狀態**"1"。 這些記錄的資料行</span><span class="sxs-lookup"><span data-stu-id="8f747-116">After reading the new records, the stored procedure also sets the **Status** column for those records to “1.”</span></span>  
  
 <span data-ttu-id="8f747-117">現在您已經瞭解為何需要執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="8f747-117">Now you know why you need to execute the stored procedure.</span></span> <span data-ttu-id="8f747-118">您現在需要思考如何執行此協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f747-118">You now need to think about how to execute this as part of the orchestration.</span></span> <span data-ttu-id="8f747-119">協調流程需要的要求訊息**UPDATE_EMPLOYEE**預存程序。</span><span class="sxs-lookup"><span data-stu-id="8f747-119">The orchestration needs a request message for the **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="8f747-120">在本教學課程中，您將建立的自訂類別庫會動態建立訊息，然後將它提供給協調流程。</span><span class="sxs-lookup"><span data-stu-id="8f747-120">In this tutorial, you will create a custom class library that will create the message on the fly and then provide it to the orchestration.</span></span> <span data-ttu-id="8f747-121">協調流程收到訊息之後，它會將訊息傳送至 SQL Server 使用 SQL 配接器，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="8f747-121">After the orchestration receives the message, it will send the message to the SQL Server using the SQL adapter and receive the response.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f747-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="8f747-122">In This Section</span></span>  
  
-   [<span data-ttu-id="8f747-123">步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序</span><span class="sxs-lookup"><span data-stu-id="8f747-123">Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [<span data-ttu-id="8f747-124">步驟 2： 將要求訊息傳送至 SQL Server，並接收回應</span><span class="sxs-lookup"><span data-stu-id="8f747-124">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)