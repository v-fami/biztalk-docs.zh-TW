---
title: 第 2 課： 加入專案參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- references [projects]
- projects, adding references
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e7ade122e725c07772dba431bd364bc8f933b82
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969695"
---
# <a name="lesson-2-adding-project-references"></a><span data-ttu-id="0c752-102">第 2 課： 加入專案參考</span><span class="sxs-lookup"><span data-stu-id="0c752-102">Lesson 2: Adding Project References</span></span>
<span data-ttu-id="0c752-103">讓您的管線可以存取位於 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll 檔案中的預設執行階段結構描述，您就會加入專案參考。</span><span class="sxs-lookup"><span data-stu-id="0c752-103">You add project references so your pipelines can access the default runtime schemas located in the Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll file.</span></span> <span data-ttu-id="0c752-104">此組件檔會包含標頭結構描述具有訊息類型解析所需的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="0c752-104">This assembly file contains the header schema with promoted properties required for message-type resolution.</span></span>  
  
 <span data-ttu-id="0c752-105">您參考標頭結構描述稍後當您將反組譯碼元件新增至接收管線。</span><span class="sxs-lookup"><span data-stu-id="0c752-105">You reference the header schemas later when you add the disassembly component to the receive pipeline.</span></span>  
  
### <a name="to-add-a-reference-to-the-default-swift-runtimeschemas-assembly"></a><span data-ttu-id="0c752-106">若要加入預設 SWIFT RuntimeSchemas 組件的參考</span><span class="sxs-lookup"><span data-stu-id="0c752-106">To add a reference to the default SWIFT RuntimeSchemas assembly</span></span>  
  
1.  <span data-ttu-id="0c752-107">在 [方案總管] 中，請確認**SWIFTPipelines**專案就會展開。</span><span class="sxs-lookup"><span data-stu-id="0c752-107">In Solution Explorer, ensure that the **SWIFTPipelines** project is expanded.</span></span> <span data-ttu-id="0c752-108">以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="0c752-108">Right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="0c752-109">在 加入參考 對話方塊中，按一下**瀏覽** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0c752-109">In the Add Reference dialog box, click the **Browse** tab.</span></span>  
  
3.  <span data-ttu-id="0c752-110">瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**。</span><span class="sxs-lookup"><span data-stu-id="0c752-110">Browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**.</span></span>  
  
4.  <span data-ttu-id="0c752-111">選取  **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll**檔案。</span><span class="sxs-lookup"><span data-stu-id="0c752-111">Select the **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** file.</span></span>  
  
5.  <span data-ttu-id="0c752-112">按一下 **新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0c752-112">Click **Add**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c752-113">您現在已選取 RuntimeSchemas 組件 (dll) 會出現在 SWIFTPipelines 專案中參考集合。</span><span class="sxs-lookup"><span data-stu-id="0c752-113">The RuntimeSchemas assembly (dll) that you selected now appears in the references collection in the SWIFTPipelines project.</span></span>  
  
#### <a name="to-add-a-reference-to-the-swiftpipelines-schemas-assembly"></a><span data-ttu-id="0c752-114">若要新增 SWIFTPipelines 結構描述組件的參考</span><span class="sxs-lookup"><span data-stu-id="0c752-114">To add a reference to the SWIFTPipelines schemas assembly</span></span>  
  
1. <span data-ttu-id="0c752-115">在 方案總管底下**SWIFTPipelines**專案中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="0c752-115">In Solution Explorer, under the **SWIFTPipelines** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="0c752-116">在 加入參考 對話方塊中上,**專案**索引標籤上，按一下**SWIFTSchemas**專案，按一下 **新增**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="0c752-116">In the Add Reference dialog box, on the **Projects** tab, click the **SWIFTSchemas** project, click **Add**, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="0c752-117">在上**檔案**功能表上，按一下**全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="0c752-117">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
   <span data-ttu-id="0c752-118">請繼續進行[第 3 課： 加入自訂接收管線](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="0c752-118">Proceed to [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span></span>