---
title: "如何使用.NET 組件做為資料來源 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rule Composer, data sources
ms.assetid: 14dbec48-acc9-4c3c-bd7f-737dabf29543
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa56370cf894d0d18a36320ca97c4d028fee487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-net-assembly-as-a-data-source"></a><span data-ttu-id="ee90f-102">如何使用 .NET 組件做為資料來源</span><span class="sxs-lookup"><span data-stu-id="ee90f-102">How to Use a .NET Assembly as a Data Source</span></span>
<span data-ttu-id="ee90f-103">您可以指定 .NET 組件作為資料來源。</span><span class="sxs-lookup"><span data-stu-id="ee90f-103">You can specify a .NET assembly as a data source.</span></span> <span data-ttu-id="ee90f-104">然後從組件選取類別或類別成員，將它拖曳至詞彙定義或規則中。</span><span class="sxs-lookup"><span data-stu-id="ee90f-104">You can subsequently select a class or class member from the assembly, and drag it onto a vocabulary definition or rule.</span></span>  
  
### <a name="to-specify-a-net-assembly-as-a-data-source"></a><span data-ttu-id="ee90f-105">指定 .NET 組件作為資料來源</span><span class="sxs-lookup"><span data-stu-id="ee90f-105">To specify a .NET assembly as a data source</span></span>  
  
1.  <span data-ttu-id="ee90f-106">在 事實總管 視窗中，按一下**.NET 類別** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ee90f-106">In the Facts Explorer window, click the **.NET Classes** tab.</span></span>  
  
2.  <span data-ttu-id="ee90f-107">以滑鼠右鍵按一下**模組**節點。</span><span class="sxs-lookup"><span data-stu-id="ee90f-107">Right-click the **Modules** node.</span></span>  
  
3.  <span data-ttu-id="ee90f-108">從可用的組件中選取 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="ee90f-108">From the available assemblies, select a .NET assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee90f-109">組件必須位在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="ee90f-109">The assemblies have to be in the global assembly cache (GAC).</span></span> <span data-ttu-id="ee90f-110">當您瀏覽.NET 組件中，「 商務規則編輯器 」 會載入.NET 組件**事實總管**視窗或在**.NET 類別或類別成員定義**頁面**詞彙定義**視窗。</span><span class="sxs-lookup"><span data-stu-id="ee90f-110">The business rule composer loads a .NET assembly when you browse for the .NET assembly in the **Facts Explorer** window or in the **.NET Class or Class Member Definition** page of the **Vocabulary Definition** window.</span></span>  <span data-ttu-id="ee90f-111">如果您在 GAC 中更新此組件，請關閉商務規則編輯器並將它重新啟動，以載入更新的 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="ee90f-111">If you update the assembly in the GAC, close the business rule composer and restart it to load the updated .NET assembly.</span></span> <span data-ttu-id="ee90f-112">商務規則編輯器並不會自動重新整理此組件。</span><span class="sxs-lookup"><span data-stu-id="ee90f-112">The business rule composer does not refresh the assembly automatically.</span></span>  
  
     <span data-ttu-id="ee90f-113">![事實和定義樹狀結構瀏覽器的螢幕擷取畫面。] (../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")</span><span class="sxs-lookup"><span data-stu-id="ee90f-113">![Screenshot of facts and definition tree browser.](../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")</span></span>