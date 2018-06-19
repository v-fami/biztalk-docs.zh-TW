---
title: 關於 BizTalk 協調流程引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac12012f-6253-4589-84b3-c1bb102ce8dd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e4e686f066c2fcde921e45d08b60d6386e86640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224446"
---
# <a name="about-the-biztalk-orchestration-engine"></a><span data-ttu-id="70ff9-102">關於 BizTalk 協調流程引擎</span><span class="sxs-lookup"><span data-stu-id="70ff9-102">About the BizTalk Orchestration Engine</span></span>
<span data-ttu-id="70ff9-103">在執行階段，BizTalk 協調流程引擎會執行由 BizTalk 協調流程設計師所產生的 XLANG/s 檔案。</span><span class="sxs-lookup"><span data-stu-id="70ff9-103">At run time, the BizTalk Orchestration Engine executes XLANG/s files that are produced by BizTalk Orchestration Designer.</span></span> <span data-ttu-id="70ff9-104">協調流程設計師是一個功能豐富的圖形工具，可以視覺方式來設計商務程序。</span><span class="sxs-lookup"><span data-stu-id="70ff9-104">Orchestration Designer is a rich graphical tool for visually designing business processes.</span></span> <span data-ttu-id="70ff9-105">它會產生 XLANG/s 檔案，這些檔案具有 .odx 副檔名，而且其標頭中包含其他視覺化資訊，本文中則包含自訂屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="70ff9-105">It generates XLANG/s files that have an .odx extension and contain additional visualization information in their headers and custom attribute information in their bodies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ff9-106">XLANG/s 可視為具有某些 C# 運算式功能的訊息語言。</span><span class="sxs-lookup"><span data-stu-id="70ff9-106">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span>  
  
 <span data-ttu-id="70ff9-107">協調流程引擎的主要功能如下：</span><span class="sxs-lookup"><span data-stu-id="70ff9-107">The primary functions of the orchestration engine are:</span></span>  
  
-   <span data-ttu-id="70ff9-108">保存</span><span class="sxs-lookup"><span data-stu-id="70ff9-108">Persistence</span></span>  
  
-   <span data-ttu-id="70ff9-109">裝載 .NET 元件</span><span class="sxs-lookup"><span data-stu-id="70ff9-109">Hosting the .NET components</span></span>  
  
-   <span data-ttu-id="70ff9-110">交易</span><span class="sxs-lookup"><span data-stu-id="70ff9-110">Transactions</span></span>  
  
-   <span data-ttu-id="70ff9-111">大型訊息支援</span><span class="sxs-lookup"><span data-stu-id="70ff9-111">Large message support</span></span>  
  
-   <span data-ttu-id="70ff9-112">執行階段驗證</span><span class="sxs-lookup"><span data-stu-id="70ff9-112">Runtime validation</span></span>  
  
-   <span data-ttu-id="70ff9-113">負載節流</span><span class="sxs-lookup"><span data-stu-id="70ff9-113">Load throttling</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70ff9-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="70ff9-114">In This Section</span></span>  
  
-   [<span data-ttu-id="70ff9-115">持續性和協調流程引擎</span><span class="sxs-lookup"><span data-stu-id="70ff9-115">Persistence and the Orchestration Engine</span></span>](../core/persistence-and-the-orchestration-engine.md)  
  
-   [<span data-ttu-id="70ff9-116">協調流程凍結和解除凍結</span><span class="sxs-lookup"><span data-stu-id="70ff9-116">Orchestration Dehydration and Rehydration</span></span>](../core/orchestration-dehydration-and-rehydration.md)  
  
-   [<span data-ttu-id="70ff9-117">協調流程引擎的執行階段驗證</span><span class="sxs-lookup"><span data-stu-id="70ff9-117">Runtime Validation for the Orchestration Engine</span></span>](../core/runtime-validation-for-the-orchestration-engine.md)  
  
-   [<span data-ttu-id="70ff9-118">協調流程引擎組態</span><span class="sxs-lookup"><span data-stu-id="70ff9-118">Orchestration Engine Configuration</span></span>](../core/orchestration-engine-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="70ff9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ff9-119">See Also</span></span>  
 <span data-ttu-id="70ff9-120">[BizTalk Server 架構](../core/biztalk-server-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="70ff9-120">[BizTalk Server Architecture](../core/biztalk-server-architecture.md) </span></span>  
 <span data-ttu-id="70ff9-121">[XLANG 的語言](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="70ff9-121">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 <span data-ttu-id="70ff9-122">[透過主控件節流將資源使用最佳化](../core/optimizing-resource-usage-through-host-throttling.md) </span><span class="sxs-lookup"><span data-stu-id="70ff9-122">[Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md) </span></span>  
 [<span data-ttu-id="70ff9-123">BizTalk Server 如何處理大型訊息</span><span class="sxs-lookup"><span data-stu-id="70ff9-123">How BizTalk Server Processes Large Messages</span></span>](../core/how-biztalk-server-processes-large-messages.md)