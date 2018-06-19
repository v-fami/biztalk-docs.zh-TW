---
title: 編譯對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, compiling
- XSLT, generating
- maps, validating
- BizTalk Mapper, compiling
- BizTalk Mapper, validating
ms.assetid: 967181d6-22a9-4a76-ae45-3317c0c6321b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346769519343afe9456a7b1e7cf9a3bd5bb159ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231862"
---
# <a name="compiling-maps"></a><span data-ttu-id="16af4-102">編譯對應</span><span class="sxs-lookup"><span data-stu-id="16af4-102">Compiling Maps</span></span>
<span data-ttu-id="16af4-103">當您驗證對應時，BizTalk 對應工具編譯器元件會產生「可延伸樣式表語言轉換」(XSLT) 樣式表。</span><span class="sxs-lookup"><span data-stu-id="16af4-103">When you validate maps, the BizTalk Mapper compiler component generates an Extensible Stylesheet Language Transformations (XSLT) style sheet.</span></span> <span data-ttu-id="16af4-104">這會建立經過編譯的對應，可將來源結構描述定義的執行個體訊息轉換為目的結構描述定義的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="16af4-104">This creates a compiled map that transforms an instance message defined by the source schema to an instance message defined by the destination schema.</span></span> <span data-ttu-id="16af4-105">編譯對應可強制使用格線頁中指定的結構化規則與轉換。</span><span class="sxs-lookup"><span data-stu-id="16af4-105">Compiling a map enforces the structural rules and transformations specified in the grid pages.</span></span>  
  
 <span data-ttu-id="16af4-106">轉換 (例如連結) 會以記錄與欄位顯示在目的結構描述的相同順序處理。</span><span class="sxs-lookup"><span data-stu-id="16af4-106">Transformations, such as links, are processed in the same order that records and fields appear in the destination schema.</span></span> <span data-ttu-id="16af4-107">例如，當 BizTalk 對應工具到達目的地**記錄**或**欄位**節點的連結，BizTalk 對應工具會編譯連結的屬性。</span><span class="sxs-lookup"><span data-stu-id="16af4-107">For example, when BizTalk Mapper reaches a destination **Record** or **Field** node with a link, BizTalk Mapper compiles the properties of the link.</span></span> <span data-ttu-id="16af4-108">進行的動作可能只是從來源結構描述的記錄或欄位複製值，或可能包含使用運算質和多個記錄與欄位的多個運算式。</span><span class="sxs-lookup"><span data-stu-id="16af4-108">The action might be a simple copy value from a record or field in the source schema, or the action might involve multiple calculations using functoids and multiple records and fields.</span></span>  
  
 <span data-ttu-id="16af4-109">BizTalk 對應工具會產生警告中的**輸出**視窗和**工作清單**當編譯器遇到的情況，可能會產生不正確的輸出 視窗。</span><span class="sxs-lookup"><span data-stu-id="16af4-109">BizTalk Mapper generates warnings in the **Output** window and **Task List** window when the compiler encounters a situation that might yield incorrect output.</span></span> <span data-ttu-id="16af4-110">例如，如果運算質需要一個輸入的參數，而且沒有輸入參數，BizTalk 對應工具會產生一個警告**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="16af4-110">For example, if a functoid requires one input parameter and has no input parameters, BizTalk Mapper generates a warning in the **Output** window.</span></span> <span data-ttu-id="16af4-111">一般而言，若產生警告，就不應在生產環境中使用對應。</span><span class="sxs-lookup"><span data-stu-id="16af4-111">In general, you should not use a map in a production environment if it is generating warnings.</span></span>  
  
 <span data-ttu-id="16af4-112">產生的 XSLT 樣式表的連結也會出現在**輸出**會正確編譯對應時，視窗。</span><span class="sxs-lookup"><span data-stu-id="16af4-112">A link to the generated XSLT style sheet also appears in the **Output** window when the map compiles correctly.</span></span>  
  
 <span data-ttu-id="16af4-113">BizTalk Server 會使用已編譯的對應，將輸入執行個體訊息轉譯成輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="16af4-113">BizTalk Server uses the compiled map to perform the translation of an input instance message to an output instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16af4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16af4-114">See Also</span></span>  
 <span data-ttu-id="16af4-115">[測試對應](../core/testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="16af4-115">[Testing Maps](../core/testing-maps.md) </span></span>  
 <span data-ttu-id="16af4-116">[資料轉換組態](../core/data-transformation-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="16af4-116">[Data Transformation Configuration](../core/data-transformation-configuration.md) </span></span>  
 [<span data-ttu-id="16af4-117">節點階層層級比對</span><span class="sxs-lookup"><span data-stu-id="16af4-117">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)