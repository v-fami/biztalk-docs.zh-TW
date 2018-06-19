---
title: 接收來自 PeopleSoft |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9acc71ec-05b8-4490-b3ba-0ce7f27a5a6a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca87df1875f648abe2a986fb0d94b16865ee72f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014381"
---
# <a name="receiving-from-peoplesoft"></a><span data-ttu-id="dc5d8-102">從 PeopleSoft 接收</span><span class="sxs-lookup"><span data-stu-id="dc5d8-102">Receiving from PeopleSoft</span></span>
<span data-ttu-id="dc5d8-103">Microsoft Adapter for PeopleSoft Enterprise 為傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-103">The Microsoft Adapter for PeopleSoft Enterprise is a send adapter.</span></span> <span data-ttu-id="dc5d8-104">配接器支援請求-回應，以便您可以先傳送查詢，並取得回應。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-104">The adapter supports solicit-response, so that you can send a query and get back a response.</span></span> <span data-ttu-id="dc5d8-105">不過，如果您只想接收來自 PeopleSoft 的資料，則必須採取額外兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="dc5d8-105">However, if you want only to receive data from PeopleSoft, you must take two additional steps:</span></span>  
  
1.  <span data-ttu-id="dc5d8-106">使用「設定命名空間」管線元件，建立自訂接收管線。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-106">Create a custom receive pipeline using the Set Namespace pipeline component.</span></span>  
  
2.  <span data-ttu-id="dc5d8-107">建立可從 PeopleSoft 存取的接收埠，例如使用 HTTP 配接器的連接埠。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-107">Create a receive port accessible from PeopleSoft such as a port using the HTTP Adapter.</span></span> <span data-ttu-id="dc5d8-108">將自訂接收管線與此接收埠搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-108">Use the custom receive pipeline with the receive port.</span></span>  
  
## <a name="set-namespace-pipeline-component"></a><span data-ttu-id="dc5d8-109">設定命名空間管線元件</span><span class="sxs-lookup"><span data-stu-id="dc5d8-109">Set Namespace Pipeline Component</span></span>  
 <span data-ttu-id="dc5d8-110">接收自 PeopleSoft 的訊息不包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-110">Messages received from PeopleSoft do not include namespaces.</span></span> <span data-ttu-id="dc5d8-111">「設定命名空間」管線元件可讓您將命名空間新增至內送訊息。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-111">The Set Namespace pipeline component enables you to add a namespace to the incoming message.</span></span>  
  
 <span data-ttu-id="dc5d8-112">「設定命名空間」管線元件的預設位置是 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-112">The default location for the Set Namespace pipeline component is C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component.</span></span> <span data-ttu-id="dc5d8-113">您需要將 Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll 元件複製到 BizTalk 所使用的管線元件目錄。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-113">You need to copy the component, Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll, to the Pipeline Component directory used by BizTalk.</span></span> <span data-ttu-id="dc5d8-114">您還需要將此元件新增至 Visual Studio 工具箱，才能在 [管線設計師] 中使用該元件。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-114">You also need to add the component to the Visual Studio Toolbox in order to use it in the Pipeline Designer.</span></span>  
  
 <span data-ttu-id="dc5d8-115">元件的安裝位置的相關資訊，請參閱[部署管線元件](../core/deploying-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-115">For information about where to install the component, see [Deploying Pipeline Components](../core/deploying-pipeline-components.md).</span></span>  
  
 <span data-ttu-id="dc5d8-116">如需將元件加入至 Visual Studio 工具箱，請參閱[如何使用 [工具箱]](../core/how-to-use-the-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-116">For information about adding the component to the Visual Studio Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).</span></span>  
  
## <a name="configure-the-set-namespace-pipeline-component"></a><span data-ttu-id="dc5d8-117">設定設定命名空間管線元件</span><span class="sxs-lookup"><span data-stu-id="dc5d8-117">Configure the Set Namespace Pipeline Component</span></span>  
 <span data-ttu-id="dc5d8-118">「設定命名空間」管線元件有兩個屬性可讓您設定：</span><span class="sxs-lookup"><span data-stu-id="dc5d8-118">The Set Namespace pipeline component has two properties you can set:</span></span>  
  
|<span data-ttu-id="dc5d8-119">使用</span><span class="sxs-lookup"><span data-stu-id="dc5d8-119">Use this</span></span>|<span data-ttu-id="dc5d8-120">動作</span><span class="sxs-lookup"><span data-stu-id="dc5d8-120">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="dc5d8-121">**預設目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="dc5d8-121">**Default Target Namespace**</span></span>|<span data-ttu-id="dc5d8-122">將固定的命名空間放在內送訊息中。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-122">Put a fixed namespace in the incoming message.</span></span>|  
|<span data-ttu-id="dc5d8-123">**目標命名空間的 XPath**</span><span class="sxs-lookup"><span data-stu-id="dc5d8-123">**Target Namespace XPath**</span></span>|<span data-ttu-id="dc5d8-124">根據 XPath 指定的位置，從內送訊息中擷取命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-124">Extract the namespace from the incoming message taking it from the location specified by the XPath.</span></span> <span data-ttu-id="dc5d8-125">元件若是找不到有效的命名空間，就會在應用程式事件日誌中記錄警告，並使用預設目標命名空間 (若已指定)。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-125">If the component does not find a valid namespace, it logs a warning in the Application Event Log and, if it is specified, uses the Default Target Namespace.</span></span>|  
  
 <span data-ttu-id="dc5d8-126">如果您將這兩個屬性保留空白，則元件不會指派命名空間給內送訊息，但是會將警告寫入至應用程式事件日誌。</span><span class="sxs-lookup"><span data-stu-id="dc5d8-126">If you leave both properties blank, the component does not assign namespaces to incoming messages but does write warnings to the Application Event Log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5d8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc5d8-127">See Also</span></span>  
 [<span data-ttu-id="dc5d8-128">開發應用程式</span><span class="sxs-lookup"><span data-stu-id="dc5d8-128">Developing Applications</span></span>](../core/developing-applications4.md)