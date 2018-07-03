---
title: 教學課程： 移轉 BizTalk 專案到 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a393219-bae8-4e08-acc8-76986600d0de
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdde0ae8992fc9ae0c7dd30b91b7f38733c1de2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999839"
---
# <a name="tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter"></a><span data-ttu-id="3f988-102">教學課程： 移轉 BizTalk 專案到 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="3f988-102">Tutorial: Migrate BizTalk Projects to the Oracle Database adapter</span></span>
<span data-ttu-id="3f988-103">不同於以 WCF 為基礎的 BizTalk ODBC 配接器，與 Microsoft BizTalk Server 中的出貨針對 Oracle 資料庫[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="3f988-103">The BizTalk ODBC Adapter for Oracle Database that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in many aspects, including:</span></span>  
  
- <span data-ttu-id="3f988-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="3f988-104">The design-time experience of creating a BizTalk project.</span></span>  
  
- <span data-ttu-id="3f988-105">中繼資料的擷取體驗。</span><span class="sxs-lookup"><span data-stu-id="3f988-105">The metadata retrieval experience.</span></span>  
  
- <span data-ttu-id="3f988-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="3f988-106">Schema file name and namespace.</span></span>  
  
- <span data-ttu-id="3f988-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="3f988-107">Data type mappings.</span></span>  
  
- <span data-ttu-id="3f988-108">可以使用配接器執行的作業。</span><span class="sxs-lookup"><span data-stu-id="3f988-108">The operations that can be performed using the adapter.</span></span>  
  
- <span data-ttu-id="3f988-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="3f988-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
  <span data-ttu-id="3f988-110">中的主題會說明這些差異[移轉 BizTalk 專案建立使用 BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。</span><span class="sxs-lookup"><span data-stu-id="3f988-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).</span></span>  
  
  <span data-ttu-id="3f988-111">不過，您可以對 Oracle 資料庫中使用 BizTalk ODBC 配接器所建立的 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f988-111">However, you can make changes to the BizTalk project that was created using the BizTalk ODBC Adapter for Oracle Database and make it work with the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
  <span data-ttu-id="3f988-112">本教學課程會提供指示，您應該對現有的 Oracle 資料庫中使用 BizTalk ODBC 配接器所建立的 BizTalk 專案的變更。</span><span class="sxs-lookup"><span data-stu-id="3f988-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the BizTalk ODBC Adapter for Oracle Database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f988-113">在本教學課程中，為了保持簡潔，Oracle 資料庫的 BizTalk ODBC 配接器會稱為 「 vPrev Oracle 資料庫配接器 」。</span><span class="sxs-lookup"><span data-stu-id="3f988-113">In this tutorial, for the sake of brevity, the BizTalk ODBC Adapter for Oracle Database  will be referred to as “vPrev Oracle Database adapter.”</span></span> <span data-ttu-id="3f988-114">同樣地，使用 vPrev Oracle 資料庫配接器的 BizTalk 專案會被稱為 「 vPrev BizTalk 專案 」。</span><span class="sxs-lookup"><span data-stu-id="3f988-114">Similarly, a BizTalk project that uses the vPrev Oracle Database adapter will be referred to as “vPrev BizTalk project.”</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="3f988-115">用於本教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="3f988-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="3f988-116">本教學課程是以示範如何移轉 vPrev BizTalk 專案的範例 (Oracle_Migration) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="3f988-116">This tutorial is based upon a sample (Oracle_Migration) that demonstrates how to migrate a vPrev BizTalk project.</span></span> <span data-ttu-id="3f988-117">提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f988-117">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3f988-118">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="3f988-118">For more information, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3f988-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="3f988-119">Prerequisites</span></span>  
  
- <span data-ttu-id="3f988-120">您必須具有 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3f988-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="3f988-121">本教學課程包含執行插入作業的客戶資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3f988-121">This tutorial involves a BizTalk project that performs an Insert operation on a CUSTOMER table.</span></span> <span data-ttu-id="3f988-122">CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="3f988-122">The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span>  
  
- <span data-ttu-id="3f988-123">您必須擁有執行插入作業使用 vPrev Oracle 資料庫配接器的 Oracle 資料庫上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3f988-123">You must have a request message to perform an Insert operation on the Oracle database using the vPrev Oracle Database adapter.</span></span> <span data-ttu-id="3f988-124">使用 vPrev Oracle 資料庫配接器所產生的插入作業的結構描述必須符合 「 要求 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="3f988-124">The request message must conform to the schema of the Insert operation generated using the vPrev Oracle Database adapter.</span></span>  
  
- <span data-ttu-id="3f988-125">您必須先完成中的步驟[必要條件](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md)</span><span class="sxs-lookup"><span data-stu-id="3f988-125">You must have completed the steps in [Prerequisites](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md)</span></span> 
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="3f988-126">了解 BizTalk 專案使用舊版配接器的建立</span><span class="sxs-lookup"><span data-stu-id="3f988-126">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="3f988-127">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="3f988-127">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
- <span data-ttu-id="3f988-128">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="3f988-128">**BizTalk orchestration**.</span></span> <span data-ttu-id="3f988-129">這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Oracle 的 Oracle 資料庫的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="3f988-129">This is a simple orchestration that picks request messages from a file location, sends the request message to the Oracle database using an Oracle send-receive port, receives the response, and saves it to another file location.</span></span>  
  
- <span data-ttu-id="3f988-130">**您想要的 Oracle 資料庫上執行的作業結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3f988-130">**Schema for the operation you wish to perform on the Oracle database**.</span></span> <span data-ttu-id="3f988-131">本教學課程包含 SCOTT 結構描述中，執行插入作業在 CUSTOMER 資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3f988-131">This tutorial involves a BizTalk project that performs an Insert operation on the CUSTOMER table in the SCOTT schema.</span></span> <span data-ttu-id="3f988-132">CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="3f988-132">The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="3f988-133">產生針對 CUSTOMER 資料表的結構描述是 CUSTOMERService_CUSTOMER_x5d.xsd。</span><span class="sxs-lookup"><span data-stu-id="3f988-133">The schema generated for the CUSTOMER table is CUSTOMERService_CUSTOMER_x5d.xsd.</span></span> <span data-ttu-id="3f988-134">此結構描述是使用 vPrev Oracle 資料庫配接器所產生的。</span><span class="sxs-lookup"><span data-stu-id="3f988-134">This schema is generated using the vPrev Oracle Database adapter.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="3f988-135">不同於以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，vPrev Oracle 資料庫配接器不支援在 Oracle 資料庫資料表上的特定作業產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3f988-135">Unlike the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], the vPrev Oracle Database adapter does not support generating metadata for specific operations on an Oracle database table.</span></span> <span data-ttu-id="3f988-136">根據預設，配接器會產生結構描述支援的資料表的所有作業。</span><span class="sxs-lookup"><span data-stu-id="3f988-136">By default, the adapter generates schema for all the operations supported on the table.</span></span> <span data-ttu-id="3f988-137">多個這類之間的差異 vPrev Oracle 資料庫配接器以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 移轉 BizTalk 專案建立使用 BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。</span><span class="sxs-lookup"><span data-stu-id="3f988-137">For more such differences between the vPrev Oracle Database adapter and the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).</span></span>  
  
- <span data-ttu-id="3f988-138">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="3f988-138">**Request message**.</span></span> <span data-ttu-id="3f988-139">要執行插入作業在 CUSTOMER 資料表上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3f988-139">The request message to perform an Insert operation on the CUSTOMER table.</span></span> <span data-ttu-id="3f988-140">如先前版本的 Oracle 資料庫配接器所呈現的插入作業結構描述符合要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3f988-140">The schema of the request message conforms to the schema of the Insert operation as surfaced by the previous version of the Oracle Database adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="3f988-141">如何移轉 BizTalk 專案可讓您建立使用舊版的配接器</span><span class="sxs-lookup"><span data-stu-id="3f988-141">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="3f988-142">本移轉教學課程的目標是要讓您傳送要求訊息，產生 vPrev Oracle 資料庫配接器，使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息結構描述符合[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f988-142">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by vPrev Oracle Database adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="3f988-143">因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3f988-143">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="3f988-144">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3f988-144">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
- <span data-ttu-id="3f988-145">產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f988-145">Generate metadata for the Insert operation on the SCOTT.CUSTOMER table using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
- <span data-ttu-id="3f988-146">執行插入作業使用 vPrev Oracle 資料庫配接器的要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f988-146">Map the request message for performing an Insert operation using the vPrev Oracle Database adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
- <span data-ttu-id="3f988-147">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3f988-147">Map the response message received using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the response message for the vPrev Oracle Database adapter.</span></span>  
  
- <span data-ttu-id="3f988-148">建立 WCF 自訂 Oracle 傳送接收 BizTalk Server 管理主控台中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3f988-148">Create a WCF-Custom Oracle send-receive port in the BizTalk Server Administration console.</span></span>  
  
- <span data-ttu-id="3f988-149">設定 WCF 自訂連接埠，若要使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="3f988-149">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="3f988-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f988-150">See Also</span></span>  
[<span data-ttu-id="3f988-151">開始使用 Biztalk Server</span><span class="sxs-lookup"><span data-stu-id="3f988-151">Getting started with Biztalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)