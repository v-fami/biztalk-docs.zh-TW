---
title: "配接器介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7398aeb-7c1c-400e-a552-d0ab39e55a0b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717adcf5d4a706a7cc072b42b224ab0f9f8cc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-interfaces"></a><span data-ttu-id="9121f-102">配接器介面</span><span class="sxs-lookup"><span data-stu-id="9121f-102">Adapter Interfaces</span></span>
<span data-ttu-id="9121f-103">在自訂配接器所實作的介面中，有三種介面是必要項目，另外兩種則是選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9121f-103">There are three interfaces that custom adapters must implement, and two interfaces that are optional.</span></span>  
  
## <a name="mandatory-interfaces"></a><span data-ttu-id="9121f-104">必要的介面</span><span class="sxs-lookup"><span data-stu-id="9121f-104">Mandatory interfaces</span></span>  
 <span data-ttu-id="9121f-105">所有配置器都必須實作下列介面。</span><span class="sxs-lookup"><span data-stu-id="9121f-105">All adapters must implement the following interfaces.</span></span>  
  
### <a name="ibasecomponent"></a><span data-ttu-id="9121f-106">IBaseComponent</span><span class="sxs-lookup"><span data-stu-id="9121f-106">IBaseComponent</span></span>  
 <span data-ttu-id="9121f-107">這個介面會詳細**名稱**，**版本**，和**描述**配接器。</span><span class="sxs-lookup"><span data-stu-id="9121f-107">This interface details the **Name**, **Version**, and **Description** of the adapter.</span></span>  
  
### <a name="ibttransport"></a><span data-ttu-id="9121f-108">IBTTransport</span><span class="sxs-lookup"><span data-stu-id="9121f-108">IBTTransport</span></span>  
 <span data-ttu-id="9121f-109">這個介面會詳細**傳輸類型**和**ClassID**配接器。</span><span class="sxs-lookup"><span data-stu-id="9121f-109">This interface details the **Transport Type** and **ClassID** of the adapter.</span></span>  
  
### <a name="ibtbatchcallback"></a><span data-ttu-id="9121f-110">IBTBatchCallback</span><span class="sxs-lookup"><span data-stu-id="9121f-110">IBTBatchCallback</span></span>  
 <span data-ttu-id="9121f-111">這個介面是回呼介面，透過此介面，配接器可針對提交給傳訊引擎的訊息批次而收到其狀態及錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9121f-111">This interface is a callback interface through which the adapter receives status and error information for a batch of messages it submits to the Messaging Engine.</span></span>  
  
## <a name="optional-interfaces"></a><span data-ttu-id="9121f-112">選擇性介面</span><span class="sxs-lookup"><span data-stu-id="9121f-112">Optional interfaces</span></span>  
 <span data-ttu-id="9121f-113">配接器可以依其需求，選擇是否要實作下列介面。</span><span class="sxs-lookup"><span data-stu-id="9121f-113">Adapters may or may not implement the following interfaces, depending on their needs.</span></span>  
  
### <a name="ipersistpropertybag"></a><span data-ttu-id="9121f-114">IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="9121f-114">IPersistPropertyBag</span></span>  
 <span data-ttu-id="9121f-115">這是組態介面，處理常式組態會透過此介面而傳遞到配接器。</span><span class="sxs-lookup"><span data-stu-id="9121f-115">This is a configuration interface through which handler configuration is delivered to the adapter.</span></span> <span data-ttu-id="9121f-116">只有具有處理常式組態資訊的配接器，才需要使用這個介面。</span><span class="sxs-lookup"><span data-stu-id="9121f-116">This interface is required only for adapters that have handler configuration information.</span></span>  
  
### <a name="ibttransportcontrol"></a><span data-ttu-id="9121f-117">IBTTransportControl</span><span class="sxs-lookup"><span data-stu-id="9121f-117">IBTTransportControl</span></span>  
 <span data-ttu-id="9121f-118">這個介面會用來初始化及終止配接器。</span><span class="sxs-lookup"><span data-stu-id="9121f-118">This interface is used to initialize and terminate an adapter.</span></span> <span data-ttu-id="9121f-119">傳輸 Proxy 會透過這個介面而傳遞給配接器。</span><span class="sxs-lookup"><span data-stu-id="9121f-119">The adapter's transport proxy is passed to it through this interface.</span></span> <span data-ttu-id="9121f-120">對外掛式配接器而言，這個介面不是必要的。</span><span class="sxs-lookup"><span data-stu-id="9121f-120">This interface is not required for isolated adapters.</span></span>