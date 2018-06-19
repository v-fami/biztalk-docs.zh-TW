---
title: 步驟 1： 作業產生結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63218a5e-9af2-40af-9992-ac5e204d2832
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16372bd950088b89f8e7808cda751f5fc3833944
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224958"
---
# <a name="step-1-generate-schema-for-operations"></a><span data-ttu-id="147fb-102">步驟 1： 作業產生結構描述</span><span class="sxs-lookup"><span data-stu-id="147fb-102">Step 1: Generate Schema for Operations</span></span>
<span data-ttu-id="147fb-103">![步驟 2 之 1](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span><span class="sxs-lookup"><span data-stu-id="147fb-103">![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span></span>  
  
 <span data-ttu-id="147fb-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="147fb-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="147fb-105">**目標：** 在此步驟中，您會產生結構描述在 SQL Server 資料庫使用中執行的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-105">**Objective:** In this step, you generate schemas for the operations that you perform on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="147fb-106">此教學課程中，您必須產生以下的結構描述：</span><span class="sxs-lookup"><span data-stu-id="147fb-106">For this tutorial, you must generate schema for the following:</span></span>  
  
-   <span data-ttu-id="147fb-107">**通知**（輸入作業）。</span><span class="sxs-lookup"><span data-stu-id="147fb-107">**Notification** (inbound operation).</span></span>  
  
-   <span data-ttu-id="147fb-108">**UPDATE_EMPLOYEE**預存程序 （輸出作業）。</span><span class="sxs-lookup"><span data-stu-id="147fb-108">**UPDATE_EMPLOYEE** stored procedure (outbound operation).</span></span>  
  
-   <span data-ttu-id="147fb-109">**插入**作業**Purchase_Order**資料表 （輸出作業）。</span><span class="sxs-lookup"><span data-stu-id="147fb-109">**Insert** operation on the **Purchase_Order** table (outbound operation).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="147fb-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="147fb-110">Prerequisites</span></span>  
 <span data-ttu-id="147fb-111">在繼續本教學課程之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="147fb-111">Before you proceed with the tutorial, make sure:</span></span>  
  
-   <span data-ttu-id="147fb-112">您必須先完成中的步驟[之前您開發 BizTalk 應用程式](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6)。</span><span class="sxs-lookup"><span data-stu-id="147fb-112">You must have completed the steps in [Before You Develop BizTalk Applications](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).</span></span>  
  
-   <span data-ttu-id="147fb-113">您必須以 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="147fb-113">You must log on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-generate-schema-for-operations"></a><span data-ttu-id="147fb-114">若要產生結構描述的作業</span><span class="sxs-lookup"><span data-stu-id="147fb-114">To generate schema for operations</span></span>  
  
1.  <span data-ttu-id="147fb-115">建立新的 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-115">Create a new BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="147fb-116">此教學課程中，做為專案名稱， `Employee_PurchaseOrder`。</span><span class="sxs-lookup"><span data-stu-id="147fb-116">For this tutorial, name the project as `Employee_PurchaseOrder`.</span></span>  
  
2.  <span data-ttu-id="147fb-117">ADAPTER_SAMPLES SQL Server 資料庫使用以連接到[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-117">Connect to the ADAPTER_SAMPLES SQL Server database using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="147fb-118">如需如何使用連接的指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[連接到 Visual Studio 使用取用配接器服務增益集中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。</span><span class="sxs-lookup"><span data-stu-id="147fb-118">For instructions on how to connect using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Connect to SQL Server in Visual Studio Using Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="147fb-119">您也可以連接到 SQL Server 使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-119">You can also connect to SQL Server using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="147fb-120">不過，本教學課程中您會使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-120">However, for this tutorial you will use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
3.  <span data-ttu-id="147fb-121">產生結構描述的**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="147fb-121">Generate schema for the **Notification** inbound operation.</span></span>  
  
    1.  <span data-ttu-id="147fb-122">在連接到 ADAPTER_SAMPLES 資料庫之後, [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，從**選取合約型別**清單中，選取**服務 （輸入操作）**。</span><span class="sxs-lookup"><span data-stu-id="147fb-122">After connecting to the ADAPTER_SAMPLES database, in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], from the **Select contract type** list, select **Service (Inbound operations)**.</span></span>  
  
    2.  <span data-ttu-id="147fb-123">從**選取類別目錄**方塊中，按一下根節點 (**/**)。</span><span class="sxs-lookup"><span data-stu-id="147fb-123">From the **Select a category** box, click the root node (**/**).</span></span>  
  
    3.  <span data-ttu-id="147fb-124">從**可用的類別和作業**方塊中，選取**通知**按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="147fb-124">From the **Available categories and operations** box, select **Notification** and click **Add**.</span></span> <span data-ttu-id="147fb-125">**通知**作業現在會顯示在**加入的類別和作業**方塊。</span><span class="sxs-lookup"><span data-stu-id="147fb-125">The **Notification** operation is now displayed in the **Added categories and operations** box.</span></span> <span data-ttu-id="147fb-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="147fb-126">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="147fb-127">產生結構描述的**UPDATE_EMPLOYEE**上預存程序和插入作業**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="147fb-127">Generate schema for the **UPDATE_EMPLOYEE** stored procedure and the Insert operation on **Purchase_Order** table.</span></span>  
  
    1.  <span data-ttu-id="147fb-128">重複步驟 2，連接到 SQL Server 使用 ADAPTER_SAMPLES 資料庫[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147fb-128">Repeat step 2 to connect to ADAPTER_SAMPLES database in SQL Server using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="147fb-129">您無法在相同的時間來產生結構描述的輸入和輸出作業。</span><span class="sxs-lookup"><span data-stu-id="147fb-129">You cannot generate schema for inbound and outbound operations at the same time.</span></span> <span data-ttu-id="147fb-130">因此，在步驟 3，在您按一下之後**確定**產生結構描述**通知**作業，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]關閉。</span><span class="sxs-lookup"><span data-stu-id="147fb-130">Hence, in step 3, after you click **OK** to generate the schema for **Notification** operation, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] closes.</span></span> <span data-ttu-id="147fb-131">您必須重新連接到 SQL Server 資料庫來產生結構描述的傳出作業。</span><span class="sxs-lookup"><span data-stu-id="147fb-131">You must reconnect to the SQL Server database to generate schema for outbound operations.</span></span>  
  
    2.  <span data-ttu-id="147fb-132">從**選取合約型別**清單中，選取**用戶端 （輸出作業）**。</span><span class="sxs-lookup"><span data-stu-id="147fb-132">From the **Select contract type** list, select **Client (Outbound operations)**.</span></span>  
  
    3.  <span data-ttu-id="147fb-133">從**選取類別目錄**方塊中，按一下**Strongly-Typed 程序**節點。</span><span class="sxs-lookup"><span data-stu-id="147fb-133">From the **Select a category** box, click the **Strongly-Typed Procedures** node.</span></span> <span data-ttu-id="147fb-134">從**可用的類別和作業**s 方塊中，選取**UPDATE_EMPLOYEE**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="147fb-134">From the **Available categories and operation**s box, select **UPDATE_EMPLOYEE**, and then click **Add**.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="147fb-135">**UPDATE_EMPLOYEE**預存程序也會提供下**程序**節點。</span><span class="sxs-lookup"><span data-stu-id="147fb-135">The **UPDATE_EMPLOYEE** stored procedure is also available under the **Procedures** node.</span></span> <span data-ttu-id="147fb-136">不過，如果您產生結構描述的預存程序從**程序**節點，回應訊息結構描述無法在設計階段，但是之後執行預存程序可能會收到回應訊息。</span><span class="sxs-lookup"><span data-stu-id="147fb-136">However, if you generate schema for the stored procedure from under the **Procedures** node, the response message schema is not available at design-time but is received with the response message after you execute the stored procedure.</span></span>  
        >   
        >  <span data-ttu-id="147fb-137">在此教學課程中，您將對應的插入作業的輸入結構描述的預存程序的回應結構描述上**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="147fb-137">In this tutorial, you will map the response schema of the stored procedure to the input schema of the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="147fb-138">因此，您將需要的結構描述**UPDATE_EMPLOYEE**預存程序，在設計階段和您必須選取預存程序從**Strongly-Typed 程序**。</span><span class="sxs-lookup"><span data-stu-id="147fb-138">Therefore, you will need the schema for the **UPDATE_EMPLOYEE** stored procedure at design-time and you must select the stored procedure from under the **Strongly-Typed Procedures**.</span></span> <span data-ttu-id="147fb-139">如此一來，您會在設計階段收到預存程序的結構描述。</span><span class="sxs-lookup"><span data-stu-id="147fb-139">By doing so, you will get the schema of the stored procedure at design-time.</span></span>  
  
    4.  <span data-ttu-id="147fb-140">從**選取類別目錄**方塊中，展開 **資料表**節點中，按一下節點**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="147fb-140">From the **Select a category** box, expand the **Tables** node, and click the node for **Purchase_Order** table.</span></span> <span data-ttu-id="147fb-141">從**可用的類別和作業**s 方塊中，選取**插入**，按一下 **新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="147fb-141">From the **Available categories and operation**s box, select **Insert**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="147fb-142">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="147fb-142">What did I just do?</span></span>  
 <span data-ttu-id="147fb-143">在此步驟中，您會產生結構描述**通知**（輸入作業） **UPDATE_EMPLOYEE**預存程序，和**插入**作業**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="147fb-143">In this step, you generated schemas for **Notification** (inbound operation), **UPDATE_EMPLOYEE** stored procedure, and **Insert** operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="147fb-144">在您產生結構描述中之後,[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]將下列檔案加入至您的 BizTalk 專案：</span><span class="sxs-lookup"><span data-stu-id="147fb-144">After you generate the schema, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] adds the following files to your BizTalk project:</span></span>  
  
-   <span data-ttu-id="147fb-145">包含要叫用 SQL Server 上的作業的要求訊息的結構描述的 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="147fb-145">XSD files that contain schema for the request message to invoke operations on SQL Server.</span></span>  
  
-   <span data-ttu-id="147fb-146">可用來建立 Wcf-custom 傳送埠和接收埠中的 XML 繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="147fb-146">XML binding files that you can use to create WCF-Custom send and receive ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="147fb-147">如需有關如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋和使用 SQL 配接器的 SQL 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="147fb-147">For more information about generating schemas, see [Browse, search, and get metadata for SQL operations using the SQL adapter](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="147fb-148">後續步驟</span><span class="sxs-lookup"><span data-stu-id="147fb-148">Next Steps</span></span>  
 <span data-ttu-id="147fb-149">您可以建立訊息中的結構描述的 BizTalk 專案中[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="147fb-149">You create messages in the BizTalk project for the schemas in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147fb-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147fb-150">See Also</span></span>  
 [<span data-ttu-id="147fb-151">第 1 課： 產生結構描述和建立訊息</span><span class="sxs-lookup"><span data-stu-id="147fb-151">Lesson 1: Generate Schemas and Create Messages</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)