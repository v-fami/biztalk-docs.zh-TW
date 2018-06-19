---
title: 部署 A4SWIFT 信封結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, envelope schemas
- A4SWIFT, deploying envelope schemas
- envelope schemas
- schemas, envelope schemas
ms.assetid: 6440608c-d30d-4d82-827a-8a4b2738db85
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8811f1dd056ca5a4ea4582d593af30e2ffc879f
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25967044"
---
# <a name="deploying-a4swift-envelope-schemas"></a><span data-ttu-id="81ebf-102">部署 A4SWIFT 信封結構描述</span><span class="sxs-lookup"><span data-stu-id="81ebf-102">Deploying A4SWIFT Envelope Schemas</span></span>
<span data-ttu-id="81ebf-103">每當您設定 Message Repair 和 New Submission 時，您必須在結構描述專案中包含信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="81ebf-103">You must include envelope schemas in schema projects whenever you set up Message Repair and New Submission.</span></span> <span data-ttu-id="81ebf-104">信封結構描述，例如 EnvelopeMT103.xsd，才能寫入 MRSR 網站。</span><span class="sxs-lookup"><span data-stu-id="81ebf-104">An envelope schema, such as EnvelopeMT103.xsd, is required to write to MRSR site.</span></span>  
  
 <span data-ttu-id="81ebf-105">**摘要**</span><span class="sxs-lookup"><span data-stu-id="81ebf-105">**Summary**</span></span>  
  
 <span data-ttu-id="81ebf-106">加入信封結構描述您的專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="81ebf-106">Add envelope schemas to your project, as follows:</span></span>  
  
-   <span data-ttu-id="81ebf-107">在 Visual Studio 中，若要包含您的訊息結構描述的專案加入信封結構描述每個訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="81ebf-107">In Visual Studio, to the project that contains your message schemas, add an envelope schema for each message schema.</span></span>  
  
-   <span data-ttu-id="81ebf-108">RuntimeSchemas.dll 參考加入至任何包含一個或多個信封結構描述的專案。</span><span class="sxs-lookup"><span data-stu-id="81ebf-108">Add a reference to RuntimeSchemas.dll to any project that contains one or more envelope schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81ebf-109">將參考加入至 RuntimeSchemas.dll 需[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]只在訊息修復和新送出至專案中加入信封結構描述專案。</span><span class="sxs-lookup"><span data-stu-id="81ebf-109">Adding a reference to RuntimeSchemas.dll is required for an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] project only when you have added an envelope schema for Message Repair and New Submission to the project.</span></span>  
  
-   <span data-ttu-id="81ebf-110">未剖析訊息信封結構描述 (EnvelopeUnparsedMessage.xsd) 加入專案。</span><span class="sxs-lookup"><span data-stu-id="81ebf-110">Add the Unparsed Message envelope schema (EnvelopeUnparsedMessage.xsd) to the project.</span></span>  
  
### <a name="to-add-a-swift-envelope-schema"></a><span data-ttu-id="81ebf-111">若要加入 SWIFT 信封結構描述</span><span class="sxs-lookup"><span data-stu-id="81ebf-111">To add a SWIFT envelope schema</span></span>  
  
1.  <span data-ttu-id="81ebf-112">在 Visual Studio 的方案總管中開啟您的結構描述的專案。</span><span class="sxs-lookup"><span data-stu-id="81ebf-112">In Solution Explorer of Visual Studio, open your schemas project.</span></span>  
  
2.  <span data-ttu-id="81ebf-113">以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-113">Right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="81ebf-114">在 [加入參考] 對話方塊中，按一下**瀏覽**標記。</span><span class="sxs-lookup"><span data-stu-id="81ebf-114">In the Add Reference dialog box, click the **Browse** tag.</span></span>  
  
4.  <span data-ttu-id="81ebf-115">在 [選取元件] 對話方塊中，開啟**查看**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81ebf-115">In the Select Component dialog box, open the **Look in** drop-down list.</span></span> <span data-ttu-id="81ebf-116">移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\Assemblies**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-116">Move to ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\Assemblies**.</span></span> <span data-ttu-id="81ebf-117">選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll**從組件，然後再按一下清單**新增**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-117">Select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** from the list of assemblies, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="81ebf-118">在**加入參考**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-118">In the **Add Reference** dialog box, click **OK**.</span></span>  
  
6.  <span data-ttu-id="81ebf-119">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-119">Right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
7.  <span data-ttu-id="81ebf-120">在 [新增現有的項目] 對話方塊中**查看**下拉式清單方塊中，移至**\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Categoryn\MTxxx**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-120">In the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Categoryn\MTxxx**.</span></span> <span data-ttu-id="81ebf-121">例如，選取信封結構描述， **EnvelopeMT103.xsd**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-121">Select the envelope schema, for example, **EnvelopeMT103.xsd**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="81ebf-122">在 [新增現有的項目] 對話方塊中**查看**下拉式清單方塊中，移至。</span><span class="sxs-lookup"><span data-stu-id="81ebf-122">In the Add Existing Item dialog box, in the **Look in** drop-down box, move to.</span></span> <span data-ttu-id="81ebf-123">選取信封結構描述，例如 EnvelopeMT103.xsd，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="81ebf-123">Select the envelope schema, for example, EnvelopeMT103.xsd, and then click Add.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81ebf-124">A4SWIFT 加入信封結構描述，針對您的專案，在 [方案總管] 中所示。</span><span class="sxs-lookup"><span data-stu-id="81ebf-124">A4SWIFT adds the envelope schema for your project, as shown in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="81ebf-125">在 方案總管 中，以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-125">In Solution Explorer, right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
9. <span data-ttu-id="81ebf-126">如果使用 Message Repair 和 New Submission 功能，在 [加入現有項目] 對話方塊中**查看**下拉式清單方塊中，移至 **\<*磁碟機*\>: \Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Unparsed 訊息**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-126">If using the Message Repair and New Submission feature, in the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<*drive*\>:\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Unparsed Message**.</span></span> <span data-ttu-id="81ebf-127">選取**EnvelopeUnparsedMessage.xsd**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-127">Select **EnvelopeUnparsedMessage.xsd**, and then click **Add**.</span></span>  
  
10. <span data-ttu-id="81ebf-128">在 方案總管 中，以滑鼠右鍵按一下專案名稱，以及  **建置**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-128">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
11. <span data-ttu-id="81ebf-129">在 方案總管 中，以滑鼠右鍵按一下專案名稱，以及  **部署**。</span><span class="sxs-lookup"><span data-stu-id="81ebf-129">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>