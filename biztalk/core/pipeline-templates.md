---
title: "管線範本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, templates
- Pipeline Designer, templates
- send pipelines, templates
- receive pipelines, templates
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6af41d3c23c889b7a7e9bd2529adc80bc7bcd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-templates"></a><span data-ttu-id="2df54-102">管線範本</span><span class="sxs-lookup"><span data-stu-id="2df54-102">Pipeline Templates</span></span>
<span data-ttu-id="2df54-103">除了預設管線，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還包含兩個管線範本：接收管線範本和傳送管線範本。</span><span class="sxs-lookup"><span data-stu-id="2df54-103">In addition to the default pipelines, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes two pipeline templates: a receive pipeline template and a send pipeline template.</span></span> <span data-ttu-id="2df54-104">從 BizTalk 專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您也可以使用您的專案新增管線範本**加入新項目**命令**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="2df54-104">From a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can add a pipeline template to your project by using the **Add New Item** command on the **Project** menu.</span></span> <span data-ttu-id="2df54-105">各個範本都有相關聯的原則檔案，可決定管線的階段並指出管線中可以使用哪些管線元件。</span><span class="sxs-lookup"><span data-stu-id="2df54-105">Each template has an associated policy file, which determines the pipeline's stages and indicates which pipeline components are allowed in the pipeline.</span></span> <span data-ttu-id="2df54-106">您無法重新排序原則檔案中的階段，但您可以使用「管線設計師」來重新排序階段中的元件。</span><span class="sxs-lookup"><span data-stu-id="2df54-106">While you cannot reorder the stages in a policy file, you can use Pipeline Designer to reorder the components within a stage.</span></span>  
  
 <span data-ttu-id="2df54-107">原則檔案可以指定：</span><span class="sxs-lookup"><span data-stu-id="2df54-107">A policy file specifies:</span></span>  
  
-   <span data-ttu-id="2df54-108">各階段的順序。</span><span class="sxs-lookup"><span data-stu-id="2df54-108">The sequence of stages.</span></span>  
  
-   <span data-ttu-id="2df54-109">各階段允許的元件數目。</span><span class="sxs-lookup"><span data-stu-id="2df54-109">The number of components allowed per stage.</span></span>  
  
-   <span data-ttu-id="2df54-110">各階段的執行模式。</span><span class="sxs-lookup"><span data-stu-id="2df54-110">The execution mode of each stage.</span></span>  
  
 <span data-ttu-id="2df54-111">管線範本的原則檔案會儲存在 *\<BizTalk Server 安裝目錄 >*\Developer Tools\Pipeline 原則檔。</span><span class="sxs-lookup"><span data-stu-id="2df54-111">The policy files for the pipeline templates are stored in *\<BizTalk Server installation directory>*\Developer Tools\Pipeline Policy Files.</span></span> <span data-ttu-id="2df54-112">請勿修改原則檔案。</span><span class="sxs-lookup"><span data-stu-id="2df54-112">Do not modify the policy files.</span></span> <span data-ttu-id="2df54-113">若要對管線進行變更，請開啟管線範本並使用「管線設計師」進行修改。</span><span class="sxs-lookup"><span data-stu-id="2df54-113">To make changes to a pipeline, open the pipeline template and use Pipeline Designer to modify it.</span></span> <span data-ttu-id="2df54-114">如需使用管線設計師 」 的詳細資訊，請參閱[使用管線設計師](../core/using-pipeline-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="2df54-114">For more information about using Pipeline Designer, see [Using Pipeline Designer](../core/using-pipeline-designer.md).</span></span>  
  
 <span data-ttu-id="2df54-115">空白管線範本檔案會儲存在 *\<BizTalk Server 安裝目錄 >*\Developer Tools\BizTalkProjectItems，且名為 BTSReceivePipeline.btp 和 BTSTransmitPipeline.btp。</span><span class="sxs-lookup"><span data-stu-id="2df54-115">The empty pipeline template files are stored in *\<BizTalk Server installation directory>*\Developer Tools\BizTalkProjectItems, and are named BTSReceivePipeline.btp and BTSTransmitPipeline.btp.</span></span> <span data-ttu-id="2df54-116">副檔名.btp 表示檔案是 BizTalk Server 管線可以在管線設計師中編輯。</span><span class="sxs-lookup"><span data-stu-id="2df54-116">The file name extension .btp indicates that the file is a BizTalk Server pipeline and can be edited in Pipeline Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df54-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df54-117">See Also</span></span>  
 <span data-ttu-id="2df54-118">[類型的管線](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="2df54-118">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="2df54-119">[類型的管線元件](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="2df54-119">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="2df54-120">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="2df54-120">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="2df54-121">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="2df54-121">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="2df54-122">關於管線、 階段和元件</span><span class="sxs-lookup"><span data-stu-id="2df54-122">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)