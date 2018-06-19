---
title: 教學課程： 將 BizTalk 專案移轉至 Oracle 資料庫配接器 |Microsoft 文件
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
ms.openlocfilehash: 0948e79b7f236bb20bbff9101195809bcc921a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215342"
---
# <a name="tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter"></a><span data-ttu-id="ad2f3-102">教學課程： 將 BizTalk 專案移轉至 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="ad2f3-102">Tutorial: Migrate BizTalk Projects to the Oracle Database adapter</span></span>
<span data-ttu-id="ad2f3-103">BizTalk ODBC 配接器，為 Microsoft BizTalk server 隨附 Oracle 資料庫與 WCF 架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="ad2f3-103">The BizTalk ODBC Adapter for Oracle Database that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="ad2f3-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="ad2f3-105">中繼資料擷取的經驗。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="ad2f3-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="ad2f3-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="ad2f3-108">可以使用配接器中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="ad2f3-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="ad2f3-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
 <span data-ttu-id="ad2f3-110">中的主題將說明這些差異所[移轉 BizTalk 專案建立使用 Oracle 資料庫的 BizTalk ODBC 配接器](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).</span></span>  
  
 <span data-ttu-id="ad2f3-111">不過，您可以變更使用 Oracle 資料庫的 BizTalk ODBC 配接器所建立的 BizTalk 專案，並讓它運作以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-111">However, you can make changes to the BizTalk project that was created using the BizTalk ODBC Adapter for Oracle Database and make it work with the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="ad2f3-112">本教學課程提供的變更，您應該對現有的 BizTalk 專案建立 BizTalk ODBC 配接器使用 Oracle 資料庫的指示。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the BizTalk ODBC Adapter for Oracle Database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad2f3-113">在此教學課程中，為了簡短起見，BizTalk ODBC Adapter for Oracle 資料庫將被稱為 「 vPrev Oracle 資料庫介面卡 」。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-113">In this tutorial, for the sake of brevity, the BizTalk ODBC Adapter for Oracle Database  will be referred to as “vPrev Oracle Database adapter.”</span></span> <span data-ttu-id="ad2f3-114">同樣地，使用 vPrev Oracle 資料庫配接器的 BizTalk 專案將被稱為 「 vPrev BizTalk 專案 」。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-114">Similarly, a BizTalk project that uses the vPrev Oracle Database adapter will be referred to as “vPrev BizTalk project.”</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="ad2f3-115">教學課程使用範例</span><span class="sxs-lookup"><span data-stu-id="ad2f3-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="ad2f3-116">本教學課程根據範例 (Oracle_Migration)，示範如何移轉 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-116">This tutorial is based upon a sample (Oracle_Migration) that demonstrates how to migrate a vPrev BizTalk project.</span></span> <span data-ttu-id="ad2f3-117">此範例之提供與 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-117">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="ad2f3-118">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-118">For more information, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ad2f3-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="ad2f3-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="ad2f3-120">您必須 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="ad2f3-121">本教學課程牽涉到執行插入作業的客戶資料表上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-121">This tutorial involves a BizTalk project that performs an Insert operation on a CUSTOMER table.</span></span> <span data-ttu-id="ad2f3-122">CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-122">The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span>  
  
-   <span data-ttu-id="ad2f3-123">您必須擁有執行插入作業使用 vPrev Oracle 資料庫配接器的 Oracle 資料庫上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-123">You must have a request message to perform an Insert operation on the Oracle database using the vPrev Oracle Database adapter.</span></span> <span data-ttu-id="ad2f3-124">要求訊息必須符合使用 vPrev Oracle 資料庫配接器所產生的插入作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-124">The request message must conform to the schema of the Insert operation generated using the vPrev Oracle Database adapter.</span></span>  
  
-   <span data-ttu-id="ad2f3-125">您必須先完成中的步驟[必要條件](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md)</span><span class="sxs-lookup"><span data-stu-id="ad2f3-125">You must have completed the steps in [Prerequisites](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md)</span></span> 
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="ad2f3-126">了解 BizTalk 專案建立使用配接器的先前版本</span><span class="sxs-lookup"><span data-stu-id="ad2f3-126">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="ad2f3-127">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="ad2f3-127">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
-   <span data-ttu-id="ad2f3-128">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-128">**BizTalk orchestration**.</span></span> <span data-ttu-id="ad2f3-129">這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Oracle 與 Oracle 資料庫的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-129">This is a simple orchestration that picks request messages from a file location, sends the request message to the Oracle database using an Oracle send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="ad2f3-130">**您想要在 Oracle 資料庫上執行作業的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-130">**Schema for the operation you wish to perform on the Oracle database**.</span></span> <span data-ttu-id="ad2f3-131">本教學課程牽涉到客戶資料表上的 Insert 作業執行 SCOTT 結構描述中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-131">This tutorial involves a BizTalk project that performs an Insert operation on the CUSTOMER table in the SCOTT schema.</span></span> <span data-ttu-id="ad2f3-132">CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-132">The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="ad2f3-133">產生客戶資料表的結構描述是 CUSTOMERService_CUSTOMER_x5d.xsd。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-133">The schema generated for the CUSTOMER table is CUSTOMERService_CUSTOMER_x5d.xsd.</span></span> <span data-ttu-id="ad2f3-134">此結構描述會產生使用 vPrev Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-134">This schema is generated using the vPrev Oracle Database adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad2f3-135">不同於 WCF 基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，vPrev Oracle 資料庫配接器不支援針對 Oracle 資料庫資料表上的特定作業產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-135">Unlike the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], the vPrev Oracle Database adapter does not support generating metadata for specific operations on an Oracle database table.</span></span> <span data-ttu-id="ad2f3-136">根據預設，配接器會產生結構描述支援的資料表的所有作業。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-136">By default, the adapter generates schema for all the operations supported on the table.</span></span> <span data-ttu-id="ad2f3-137">VPrev Oracle 資料庫配接器和 WCF 為基礎的多這類差異[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[移轉 BizTalk 專案建立使用 Oracle 資料庫的 BizTalk ODBC 配接器](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-137">For more such differences between the vPrev Oracle Database adapter and the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).</span></span>  
  
-   <span data-ttu-id="ad2f3-138">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-138">**Request message**.</span></span> <span data-ttu-id="ad2f3-139">要執行插入作業客戶資料表上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-139">The request message to perform an Insert operation on the CUSTOMER table.</span></span> <span data-ttu-id="ad2f3-140">因為由舊版的 Oracle 資料庫配接器顯示的插入作業結構描述符合要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-140">The schema of the request message conforms to the schema of the Insert operation as surfaced by the previous version of the Oracle Database adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="ad2f3-141">使用舊版的配接器如何移轉 BizTalk 專案建立</span><span class="sxs-lookup"><span data-stu-id="ad2f3-141">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="ad2f3-142">本移轉教學課程的目標是要讓您傳送要求訊息，符合 vPrev Oracle 資料庫配接器，使用 WCF 自訂連接埠，可以只處理符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-142">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by vPrev Oracle Database adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="ad2f3-143">因此，簡單地說，在移轉作業牽涉到設定不符合以 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-143">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="ad2f3-144">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="ad2f3-144">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="ad2f3-145">產生 SCOTT 的 Insert 作業的中繼資料。使用 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-145">Generate metadata for the Insert operation on the SCOTT.CUSTOMER table using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
-   <span data-ttu-id="ad2f3-146">執行使用 vPrev Oracle 資料庫配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-146">Map the request message for performing an Insert operation using the vPrev Oracle Database adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
-   <span data-ttu-id="ad2f3-147">使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-147">Map the response message received using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the response message for the vPrev Oracle Database adapter.</span></span>  
  
-   <span data-ttu-id="ad2f3-148">建立 WCF 自訂 Oracle 傳送接收 BizTalk Server 管理主控台中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-148">Create a WCF-Custom Oracle send-receive port in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="ad2f3-149">設定 WCF 自訂連接埠使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="ad2f3-149">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="ad2f3-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad2f3-150">See Also</span></span>  
[<span data-ttu-id="ad2f3-151">Biztalk Server 使用者入門</span><span class="sxs-lookup"><span data-stu-id="ad2f3-151">Getting started with Biztalk Server</span></span>](../../core/getting-started-with-biztalk-server.md)