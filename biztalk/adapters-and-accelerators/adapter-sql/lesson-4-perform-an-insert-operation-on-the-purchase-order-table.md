---
title: "第 4 課： 執行插入作業的採購訂單資料表 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66fc64c5-a3da-4014-8545-f34e6577bd73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c966e3c10f18424b2cfb1fde0235caedbb5f58f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-4-perform-an-insert-operation-on-the-purchase-order-table"></a><span data-ttu-id="a2541-102">第 4 課： 執行插入作業的採購訂單資料表</span><span class="sxs-lookup"><span data-stu-id="a2541-102">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>
<span data-ttu-id="a2541-103">在[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)，您可以執行**UPDATE_EMPLOYEE**預存程序，並接收回應訊息包含詳細資料的新插入位員工的記錄。</span><span class="sxs-lookup"><span data-stu-id="a2541-103">In [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md), you executed the **UPDATE_EMPLOYEE** stored procedure and received a response message that contains the details of the newly inserted employee record.</span></span> <span data-ttu-id="a2541-104">在這一課，您將會根據上一課並更新協調流程以執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2541-104">In this lesson, you will build on the previous lesson and update the orchestration to perform the following steps:</span></span>  
  
1.  <span data-ttu-id="a2541-105">在協調流程中，您建立訊息上執行插入作業**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="a2541-105">Within the orchestration, you build the message to perform an Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="a2541-106">這個步驟是類似於[步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="a2541-106">This step is similar to [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span></span>  
  
2.  <span data-ttu-id="a2541-107">建立要求訊息之後，您將對應的回應訊息**UPDATE_EMPLOYEE**預存程序來插入作業的要求訊息**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="a2541-107">After you build the request message, you map the response message of the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="a2541-108">藉由對應的訊息，您將傳遞回應訊息從接收到插入作業的要求訊息的值。</span><span class="sxs-lookup"><span data-stu-id="a2541-108">By mapping the messages, you pass the values received from the response messages to the request message for Insert operation.</span></span>  
  
3.  <span data-ttu-id="a2541-109">傳送要插入資料錄中的訊息**Purchase_Order**資料表，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="a2541-109">You send the message to insert a record in the **Purchase_Order** table and receive a response.</span></span>  
  
4.  <span data-ttu-id="a2541-110">您傳送至傳送埠的回應。</span><span class="sxs-lookup"><span data-stu-id="a2541-110">You send the response to a send port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2541-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="a2541-111">In This Section</span></span>  
  
-   [<span data-ttu-id="a2541-112">步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業</span><span class="sxs-lookup"><span data-stu-id="a2541-112">Step 1: Create the Request Message for Insert Operation on Purchase_Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)  
  
-   [<span data-ttu-id="a2541-113">步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息</span><span class="sxs-lookup"><span data-stu-id="a2541-113">Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)  
  
-   [<span data-ttu-id="a2541-114">步驟 3： 傳送要插入的記錄，並接收回應的要求訊息</span><span class="sxs-lookup"><span data-stu-id="a2541-114">Step 3: Send the Request Message to Insert Records and Receive a Response</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)  
  
-   [<span data-ttu-id="a2541-115">步驟 4： 建置專案</span><span class="sxs-lookup"><span data-stu-id="a2541-115">Step 4: Build the Project</span></span>](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)