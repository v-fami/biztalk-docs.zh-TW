---
title: "步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fde018d8-9d9a-42ea-8ee9-e3632450b9d7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71021bb0a9bbb71f17f0899e625ac184f9087429
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-the-request-message-for-insert-operation-on-purchaseorder-table"></a><span data-ttu-id="679dd-102">步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業</span><span class="sxs-lookup"><span data-stu-id="679dd-102">Step 1: Create the Request Message for Insert Operation on Purchase_Order Table</span></span>
<span data-ttu-id="679dd-103">![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="679dd-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="679dd-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="679dd-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="679dd-105">**目標：**在此步驟中，您必須將 C# 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="679dd-105">**Objective:** In this step, you add a C# class library project to your solution.</span></span> <span data-ttu-id="679dd-106">此文件庫上建立記憶體中要求訊息的 Insert 作業**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="679dd-106">This library creates an in-memory request message for the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="679dd-107">在稍後步驟中，協調流程會將此訊息傳送到 SQL Server 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="679dd-107">In later steps, the orchestration sends this message to SQL Server to insert records in the table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="679dd-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="679dd-108">Prerequisites</span></span>  
 <span data-ttu-id="679dd-109">您必須先完成中的步驟[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)。</span><span class="sxs-lookup"><span data-stu-id="679dd-109">You must have completed the steps in [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).</span></span>  
  
### <a name="to-create-a-request-message-for-insert-operation"></a><span data-ttu-id="679dd-110">若要建立用於插入作業的要求訊息</span><span class="sxs-lookup"><span data-stu-id="679dd-110">To create a request message for Insert operation</span></span>  
  
1.  <span data-ttu-id="679dd-111">將 Visual C# 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="679dd-111">Add a Visual C# class library project to your solution.</span></span> <span data-ttu-id="679dd-112">如需專案的名稱，輸入`UpdatePOMessageCreator`。</span><span class="sxs-lookup"><span data-stu-id="679dd-112">For the name of the project, type `UpdatePOMessageCreator`.</span></span>  
  
2.  <span data-ttu-id="679dd-113">重新命名**Class1.cs**至**UpdatePOMessageCreator.cs**。</span><span class="sxs-lookup"><span data-stu-id="679dd-113">Rename **Class1.cs** to **UpdatePOMessageCreator.cs**.</span></span>  
  
3.  <span data-ttu-id="679dd-114">將下列程式碼複製到.cs 檔案中：</span><span class="sxs-lookup"><span data-stu-id="679dd-114">Copy the following code to the .cs file:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdatePOMessageCreator  
    {  
        public class UpdatePOMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreatePOMessage";  
                try  
                {  
                    ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                    Console.WriteLine("EXCEPTION: " + ex.ToString());  
                    throw ex;  
                }  
  
                //Create Message From XML  
                Message = new XmlDocument();  
  
                Message.PreserveWhitespace = true;  
  
                Message.Load(ResponseDoc);  
  
                return Message;  
            }  
        }  
    }  
  
    ```  
  
     <span data-ttu-id="679dd-115">此程式碼片段必須插入作業的要求訊息上**Purchase_Order**守在 C:\TestLocation\CreatePOMessage 的資料表。</span><span class="sxs-lookup"><span data-stu-id="679dd-115">This code snippet expects a request message for the Insert operation on the **Purchase_Order** table to be present at C:\TestLocation\CreatePOMessage.</span></span> <span data-ttu-id="679dd-116">程式碼會使用要求訊息，在執行階段建立類似的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="679dd-116">The code uses the request message to create a similar request message at run time.</span></span>  
  
4.  <span data-ttu-id="679dd-117">將強式名稱金鑰檔加入專案。</span><span class="sxs-lookup"><span data-stu-id="679dd-117">Add a strong-name key file to the project.</span></span> <span data-ttu-id="679dd-118">如需建立強式名稱金鑰檔的指示，請參閱[來建立使用 SQL 配接器的 SQL 應用程式的必要條件](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="679dd-118">For instructions on creating a strong-name key file, see [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md).</span></span>  
  
    1.  <span data-ttu-id="679dd-119">在 [方案總管] 中，以滑鼠右鍵按一下**UpdatePOMessageCreator**專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="679dd-119">In the Solution Explorer, right-click the **UpdatePOMessageCreator** project and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="679dd-120">在**屬性**視窗中，按一下 **簽署**。</span><span class="sxs-lookup"><span data-stu-id="679dd-120">In the **Property** window, click **Signing**.</span></span>  
  
    3.  <span data-ttu-id="679dd-121">在**簽署**索引標籤上，選取**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="679dd-121">In the **Signing** tab, select the **Sign the assembly** check box.</span></span>  
  
    4.  <span data-ttu-id="679dd-122">從**選擇強式名稱金鑰檔**清單中，按一下**\<瀏覽\>**。</span><span class="sxs-lookup"><span data-stu-id="679dd-122">From the **Choose a strong-name key file** list, click **\<Browse\>**.</span></span>  
  
    5.  <span data-ttu-id="679dd-123">導覽至您用來建立強式名稱金鑰檔案的資料夾，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="679dd-123">Navigate to the folder where you created the strong-name key file, and then click **Open**.</span></span>  
  
    6.  <span data-ttu-id="679dd-124">按一下**儲存**上**標準**功能表列。</span><span class="sxs-lookup"><span data-stu-id="679dd-124">Click **Save** on the **Standard** menu bar.</span></span> <span data-ttu-id="679dd-125">關閉**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="679dd-125">Close the **Property** window.</span></span>  
  
5.  <span data-ttu-id="679dd-126">建置專案。</span><span class="sxs-lookup"><span data-stu-id="679dd-126">Build the project.</span></span> <span data-ttu-id="679dd-127">以滑鼠右鍵按一下專案，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="679dd-127">Right-click the project and click **Build**.</span></span>  
  
6.  <span data-ttu-id="679dd-128">這個專案的參考加入至方案中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="679dd-128">Add a reference of this project to the BizTalk project in the solution.</span></span>  
  
    1.  <span data-ttu-id="679dd-129">在 方案總管 中，展開 BizTalk 專案，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="679dd-129">In the Solution Explorer, expand the BizTalk project, right-click **References**, and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="679dd-130">在**加入參考**對話方塊中，按一下 [**專案**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="679dd-130">In the **Add Reference** dialog box, click the **Projects** tab.</span></span>  
  
    3.  <span data-ttu-id="679dd-131">從 專案名稱的清單，選取  **UpdatePOMessageCreator**，按一下**新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="679dd-131">From the list of project names, select **UpdatePOMessageCreator**, click **Add**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="679dd-132">建置專案時，會建立組件 DLL 專案的 \bin\Debug 資料夾下。</span><span class="sxs-lookup"><span data-stu-id="679dd-132">Building the project creates the assembly DLL under \bin\Debug folder of the project.</span></span> <span data-ttu-id="679dd-133">您必須加入這個 DLL 到全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="679dd-133">You must add this DLL to the Global Assembly Cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="679dd-134">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="679dd-134">Start a Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="679dd-135">從命令提示字元中，瀏覽至的 \bin\Debug\ 資料夾**UpdatePOMessageCreator**專案。</span><span class="sxs-lookup"><span data-stu-id="679dd-135">From the command prompt, navigate to the \bin\Debug\ folder of the **UpdatePOMessageCreator** project.</span></span>  
  
    3.  <span data-ttu-id="679dd-136">在命令提示字元處執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="679dd-136">Run the following command on the command prompt:</span></span>  
  
        ```  
        gacutil /i UpdatePOMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="679dd-137">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="679dd-137">What did I just do?</span></span>  
 <span data-ttu-id="679dd-138">在此步驟中，您可以加入 UpdatePOMessageCreator 類別庫專案會建立在執行階段的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="679dd-138">In this step, you added an UpdatePOMessageCreator class library project that creates request message at run-time.</span></span> <span data-ttu-id="679dd-139">您在 BizTalk 專案中加入此專案的參考，也加入至 GAC 的組件 DLL。</span><span class="sxs-lookup"><span data-stu-id="679dd-139">You added the reference to this project in the BizTalk project and also added the assembly DLL to the GAC.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="679dd-140">後續步驟</span><span class="sxs-lookup"><span data-stu-id="679dd-140">Next Steps</span></span>  
 <span data-ttu-id="679dd-141">您在對應的插入作業的要求訊息的 UPDATE_EMPLOYEE 預存程序的回應訊息**Purchaser_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="679dd-141">You map the response message for the UPDATE_EMPLOYEE stored procedure to the request message for the Insert operation on **Purchaser_Order** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679dd-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="679dd-142">See Also</span></span>  
 <span data-ttu-id="679dd-143">[步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span><span class="sxs-lookup"><span data-stu-id="679dd-143">[Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span></span>  
 [<span data-ttu-id="679dd-144">第 4 課：在訂單資料表上執行插入作業</span><span class="sxs-lookup"><span data-stu-id="679dd-144">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)