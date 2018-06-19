---
title: 開發解譯管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDisassemblerComponent interface, disassembling
- pipeline components [custom], IDisassemblerComponent
- pipeline components [custom], IBaseComponent
- IBaseComponent interface, disassembling
- pipeline components [custom], disassembling
ms.assetid: 77c0aa7d-4d1b-4a8f-bef8-d38e7e4045c6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc4e831561f9940ad7e8ee91479a2fada1fcd910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239702"
---
# <a name="developing-a-disassembling-pipeline-component"></a><span data-ttu-id="4af8b-102">開發解譯管線元件</span><span class="sxs-lookup"><span data-stu-id="4af8b-102">Developing a Disassembling Pipeline Component</span></span>
<span data-ttu-id="4af8b-103">解譯管線元件會接收單一輸入訊息，並產生零個或多個輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="4af8b-103">A disassembling pipeline component receives one message on input and produces zero or more messages on output.</span></span> <span data-ttu-id="4af8b-104">解譯元件的用途是將交換的訊息分割成個別的文件。</span><span class="sxs-lookup"><span data-stu-id="4af8b-104">Disassembling components are used to split interchanges of messages into individual documents.</span></span> <span data-ttu-id="4af8b-105">解譯器元件必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="4af8b-105">Disassembler components must implement the following interfaces:</span></span>  
  
-   `IBaseComponent`
  
-   `IDisassemblerComponent`
  
-   `IComponentUI`
  
-   <span data-ttu-id="4af8b-106">**IPersistPropertyBag。**</span><span class="sxs-lookup"><span data-stu-id="4af8b-106">**IPersistPropertyBag .**</span></span> <span data-ttu-id="4af8b-107">如需此介面的詳細資訊，請參閱 .NET Framework SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="4af8b-107">Refer to the .NET Framework SDK documentation for this interface.</span></span>  
  
 <span data-ttu-id="4af8b-108">您可以建立自己的反組譯的元件擴充**FFDasmComp**或**XMLDasmComp**類別。</span><span class="sxs-lookup"><span data-stu-id="4af8b-108">You can create your own disassembling component by extending the **FFDasmComp** or **XMLDasmComp** class.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4af8b-109">如果自訂解譯器的 MessageDestination 內容屬性設定為 SuspendQueue，解譯器傳回的資料流就必須支援 Seek(0)，否則無法擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="4af8b-109">If your custom disassembler will be setting the MessageDestination context property to SuspendQueue, the stream returned by the disassembler must to support Seek(0) for the suspension to work.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4af8b-110">自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="4af8b-110">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="4af8b-111">其用意是要將這些部分保留到管線中做進一步處理。</span><span class="sxs-lookup"><span data-stu-id="4af8b-111">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4af8b-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="4af8b-112">In This Section</span></span>  
  
-   [<span data-ttu-id="4af8b-113">管線元件中處理內送資料流</span><span class="sxs-lookup"><span data-stu-id="4af8b-113">Handling Incoming Data Streams in Pipeline Components</span></span>](../core/handling-incoming-data-streams-in-pipeline-components.md)  
  
-   [<span data-ttu-id="4af8b-114">處理解譯器管線元件中的編碼</span><span class="sxs-lookup"><span data-stu-id="4af8b-114">Handling Encoding in a Disassembler Pipeline Component</span></span>](../core/handling-encoding-in-a-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4af8b-115">延伸一般檔案解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="4af8b-115">Extending the Flat File Disassembler Pipeline Component</span></span>](../core/extending-the-flat-file-disassembler-pipeline-component.md)