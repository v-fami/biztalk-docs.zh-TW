---
title: "第 2 課： 加入專案參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- references [projects]
- projects, adding references
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce151a83389fe5f0b3884446b5b793d1b58c618
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-project-references"></a><span data-ttu-id="abd61-102">第 2 課： 加入專案參考</span><span class="sxs-lookup"><span data-stu-id="abd61-102">Lesson 2: Adding Project References</span></span>
<span data-ttu-id="abd61-103">讓您的管線能夠存取位於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll 檔案中的預設執行階段結構描述，您會加入專案參考。</span><span class="sxs-lookup"><span data-stu-id="abd61-103">You add project references so your pipelines can access the default runtime schemas located in the Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll file.</span></span> <span data-ttu-id="abd61-104">此組件檔會包含標頭結構描述具有訊息類型解析所需的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="abd61-104">This assembly file contains the header schema with promoted properties required for message-type resolution.</span></span>  
  
 <span data-ttu-id="abd61-105">您的標頭結構描述供稍後參考反組譯碼元件加入的接收管線時。</span><span class="sxs-lookup"><span data-stu-id="abd61-105">You reference the header schemas later when you add the disassembly component to the receive pipeline.</span></span>  
  
### <a name="to-add-a-reference-to-the-default-swift-runtimeschemas-assembly"></a><span data-ttu-id="abd61-106">若要加入預設 SWIFT RuntimeSchemas 組件的參考</span><span class="sxs-lookup"><span data-stu-id="abd61-106">To add a reference to the default SWIFT RuntimeSchemas assembly</span></span>  
  
1.  <span data-ttu-id="abd61-107">在 [方案總管] 中，確定**SWIFTPipelines**專案就會展開。</span><span class="sxs-lookup"><span data-stu-id="abd61-107">In Solution Explorer, ensure that the **SWIFTPipelines** project is expanded.</span></span> <span data-ttu-id="abd61-108">以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="abd61-108">Right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="abd61-109">在 加入參考 對話方塊中，按一下**瀏覽** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="abd61-109">In the Add Reference dialog box, click the **Browse** tab.</span></span>  
  
3.  <span data-ttu-id="abd61-110">瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies * *。</span><span class="sxs-lookup"><span data-stu-id="abd61-110">Browse to **\<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**.</span></span>  
  
4.  <span data-ttu-id="abd61-111">選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll**檔案。</span><span class="sxs-lookup"><span data-stu-id="abd61-111">Select the **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** file.</span></span>  
  
5.  <span data-ttu-id="abd61-112">按一下**新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="abd61-112">Click **Add**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abd61-113">您現在選取 RuntimeSchemas 組件 (dll) 會出現在 SWIFTPipelines 專案中參考集合。</span><span class="sxs-lookup"><span data-stu-id="abd61-113">The RuntimeSchemas assembly (dll) that you selected now appears in the references collection in the SWIFTPipelines project.</span></span>  
  
#### <a name="to-add-a-reference-to-the-swiftpipelines-schemas-assembly"></a><span data-ttu-id="abd61-114">若要加入 SWIFTPipelines 結構描述組件的參考</span><span class="sxs-lookup"><span data-stu-id="abd61-114">To add a reference to the SWIFTPipelines schemas assembly</span></span>  
  
1.  <span data-ttu-id="abd61-115">在 方案總管下**SWIFTPipelines**專案中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="abd61-115">In Solution Explorer, under the **SWIFTPipelines** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="abd61-116">在 加入參考 對話方塊上**專案**索引標籤上，按一下  **SWIFTSchemas**專案中，按一下 **新增**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="abd61-116">In the Add Reference dialog box, on the **Projects** tab, click the **SWIFTSchemas** project, click **Add**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="abd61-117">在**檔案**功能表上，按一下 **全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="abd61-117">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="abd61-118">若要繼續[第 3 課： 加入自訂接收管線](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="abd61-118">Proceed to [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span></span>