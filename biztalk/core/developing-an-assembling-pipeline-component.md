---
title: "開發組合管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IComponentUI interface, assembling
- IBaseComponent interface, assembling
- pipeline interfaces, IBaseComponent
- pipeline components [custom], interfaces
- pipeline interfaces, IComponentUI
- IAssemblerComponent interface, assembling
- pipeline interfaces, IAssemblerComponent
- pipeline components [custom], assembling
ms.assetid: 2f85421d-2010-4a36-82b5-ea8016f8aa99
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de06a815e1c5a6bf71700ad373ae3f278b3a9a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-an-assembling-pipeline-component"></a><span data-ttu-id="dbb3e-102">開發組合管線元件</span><span class="sxs-lookup"><span data-stu-id="dbb3e-102">Developing an Assembling Pipeline Component</span></span>
<span data-ttu-id="dbb3e-103">組合管線元件是一種 .NET 或 COM 元件，會接收數個輸入訊息，並產生一個輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-103">An assembling pipeline component is a .NET or COM component that receives several messages on input and produces one message on output.</span></span> <span data-ttu-id="dbb3e-104">組合元件的用途是將個別文件收集到訊息交換批次中。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-104">Assembling components are used to collect individual documents into the message interchange batch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbb3e-105">因為並沒有使用組件功能，所以 BizTalk Server 永遠都會將一份文件傳遞給元件輸入。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-105">Assembly functionality is not used, so BizTalk Server always passes one document to the component input.</span></span>  
  
 <span data-ttu-id="dbb3e-106">組合元件必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="dbb3e-106">An assembling component must implement the following interfaces:</span></span>  
  
-   `IBaseComponent`  
  
-   `IAssemblerComponent`
  
-   `IComponentUI`
  
-   <span data-ttu-id="dbb3e-107">**IPersistPropertyBag。**</span><span class="sxs-lookup"><span data-stu-id="dbb3e-107">**IPersistPropertyBag .**</span></span> <span data-ttu-id="dbb3e-108">如需此介面的詳細資訊，請參閱 .NET Framework SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-108">Refer to the .NET Framework SDK documentation for this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbb3e-109">自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-109">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="dbb3e-110">其用意是要將這些部分保留到管線中做進一步處理。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-110">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb3e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbb3e-111">See Also</span></span>  
 <span data-ttu-id="dbb3e-112">[開發一般管線元件](../core/developing-a-general-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-112">[Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md) </span></span>  
 <span data-ttu-id="dbb3e-113">[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-113">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="dbb3e-114">[開發探查管線元件](../core/developing-a-probing-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-114">[Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md) </span></span>  
 <span data-ttu-id="dbb3e-115">[報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-115">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="dbb3e-116">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-116">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="dbb3e-117">[部署管線元件](../core/deploying-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="dbb3e-117">[Deploying Pipeline Components](../core/deploying-pipeline-components.md) </span></span>  
 [<span data-ttu-id="dbb3e-118">CustomComponent （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="dbb3e-118">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)