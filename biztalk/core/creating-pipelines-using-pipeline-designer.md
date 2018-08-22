---
title: 使用管線設計師建立管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, processing messages
- pipelines, Pipeline Designer
- Pipeline Designer, about Pipeline Designer
ms.assetid: 858302d8-a912-4199-95e5-4322db789b4e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62e182440522e82f7ae6eaeaf52234161bee7483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998607"
---
# <a name="creating-pipelines-using-pipeline-designer"></a><span data-ttu-id="40f7c-102">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="40f7c-102">Creating Pipelines Using Pipeline Designer</span></span>
<span data-ttu-id="40f7c-103">Microsoft BizTalk Server 主要處理 XML 文件格式。</span><span class="sxs-lookup"><span data-stu-id="40f7c-103">Microsoft BizTalk Server works mainly with the XML document format.</span></span> <span data-ttu-id="40f7c-104">為能充分利用 BizTalk Server 處理優點，必須經常將訊息由其原生格式轉換為 XML 表示法。</span><span class="sxs-lookup"><span data-stu-id="40f7c-104">For a message to take full advantage of BizTalk Server processing, it must often be transformed from its native format into its XML representation.</span></span> <span data-ttu-id="40f7c-105">BizTalk Server 管線會針對內送與外寄訊息執行此轉換，以及其他資料特定動作 (例如，資料加密或解密、屬性升級等)。</span><span class="sxs-lookup"><span data-stu-id="40f7c-105">BizTalk Server pipelines perform this transformation, as well as other data-specific actions (such as data encryption or decryption, property promotion, and so on) on incoming and outgoing messages.</span></span> <span data-ttu-id="40f7c-106">本節提供關於管線和「管線設計師」的概念性和工作特定資訊。</span><span class="sxs-lookup"><span data-stu-id="40f7c-106">This section provides conceptual and task-specific information about pipelines and Pipeline Designer.</span></span>  
  
 <span data-ttu-id="40f7c-107">管線的目的是在配接器收到訊息之後準備訊息以供伺服器處理，或是在伺服器處理之後準備訊息以供傳送。</span><span class="sxs-lookup"><span data-stu-id="40f7c-107">The purpose of a pipeline is to prepare a message for processing by the server after being received by an adapter or to prepare a message for sending after being processed by the server.</span></span>  
  
 <span data-ttu-id="40f7c-108">管線通常執行的作業：</span><span class="sxs-lookup"><span data-stu-id="40f7c-108">Pipelines commonly perform:</span></span>  
  
- <span data-ttu-id="40f7c-109">將各種格式資料正規化為 XML。</span><span class="sxs-lookup"><span data-stu-id="40f7c-109">Data normalization from various formats to XML.</span></span>  
  
- <span data-ttu-id="40f7c-110">將 XML 資料轉換為各種格式。</span><span class="sxs-lookup"><span data-stu-id="40f7c-110">Data transformation from XML to various formats.</span></span>  
  
- <span data-ttu-id="40f7c-111">屬性升級和降級。</span><span class="sxs-lookup"><span data-stu-id="40f7c-111">Property promotion and demotion.</span></span>  
  
- <span data-ttu-id="40f7c-112">文件解譯和組合。</span><span class="sxs-lookup"><span data-stu-id="40f7c-112">Document disassembly and assembly.</span></span>  
  
- <span data-ttu-id="40f7c-113">文件解碼和編碼。</span><span class="sxs-lookup"><span data-stu-id="40f7c-113">Document decoding and encoding.</span></span>  
  
- <span data-ttu-id="40f7c-114">文件解密和加密。</span><span class="sxs-lookup"><span data-stu-id="40f7c-114">Document decryption and encryption.</span></span>  
  
- <span data-ttu-id="40f7c-115">文件簽章和數位簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="40f7c-115">Document signing and digital signature verification.</span></span>  
  
  <span data-ttu-id="40f7c-116">下圖顯示使用管線處理訊息所需的工作流程。</span><span class="sxs-lookup"><span data-stu-id="40f7c-116">The following figure shows the workflow involved in processing a message by using pipelines.</span></span>  
  
  <span data-ttu-id="40f7c-117">![處理訊息的工作流程的圖表。](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span><span class="sxs-lookup"><span data-stu-id="40f7c-117">![Diagram of workflow for processing a message.](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span></span>  
  <span data-ttu-id="40f7c-118">描述訊息處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="40f7c-118">Depicts the message processing workflow.</span></span>  
  
  <span data-ttu-id="40f7c-119">如圖所示，訊息從配接器傳送到接收管線，在此轉換為 XML。</span><span class="sxs-lookup"><span data-stu-id="40f7c-119">As shown in the figure, the message is passed from the adapter to the receive pipeline where it is transformed to XML.</span></span> <span data-ttu-id="40f7c-120">然後訊息可供協調流程使用，或傳遞到傳送管線，然後到達傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="40f7c-120">The message can then be used by orchestrations, or passed to a send pipeline, and then to a send adapter.</span></span>  
  
  <span data-ttu-id="40f7c-121">如需使用管線設計師鍵盤快速鍵的詳細資訊，請參閱[管線設計師鍵盤快速鍵](../core/pipeline-designer-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="40f7c-121">For information about using the keyboard shortcuts for Pipeline Designer, see [Pipeline Designer Keyboard Shortcuts](../core/pipeline-designer-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40f7c-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="40f7c-122">In This Section</span></span>  
  
-   [<span data-ttu-id="40f7c-123">關於管線、階段和元件</span><span class="sxs-lookup"><span data-stu-id="40f7c-123">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)  
  
-   [<span data-ttu-id="40f7c-124">使用管線設計師</span><span class="sxs-lookup"><span data-stu-id="40f7c-124">Using Pipeline Designer</span></span>](../core/using-pipeline-designer.md)  
  
-   [<span data-ttu-id="40f7c-125">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="40f7c-125">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)  
  
-   [<span data-ttu-id="40f7c-126">設定原生管線元件</span><span class="sxs-lookup"><span data-stu-id="40f7c-126">Configuring Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)  
  
-   [<span data-ttu-id="40f7c-127">如何部署管線</span><span class="sxs-lookup"><span data-stu-id="40f7c-127">How to Deploy Pipelines</span></span>](../core/how-to-deploy-pipelines.md)  
  
-   [<span data-ttu-id="40f7c-128">如何保護管線</span><span class="sxs-lookup"><span data-stu-id="40f7c-128">How to Secure Pipelines</span></span>](../core/how-to-secure-pipelines.md)