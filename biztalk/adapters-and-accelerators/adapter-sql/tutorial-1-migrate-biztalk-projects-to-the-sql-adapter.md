---
title: 教學課程 1： 將 BizTalk 專案移轉至 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b4d2dbb-e37c-4d70-831f-3bdac3c28c97
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea64d98404d247a47e8cad8df421c81752fe63e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013303"
---
# <a name="tutorial-1-migrate-biztalk-projects-to-the-sql-adapter"></a><span data-ttu-id="d4f3b-102">教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="d4f3b-102">Tutorial 1: Migrate BizTalk Projects to the SQL adapter</span></span>
<span data-ttu-id="d4f3b-103">舊版的 SQL 配接器隨附於 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]不同於以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="d4f3b-103">The previous version of the SQL adapter that shipped with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] differs from the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in many aspects, including:</span></span>  
  
- <span data-ttu-id="d4f3b-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-104">The design-time experience of creating a BizTalk project.</span></span>  
  
- <span data-ttu-id="d4f3b-105">中繼資料的擷取體驗。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-105">The metadata retrieval experience.</span></span>  
  
- <span data-ttu-id="d4f3b-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-106">Schema file name and namespace.</span></span>  
  
- <span data-ttu-id="d4f3b-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-107">Data type mappings.</span></span>  
  
- <span data-ttu-id="d4f3b-108">可以使用配接器執行的作業。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-108">The operations that can be performed using the adapter.</span></span>  
  
- <span data-ttu-id="d4f3b-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="d4f3b-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
  <span data-ttu-id="d4f3b-110">移轉 BizTalk 專案建立使用 SQLadapter 舊版的主題會說明這些差異。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-110">These differences are explained in the topics within Migrating BizTalk Projects Created Using the Previous Version of the SQLadapter.</span></span>  
  
  <span data-ttu-id="d4f3b-111">不過，您可以對使用舊版的配接器所建立的 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-111">However, you can make changes to the BizTalk project that was created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
  <span data-ttu-id="d4f3b-112">本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4f3b-113">在本教學課程中，為了保持簡潔，舊版的 SQL 配接器將會被稱為 vPrev SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-113">In this tutorial, for the sake of brevity, the previous version of the SQL adapter will be referred to as vPrev SQL adapter.</span></span> <span data-ttu-id="d4f3b-114">同樣地，使用 vPrev SQL 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-114">Similarly, a BizTalk project that uses the vPrev SQL adapter will be referred to as vPrev BizTalk project.</span></span>  
> 
> [!IMPORTANT]
>  <span data-ttu-id="d4f3b-115">本教學課程提供有關如何移轉 vPrev SQL 配接器 BizTalk 專案的執行基本的插入作業會在 SQL Server 資料庫資料表的指引。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-115">This tutorial provides guidance on how to migrate a vPrev SQL adapter BizTalk project that performs a basic insert operation on a SQL Server database table.</span></span> <span data-ttu-id="d4f3b-116">本教學課程並未涵蓋所有可能的案例，從 vPrev SQL 配接器移轉至新的 WCF 式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-116">This tutorial does not cover all possible scenarios for migration from the vPrev SQL adapter to the new WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="d4f3b-117">您必須使用本移轉教學課程中，做為基礎，並據此修改要與您現有的專案相關的變更。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-117">You must use this migration tutorial as a foundation and modify accordingly to make changes that are relevant to your existing project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="d4f3b-118">用於本教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="d4f3b-118">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="d4f3b-119">本教學課程是以示範如何移轉 vPrev BizTalk 專案的範例 (SQL_Migration) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-119">This tutorial is based upon a sample (SQL_Migration) that demonstrates how to migrate a vPrev BizTalk project.</span></span> <span data-ttu-id="d4f3b-120">提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-120">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d4f3b-121">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-121">For more information, see Samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4f3b-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="d4f3b-122">Prerequisites</span></span>  
  
-   <span data-ttu-id="d4f3b-123">您必須具有 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-123">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="d4f3b-124">本教學課程包含 SQL Server 資料庫中，執行插入作業的客戶資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-124">This tutorial involves a BizTalk project that performs an Insert operation on a Customer table in the SQL Server database.</span></span> <span data-ttu-id="d4f3b-125">Customer 資料表具有下列設計：</span><span class="sxs-lookup"><span data-stu-id="d4f3b-125">The Customer table has the following design:</span></span>  
  
    |<span data-ttu-id="d4f3b-126">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="d4f3b-126">Column Name</span></span>|<span data-ttu-id="d4f3b-127">描述</span><span class="sxs-lookup"><span data-stu-id="d4f3b-127">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="d4f3b-128">v_custid</span><span class="sxs-lookup"><span data-stu-id="d4f3b-128">v_custid</span></span>|<span data-ttu-id="d4f3b-129">主索引鍵，整數類型，識別欄位</span><span class="sxs-lookup"><span data-stu-id="d4f3b-129">Primary key, integer type, identity field</span></span>|  
    |<span data-ttu-id="d4f3b-130">[屬性]</span><span class="sxs-lookup"><span data-stu-id="d4f3b-130">Name</span></span>|<span data-ttu-id="d4f3b-131">nchar(10) 類型</span><span class="sxs-lookup"><span data-stu-id="d4f3b-131">nchar(10) type</span></span>|  
  
-   <span data-ttu-id="d4f3b-132">您必須擁有執行插入作業使用 vPrev SQL 配接器的 SQL Server 資料庫的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-132">You must have a request message to perform an Insert operation on the SQL Server database using the vPrev SQL adapter.</span></span> <span data-ttu-id="d4f3b-133">產生使用 vPrev SQL 配接器的插入作業的結構描述必須符合 「 要求 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-133">The request message must conform to the schema of the Insert operation generated using the vPrev SQL adapter.</span></span>  
  
-   <span data-ttu-id="d4f3b-134">您應已完成中的步驟[之前您開發 BizTalk 應用程式](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6)。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-134">You should have completed the steps in [Before You Develop BizTalk Applications](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).</span></span>  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="d4f3b-135">了解 BizTalk 專案使用舊版配接器的建立</span><span class="sxs-lookup"><span data-stu-id="d4f3b-135">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="d4f3b-136">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="d4f3b-136">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
-   <span data-ttu-id="d4f3b-137">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-137">**BizTalk orchestration**.</span></span> <span data-ttu-id="d4f3b-138">這是簡單的協調流程會挑選要求訊息的檔案位置，傳送要求訊息至 SQL Server 資料庫使用 Wcf-custom 傳送接收連接埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-138">This is a simple orchestration that picks request messages from a file location, sends the request message to the SQL Server database using a WCF-Custom send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="d4f3b-139">**您想要在 SQL Server 資料庫上執行的作業結構描述**。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-139">**Schema for the operation you wish to perform on the SQL Server database**.</span></span> <span data-ttu-id="d4f3b-140">本教學課程包含執行插入作業在 Customer 資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-140">This tutorial involves a BizTalk project that performs an Insert operation on the Customer table.</span></span> <span data-ttu-id="d4f3b-141">產生針對 Customer 資料表的結構描述是 InsertCustomerService.xsd。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-141">The schema generated for the Customer table is InsertCustomerService.xsd.</span></span> <span data-ttu-id="d4f3b-142">此結構描述會產生使用 vPrev SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-142">This schema is generated using the vPrev SQL adapter.</span></span>  
  
-   <span data-ttu-id="d4f3b-143">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-143">**Request message**.</span></span> <span data-ttu-id="d4f3b-144">要執行插入作業在 Customer 資料表上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-144">The request message to perform an Insert operation on the Customer table.</span></span> <span data-ttu-id="d4f3b-145">要求訊息的結構描述符合的插入作業結構描述，因為由舊版的 SQL 配接器顯示。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-145">The schema of the request message conforms to the schema of the Insert operation as surfaced by the previous version of the SQL adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="d4f3b-146">如何移轉 BizTalk 專案可讓您建立使用舊版的配接器</span><span class="sxs-lookup"><span data-stu-id="d4f3b-146">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="d4f3b-147">本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev SQL 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-147">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by vPrev SQL adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="d4f3b-148">因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-148">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="d4f3b-149">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d4f3b-149">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
- <span data-ttu-id="d4f3b-150">產生使用 WCF 為基礎的 Customer 資料表的 Insert 作業的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-150">Generate metadata for the Insert operation on the Customer table using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
- <span data-ttu-id="d4f3b-151">執行插入作業使用 vPrev SQL 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-151">Map the request message for performing an Insert operation using the vPrev SQL adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
- <span data-ttu-id="d4f3b-152">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]vPrev SQL 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-152">Map the response message received using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to the response message for the vPrev SQL adapter.</span></span>  
  
- <span data-ttu-id="d4f3b-153">建立 WCF 自訂 SQL 傳送接收中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-153">Create a WCF-Custom SQL send-receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
- <span data-ttu-id="d4f3b-154">設定 WCF 自訂連接埠，若要使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="d4f3b-154">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4f3b-155">本節內容</span><span class="sxs-lookup"><span data-stu-id="d4f3b-155">In This Section</span></span>  
  
-   [<span data-ttu-id="d4f3b-156">步驟 1： 修改 vPrev BizTalk 專案使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="d4f3b-156">Step 1: Modify the vPrev BizTalk Project using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="d4f3b-157">步驟 2： 設定協調流程中使用 SQL 配接器的 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="d4f3b-157">Step 2: Configure the Orchestration in BizTalk Server Administration Console using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)  
  
-   [<span data-ttu-id="d4f3b-158">步驟 3： 測試移轉應用程式使用 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="d4f3b-158">Step 3: Test the Migrated Application that uses the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="d4f3b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4f3b-159">See Also</span></span>  
 [<span data-ttu-id="d4f3b-160">SQL 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="d4f3b-160">SQL Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)