---
title: 預設管線 |Microsoft 文件
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
- pipelines, XMLTransmit
- pipelines, StsReceive
- pipelines, StsSend
- pipelines, StsFileReceive
- Microsoft.BizTalk.KwTpm.StsDefaultPipelines.EnvSchema XML envelope
- pipelines, XMLReceive
- pipelines, backward compatibility
- Microsoft.BizTalk.DefaultPipelines assembly
- pipelines, default
ms.assetid: 7d82bb2c-c7f1-44a1-9e1b-89b0bb806845
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ceb3f06f2e2b57ec37bc4a95a385574de594940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239302"
---
# <a name="default-pipelines"></a><span data-ttu-id="1e053-102">預設管線</span><span class="sxs-lookup"><span data-stu-id="1e053-102">Default Pipelines</span></span>
<span data-ttu-id="1e053-103">當您建立新的應用程式時，依照預設會建立和部署預設管線，並顯示在每個 BizTalk 專案的 \References 資料夾的 Microsoft.BizTalk.DefaultPipelines 組件中。</span><span class="sxs-lookup"><span data-stu-id="1e053-103">When you create a new application, the default pipelines are created and deployed by default and appear in the Microsoft.BizTalk.DefaultPipelines assembly in the \References folder for every BizTalk project.</span></span> <span data-ttu-id="1e053-104">在「管線設計師」中不能修改預設管線。</span><span class="sxs-lookup"><span data-stu-id="1e053-104">The default pipelines cannot be modified in Pipeline Designer.</span></span> <span data-ttu-id="1e053-105">在 [BizTalk 總管] 中設定傳送埠或接收位置時會選取這些管線。</span><span class="sxs-lookup"><span data-stu-id="1e053-105">These pipelines can be selected when configuring a send port or receive location in BizTalk Explorer.</span></span> <span data-ttu-id="1e053-106">本主題描述預設管線及其使用時機。</span><span class="sxs-lookup"><span data-stu-id="1e053-106">This topic describes the default pipelines and when to use them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e053-107">XML 接收和 XML 傳送管線不支援大於 4 GB 的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1e053-107">The XML receive and XML send pipelines do not support XML documents larger than 4 gigabytes.</span></span>  
  
## <a name="passthrureceive-pipeline"></a><span data-ttu-id="1e053-108">PassThruReceive 管線</span><span class="sxs-lookup"><span data-stu-id="1e053-108">PassThruReceive pipeline</span></span>  
 <span data-ttu-id="1e053-109">通過接收管線沒有元件。</span><span class="sxs-lookup"><span data-stu-id="1e053-109">The pass-through receive pipeline has no components.</span></span> <span data-ttu-id="1e053-110">它用於不需要處理訊息內容的簡單通過實例。</span><span class="sxs-lookup"><span data-stu-id="1e053-110">It is used for simple pass-through scenarios when no message payload processing is necessary.</span></span> <span data-ttu-id="1e053-111">此管線一般用在已知訊息來源和目的，且訊息不需驗證、編碼或解譯的時候。</span><span class="sxs-lookup"><span data-stu-id="1e053-111">This pipeline is generally used when the source and the destination of the message are known, and the message requires no validation, encoding, or disassembling.</span></span> <span data-ttu-id="1e053-112">此管線通常與通過傳送管線搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1e053-112">This pipeline is commonly used in conjunction with the pass-through send pipeline.</span></span>  
  
 <span data-ttu-id="1e053-113">因為通過接收管線不包含解譯器，所以不能用以路由訊息至協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e053-113">Because it does not contain a disassembler, the pass-through receive pipeline cannot be used to route messages to orchestrations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e053-114">通過接收管線不支援屬性升級。</span><span class="sxs-lookup"><span data-stu-id="1e053-114">The pass-through receive pipeline does not support property promotion.</span></span>  
  
## <a name="passthrutransmit-pipeline"></a><span data-ttu-id="1e053-115">PassThruTransmit 管線</span><span class="sxs-lookup"><span data-stu-id="1e053-115">PassThruTransmit pipeline</span></span>  
 <span data-ttu-id="1e053-116">通過傳送管線沒有元件。</span><span class="sxs-lookup"><span data-stu-id="1e053-116">The pass-through-send pipeline has no components.</span></span> <span data-ttu-id="1e053-117">此管線一般用在傳送訊息到目的之前不需要處理文件的時候。</span><span class="sxs-lookup"><span data-stu-id="1e053-117">This pipeline is generally used when no document processing is necessary before sending the message to a destination.</span></span>  
  
## <a name="xmlreceive-pipeline"></a><span data-ttu-id="1e053-118">XMLReceive 管線</span><span class="sxs-lookup"><span data-stu-id="1e053-118">XMLReceive pipeline</span></span>  
 <span data-ttu-id="1e053-119">XML 接收管線包含下列階段：</span><span class="sxs-lookup"><span data-stu-id="1e053-119">The XML receive pipeline consists of the following stages:</span></span>  
  
-   <span data-ttu-id="1e053-120">**解碼。**</span><span class="sxs-lookup"><span data-stu-id="1e053-120">**Decode.**</span></span> <span data-ttu-id="1e053-121">Empty</span><span class="sxs-lookup"><span data-stu-id="1e053-121">Empty</span></span>  
  
-   <span data-ttu-id="1e053-122">**反組譯。**</span><span class="sxs-lookup"><span data-stu-id="1e053-122">**Disassemble.**</span></span> <span data-ttu-id="1e053-123">包含 XML 解譯器元件</span><span class="sxs-lookup"><span data-stu-id="1e053-123">Contains the XML Disassembler component</span></span>  
  
-   <span data-ttu-id="1e053-124">**驗證。**</span><span class="sxs-lookup"><span data-stu-id="1e053-124">**Validate.**</span></span> <span data-ttu-id="1e053-125">Empty</span><span class="sxs-lookup"><span data-stu-id="1e053-125">Empty</span></span>  
  
-   <span data-ttu-id="1e053-126">**解析合作對象。**</span><span class="sxs-lookup"><span data-stu-id="1e053-126">**ResolveParty.**</span></span> <span data-ttu-id="1e053-127">執行「合作對象解析」元件，將憑證主旨或來源安全性識別碼解析為合作對象識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e053-127">Runs the Party Resolution component, which resolves the certificate subject or the source security ID to the party ID.</span></span>  
  
## <a name="xmltransmit-pipeline"></a><span data-ttu-id="1e053-128">XMLTransmit 管線</span><span class="sxs-lookup"><span data-stu-id="1e053-128">XMLTransmit pipeline</span></span>  
 <span data-ttu-id="1e053-129">XML 傳送管線包含下列階段：</span><span class="sxs-lookup"><span data-stu-id="1e053-129">The XML send pipeline consists of the following stages:</span></span>  
  
-   <span data-ttu-id="1e053-130">**預先組合。**</span><span class="sxs-lookup"><span data-stu-id="1e053-130">**Pre-assemble.**</span></span> <span data-ttu-id="1e053-131">Empty</span><span class="sxs-lookup"><span data-stu-id="1e053-131">Empty</span></span>  
  
-   <span data-ttu-id="1e053-132">**組合。**</span><span class="sxs-lookup"><span data-stu-id="1e053-132">**Assemble.**</span></span> <span data-ttu-id="1e053-133">包含 XML 組合器元件</span><span class="sxs-lookup"><span data-stu-id="1e053-133">Contains the XML Assembler component</span></span>  
  
-   <span data-ttu-id="1e053-134">**編碼。**</span><span class="sxs-lookup"><span data-stu-id="1e053-134">**Encode.**</span></span> <span data-ttu-id="1e053-135">Empty</span><span class="sxs-lookup"><span data-stu-id="1e053-135">Empty</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e053-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e053-136">See Also</span></span>  
 <span data-ttu-id="1e053-137">[類型的管線](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="1e053-137">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="1e053-138">[類型的管線元件](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="1e053-138">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="1e053-139">[管線範本](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="1e053-139">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="1e053-140">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="1e053-140">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="1e053-141">關於管線、 階段和元件</span><span class="sxs-lookup"><span data-stu-id="1e053-141">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)