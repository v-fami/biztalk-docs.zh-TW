---
title: 使用動態路由 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caa3a35f-cafa-4524-8b96-f8a333b7ff87
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38b668f53ba87a461441b0dbb498ae0677fa5956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295694"
---
# <a name="using-dynamic-routing"></a><span data-ttu-id="a0b4f-102">使用動態路由</span><span class="sxs-lookup"><span data-stu-id="a0b4f-102">Using Dynamic Routing</span></span>
<span data-ttu-id="a0b4f-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援動態路由的訊息使用內建的程序和泛型傳遞代理程式; 它也支援動態路由使用 ESB 發送器或 ESB 發送器解譯管線元件在訊息層級的訊息。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports dynamic routing of messages using a built-in process and a generic delivery agent; it also supports dynamic routing of messages at the messaging layer using the ESB Dispatcher or ESB Dispatcher Disassemble pipeline components.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a0b4f-104">概觀</span><span class="sxs-lookup"><span data-stu-id="a0b4f-104">Overview</span></span>  
 <span data-ttu-id="a0b4f-105">中的動態解析機制[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]訊息抵達時，或在傳遞訊息之前，可讓探索端點。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-105">The dynamic resolution mechanism in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] enables discovery of endpoints when a message arrives or immediately before a message is delivered.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="a0b4f-106">運作方式</span><span class="sxs-lookup"><span data-stu-id="a0b4f-106">How It Works</span></span>  
 <span data-ttu-id="a0b4f-107">一般傳遞代理程式提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是範例，並開發和動態路由技術的使用方式的指引。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-107">The generic delivery agent provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is both a sample and a guide to the development and usage of dynamic routing techniques.</span></span> <span data-ttu-id="a0b4f-108">您可以輕鬆地建立其他傳遞的代理程式，或實作傳遞的代理程式只傳送埠所組成 （不會實作協調流程）。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-108">You can easily create additional delivery agents or implement delivery agents consisting of just a send port (which do not implement an orchestration).</span></span> <span data-ttu-id="a0b4f-109">根據預設，ESB 分派和 ESB 分派解譯器管線元件會提供更多了最佳化的動態路由的功能。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-109">By default, the ESB Dispatch and ESB Dispatch Disassembler pipeline components offer a much more optimized dynamic routing capability.</span></span>  
  
 <span data-ttu-id="a0b4f-110">一般傳遞代理程式本身實作訂閱訊息的協調流程其中**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-110">The generic delivery agent itself implements an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Routing**.</span></span> <span data-ttu-id="a0b4f-111">代理程式會執行下列一系列的作業：</span><span class="sxs-lookup"><span data-stu-id="a0b4f-111">The agent performs the following sequence of operations:</span></span>  
  
1.  <span data-ttu-id="a0b4f-112">接收不具型別的的訊息 (System.Xml.XmlDocument)。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-112">It receives an un-typed message (System.Xml.XmlDocument).</span></span>  
  
2.  <span data-ttu-id="a0b4f-113">它會嘗試解決 n 個端點使用的解析程式管理員。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-113">It attempts to resolve n number of endpoints using the resolver manager.</span></span>  
  
3.  <span data-ttu-id="a0b4f-114">它使用配接器管理員來設定訊息內容和邏輯的動態連接埠的端點內容。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-114">It uses the adapter manager to set the endpoint properties of the message context and the logical dynamic port.</span></span>  
  
4.  <span data-ttu-id="a0b4f-115">它將透過直接繫結傳送埠，進而觸發進一步訊息路由的動態傳送埠上的 BizTalk Server 訂用帳戶訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-115">It publishes the message through the direct-bound send port, which triggers the BizTalk Server subscription on the dynamic send port for further message routing.</span></span>  
  
## <a name="how-to-configure-dynamic-routing"></a><span data-ttu-id="a0b4f-116">如何設定動態路由</span><span class="sxs-lookup"><span data-stu-id="a0b4f-116">How to Configure Dynamic Routing</span></span>  
 <span data-ttu-id="a0b4f-117">如需如何設定動態路由使用路線設計工具的詳細資訊，請參閱 < 建立行程使用路線設計工具。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-117">For more information about how to configure dynamic routing using the Itinerary Designer, see Creating Itineraries Using Itinerary Designer.</span></span>  
  
## <a name="dynamic-routing-errors"></a><span data-ttu-id="a0b4f-118">動態路由的錯誤</span><span class="sxs-lookup"><span data-stu-id="a0b4f-118">Dynamic Routing Errors</span></span>  
 <span data-ttu-id="a0b4f-119">動態路由機制，將會建立並發行[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]在下列情況中的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a0b4f-119">The dynamic routing mechanism will create and publish an [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Fault message in the following cases:</span></span>  
  
-   <span data-ttu-id="a0b4f-120">傳遞代理程式無法判斷端點，在 just-in-time (JIT) 解析期間。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-120">The delivery agent cannot determine the endpoint during just-in-time (JIT) resolution.</span></span>  
  
-   <span data-ttu-id="a0b4f-121">傳遞失敗，就會發生。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-121">A delivery failure occurs.</span></span>  
  
-   <span data-ttu-id="a0b4f-122">沒有任何訂閱者有輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-122">No subscriber exists for the output message.</span></span>  
  
-   <span data-ttu-id="a0b4f-123">發生任何系統例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a0b4f-123">Any system exception occurs.</span></span>