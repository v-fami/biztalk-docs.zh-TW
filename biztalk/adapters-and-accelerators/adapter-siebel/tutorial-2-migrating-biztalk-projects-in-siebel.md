---
title: 教學課程 2： Siebel 中的移轉 BizTalk 專案 |Microsoft 文件
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
ms.openlocfilehash: 2b8d138d348e750102d82a4aba2e39bc7d119c8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223006"
---
# <a name="tutorial-2-migrating-biztalk-projects-in-siebel"></a><span data-ttu-id="088c7-102">教學課程 2： 移轉 Siebel 中的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="088c7-102">Tutorial 2: Migrating BizTalk Projects in Siebel</span></span>
<span data-ttu-id="088c7-103">Siebel 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於 WCF 基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="088c7-103">The previous version of the Siebel adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="088c7-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="088c7-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="088c7-105">中繼資料擷取的經驗。</span><span class="sxs-lookup"><span data-stu-id="088c7-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="088c7-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="088c7-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="088c7-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="088c7-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="088c7-108">可以使用配接器中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="088c7-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="088c7-109">在 BizTalk Server 管理主控台中的實體連接埠設定</span><span class="sxs-lookup"><span data-stu-id="088c7-109">Physical port configuration in the BizTalk Server Administration console</span></span>  
  
 <span data-ttu-id="088c7-110">中的主題將說明這些差異所[移轉 BizTalk 專案建立使用 Siebel 配接器的先前版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。</span><span class="sxs-lookup"><span data-stu-id="088c7-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the Siebel Adapter](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).</span></span>  
  
 <span data-ttu-id="088c7-111">不過，您可以使用舊版的配接器所建立的 BizTalk 專案中進行變更並讓它運作以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="088c7-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
 <span data-ttu-id="088c7-112">本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="088c7-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="088c7-113">在此教學課程中，為了簡短起見，舊版的 Siebel 配接器將會稱為 vPrev Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="088c7-113">In this tutorial, for the sake of brevity, the previous version of the Siebel adapter will be referred to as vPrev Siebel adapter.</span></span> <span data-ttu-id="088c7-114">同樣地，使用 vPrev Siebel 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="088c7-114">Similarly, a BizTalk project that uses the vPrev Siebel adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="088c7-115">教學課程使用範例</span><span class="sxs-lookup"><span data-stu-id="088c7-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="088c7-116">本教學課程根據範例 (Siebel_BussComp_Migration)，示範如何移轉執行插入作業帳戶 Siebel 商務元件上的 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="088c7-116">This tutorial is based upon a sample (Siebel_BussComp_Migration) that demonstrates how to migrate a vPrev BizTalk project that performs an Insert operation on the Account Siebel business component.</span></span> <span data-ttu-id="088c7-117">此範例之提供與 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="088c7-117">The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="088c7-118">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="088c7-118">For more information, see [Adapter Sample](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="088c7-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="088c7-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="088c7-120">您必須 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="088c7-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="088c7-121">本教學課程牽涉到執行插入作業帳戶商務元件上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="088c7-121">This tutorial involves a BizTalk project that performs an Insert operation on the Account business component.</span></span>  
  
-   <span data-ttu-id="088c7-122">您必須擁有執行插入作業使用 vPrev Siebel 配接器帳戶商務元件上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="088c7-122">You must have a request message to perform an Insert operation on the Account business component using the vPrev Siebel adapter.</span></span> <span data-ttu-id="088c7-123">要求訊息必須符合使用 vPrev Siebel 配接器所產生的插入作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="088c7-123">The request message must conform to the schema of the Insert operation generated using the vPrev Siebel adapter.</span></span>  
  
-   <span data-ttu-id="088c7-124">您必須先完成中的步驟[要建立 Siebel 應用程式的必要條件](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="088c7-124">You must have completed the steps in [Prerequisites to create Siebel applications](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md).</span></span>  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="088c7-125">了解 BizTalk 專案建立使用配接器的先前版本</span><span class="sxs-lookup"><span data-stu-id="088c7-125">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="088c7-126">建立 vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="088c7-126">The key constituents of a vPrev BizTalk project created are:</span></span>  
  
-   <span data-ttu-id="088c7-127">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="088c7-127">**BizTalk orchestration**.</span></span> <span data-ttu-id="088c7-128">這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Siebel Siebel 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="088c7-128">This is a simple orchestration that picks request messages from a file location, sends the request message to the Siebel system using a Siebel send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="088c7-129">**您想要在 Siebel 商務元件上執行作業的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="088c7-129">**Schema for the operation you wish to perform on the Siebel business component**.</span></span> <span data-ttu-id="088c7-130">本教學課程牽涉到執行插入作業帳戶商務元件上的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="088c7-130">This tutorial involves a BizTalk project that performs an Insert operation on the Account business component.</span></span> <span data-ttu-id="088c7-131">帳戶商務元件產生的結構描述是 AccountService_Account_x5d.xsd。</span><span class="sxs-lookup"><span data-stu-id="088c7-131">The schema generated for the Account business component is AccountService_Account_x5d.xsd.</span></span> <span data-ttu-id="088c7-132">此結構描述會產生使用 vPrev Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="088c7-132">This schema is generated using the vPrev Siebel adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="088c7-133">不同於 WCF 基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，vPrev Siebel 配接器不支援在商務元件上的特定作業產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="088c7-133">Unlike the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the vPrev Siebel adapter does not support generating metadata for specific operations on a business component.</span></span> <span data-ttu-id="088c7-134">根據預設，配接器會產生結構描述支援商務元件上的所有作業。</span><span class="sxs-lookup"><span data-stu-id="088c7-134">By default, the adapter generates schema for all the operations supported on the business component.</span></span> <span data-ttu-id="088c7-135">VPrev Siebel 配接器和 WCF 為基礎的多這類差異[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[移轉 BizTalk 專案建立使用 Siebel 配接器的先前版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。</span><span class="sxs-lookup"><span data-stu-id="088c7-135">For more such differences between the vPrev Siebel adapter and the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Migrating BizTalk Projects Created Using the Previous Version of the Siebel Adapter](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).</span></span>  
  
-   <span data-ttu-id="088c7-136">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="088c7-136">**Request message**.</span></span> <span data-ttu-id="088c7-137">要執行插入作業帳戶商務元件上的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="088c7-137">The request message to perform an Insert operation on the Account business component.</span></span> <span data-ttu-id="088c7-138">因為 vPrev Siebel 配接器所顯示的插入作業結構描述符合要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="088c7-138">The schema of the request message conforms to the schema of the Insert operation as surfaced by the vPrev Siebel adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="088c7-139">使用舊版的配接器如何移轉 BizTalk 專案建立</span><span class="sxs-lookup"><span data-stu-id="088c7-139">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="088c7-140">本移轉教學課程的目標是要讓您傳送要求訊息，符合 vPrev Siebel 配接器使用 WCF 自訂連接埠，可以只處理符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="088c7-140">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by the vPrev Siebel adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="088c7-141">因此，簡單地說，在移轉作業牽涉到設定不符合以 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="088c7-141">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="088c7-142">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="088c7-142">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="088c7-143">產生使用 WCF 為基礎之帳戶商務元件的 Insert 作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="088c7-143">Generate metadata for the Insert operation on the Account business component using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
-   <span data-ttu-id="088c7-144">執行使用 vPrev Siebel 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="088c7-144">Map the request message for performing an Insert operation using the vPrev Siebel adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
-   <span data-ttu-id="088c7-145">使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="088c7-145">Map the response message received using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to the response message for the vPrev Siebel adapter.</span></span>  
  
-   <span data-ttu-id="088c7-146">建立 WCF 自訂 Siebel 傳送接收 BizTalk Server 管理主控台中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="088c7-146">Create a WCF-Custom Siebel send-receive port in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="088c7-147">設定 WCF 自訂連接埠使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="088c7-147">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="088c7-148">本節內容</span><span class="sxs-lookup"><span data-stu-id="088c7-148">In This Section</span></span>  
  
-   [<span data-ttu-id="088c7-149">步驟 1： 修改 vPrev Oracle 資料庫中的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="088c7-149">Step 1: Modify the vPrev BizTalk Project in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/step-1-modify-the-vprev-biztalk-project-in-oracle-database.md)  
  
-   [<span data-ttu-id="088c7-150">步驟 2： 使用 ORacle 資料庫配接器的 BizTalk Server 管理主控台中設定協調流程</span><span class="sxs-lookup"><span data-stu-id="088c7-150">Step 2: Configure the Orchestration in BizTalk Server Administration Console to use the ORacle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)  
  
-   [<span data-ttu-id="088c7-151">步驟 3： 測試移轉應用程式使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="088c7-151">Step 3: Test the Migrated Application with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="088c7-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="088c7-152">See Also</span></span>  
 [<span data-ttu-id="088c7-153">Siebel 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="088c7-153">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)