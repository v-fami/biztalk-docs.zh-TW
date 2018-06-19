---
title: 範例案例的威脅模型分析 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TMA, security
- security examples [TMA]
- TMA, examples
- examples, TMA
ms.assetid: e35d1d7f-a71a-42f5-b1f4-fe3234ba7686
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afc1e375945ec7b40c56274adc5e18cb1ee67f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269110"
---
# <a name="sample-scenarios-for-threat-model-analysis"></a><span data-ttu-id="bb1b4-102">威脅模型分析的範例實例</span><span class="sxs-lookup"><span data-stu-id="bb1b4-102">Sample Scenarios for Threat Model Analysis</span></span>
<span data-ttu-id="bb1b4-103">本節提供針對範例架構識別在每個使用案例的步驟和結果的威脅模型分析 (TMA)[小 & Medium-Sized 公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)。</span><span class="sxs-lookup"><span data-stu-id="bb1b4-103">This section provides the steps and results of a threat model analysis (TMA) for each usage scenario for the sample architecture identified in [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md).</span></span> <span data-ttu-id="bb1b4-104">本節的目的是向您展示 TMA 的步驟。</span><span class="sxs-lookup"><span data-stu-id="bb1b4-104">The purpose of this section is to show you the steps of a TMA.</span></span> <span data-ttu-id="bb1b4-105">這可協助您瞭解 TMA 如何運作，並向您描述我們為範例架構識別的潛在威脅，以及如何降低其影響的建議。</span><span class="sxs-lookup"><span data-stu-id="bb1b4-105">This helps you understand how a TMA works, and describes for you the potential threats we identified for the sample architecture and how we recommend that you reduce their effect.</span></span>  
  
 <span data-ttu-id="bb1b4-106">我們根據您可以搭配 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用的不同配接器，以及企業單一登入的使用方式來分類使用實例。</span><span class="sxs-lookup"><span data-stu-id="bb1b4-106">We categorize the usage scenarios based on the different adapters you can use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and the use of Enterprise Single-Sign On.</span></span>  
  
 <span data-ttu-id="bb1b4-107">對於每個實例，我們遵循下列步驟來完成威脅模型分析：</span><span class="sxs-lookup"><span data-stu-id="bb1b4-107">For each scenario, we followed these steps to complete the Threat Model Analysis:</span></span>  
  
-   <span data-ttu-id="bb1b4-108">收集背景資訊</span><span class="sxs-lookup"><span data-stu-id="bb1b4-108">Collect background information</span></span>  
  
-   <span data-ttu-id="bb1b4-109">建立和分析威脅模型</span><span class="sxs-lookup"><span data-stu-id="bb1b4-109">Create and analyze the threat model</span></span>  
  
-   <span data-ttu-id="bb1b4-110">檢視威脅</span><span class="sxs-lookup"><span data-stu-id="bb1b4-110">Review threats</span></span>  
  
-   <span data-ttu-id="bb1b4-111">識別防護技巧與技術</span><span class="sxs-lookup"><span data-stu-id="bb1b4-111">Identify mitigation techniques and technologies</span></span>  
  
 <span data-ttu-id="bb1b4-112">威脅模型分析的詳細資訊，請參閱[威脅模型分析](../core/threat-model-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="bb1b4-112">For more information Threat Model Analysis, see [Threat Model Analysis](../core/threat-model-analysis.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb1b4-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="bb1b4-113">In This Section</span></span>  
  
-   [<span data-ttu-id="bb1b4-114">範例實例的背景資訊</span><span class="sxs-lookup"><span data-stu-id="bb1b4-114">Background Information for Sample Scenarios</span></span>](../core/background-information-for-sample-scenarios.md)  
  
-   [<span data-ttu-id="bb1b4-115">範例 TMA: HTTP 與 SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="bb1b4-115">Sample TMA: HTTP and SOAP Adapters</span></span>](../core/sample-tma-http-and-soap-adapters.md)  
  
-   [<span data-ttu-id="bb1b4-116">範例 TMA: BizTalk 訊息佇列配接器</span><span class="sxs-lookup"><span data-stu-id="bb1b4-116">Sample TMA: BizTalk Message Queuing Adapter</span></span>](../core/sample-tma-biztalk-message-queuing-adapter.md)  
  
-   [<span data-ttu-id="bb1b4-117">範例 TMA: File 配接器</span><span class="sxs-lookup"><span data-stu-id="bb1b4-117">Sample TMA: File Adapter</span></span>](../core/sample-tma-file-adapter.md)  
  
-   [<span data-ttu-id="bb1b4-118">範例 TMA: FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="bb1b4-118">Sample TMA: FTP Adapter</span></span>](../core/sample-tma-ftp-adapter.md)  
  
-   [<span data-ttu-id="bb1b4-119">範例 TMA： 企業單一登入</span><span class="sxs-lookup"><span data-stu-id="bb1b4-119">Sample TMA: Enterprise Single Sign-On</span></span>](../core/sample-tma-enterprise-single-sign-on.md)