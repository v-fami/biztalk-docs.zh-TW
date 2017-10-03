---
title: "使用管線設計師 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, how to
- pipelines, Pipeline Designer
ms.assetid: bdb2f5c7-f8a2-4bd6-a8d8-8b7a64f97bd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7a8bc7c7943ff96f0d70a802a2756f8d8c4783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-designer"></a><span data-ttu-id="d15d8-102">使用管線設計師</span><span class="sxs-lookup"><span data-stu-id="d15d8-102">Using Pipeline Designer</span></span>
<span data-ttu-id="d15d8-103">管線設計師是一套裝載於 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的圖形化編輯器，可讓您建立新管線、檢視 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的管線範本、移動管線內的管線元件，還可以設定管線、階段以及管線元件。</span><span class="sxs-lookup"><span data-stu-id="d15d8-103">Pipeline Designer is a graphical editor, hosted in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], which enables you to create new pipelines; view the pipeline templates included with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]; move pipeline components within a pipeline; and configure pipelines, stages, and pipeline components.</span></span>  
  
 <span data-ttu-id="d15d8-104">管線設計師會使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 殼層的三項主要工具，作為設計經驗的一部分：</span><span class="sxs-lookup"><span data-stu-id="d15d8-104">Pipeline Designer uses three key tools of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell as part of the design experience:</span></span>  
  
-   <span data-ttu-id="d15d8-105">[屬性] 視窗，可在其中檢視和修改管線物件的大部分特性。</span><span class="sxs-lookup"><span data-stu-id="d15d8-105">The Properties window, where most of the characteristics of pipeline objects are viewed and modified.</span></span>  
  
-   <span data-ttu-id="d15d8-106">[工具箱]，作為設計介面的來源。</span><span class="sxs-lookup"><span data-stu-id="d15d8-106">The Toolbox, which is used as a source for the design surface.</span></span>  
  
-   <span data-ttu-id="d15d8-107">設計介面，[工具箱] 的元件可拖放至此。</span><span class="sxs-lookup"><span data-stu-id="d15d8-107">The design surface, where components from the Toolbox are dragged and dropped.</span></span>  
  
 <span data-ttu-id="d15d8-108">下圖顯示管線設計師的環境。</span><span class="sxs-lookup"><span data-stu-id="d15d8-108">The following figure shows the Pipeline Designer environment.</span></span>  
  
 <span data-ttu-id="d15d8-109">![管線設計師編輯環境](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")</span><span class="sxs-lookup"><span data-stu-id="d15d8-109">![The Pipeline Designer editing environment](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")</span></span>  
<span data-ttu-id="d15d8-110">描述管線設計師的環境。</span><span class="sxs-lookup"><span data-stu-id="d15d8-110">Depicts the Pipeline Designer environment.</span></span>  
  
 <span data-ttu-id="d15d8-111">為了增強您的開發經驗，管線設計師已和 BizTalk 專案範本進行整合。</span><span class="sxs-lookup"><span data-stu-id="d15d8-111">Pipeline Designer is integrated with the BizTalk project template to enhance your development experience.</span></span> <span data-ttu-id="d15d8-112">若要建立新的 BizTalk 專案中使用專案系統之後, 您可以使用**加入新項目**命令**檔案**功能表來新增管線到您的方案。</span><span class="sxs-lookup"><span data-stu-id="d15d8-112">After using the project system to create a new BizTalk project, you can use the **Add New Item** command on the **File** menu to add a pipeline to your solution.</span></span> <span data-ttu-id="d15d8-113">如需 BizTalk 專案範本的詳細資訊，請參閱[使用 BizTalk 專案系統](../core/using-the-biztalk-project-system.md)。</span><span class="sxs-lookup"><span data-stu-id="d15d8-113">For more information about the BizTalk project template, see [Using the BizTalk Project System](../core/using-the-biztalk-project-system.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d15d8-114">在舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，管線的概念封裝在訊息通道和連接埠中，而這些通道和連接埠為套用至文件的特定元件定義了設定順序。</span><span class="sxs-lookup"><span data-stu-id="d15d8-114">In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the concept of a pipeline was encapsulated in message channels and ports, which defined a set order of specific components that were applied to a document.</span></span> <span data-ttu-id="d15d8-115">在這個版本中，管線變的更有彈性，因為您可以自由地重新排列管線各階段的元件，也可以輕易地在管線中插入多個自訂元件。</span><span class="sxs-lookup"><span data-stu-id="d15d8-115">In this version, the pipeline is flexible because you are free to reorder the components in each stage of the pipeline and can easily insert multiple custom components throughout the pipeline.</span></span>  
  
 <span data-ttu-id="d15d8-116">管線設計師的設計介面可讓您繪製管線的圖形表示。</span><span class="sxs-lookup"><span data-stu-id="d15d8-116">The Pipeline Designer design surface enables you to draw a graphical representation of a pipeline.</span></span> <span data-ttu-id="d15d8-117">設計介面佔據了 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 視窗的主要區段，可讓您編輯屬於 BizTalk 專案的管線。</span><span class="sxs-lookup"><span data-stu-id="d15d8-117">The design surface occupies the main section of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window and enables you to edit the pipelines belonging to a BizTalk project.</span></span> <span data-ttu-id="d15d8-118">您可以按一下設計介面上方的索引標籤，在管線之間瀏覽。</span><span class="sxs-lookup"><span data-stu-id="d15d8-118">You can navigate between pipelines by clicking the tabs above the design surface.</span></span>  
  
 <span data-ttu-id="d15d8-119">每個管線都由階段組成，而每個階段都包含了一個或多個元件。</span><span class="sxs-lookup"><span data-stu-id="d15d8-119">Each pipeline is composed of stages, with each stage containing one or more components.</span></span> <span data-ttu-id="d15d8-120">若階段中沒有元件，則浮水印文字即表示可以從 [工具箱] 插入圖形。</span><span class="sxs-lookup"><span data-stu-id="d15d8-120">If there are no components in a stage, a watermark with text indicates that shapes can be inserted from the Toolbox.</span></span> <span data-ttu-id="d15d8-121">當插入第一個圖形到階段中時，這段初始文字就會消失。</span><span class="sxs-lookup"><span data-stu-id="d15d8-121">When the first shape is inserted into a stage, the initial text disappears.</span></span> <span data-ttu-id="d15d8-122">設計介面會以垂直方式顯示管線，從頂端 (開始) 到底端 (結束)。</span><span class="sxs-lookup"><span data-stu-id="d15d8-122">The design surface shows the pipeline vertically, running from top (start) to bottom (end).</span></span>  
  
 <span data-ttu-id="d15d8-123">和其他一般的 Microsoft Windows 程式，您可以在執行數個工作，例如**開啟**和**儲存**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d15d8-123">As with other common Microsoft Windows programs, you can perform several tasks, such as **Open** and **Save** from the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d15d8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d15d8-124">See Also</span></span>  
 <span data-ttu-id="d15d8-125">[使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d15d8-125">[Creating Pipelines with Pipeline Designer](../core/creating-pipelines-with-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="d15d8-126">建立管線使用管線設計師</span><span class="sxs-lookup"><span data-stu-id="d15d8-126">Creating Pipelines Using Pipeline Designer</span></span>](../core/creating-pipelines-using-pipeline-designer.md)