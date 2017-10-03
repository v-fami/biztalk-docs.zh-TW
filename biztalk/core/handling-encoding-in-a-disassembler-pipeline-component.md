---
title: "處理解譯器管線元件中的編碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], encoding
- pipeline components [custom], disassembling
ms.assetid: 33420357-421f-4ad0-8eee-d445376676db
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcbfb8f86847668436fae04db7bee1703dfb60ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a><span data-ttu-id="72ed0-102">處理解譯器管線元件中的編碼</span><span class="sxs-lookup"><span data-stu-id="72ed0-102">Handling Encoding in a Disassembler Pipeline Component</span></span>
<span data-ttu-id="72ed0-103">確定您的自訂解譯器元件使用下列其中一種格式為輸出文件編碼：</span><span class="sxs-lookup"><span data-stu-id="72ed0-103">Ensure that your custom disassembler component encodes outbound documents in one of the following formats:</span></span>  
  
-   <span data-ttu-id="72ed0-104">UTF-8</span><span class="sxs-lookup"><span data-stu-id="72ed0-104">UTF-8</span></span>  
  
-   <span data-ttu-id="72ed0-105">UTF-16</span><span class="sxs-lookup"><span data-stu-id="72ed0-105">UTF-16</span></span>  
  
-   <span data-ttu-id="72ed0-106">UTF-32</span><span class="sxs-lookup"><span data-stu-id="72ed0-106">UTF-32</span></span>  
  
-   <span data-ttu-id="72ed0-107">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="72ed0-107">UTF-16LE</span></span>  
  
-   <span data-ttu-id="72ed0-108">UTF-16BE</span><span class="sxs-lookup"><span data-stu-id="72ed0-108">UTF-16BE</span></span>  
  
 <span data-ttu-id="72ed0-109">協調流程引擎可能無法處理具有其他編碼格式的文件。</span><span class="sxs-lookup"><span data-stu-id="72ed0-109">The orchestration engine may not be able to process documents with other encoding formats.</span></span>  
  
 <span data-ttu-id="72ed0-110">.NET Framework 不支援 UTF-32LE 和 UTF-32BE，若要使用這些格式，您必須建立自訂編碼實作。</span><span class="sxs-lookup"><span data-stu-id="72ed0-110">UTF-32LE and UTF-32BE are not supported by the .NET Framework; to use these formats, you must create a custom encoding implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ed0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72ed0-111">See Also</span></span>  
 [<span data-ttu-id="72ed0-112">開發解譯管線元件</span><span class="sxs-lookup"><span data-stu-id="72ed0-112">Developing a Disassembling Pipeline Component</span></span>](../core/developing-a-disassembling-pipeline-component.md)