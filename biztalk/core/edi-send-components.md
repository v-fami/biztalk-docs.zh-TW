---
title: EDI 傳送元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce270db-a573-48b3-be15-0178a5b7785b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5520a0c1dd0a6ef7e42818314a9f87733aebcb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239926"
---
# <a name="edi-send-components"></a><span data-ttu-id="e4df9-102">EDI 傳送元件</span><span class="sxs-lookup"><span data-stu-id="e4df9-102">EDI Send Components</span></span>
<span data-ttu-id="e4df9-103">本主題所介紹的管線和管線元件，會處理不屬於 EDI/AS2 訊息的 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4df9-103">The pipeline and pipeline components described in this topic process EDI messages that are not EDI/AS2 messages.</span></span> <span data-ttu-id="e4df9-104">如需傳送 EDI/AS2 或非 EDI/AS2 訊息的資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e4df9-104">For information about the sending of EDI/AS2 or non-EDI/AS2 messages, see [AS2 Send Components](../core/as2-send-components.md).</span></span> <span data-ttu-id="e4df9-105">請注意，除了執行 AS2 處理之外，AS2 傳送元件也會執行 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="e4df9-105">Note that AS2 send components perform EDI processing in addition to AS2 processing.</span></span>  
  
## <a name="edi-send-pipeline"></a><span data-ttu-id="e4df9-106">EDI 傳送管線</span><span class="sxs-lookup"><span data-stu-id="e4df9-106">EDI Send Pipeline</span></span>  
 <span data-ttu-id="e4df9-107">EDI 傳送處理會在下列 EDISend 管線中執行。</span><span class="sxs-lookup"><span data-stu-id="e4df9-107">EDI send processing is performed in the following EDISend pipeline.</span></span> <span data-ttu-id="e4df9-108">這個管線會安裝在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 的 `Microsoft.BizTalk.Edi.EdiPipelines.dll` 中。</span><span class="sxs-lookup"><span data-stu-id="e4df9-108">This pipeline is installed in `Microsoft.BizTalk.Edi.EdiPipelines.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="e4df9-109">**EDISend 管線**</span><span class="sxs-lookup"><span data-stu-id="e4df9-109">**EDISend Pipeline**</span></span>  
  
 <span data-ttu-id="e4df9-110">這個管線會產生和傳送 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4df9-110">This pipeline generates and sends EDI messages.</span></span> <span data-ttu-id="e4df9-111">它不會處理透過 HTTP 接收的 AS2 編碼 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4df9-111">It does not process AS2-encoded EDI messages received over HTTP.</span></span> <span data-ttu-id="e4df9-112">AS2 編碼 EDI 訊息的處理是由 AS2 管線執行的。</span><span class="sxs-lookup"><span data-stu-id="e4df9-112">Processing of AS2-encoded EDI messages is performed by an AS2 pipeline.</span></span> <span data-ttu-id="e4df9-113">AS2 傳送管線會使用 EDI 管線所使用的相同元件來處理 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4df9-113">The AS2 send pipelines use the same components to process EDI messages as the EDI pipeline uses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4df9-114">不支援從協調流程執行 EDISend 管線。</span><span class="sxs-lookup"><span data-stu-id="e4df9-114">Running the EDISend pipeline from an orchestration is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4df9-115">AS2EDISend 管線會產生 EDI 訊息，並透過 AS2 傳輸來傳送。</span><span class="sxs-lookup"><span data-stu-id="e4df9-115">The AS2EDISend pipeline generates and sends EDI messages over AS2 transport.</span></span> <span data-ttu-id="e4df9-116">如需詳細資訊，請參閱[AS2 傳送元件](../core/as2-send-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e4df9-116">For more information, see [AS2 Send Components](../core/as2-send-components.md).</span></span>  
  
 <span data-ttu-id="e4df9-117">此管線是由 EDI 組合器管線元件組成：</span><span class="sxs-lookup"><span data-stu-id="e4df9-117">The pipeline consists of the EDI Assembler pipeline component:</span></span>  
  
## <a name="edi-send-pipeline-component"></a><span data-ttu-id="e4df9-118">EDI 傳送管線元件</span><span class="sxs-lookup"><span data-stu-id="e4df9-118">EDI Send Pipeline Component</span></span>  
 <span data-ttu-id="e4df9-119">EDISend 管線會使用 EDI 組合器管線元件。</span><span class="sxs-lookup"><span data-stu-id="e4df9-119">The EDISend pipeline uses the EDI Assembler pipeline component.</span></span> <span data-ttu-id="e4df9-120">此元件安裝在`Microsoft.BizTalk.Edi.PipelineComponents.dll`中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]管線元件\\。</span><span class="sxs-lookup"><span data-stu-id="e4df9-120">This component is installed in `Microsoft.BizTalk.Edi.PipelineComponents.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="e4df9-121">EDI 組合器會執行 EDISend 管線中大多數針對 EDI 編碼交換的處理作業。</span><span class="sxs-lookup"><span data-stu-id="e4df9-121">The EDI Assembler performs most processing of EDI-encoded interchanges in the EDISend Pipeline.</span></span> <span data-ttu-id="e4df9-122">EDI 組合器如何處理 EDI 訊息的詳細資訊，請參閱[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="e4df9-122">For information about how the EDI Assembler processes EDI messages, see [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).</span></span>