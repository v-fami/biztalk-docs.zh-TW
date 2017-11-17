---
title: "攔截器 EventSource 項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78846c1-3984-43af-a13f-9d5c0a66d3b5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b5cd6b2e872f689988f3d10d18df002f66d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-eventsource-element"></a><span data-ttu-id="2a288-102">攔截器 EventSource 項目</span><span class="sxs-lookup"><span data-stu-id="2a288-102">Interceptor EventSource Element</span></span>
<span data-ttu-id="2a288-103">**EventSource**項目會提供一或多個出現在攔截器組態檔中的事件來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2a288-103">The **EventSource** element provides information about the source of one or more of the events appearing in the interceptor configuration file.</span></span> <span data-ttu-id="2a288-104">除了事件來源名稱，您還必須指出技術和來源的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="2a288-104">In addition to an event source name, you need to indicate the technology and a manifest for the source.</span></span>  
  
## <a name="format"></a><span data-ttu-id="2a288-105">格式</span><span class="sxs-lookup"><span data-stu-id="2a288-105">Format</span></span>  
 <span data-ttu-id="2a288-106">`EventSource` 項目有三個屬性，而且會根據所包含的結構描述，決定是否使用子項目。</span><span class="sxs-lookup"><span data-stu-id="2a288-106">The `EventSource` element has three attributes and may or may not have child elements depending upon which schemas are included.</span></span> <span data-ttu-id="2a288-107">例如，WCF 結構描述 WcfInterceptorConfiguration.xsd 提供了 `NamespaceMapping` 項目。</span><span class="sxs-lookup"><span data-stu-id="2a288-107">For example, the WCF schema WcfInterceptorConfiguration.xsd provides for the `NamespaceMapping` element.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a288-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2a288-108">Attributes</span></span>  
  
|<span data-ttu-id="2a288-109">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="2a288-109">Attribute name</span></span>|<span data-ttu-id="2a288-110">Description</span><span class="sxs-lookup"><span data-stu-id="2a288-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2a288-111">名稱</span><span class="sxs-lookup"><span data-stu-id="2a288-111">Name</span></span>|<span data-ttu-id="2a288-112">此事件來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a288-112">Name for this event source.</span></span> <span data-ttu-id="2a288-113">此名稱由**OnEvent**參考來源的項目。</span><span class="sxs-lookup"><span data-stu-id="2a288-113">This name is used by **OnEvent** entries to refer to the source.</span></span>|  
|<span data-ttu-id="2a288-114">技術</span><span class="sxs-lookup"><span data-stu-id="2a288-114">Technology</span></span>|<span data-ttu-id="2a288-115">裝載資訊清單中所指出事件來源的技術類型。</span><span class="sxs-lookup"><span data-stu-id="2a288-115">Technology type hosting the event source indicated in the manifest.</span></span> <span data-ttu-id="2a288-116">使用 "WF" 代表 Windows Workflow Foundation，而 "WCF" 代表 Windows Communication Framework。</span><span class="sxs-lookup"><span data-stu-id="2a288-116">Use "WF" for Windows Workflow Foundation and "WCF" for Windows Communication Framework.</span></span>|  
|<span data-ttu-id="2a288-117">資訊清單</span><span class="sxs-lookup"><span data-stu-id="2a288-117">Manifest</span></span>|<span data-ttu-id="2a288-118">做為事件來源之類型的組件限定類別名稱。</span><span class="sxs-lookup"><span data-stu-id="2a288-118">Assembly-qualified class name of the type to use as an event source.</span></span> <span data-ttu-id="2a288-119">例如，使用 IPv4 位址的 `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`</span><span class="sxs-lookup"><span data-stu-id="2a288-119">For example, `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`</span></span><br /><br /> <span data-ttu-id="2a288-120">如果您沒有公開金鑰 Token，請使用 `PublicKeyToken=null`。</span><span class="sxs-lookup"><span data-stu-id="2a288-120">If you do not have a public key token, use `PublicKeyToken=null`.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a288-121">範例</span><span class="sxs-lookup"><span data-stu-id="2a288-121">Example</span></span>  
 <span data-ttu-id="2a288-122">下列範例包含兩個**EventSource**項目，一個目標 WF 和 WCF 一個做為目標。</span><span class="sxs-lookup"><span data-stu-id="2a288-122">The following example contains two **EventSource** elements, one targeting WF and one targeting WCF.</span></span>  
  
```  
<!-- WF -->  
<ic:EventSource Name="OrderWorkflow" Technology="WF" Manifest="SimpleWorkflow.OrderWorkflow, SimpleWorkflow, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
<!-- WCF -->  
<ic:EventSource Name="PurchaseService" Technology="WCF" Manifest="Service.IProcessPOContract, DuplexService, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
```