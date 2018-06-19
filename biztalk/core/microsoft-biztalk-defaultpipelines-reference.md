---
title: Microsoft.BizTalk.DefaultPipelines 參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines
- PassThruTransmit pipelines
- XMLReceive pipelines
- pipelines, XMLTransmit
- Pipeline Designer
- pipelines, XMLReceive
- pipelines, about pipelines
- PassThruReceive pipelines
- XMLTransmit pipelines
- namespaces, Microsoft.BizTalk.DefaultPipelines namespace
- Microsoft.BizTalk.DefaultPipelines namespace
ms.assetid: a54f8813-9c6f-4afe-8c76-2db3fa478947
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ad7cad78e3e8606371a5fa49673297cf590ddbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263406"
---
# <a name="microsoftbiztalkdefaultpipelines-reference"></a><span data-ttu-id="573bf-102">Microsoft.BizTalk.DefaultPipelines 參考</span><span class="sxs-lookup"><span data-stu-id="573bf-102">Microsoft.BizTalk.DefaultPipelines Reference</span></span>
<span data-ttu-id="573bf-103">**Microsoft.BizTalk.DefaultPipelines**命名空間包含下列管線：</span><span class="sxs-lookup"><span data-stu-id="573bf-103">The **Microsoft.BizTalk.DefaultPipelines** namespace contains the following pipelines:</span></span>  
  
-   <span data-ttu-id="573bf-104">XMLReceive</span><span class="sxs-lookup"><span data-stu-id="573bf-104">XMLReceive</span></span>  
  
-   <span data-ttu-id="573bf-105">PassThruReceive</span><span class="sxs-lookup"><span data-stu-id="573bf-105">PassThruReceive</span></span>  
  
-   <span data-ttu-id="573bf-106">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="573bf-106">XMLTransmit</span></span>  
  
-   <span data-ttu-id="573bf-107">PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="573bf-107">PassThruTransmit</span></span>  
  
 <span data-ttu-id="573bf-108">管線是一種軟體元件，可定義和連結處理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所接收或傳送之訊息的一或多個階段。</span><span class="sxs-lookup"><span data-stu-id="573bf-108">A pipeline is a software component that defines and links one or more stages for processing messages received or sent by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="573bf-109">這些階段包括諸如編碼或解碼、組譯或反組譯以及加密或解密等函式。</span><span class="sxs-lookup"><span data-stu-id="573bf-109">The stages include functions such as encoding or decoding, disassembling or assembling, and decrypting or encrypting.</span></span> <span data-ttu-id="573bf-110">這些功能會以特定的順序進行實作。</span><span class="sxs-lookup"><span data-stu-id="573bf-110">These functions are implemented in a specific order.</span></span> <span data-ttu-id="573bf-111">您可以使用「管線設計師」來建立傳送管線和接收管線。</span><span class="sxs-lookup"><span data-stu-id="573bf-111">You can use Pipeline Designer to create receive and send pipelines.</span></span>  
  
 <span data-ttu-id="573bf-112">包含在 BizTalk 專案中的預設管線參考能夠處理所有類型的文件使用**PassThruReceive**和**PassThruTransmit**管線。</span><span class="sxs-lookup"><span data-stu-id="573bf-112">The default pipeline references included in a BizTalk project can process all types of documents using the **PassThruReceive** and **PassThruTransmit** pipelines.</span></span>  
  
 <span data-ttu-id="573bf-113">下列清單列出了預設管線中的預設元件。</span><span class="sxs-lookup"><span data-stu-id="573bf-113">The following lists show the default components in the default pipelines.</span></span> <span data-ttu-id="573bf-114">這些清單也會指出各管線中元件的預設順序。</span><span class="sxs-lookup"><span data-stu-id="573bf-114">These lists also indicate the default order of the components in each pipeline.</span></span> <span data-ttu-id="573bf-115">如有需要，您可以新增或刪除元件。</span><span class="sxs-lookup"><span data-stu-id="573bf-115">You can add and delete components if necessary.</span></span>  
  
 <span data-ttu-id="573bf-116">預設 XMLReceive 管線中的預設元件為：</span><span class="sxs-lookup"><span data-stu-id="573bf-116">The default components in the default XMLReceive pipeline are:</span></span>  
  
-   <span data-ttu-id="573bf-117">解密器</span><span class="sxs-lookup"><span data-stu-id="573bf-117">Decrypter</span></span>  
  
-   <span data-ttu-id="573bf-118">解碼器</span><span class="sxs-lookup"><span data-stu-id="573bf-118">Decoder</span></span>  
  
-   <span data-ttu-id="573bf-119">解譯器</span><span class="sxs-lookup"><span data-stu-id="573bf-119">Disassembler</span></span>  
  
-   <span data-ttu-id="573bf-120">驗證器</span><span class="sxs-lookup"><span data-stu-id="573bf-120">Validator</span></span>  
  
-   <span data-ttu-id="573bf-121">合作對象解析</span><span class="sxs-lookup"><span data-stu-id="573bf-121">Party Resolution</span></span>  
  
 <span data-ttu-id="573bf-122">預設 XMLTransmit 管線中的預設元件為：</span><span class="sxs-lookup"><span data-stu-id="573bf-122">The default components in the default XMLTransmit pipeline are:</span></span>  
  
-   <span data-ttu-id="573bf-123">組合器</span><span class="sxs-lookup"><span data-stu-id="573bf-123">Assembler</span></span>  
  
-   <span data-ttu-id="573bf-124">編碼器</span><span class="sxs-lookup"><span data-stu-id="573bf-124">Encoder</span></span>  
  
-   <span data-ttu-id="573bf-125">加密器</span><span class="sxs-lookup"><span data-stu-id="573bf-125">Encrypter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573bf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="573bf-126">See Also</span></span>  
 <span data-ttu-id="573bf-127">[建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="573bf-127">[Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="573bf-128">關於在 BizTalk 專案中包含的 BizTalk 命名空間參考</span><span class="sxs-lookup"><span data-stu-id="573bf-128">About BizTalk Namespace References Included in BizTalk Projects</span></span>](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)