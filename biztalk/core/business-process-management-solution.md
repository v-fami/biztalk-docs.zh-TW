---
title: "商務程序管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business solutions, tutorials
- tutorials, orchestrations
- errors, tutorials
- business solutions, process management solutions
- process management solutions
- process management solutions, applications
- process management solutions, business solutions
- tutorials, applications
- tutorials, errors
- tutorials, process management solutions
- applications, tutorials
- tutorials, business solutions
- process management solutions, tutorials
- orchestrations, interrupting
- orchestrations, tutorials
- applications, process management solutions
ms.assetid: 30ebd248-7e31-4608-ae50-4fc6703ae613
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f37fa7691a3e780c0f972e1070a8bf639c4addcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-process-management-solution"></a><span data-ttu-id="ba2c6-102">商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="ba2c6-102">Business Process Management Solution</span></span>
<span data-ttu-id="ba2c6-103">商務程序管理解決方案會顯示如何設計 BizTalk 應用程式，以管理像是服務訂單處理等的商務程序。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-103">The Business Process Management solution shows how to design a BizTalk application to manage a business process such as service order processing.</span></span> <span data-ttu-id="ba2c6-104">解決方案會示範如何建構程式管理員，以及提供將程序分成不同階段的相關指導。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-104">The solution demonstrates how to construct a process manager and provides guidance about dividing a process into distinct stages.</span></span> <span data-ttu-id="ba2c6-105">解決方案也會描述如何建構可中斷的協調流程，以及大量且複雜的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-105">The solution also describes how to construct interruptible orchestrations as well as extensive, sophisticated exception handling.</span></span>  
  
 <span data-ttu-id="ba2c6-106">以下幾節將提供解決方案的概觀、模式與設計選擇的詳細說明，以及建置與執行解決方案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-106">The sections provide an overview of the solution, detailed explanations of the patterns and design choices, and information about building and running the solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba2c6-107">在這幾節中所記載的模式和指導，用意在於說明特定商務解決方案的處理方式。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-107">The patterns and guidance documented in these sections are intended to illustrate an approach to a particular kind of business solution.</span></span> <span data-ttu-id="ba2c6-108">模式是簡單的機制，其用意是要套用至特定的問題，而且通常都會與其他的模式合併。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-108">Patterns are simple mechanisms that are meant to be applied to a specific problem and are usually combined with other patterns.</span></span> <span data-ttu-id="ba2c6-109">這些模式不是要用來插入到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-109">They are not meant to be plugged into an application.</span></span> <span data-ttu-id="ba2c6-110">此範例程式碼係以「現況」提供，而且不適用於實際執行用途。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-110">Example code is provided "as is" and is not intended for production use.</span></span> <span data-ttu-id="ba2c6-111">此範例的目的不在於說明模式，因此並不包括額外的程式碼，像是例外狀況處理、記錄、安全性及驗證。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-111">It is only intended to illustrate the pattern and therefore does not include extra code, such as exception handling, logging, security, and validation.</span></span> <span data-ttu-id="ba2c6-112">Microsoft 不支援將範例程式碼以「現況」部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="ba2c6-112">Microsoft does not support deploying the example code "as is" to production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba2c6-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="ba2c6-113">In This Section</span></span>  
  
-   [<span data-ttu-id="ba2c6-114">了解商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="ba2c6-114">Understanding the Business Process Management Solution</span></span>](../core/understanding-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="ba2c6-115">開發商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="ba2c6-115">Developing a Business Process Management Solution</span></span>](../core/developing-a-business-process-management-solution.md)  
  
-   [<span data-ttu-id="ba2c6-116">部署商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="ba2c6-116">Deploying the Business Process Management Solution</span></span>](../core/deploying-the-business-process-management-solution.md)