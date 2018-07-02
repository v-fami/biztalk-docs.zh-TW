---
title: 開發探查管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], probing
- IProbeMessage interface
- pipeline interfaces, IProbeMessage
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0be44929609eaba5ec30a6e40c1bdda14192e351
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987359"
---
# <a name="developing-a-probing-pipeline-component"></a><span data-ttu-id="b2af3-102">開發探查管線元件</span><span class="sxs-lookup"><span data-stu-id="b2af3-102">Developing a Probing Pipeline Component</span></span>
<span data-ttu-id="b2af3-103">可實作任何管線元件 （一般、 組合或解譯）`IProbeMessage`介面必須支援訊息探查功能。</span><span class="sxs-lookup"><span data-stu-id="b2af3-103">Any pipeline component (general, assembling, or disassembling) can implement the `IProbeMessage` interface if it must support message probing functionality.</span></span> <span data-ttu-id="b2af3-104">探查元件會在管線階段具有**FirstMatch**執行模式。</span><span class="sxs-lookup"><span data-stu-id="b2af3-104">A probing component is used in the pipeline stages that have **FirstMatch** execution mode.</span></span> <span data-ttu-id="b2af3-105">在這種階段中，BizTalk 傳訊引擎會提供訊息的開頭部分給元件，以確定該元件是否可識別訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="b2af3-105">In such stages, the BizTalk Messaging Engine gives the beginning part of the message to the component to determine if the component recognizes the format of the message.</span></span> <span data-ttu-id="b2af3-106">若元件可識別格式，則會傳送完整的訊息給此元件進行處理。</span><span class="sxs-lookup"><span data-stu-id="b2af3-106">If the component recognizes the format, the entire message is given to the component for processing.</span></span>  
  
 <span data-ttu-id="b2af3-107">**IProbeMessage**介面會公開單一方法**探查**，可讓元件能夠檢查訊息的開頭部分。</span><span class="sxs-lookup"><span data-stu-id="b2af3-107">The **IProbeMessage** interface exposes a single method, **Probe**, which enables the component to check the beginning part of the message.</span></span> <span data-ttu-id="b2af3-108">其傳回值則決定此元件是否已執行。</span><span class="sxs-lookup"><span data-stu-id="b2af3-108">The return value determines whether this component is run.</span></span> <span data-ttu-id="b2af3-109">下列步驟簡要說明 BizTalk 傳訊引擎如何執行需要識別的階段。</span><span class="sxs-lookup"><span data-stu-id="b2af3-109">The following steps outline how the BizTalk Messaging Engine runs a stage that requires recognition:</span></span>  
  
1. <span data-ttu-id="b2af3-110">若階段中未包含任何元件，則不會執行此階段，而且會將訊息傳送給後續階段進行處理。</span><span class="sxs-lookup"><span data-stu-id="b2af3-110">If the stage does not contain any components, the stage is not run and the message is given to the subsequent stages for processing.</span></span>  
  
2. <span data-ttu-id="b2af3-111">檢查元件是否實作**IProbeMessage**介面。</span><span class="sxs-lookup"><span data-stu-id="b2af3-111">Check if the component implements the **IProbeMessage** interface.</span></span> <span data-ttu-id="b2af3-112">若未實作，傳訊引擎會叫用元件。</span><span class="sxs-lookup"><span data-stu-id="b2af3-112">If not, the Messaging Engine invokes the component.</span></span> <span data-ttu-id="b2af3-113">完成階段處理，並將訊息傳送到下一個階段。</span><span class="sxs-lookup"><span data-stu-id="b2af3-113">The stage processing is done and the message is given to the next stage.</span></span>  
  
3. <span data-ttu-id="b2af3-114">**探查**叫用方法。</span><span class="sxs-lookup"><span data-stu-id="b2af3-114">The **Probe** method is invoked.</span></span> <span data-ttu-id="b2af3-115">如果傳回的值是 **，則為 True**，表示元件已執行。</span><span class="sxs-lookup"><span data-stu-id="b2af3-115">If the return value is **True**, the component is run.</span></span> <span data-ttu-id="b2af3-116">接著便完成階段處理，並將訊息傳送到下一個階段。</span><span class="sxs-lookup"><span data-stu-id="b2af3-116">Then the stage processing is done and the message is given to a next stage.</span></span>  
  
4. <span data-ttu-id="b2af3-117">傳訊引擎會取得此階段中的下一個元件。</span><span class="sxs-lookup"><span data-stu-id="b2af3-117">The Messaging Engine gets the next component in the stage.</span></span> <span data-ttu-id="b2af3-118">如果已經沒有其他元件，而且尚未執行任何元作，則會產生管線處理已經失敗的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b2af3-118">If there are no more components and none of the components have been run, it generates an error that pipeline processing has failed.</span></span> <span data-ttu-id="b2af3-119">如果已經沒有其他元件，但已經執行至少一個元件，則處理已完成。</span><span class="sxs-lookup"><span data-stu-id="b2af3-119">If there are no more components and at least one component has been run, the processing is done.</span></span>  
  
   <span data-ttu-id="b2af3-120">如果階段不需要辨識 (例如，執行模式是**所有**)，傳訊引擎會叫用元件而不先查詢**IProbeMessage**介面及呼叫**探查**方法。</span><span class="sxs-lookup"><span data-stu-id="b2af3-120">If a stage does not require recognition (for example, the execution mode is **All**), the Messaging Engine invokes the component without first querying for the **IProbeMessage** interface and calling the **Probe** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2af3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2af3-121">See Also</span></span>  
 <span data-ttu-id="b2af3-122">[開發一般管線元件](../core/developing-a-general-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="b2af3-122">[Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md) </span></span>  
 <span data-ttu-id="b2af3-123">[開發組合管線元件](../core/developing-an-assembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="b2af3-123">[Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="b2af3-124">[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="b2af3-124">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="b2af3-125">[報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="b2af3-125">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="b2af3-126">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="b2af3-126">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="b2af3-127">部署管線元件</span><span class="sxs-lookup"><span data-stu-id="b2af3-127">Deploying Pipeline Components</span></span>](../core/deploying-pipeline-components.md)