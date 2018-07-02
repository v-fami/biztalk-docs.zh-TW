---
title: 如何建立新的管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, warnings
- Pipeline Designer, warnings
- pipelines, creating
ms.assetid: bd95325e-1a72-4705-80f6-37ac092d11a3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 908c0eebecaf005e22194584f9a1d1e7fafa4daf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970231"
---
# <a name="how-to-create-a-new-pipeline"></a><span data-ttu-id="9c7ce-102">如何建立新的管線</span><span class="sxs-lookup"><span data-stu-id="9c7ce-102">How to Create a New Pipeline</span></span>
<span data-ttu-id="9c7ce-103">您可以新增管線範本到您的專案，以建立新管線。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-103">You can add a pipeline template to your project to create a new pipeline.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9c7ce-104">您不應該新增的專案包含自訂管線元件的方案，包含使用該管線元件專案的實作。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-104">You should not add a project that contains an implementation of a custom pipeline component to a solution that contains a project that uses that pipleine component.</span></span> <span data-ttu-id="9c7ce-105">如果您這樣做，下次重新建置方案時，就會收到錯誤訊息，指出輸出 dll 已被其他程序使用。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-105">If you do, the next time you rebuild the solution you will get an error saying the output dll is being used by another process.</span></span>  
  
### <a name="to-create-a-new-pipeline"></a><span data-ttu-id="9c7ce-106">建立新管線</span><span class="sxs-lookup"><span data-stu-id="9c7ce-106">To create a new pipeline</span></span>  
  
1. <span data-ttu-id="9c7ce-107">在 [方案總管] 中選取您想在其中建立管線的專案。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-107">In Solution Explorer, select the project in which you want to create the pipeline.</span></span>  
  
2. <span data-ttu-id="9c7ce-108">在 [專案] 功能表上，按一下 [加入新項目]。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-108">On the **Project** menu, click **Add New Item**.</span></span>  
  
3. <span data-ttu-id="9c7ce-109">在 **加入新項目**對話方塊中，選取**接收管線**或**傳送管線**範本即可一次。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-109">In the **Add New Item** dialog box, select a **Receive Pipeline** or **Send Pipeline** template by clicking it once.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9c7ce-110">如果您按兩下範本，將會自動出現在其預設名稱建立管線**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-110">If you double-click the template, the pipeline will automatically be created with the default name that appears in the **Name** field.</span></span>  
  
4. <span data-ttu-id="9c7ce-111">在 **名稱**欄位中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-111">In the **Name** field, type a name for the pipeline.</span></span>  
  
5. <span data-ttu-id="9c7ce-112">按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-112">Click **Open**.</span></span>  
  
    <span data-ttu-id="9c7ce-113">新管線隨即出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-113">The new pipeline appears in Solution Explorer.</span></span> <span data-ttu-id="9c7ce-114">設計介面會顯示管線階段和預設元件組。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-114">The design surface displays pipeline stages and a default set of components.</span></span>  
  
   <span data-ttu-id="9c7ce-115">如需將管線元件新增至管線的資訊，請參閱[如何新增元件至管線](../core/how-to-add-a-component-to-a-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="9c7ce-115">For information about adding pipeline components to the pipeline, see [How to Add a Component to a Pipeline](../core/how-to-add-a-component-to-a-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7ce-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c7ce-116">See Also</span></span>  
 <span data-ttu-id="9c7ce-117">[如何開啟管線](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="9c7ce-117">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="9c7ce-118">[如何儲存管線](../core/how-to-save-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="9c7ce-118">[How to Save a Pipeline](../core/how-to-save-a-pipeline.md) </span></span>  
 <span data-ttu-id="9c7ce-119">[如何使用工具箱](../core/how-to-use-the-toolbox.md) </span><span class="sxs-lookup"><span data-stu-id="9c7ce-119">[How to Use the Toolbox](../core/how-to-use-the-toolbox.md) </span></span>  
 <span data-ttu-id="9c7ce-120">[如何使用鍵盤巡覽](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="9c7ce-120">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="9c7ce-121">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="9c7ce-121">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)