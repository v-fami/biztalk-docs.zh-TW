---
title: 教學課程 2： Siebel 中的移轉 BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a2a1828-8cc8-4b80-99bd-c083c04e5d04
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ada19454c3d2aef1c725987d8d37f7b98a2d1c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996431"
---
# <a name="tutorial-2-migrating-biztalk-projects-in-siebel"></a><span data-ttu-id="1ab5b-102">教學課程 2： 移轉 BizTalk 專案中 Siebel</span><span class="sxs-lookup"><span data-stu-id="1ab5b-102">Tutorial 2: Migrating BizTalk Projects in Siebel</span></span>
<span data-ttu-id="1ab5b-103">Siebel 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="1ab5b-103">The previous version of the Siebel adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in many aspects, including:</span></span>  
  
- <span data-ttu-id="1ab5b-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-104">The design-time experience of creating a BizTalk project.</span></span>  
  
- <span data-ttu-id="1ab5b-105">中繼資料的擷取體驗。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-105">The metadata retrieval experience.</span></span>  
  
- <span data-ttu-id="1ab5b-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-106">Schema file name and namespace.</span></span>  
  
- <span data-ttu-id="1ab5b-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-107">Data type mappings.</span></span>  
  
- <span data-ttu-id="1ab5b-108">可以使用配接器執行的作業。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-108">The operations that can be performed using the adapter.</span></span>  
  
- <span data-ttu-id="1ab5b-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="1ab5b-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
  <span data-ttu-id="1ab5b-110">中的主題會說明這些差異[移轉 BizTalk 專案建立使用 Siebel 配接器的上一個版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the Siebel Adapter](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).</span></span>  
  
  <span data-ttu-id="1ab5b-111">不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
  <span data-ttu-id="1ab5b-112">本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ab5b-113">在本教學課程中，為了保持簡潔，舊版的 Siebel 配接器會稱為 vPrev Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-113">In this tutorial, for the sake of brevity, the previous version of the Siebel adapter will be referred to as vPrev Siebel adapter.</span></span> <span data-ttu-id="1ab5b-114">同樣地，使用 vPrev Siebel 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-114">Similarly, a BizTalk project that uses the vPrev Siebel adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="1ab5b-115">用於本教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="1ab5b-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="1ab5b-116">本教學課程是以示範如何移轉 vPrev BizTalk 專案，執行插入作業帳戶 Siebel 商務元件上的範例 (Siebel_BussComp_Migration) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-116">This tutorial is based upon a sample (Siebel_BussComp_Migration) that demonstrates how to migrate a vPrev BizTalk project that performs an Insert operation on the Account Siebel business component.</span></span> <span data-ttu-id="1ab5b-117">提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-117">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="1ab5b-118">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-118">For more information, see [Adapter Sample](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1ab5b-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ab5b-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="1ab5b-120">您必須具有 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="1ab5b-121">本教學課程包含執行插入作業帳戶商務元件上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-121">This tutorial involves a BizTalk project that performs an Insert operation on the Account business component.</span></span>  
  
-   <span data-ttu-id="1ab5b-122">您必須擁有執行插入作業帳戶商務元件使用 vPrev Siebel 配接器上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-122">You must have a request message to perform an Insert operation on the Account business component using the vPrev Siebel adapter.</span></span> <span data-ttu-id="1ab5b-123">使用 vPrev Siebel 配接器所產生的插入作業的結構描述必須符合 「 要求 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-123">The request message must conform to the schema of the Insert operation generated using the vPrev Siebel adapter.</span></span>  
  
-   <span data-ttu-id="1ab5b-124">您必須先完成中的步驟[要建立 Siebel 應用程式的必要條件](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-124">You must have completed the steps in [Prerequisites to create Siebel applications](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md).</span></span>  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="1ab5b-125">了解 BizTalk 專案使用舊版配接器的建立</span><span class="sxs-lookup"><span data-stu-id="1ab5b-125">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="1ab5b-126">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="1ab5b-126">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
- <span data-ttu-id="1ab5b-127">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-127">**BizTalk orchestration**.</span></span> <span data-ttu-id="1ab5b-128">這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Siebel Siebel 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-128">This is a simple orchestration that picks request messages from a file location, sends the request message to the Siebel system using a Siebel send-receive port, receives the response, and saves it to another file location.</span></span>  
  
- <span data-ttu-id="1ab5b-129">**您想要在 Siebel 商務元件上執行的作業結構描述**。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-129">**Schema for the operation you wish to perform on the Siebel business component**.</span></span> <span data-ttu-id="1ab5b-130">本教學課程包含執行插入作業帳戶商務元件上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-130">This tutorial involves a BizTalk project that performs an Insert operation on the Account business component.</span></span> <span data-ttu-id="1ab5b-131">帳戶商務元件所產生的結構描述是 AccountService_Account_x5d.xsd。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-131">The schema generated for the Account business component is AccountService_Account_x5d.xsd.</span></span> <span data-ttu-id="1ab5b-132">此結構描述是使用 vPrev Siebel 配接器所產生的。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-132">This schema is generated using the vPrev Siebel adapter.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="1ab5b-133">不同於以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，vPrev Siebel 配接器不支援在商務元件上的特定作業產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-133">Unlike the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the vPrev Siebel adapter does not support generating metadata for specific operations on a business component.</span></span> <span data-ttu-id="1ab5b-134">根據預設，配接器會產生結構描述支援商務元件上的所有作業。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-134">By default, the adapter generates schema for all the operations supported on the business component.</span></span> <span data-ttu-id="1ab5b-135">多個這類之間的差異 vPrev Siebel 配接器以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 移轉 BizTalk 專案建立使用 Siebel 配接器的上一個版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-135">For more such differences between the vPrev Siebel adapter and the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Migrating BizTalk Projects Created Using the Previous Version of the Siebel Adapter](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).</span></span>  
  
- <span data-ttu-id="1ab5b-136">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-136">**Request message**.</span></span> <span data-ttu-id="1ab5b-137">要執行 Insert 作業帳戶商務元件上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-137">The request message to perform an Insert operation on the Account business component.</span></span> <span data-ttu-id="1ab5b-138">因為呈現 vPrev Siebel 配接器的插入作業結構描述符合要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-138">The schema of the request message conforms to the schema of the Insert operation as surfaced by the vPrev Siebel adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="1ab5b-139">如何移轉 BizTalk 專案可讓您建立使用舊版的配接器</span><span class="sxs-lookup"><span data-stu-id="1ab5b-139">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="1ab5b-140">本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev Siebel 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-140">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by the vPrev Siebel adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="1ab5b-141">因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-141">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="1ab5b-142">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1ab5b-142">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
- <span data-ttu-id="1ab5b-143">產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-143">Generate metadata for the Insert operation on the Account business component using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
- <span data-ttu-id="1ab5b-144">執行插入作業使用 vPrev Siebel 配接器要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-144">Map the request message for performing an Insert operation using the vPrev Siebel adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
- <span data-ttu-id="1ab5b-145">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-145">Map the response message received using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the response message for the vPrev Siebel adapter.</span></span>  
  
- <span data-ttu-id="1ab5b-146">建立 WCF 自訂 Siebel 傳送接收 BizTalk Server 管理主控台中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-146">Create a WCF-Custom Siebel send-receive port in the BizTalk Server Administration console.</span></span>  
  
- <span data-ttu-id="1ab5b-147">設定 WCF 自訂連接埠，若要使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="1ab5b-147">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ab5b-148">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ab5b-148">In This Section</span></span>  
  
-   [<span data-ttu-id="1ab5b-149">步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ab5b-149">Step 1: Modify the vPrev BizTalk Project in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/step-1-modify-the-vprev-biztalk-project-in-oracle-database.md)  
  
-   [<span data-ttu-id="1ab5b-150">步驟 2： 設定協調流程中使用 ORacle 資料庫配接器的 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="1ab5b-150">Step 2: Configure the Orchestration in BizTalk Server Administration Console to use the ORacle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)  
  
-   [<span data-ttu-id="1ab5b-151">步驟 3： 測試移轉應用程式與 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="1ab5b-151">Step 3: Test the Migrated Application with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ab5b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ab5b-152">See Also</span></span>  
 [<span data-ttu-id="1ab5b-153">Siebel 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="1ab5b-153">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)