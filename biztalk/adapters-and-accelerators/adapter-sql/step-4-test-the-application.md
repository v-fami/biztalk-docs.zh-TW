---
title: "步驟 4： 測試應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 488b13fa-7a71-4430-bbf5-dbf47ba55562
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 347c2bcf459d7e9ce7b1fb9efc07579be81d989d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-application"></a><span data-ttu-id="38fa5-102">步驟 4： 測試應用程式</span><span class="sxs-lookup"><span data-stu-id="38fa5-102">Step 4: Test the Application</span></span>
<span data-ttu-id="38fa5-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="38fa5-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="38fa5-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="38fa5-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="38fa5-105">**目標：**在此步驟中，您必須測試應用程式所插入在記錄**員工**資料表**ADAPTER_SAMPLES**資料庫。</span><span class="sxs-lookup"><span data-stu-id="38fa5-105">**Objective:** In this step, you test the application by inserting a record in the **Employee** table of the **ADAPTER_SAMPLES** database.</span></span> <span data-ttu-id="38fa5-106">如果應用程式是否正常運作，協調流程收到變更通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-106">If the application is working properly, the orchestration receives a notification for changes to the **Employee** table.</span></span> <span data-ttu-id="38fa5-107">協調流程接著會擷取收到的通知類型。</span><span class="sxs-lookup"><span data-stu-id="38fa5-107">The orchestration then extracts the type of notification received.</span></span> <span data-ttu-id="38fa5-108">如果插入作業的通知，協調流程執行**UPDATE_EMPLOYEE**預存程序，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="38fa5-108">If the notification is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure and receives a response.</span></span> <span data-ttu-id="38fa5-109">協調流程中擷取的值**Employee_ID**和**名稱**從回應，並將其插入**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-109">The orchestration extracts the values of **Employee_ID** and **Name** from the response and inserts them into the **Purchase_Order** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="38fa5-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="38fa5-110">Prerequisites</span></span>  
 <span data-ttu-id="38fa5-111">開始之前有了這個步驟，您必須確定下列各項：</span><span class="sxs-lookup"><span data-stu-id="38fa5-111">Before starting with this step, you must ensure the following:</span></span>  
  
-   <span data-ttu-id="38fa5-112">要求訊息來叫用**UPDATE_EMPLOYEE**預存程序將會位於 C:\TestLocation\CreateEmployeeMessage。</span><span class="sxs-lookup"><span data-stu-id="38fa5-112">A request message to invoke the **UPDATE_EMPLOYEE** stored procedure is available at C:\TestLocation\CreateEmployeeMessage.</span></span> <span data-ttu-id="38fa5-113">要求訊息看起來如下：</span><span class="sxs-lookup"><span data-stu-id="38fa5-113">The request message looks like the following:</span></span>  
  
    ```  
    <UPDATE_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo" />  
    ```  
  
-   <span data-ttu-id="38fa5-114">在上叫用插入作業的要求訊息**Purchase_Order**資料表將會位於 C:\TestLocation\CreatePOMessage。</span><span class="sxs-lookup"><span data-stu-id="38fa5-114">A request message to invoke the Insert operation on the **Purchase_Order** table is available at C:\TestLocation\CreatePOMessage.</span></span> <span data-ttu-id="38fa5-115">要求訊息看起來如下：</span><span class="sxs-lookup"><span data-stu-id="38fa5-115">The request message looks like the following:</span></span>  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Purchase_Order">  
      <Rows>  
        <Purchase_Order xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10</Employee_ID><Employee_Name>Employee_Name</Employee_Name>  
        </Purchase_Order>  
      </Rows>  
    </Insert>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="38fa5-116">值**Employee_ID**和**Employee_Name**欄位是預留位置。</span><span class="sxs-lookup"><span data-stu-id="38fa5-116">The values for the **Employee_ID** and **Employee_Name** fields are placeholders.</span></span> <span data-ttu-id="38fa5-117">實際的值是由協調流程在執行階段插入。</span><span class="sxs-lookup"><span data-stu-id="38fa5-117">The actual values are inserted by the orchestration at run-time.</span></span>  
  
-   <span data-ttu-id="38fa5-118">您必須先完成[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa5-118">You must have completed [Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="38fa5-119">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="38fa5-119">To test the application</span></span>  
  
1.  <span data-ttu-id="38fa5-120">插入資料錄中的**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-120">Insert a record in the **Employee** table.</span></span> <span data-ttu-id="38fa5-121">您可以從 SQL Server Management Studio 中執行下列陳述式來這麼做。</span><span class="sxs-lookup"><span data-stu-id="38fa5-121">You can do so by running the following statement from SQL Server Management Studio.</span></span>  
  
    ```  
    INSERT INTO [ADAPTER_SAMPLES].[dbo].[Employee] ([Name] ,[Designation] ,[Salary])  
    VALUES('John Smith' ,'Manager' ,500000)  
    ```  
  
2.  <span data-ttu-id="38fa5-122">請檢查**員工**資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-122">Check the **Employee** table in the database.</span></span> <span data-ttu-id="38fa5-123">您會注意到新的記錄加**狀態**資料行是"0"。</span><span class="sxs-lookup"><span data-stu-id="38fa5-123">You will notice that the new record is added by the **Status** column is “0.”</span></span>  
  
3.  <span data-ttu-id="38fa5-124">請重新整理**員工**資料表的記錄。</span><span class="sxs-lookup"><span data-stu-id="38fa5-124">Keep refreshing the **Employee** table records.</span></span> <span data-ttu-id="38fa5-125">您會注意到**狀態**新記錄的資料行現在設定為"1"。</span><span class="sxs-lookup"><span data-stu-id="38fa5-125">You will notice that the **Status** column for the new record is now set to “1.”</span></span>  
  
4.  <span data-ttu-id="38fa5-126">請檢查**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-126">Check the **Purchase_Order** table.</span></span> <span data-ttu-id="38fa5-127">您會注意到，將記錄具有相同的員工名稱和指定，如您所提供的 Insert 陳述式中，加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-127">You will notice that a record with the same employee name and designation, as you provided in the Insert statement, is added to the table.</span></span>  
  
5.  <span data-ttu-id="38fa5-128">如果您提供您的電子郵件別名，SMTP 連接埠組態中，您也會發生插入作業的回應訊息的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="38fa5-128">If you provided your e-mail alias in the SMTP port configuration, you will also receive an e-mail with the response message for the Insert operation.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="38fa5-129">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="38fa5-129">What did I just do?</span></span>  
 <span data-ttu-id="38fa5-130">測試 SampleApplication 應用程式將在資料錄**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa5-130">Tested the SampleApplication application by inserting a record in the **Employee** table.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38fa5-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="38fa5-131">Next Steps</span></span>  
 <span data-ttu-id="38fa5-132">若測試成功，恭喜！</span><span class="sxs-lookup"><span data-stu-id="38fa5-132">If the test worked, congratulations!</span></span> <span data-ttu-id="38fa5-133">您已完成[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]教學課程。</span><span class="sxs-lookup"><span data-stu-id="38fa5-133">You have completed the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] tutorial.</span></span>  
  
 <span data-ttu-id="38fa5-134">若測試不成功，請仔細地檢查您的工作，以確保您已新增所有必要的物件並正確地設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="38fa5-134">If the test did not work, carefully check your work to make sure that you added all of the necessary objects and set their properties correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fa5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38fa5-135">See Also</span></span>  
 <span data-ttu-id="38fa5-136">[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="38fa5-136">[Step 3: Configure and Start the Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md) </span></span>  
 [<span data-ttu-id="38fa5-137">第 5 課： 部署方案</span><span class="sxs-lookup"><span data-stu-id="38fa5-137">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)