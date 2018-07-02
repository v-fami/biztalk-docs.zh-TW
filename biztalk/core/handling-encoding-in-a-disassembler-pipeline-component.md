---
title: 在解譯器管線元件中處理編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], encoding
- pipeline components [custom], disassembling
ms.assetid: 33420357-421f-4ad0-8eee-d445376676db
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 596161cd2ccf5d4f9a492bbdd23cd8f6f22c5c2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995231"
---
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a><span data-ttu-id="d5f49-102">在解譯器管線元件中處理編碼</span><span class="sxs-lookup"><span data-stu-id="d5f49-102">Handling Encoding in a Disassembler Pipeline Component</span></span>
<span data-ttu-id="d5f49-103">確定您的自訂解譯器元件使用下列其中一種格式為輸出文件編碼：</span><span class="sxs-lookup"><span data-stu-id="d5f49-103">Ensure that your custom disassembler component encodes outbound documents in one of the following formats:</span></span>  
  
- <span data-ttu-id="d5f49-104">UTF-8</span><span class="sxs-lookup"><span data-stu-id="d5f49-104">UTF-8</span></span>  
  
- <span data-ttu-id="d5f49-105">UTF-16</span><span class="sxs-lookup"><span data-stu-id="d5f49-105">UTF-16</span></span>  
  
- <span data-ttu-id="d5f49-106">UTF-32</span><span class="sxs-lookup"><span data-stu-id="d5f49-106">UTF-32</span></span>  
  
- <span data-ttu-id="d5f49-107">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="d5f49-107">UTF-16LE</span></span>  
  
- <span data-ttu-id="d5f49-108">UTF-16BE</span><span class="sxs-lookup"><span data-stu-id="d5f49-108">UTF-16BE</span></span>  
  
  <span data-ttu-id="d5f49-109">協調流程引擎可能無法處理具有其他編碼格式的文件。</span><span class="sxs-lookup"><span data-stu-id="d5f49-109">The orchestration engine may not be able to process documents with other encoding formats.</span></span>  
  
  <span data-ttu-id="d5f49-110">.NET Framework 不支援 UTF-32LE 和 UTF-32BE，若要使用這些格式，您必須建立自訂編碼實作。</span><span class="sxs-lookup"><span data-stu-id="d5f49-110">UTF-32LE and UTF-32BE are not supported by the .NET Framework; to use these formats, you must create a custom encoding implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f49-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5f49-111">See Also</span></span>  
 [<span data-ttu-id="d5f49-112">開發解譯管線元件</span><span class="sxs-lookup"><span data-stu-id="d5f49-112">Developing a Disassembling Pipeline Component</span></span>](../core/developing-a-disassembling-pipeline-component.md)