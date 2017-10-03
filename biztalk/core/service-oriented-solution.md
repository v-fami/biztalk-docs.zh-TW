---
title: "服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solutions
- tutorials, legacy applications
- business solutions, back-end systems
- service solution tutorial
- tutorials, services
- Web services, tutorials
- Web services, business solutions
- tutorials, applications
- applications, tutorials
- applications, services
- legacy applications, tutorials
- service solutions, business solutions
- tutorials, Web services
- tutorials, service solutions
- business solutions, totorials
- business solutions, legacy applications
- back-end systems
- tutorials, business solutions
- legacy applications, business solutions
- business solutions, Web services
- business solutions, service solutions
ms.assetid: ce7cdf8d-ecaf-4a6a-9536-a9cf5d7f874f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a1c69d537469cc1c2a4d9d93cde37014b31daa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="service-oriented-solution"></a><span data-ttu-id="1bb9d-102">服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="1bb9d-102">Service Oriented Solution</span></span>
<span data-ttu-id="1bb9d-103">服務導向解決方案顯示如何將 BizTalk 應用程式以服務的方式呈現，可做為 Web 服務並可供舊有應用程式存取的形式來使用。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-103">The service oriented solution shows how to present a BizTalk application as a service that is available as a Web service and in forms accessible to legacy applications.</span></span> <span data-ttu-id="1bb9d-104">解決方案也顯示如何與做為 Web 服務的後端程序通訊，以及如何從多個後端系統彙總回應。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-104">The solution also shows how to communicate with back-end processes as Web services, as well as how to aggregate responses from multiple back-end systems.</span></span>  
  
 <span data-ttu-id="1bb9d-105">以下幾節將提供解決方案的概觀、模式與設計選擇的詳細說明，以及建置與執行解決方案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-105">The sections provide an overview of the solution, detailed explanations of the patterns and design choices, and information about building and running the solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bb9d-106">在這幾節中所記載的模式和指導，用意在於說明特定商務解決方案的處理方式。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-106">The patterns and guidance documented in these sections are intended to illustrate an approach to a particular kind of business solution.</span></span> <span data-ttu-id="1bb9d-107">模式是簡單的機制，其用意是要套用至特定的問題，而且通常都會與其他的模式合併。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-107">Patterns are simple mechanisms that are meant to be applied to a specific problem and are usually combined with other patterns.</span></span> <span data-ttu-id="1bb9d-108">這些模式不是要用來插入到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-108">They are not meant to be plugged into an application.</span></span> <span data-ttu-id="1bb9d-109">此範例程式碼係以「現況」提供，而且不適用於實際執行用途。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-109">Example code is provided "as is" and is not intended for production use.</span></span> <span data-ttu-id="1bb9d-110">此範例的目的不在於說明模式，因此並不包括額外的程式碼，像是例外狀況處理、記錄、安全性及驗證。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-110">It is only intended to illustrate the pattern and therefore does not include extra code, such as exception handling, logging, security, and validation.</span></span> <span data-ttu-id="1bb9d-111">Microsoft 不支援將範例程式碼以「現況」部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="1bb9d-111">Microsoft does not support deploying the example code "as is" to production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1bb9d-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="1bb9d-112">In This Section</span></span>  
  
-   [<span data-ttu-id="1bb9d-113">瞭解服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="1bb9d-113">Understanding the Service Oriented Solution</span></span>](../core/understanding-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="1bb9d-114">開發服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="1bb9d-114">Developing a Service Oriented Solution</span></span>](../core/developing-a-service-oriented-solution.md)  
  
-   [<span data-ttu-id="1bb9d-115">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="1bb9d-115">Deploying the Service Oriented Solution</span></span>](../core/deploying-the-service-oriented-solution.md)