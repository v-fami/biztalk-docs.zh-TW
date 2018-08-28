---
title: 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58ca6a63-525a-4b16-932d-6d26e68f6fab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5700b3adb0769edff4ec820b4d95353383c08e6d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968015"
---
# <a name="send-pipeline"></a><span data-ttu-id="eaebf-102">傳送管線</span><span class="sxs-lookup"><span data-stu-id="eaebf-102">Send Pipeline</span></span>
<span data-ttu-id="eaebf-103">此範例提供了有效 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]傳送管線，您可以自訂您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaebf-103">This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] send pipeline that you can customize for your application.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="eaebf-104">示範</span><span class="sxs-lookup"><span data-stu-id="eaebf-104">Demonstrates</span></span>  
 <span data-ttu-id="eaebf-105">這個範例示範如何使用 BTARN 傳送管線 (PipelineSend.btp)，將 XML 訊息外送至對等的 RNIF 訊息中。</span><span class="sxs-lookup"><span data-stu-id="eaebf-105">This sample demonstrates how to process an outgoing XML message into the equivalent RNIF message using the BTARN send pipeline (PipelineSend.btp).</span></span> <span data-ttu-id="eaebf-106">PipelineSend.btp 位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\rnpipelines。</span><span class="sxs-lookup"><span data-stu-id="eaebf-106">PipelineSend.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="eaebf-107">它包含下列階段：</span><span class="sxs-lookup"><span data-stu-id="eaebf-107">It includes the following stages:</span></span>  
  
-   <span data-ttu-id="eaebf-108">XML 組合器</span><span class="sxs-lookup"><span data-stu-id="eaebf-108">XML Assembler</span></span>  
  
-   <span data-ttu-id="eaebf-109">MIME 編碼器</span><span class="sxs-lookup"><span data-stu-id="eaebf-109">MIME Encoder</span></span>  
  
-   <span data-ttu-id="eaebf-110">傳送不可否認的訊息</span><span class="sxs-lookup"><span data-stu-id="eaebf-110">Send message Non-repudiate</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaebf-111">如果您在 Visual Studio 的「管線設計師」中選取 BTARN 傳送管線的上述其中一個元件，該元件的屬性將不會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="eaebf-111">If you select one of the above components of the BTARN send pipeline in the Pipeline Designer in Visual Studio, the properties for that component will not be displayed in the Properties pane.</span></span> <span data-ttu-id="eaebf-112">若要顯示元件的屬性，您必須將元件加入 工具箱 中使用**選擇工具箱項目**工具 功能表中的命令; 刪除現有的元件從傳送管線，然後再新增從元件工具箱拖曳到 管線設計師 」 中的適當階段。</span><span class="sxs-lookup"><span data-stu-id="eaebf-112">To display the properties of the component, you must add the component to the Toolbox by using the **Choose Toolbox Items** command in the Tools menu; delete the existing component from the send pipeline; and then add the component from the Toolbox into the appropriate stage in the Pipeline Designer.</span></span> <span data-ttu-id="eaebf-113">然後如果您再選取該元件，它的屬性就會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="eaebf-113">If you then select the component, its properties will be displayed in the Properties pane.</span></span>  
  
 <span data-ttu-id="eaebf-114">此管線中，以及此管線內的訊息流程元件的相關資訊，請參閱[BTARN 傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="eaebf-114">For more information about the components of this pipeline, and the message flow within this pipeline, see [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaebf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaebf-115">See Also</span></span>  
 <span data-ttu-id="eaebf-116">[管線範例](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span><span class="sxs-lookup"><span data-stu-id="eaebf-116">[Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span></span>  
 [<span data-ttu-id="eaebf-117">BTARN 傳送管線</span><span class="sxs-lookup"><span data-stu-id="eaebf-117">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)