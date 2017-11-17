---
title: "教學課程 1： 將 BizTalk 專案移轉至 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b4d2dbb-e37c-4d70-831f-3bdac3c28c97
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ca17095841fb154be9ec34766a34f174414cd82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-migrate-biztalk-projects-to-the-sql-adapter"></a><span data-ttu-id="b447e-102">教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="b447e-102">Tutorial 1: Migrate BizTalk Projects to the SQL adapter</span></span>
<span data-ttu-id="b447e-103">舊版的 SQL 配接器隨附於 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]與 WCF 架構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="b447e-103">The previous version of the SQL adapter that shipped with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] differs from the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="b447e-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="b447e-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="b447e-105">中繼資料擷取的經驗。</span><span class="sxs-lookup"><span data-stu-id="b447e-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="b447e-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="b447e-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="b447e-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="b447e-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="b447e-108">可以使用配接器中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="b447e-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="b447e-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="b447e-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
 <span data-ttu-id="b447e-110">移轉 BizTalk 專案建立使用 SQLadapter 舊版中的主題會說明這些差異。</span><span class="sxs-lookup"><span data-stu-id="b447e-110">These differences are explained in the topics within Migrating BizTalk Projects Created Using the Previous Version of the SQLadapter.</span></span>  
  
 <span data-ttu-id="b447e-111">不過，您可以變更使用舊版的配接器所建立的 BizTalk 專案，並讓它運作以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-111">However, you can make changes to the BizTalk project that was created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="b447e-112">本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="b447e-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b447e-113">在此教學課程中，為了簡短起見，舊版的 SQL 配接器將會稱為 vPrev SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="b447e-113">In this tutorial, for the sake of brevity, the previous version of the SQL adapter will be referred to as vPrev SQL adapter.</span></span> <span data-ttu-id="b447e-114">同樣地，使用 vPrev SQL 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b447e-114">Similarly, a BizTalk project that uses the vPrev SQL adapter will be referred to as vPrev BizTalk project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b447e-115">本教學課程提供如何執行基本的插入作業會在 SQL Server 資料庫資料表 vPrev SQL 配接器 BizTalk 專案，將移轉的指引。</span><span class="sxs-lookup"><span data-stu-id="b447e-115">This tutorial provides guidance on how to migrate a vPrev SQL adapter BizTalk project that performs a basic insert operation on a SQL Server database table.</span></span> <span data-ttu-id="b447e-116">本教學課程未涵蓋所有可能的案例，從 vPrev SQL 配接器移轉至新的 WCF 架構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-116">This tutorial does not cover all possible scenarios for migration from the vPrev SQL adapter to the new WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="b447e-117">您必須使用本移轉教學課程為基礎，並據此修改您現有的專案相關的變更。</span><span class="sxs-lookup"><span data-stu-id="b447e-117">You must use this migration tutorial as a foundation and modify accordingly to make changes that are relevant to your existing project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="b447e-118">教學課程使用範例</span><span class="sxs-lookup"><span data-stu-id="b447e-118">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="b447e-119">本教學課程根據範例 (SQL_Migration)，示範如何移轉 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b447e-119">This tutorial is based upon a sample (SQL_Migration) that demonstrates how to migrate a vPrev BizTalk project.</span></span> <span data-ttu-id="b447e-120">此範例之提供與 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-120">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="b447e-121">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="b447e-121">For more information, see Samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b447e-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="b447e-122">Prerequisites</span></span>  
  
-   <span data-ttu-id="b447e-123">您必須 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b447e-123">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="b447e-124">本教學課程牽涉到 SQL Server 資料庫中執行插入作業的客戶資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b447e-124">This tutorial involves a BizTalk project that performs an Insert operation on a Customer table in the SQL Server database.</span></span> <span data-ttu-id="b447e-125">Customer 資料表具有下列設計：</span><span class="sxs-lookup"><span data-stu-id="b447e-125">The Customer table has the following design:</span></span>  
  
    |<span data-ttu-id="b447e-126">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="b447e-126">Column Name</span></span>|<span data-ttu-id="b447e-127">Description</span><span class="sxs-lookup"><span data-stu-id="b447e-127">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="b447e-128">v_custid</span><span class="sxs-lookup"><span data-stu-id="b447e-128">v_custid</span></span>|<span data-ttu-id="b447e-129">主索引鍵，整數類型，識別欄位</span><span class="sxs-lookup"><span data-stu-id="b447e-129">Primary key, integer type, identity field</span></span>|  
    |<span data-ttu-id="b447e-130">名稱</span><span class="sxs-lookup"><span data-stu-id="b447e-130">Name</span></span>|<span data-ttu-id="b447e-131">nchar(10) 類型</span><span class="sxs-lookup"><span data-stu-id="b447e-131">nchar(10) type</span></span>|  
  
-   <span data-ttu-id="b447e-132">您必須擁有執行插入作業使用 vPrev SQL 配接器的 SQL Server 資料庫的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b447e-132">You must have a request message to perform an Insert operation on the SQL Server database using the vPrev SQL adapter.</span></span> <span data-ttu-id="b447e-133">要求訊息必須符合使用 vPrev SQL 配接器所產生的插入作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b447e-133">The request message must conform to the schema of the Insert operation generated using the vPrev SQL adapter.</span></span>  
  
-   <span data-ttu-id="b447e-134">您應已完成的步驟[之前您開發 BizTalk 應用程式](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6)。</span><span class="sxs-lookup"><span data-stu-id="b447e-134">You should have completed the steps in [Before You Develop BizTalk Applications](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).</span></span>  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="b447e-135">了解 BizTalk 專案建立使用配接器的先前版本</span><span class="sxs-lookup"><span data-stu-id="b447e-135">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="b447e-136">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="b447e-136">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
-   <span data-ttu-id="b447e-137">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="b447e-137">**BizTalk orchestration**.</span></span> <span data-ttu-id="b447e-138">這是簡單的協調流程會挑選要求訊息的檔案位置、 傳送要求訊息至 SQL Server 資料庫使用 Wcf-custom 傳送接收連接埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="b447e-138">This is a simple orchestration that picks request messages from a file location, sends the request message to the SQL Server database using a WCF-Custom send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="b447e-139">**您想要在 SQL Server 資料庫上執行作業的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="b447e-139">**Schema for the operation you wish to perform on the SQL Server database**.</span></span> <span data-ttu-id="b447e-140">本教學課程牽涉到執行插入作業客戶資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b447e-140">This tutorial involves a BizTalk project that performs an Insert operation on the Customer table.</span></span> <span data-ttu-id="b447e-141">產生客戶資料表的結構描述是 InsertCustomerService.xsd。</span><span class="sxs-lookup"><span data-stu-id="b447e-141">The schema generated for the Customer table is InsertCustomerService.xsd.</span></span> <span data-ttu-id="b447e-142">此結構描述會產生使用 vPrev SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="b447e-142">This schema is generated using the vPrev SQL adapter.</span></span>  
  
-   <span data-ttu-id="b447e-143">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="b447e-143">**Request message**.</span></span> <span data-ttu-id="b447e-144">要執行插入作業客戶資料表上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b447e-144">The request message to perform an Insert operation on the Customer table.</span></span> <span data-ttu-id="b447e-145">因為由舊版的 SQL 配接器顯示的插入作業結構描述符合要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b447e-145">The schema of the request message conforms to the schema of the Insert operation as surfaced by the previous version of the SQL adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="b447e-146">使用舊版的配接器如何移轉 BizTalk 專案建立</span><span class="sxs-lookup"><span data-stu-id="b447e-146">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="b447e-147">本移轉教學課程的目標是要讓您傳送要求訊息，符合 vPrev SQL 配接器使用 WCF 自訂連接埠，可以只處理符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-147">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by vPrev SQL adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="b447e-148">因此，簡單地說，在移轉作業牽涉到設定不符合以 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b447e-148">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="b447e-149">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b447e-149">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b447e-150">產生使用 WCF 為基礎的客戶資料表的 Insert 作業的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-150">Generate metadata for the Insert operation on the Customer table using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="b447e-151">執行使用 vPrev SQL 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b447e-151">Map the request message for performing an Insert operation using the vPrev SQL adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="b447e-152">使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]vPrev SQL 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="b447e-152">Map the response message received using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to the response message for the vPrev SQL adapter.</span></span>  
  
-   <span data-ttu-id="b447e-153">建立 WCF 自訂 SQL 傳送-接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b447e-153">Create a WCF-Custom SQL send-receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
-   <span data-ttu-id="b447e-154">設定 WCF 自訂連接埠使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="b447e-154">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b447e-155">本節內容</span><span class="sxs-lookup"><span data-stu-id="b447e-155">In This Section</span></span>  
  
-   [<span data-ttu-id="b447e-156">步驟 1： 修改 vPrev 使用 SQL 配接器的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="b447e-156">Step 1: Modify the vPrev BizTalk Project using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="b447e-157">步驟 2： 使用 SQL 配接器的 BizTalk Server 管理主控台中設定協調流程</span><span class="sxs-lookup"><span data-stu-id="b447e-157">Step 2: Configure the Orchestration in BizTalk Server Administration Console using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)  
  
-   [<span data-ttu-id="b447e-158">步驟 3： 測試移轉應用程式使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="b447e-158">Step 3: Test the Migrated Application that uses the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="b447e-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b447e-159">See Also</span></span>  
 [<span data-ttu-id="b447e-160">SQL 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="b447e-160">SQL Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)