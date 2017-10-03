---
title: "商務解決方案的實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business solutions, tutorials
- tutorials, applications
- applications, tutorials
- applications, business solutions
- tutorials, business solutions
- solutions, tutorials
ms.assetid: f6239905-a1bf-4223-bdca-6677f2d6049b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 024f3a1f0422b6e7adf338610e1bbdb1fdc9857a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenarios-for-business-solutions"></a><span data-ttu-id="34111-102">商務解決方案的實例</span><span class="sxs-lookup"><span data-stu-id="34111-102">Scenarios for Business Solutions</span></span>
<span data-ttu-id="34111-103">本節說明兩個完整的模型 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="34111-103">This section describes two complete, model BizTalk applications.</span></span> <span data-ttu-id="34111-104">每個應用程式都代表一個特定的商務模式，並展示其他結構成分的整合模式。</span><span class="sxs-lookup"><span data-stu-id="34111-104">Each application represents a particular business pattern and demonstrates other constituent integration patterns.</span></span>  
  
 <span data-ttu-id="34111-105">以下幾節將說明應用程式的概觀、描述在開發應用程式的過程中要達成之模式和設計決策的開發人員手冊，以及繫結和執行應用程式的部署資訊。</span><span class="sxs-lookup"><span data-stu-id="34111-105">Each section presents an overview of the application, a developer's guide that describes the patterns and design decisions reached in the course of developing the application, and deployment information for building and running the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34111-106">在這幾節中所記載的模式和指導，用意在於說明特定商務解決方案的處理方式。</span><span class="sxs-lookup"><span data-stu-id="34111-106">The patterns and guidance documented in these sections are intended to illustrate an approach to a particular kind of business solution.</span></span> <span data-ttu-id="34111-107">模式是簡單的機制，其用意是要套用至特定的問題，而且通常都會與其他的模式合併。</span><span class="sxs-lookup"><span data-stu-id="34111-107">Patterns are simple mechanisms that are meant to be applied to a specific problem and are usually combined with other patterns.</span></span> <span data-ttu-id="34111-108">這些模式不是要用來插入到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="34111-108">They are not meant to be plugged into an application.</span></span> <span data-ttu-id="34111-109">此範例程式碼係以「現況」提供，而且不適用於實際執行用途。</span><span class="sxs-lookup"><span data-stu-id="34111-109">Example code is provided "as is" and is not intended for production use.</span></span> <span data-ttu-id="34111-110">此範例的目的不在於說明模式，因此並不包括額外的程式碼，像是例外狀況處理、記錄、安全性及驗證。</span><span class="sxs-lookup"><span data-stu-id="34111-110">It is only intended to illustrate the pattern and therefore does not include extra code, such as exception handling, logging, security, and validation.</span></span> <span data-ttu-id="34111-111">Microsoft 不支援將範例程式碼以「現況」部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="34111-111">Microsoft does not support deploying the example code "as is" to production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34111-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="34111-112">In This Section</span></span>  
  
-   [<span data-ttu-id="34111-113">服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="34111-113">Service Oriented Solution</span></span>](../core/service-oriented-solution.md)  
  
-   [<span data-ttu-id="34111-114">商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="34111-114">Business Process Management Solution</span></span>](../core/business-process-management-solution.md)