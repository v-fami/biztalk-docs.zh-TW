---
title: "連接埠繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, warnings
- ports, bindings
- bindings, Web ports
- bindings, design time
- Web ports, port bindings
- bindings, ports
- bindings, direct
- bindings, warnings
- bindings, deployment
- bindings, dynamic
ms.assetid: b61c725a-0082-42d3-b88a-533583161734
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943cbbaa6db9413ffad15bfcf3302d2216e3ab17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="port-bindings"></a><span data-ttu-id="ea16a-102">連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="ea16a-102">Port Bindings</span></span>
<span data-ttu-id="ea16a-103">連接埠繫結是組態資訊，用來決定傳送或接收訊息的位置與方式。</span><span class="sxs-lookup"><span data-stu-id="ea16a-103">A port binding is the configuration information that determines where and how a message will be sent or received.</span></span> <span data-ttu-id="ea16a-104">根據其類型，連接埠繫結可以指實體位置、管線或其他協調流程。</span><span class="sxs-lookup"><span data-stu-id="ea16a-104">Depending on its type, a port binding might refer to physical locations, pipelines, or other orchestrations.</span></span>  
  
 <span data-ttu-id="ea16a-105">接收訊息之連接埠的連接埠繫結有三種類型：</span><span class="sxs-lookup"><span data-stu-id="ea16a-105">There are three types of port binding for ports that receive messages:</span></span>  
  
-   <span data-ttu-id="ea16a-106">立即指定</span><span class="sxs-lookup"><span data-stu-id="ea16a-106">Specify now</span></span>  
  
-   <span data-ttu-id="ea16a-107">稍後指定</span><span class="sxs-lookup"><span data-stu-id="ea16a-107">Specify later</span></span>  
  
-   <span data-ttu-id="ea16a-108">直接</span><span class="sxs-lookup"><span data-stu-id="ea16a-108">Direct</span></span>  
  
 <span data-ttu-id="ea16a-109">傳送訊息之連接埠的連接埠繫結有四種類型：</span><span class="sxs-lookup"><span data-stu-id="ea16a-109">There are four types of port binding for ports that send messages:</span></span>  
  
-   <span data-ttu-id="ea16a-110">立即指定</span><span class="sxs-lookup"><span data-stu-id="ea16a-110">Specify now</span></span>  
  
-   <span data-ttu-id="ea16a-111">稍後指定</span><span class="sxs-lookup"><span data-stu-id="ea16a-111">Specify later</span></span>  
  
-   <span data-ttu-id="ea16a-112">直接</span><span class="sxs-lookup"><span data-stu-id="ea16a-112">Direct</span></span>  
  
-   <span data-ttu-id="ea16a-113">動態</span><span class="sxs-lookup"><span data-stu-id="ea16a-113">Dynamic</span></span>  
  
## <a name="binding-at-deployment-time"></a><span data-ttu-id="ea16a-114">部署階段的繫結</span><span class="sxs-lookup"><span data-stu-id="ea16a-114">Binding at Deployment Time</span></span>  
 <span data-ttu-id="ea16a-115">您可以將您的連接埠繫結至接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ea16a-115">You can bind your port to a receive location or to a send port.</span></span> <span data-ttu-id="ea16a-116">如果您沒有所有您需要指定實體位置的資訊，您可以選取**稍後指定**連接埠繫結選項，在協調流程設計師 」，而且您只需要指定描述該連接埠的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="ea16a-116">If you do not have all of the information you need to specify a physical location, you can select the **Specify later** port binding option in Orchestration Designer, and you only need to specify the port type that describes the port.</span></span> <span data-ttu-id="ea16a-117">當部署應用程式之後，您可以使用 BizTalk Server 管理主控台來指定此位置的相關資訊，或是可以透過程式設計方式來設定位置資訊。</span><span class="sxs-lookup"><span data-stu-id="ea16a-117">After the application has been deployed, you can specify information about the location by using the BizTalk Server Administration console, or you can configure the location information programmatically.</span></span>  
  
## <a name="binding-at-design-time"></a><span data-ttu-id="ea16a-118">設計階段的繫結</span><span class="sxs-lookup"><span data-stu-id="ea16a-118">Binding at Design Time</span></span>  
 <span data-ttu-id="ea16a-119">您可以選取**現在指定**連接埠在協調流程設計師 」 中的繫結選項，在設計階段指定的傳輸和管線。</span><span class="sxs-lookup"><span data-stu-id="ea16a-119">You can select the **Specify now** port binding option in Orchestration Designer to specify the transport and pipeline at design time.</span></span> <span data-ttu-id="ea16a-120">當您指定要用於接收訊息的連接埠時，下拉式清單中只會提供 HTTP、SOAP 和 FILE 傳輸。</span><span class="sxs-lookup"><span data-stu-id="ea16a-120">When specifying the port for receiving messages, only HTTP, SOAP, and FILE transports are available from the drop-down list.</span></span> <span data-ttu-id="ea16a-121">當您指定要用於傳送訊息的連接埠時，下拉式清單中只會提供 HTTP、FILE 和 SMTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="ea16a-121">When specifying the port for sending messages, only HTTP, FILE, and SMTP transports are available from the drop-down list.</span></span> <span data-ttu-id="ea16a-122">若您事先知道傳輸訊息的來源或目的地，這個選項會很有用。</span><span class="sxs-lookup"><span data-stu-id="ea16a-122">This option is useful if you know in advance the source or destination of transmitted messages.</span></span>  
  
## <a name="direct-binding"></a><span data-ttu-id="ea16a-123">直接繫結</span><span class="sxs-lookup"><span data-stu-id="ea16a-123">Direct Binding</span></span>  
 <span data-ttu-id="ea16a-124">直接繫結連接埠是協調流程中未明確繫結至任何實體連接埠的邏輯單向或雙向連接埠。</span><span class="sxs-lookup"><span data-stu-id="ea16a-124">Direct bound ports are logical one-way or two-way ports in your orchestrations that are not explicitly bound to any physical ports.</span></span> <span data-ttu-id="ea16a-125">直接繫結連接埠可讓您在服務中有不同的通訊模式。</span><span class="sxs-lookup"><span data-stu-id="ea16a-125">Direct bound ports allow you to have different communication patterns among your services.</span></span> <span data-ttu-id="ea16a-126">若要實作直接繫結，請選取**直接**連接埠在協調流程設計師在設計階段的繫結選項。</span><span class="sxs-lookup"><span data-stu-id="ea16a-126">To implement direct binding, select the **Direct** port binding option in Orchestration Designer at design time.</span></span>  
  
 <span data-ttu-id="ea16a-127">有三種類型的直接繫結連接埠：</span><span class="sxs-lookup"><span data-stu-id="ea16a-127">There are three types of direct bound ports:</span></span>  
  
-   <span data-ttu-id="ea16a-128">MessageBox 直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="ea16a-128">MessageBox direct bound port</span></span>  
  
-   <span data-ttu-id="ea16a-129">自我相互關聯的直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="ea16a-129">Self-correlating direct bound port</span></span>  
  
-   <span data-ttu-id="ea16a-130">夥伴協調流程直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="ea16a-130">Partner orchestration direct bound port</span></span>  
  
 <span data-ttu-id="ea16a-131">如需如何使用直接繫結連接埠的詳細資訊，請參閱[直接繫結連接埠在協調流程中使用](../core/working-with-direct-bound-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="ea16a-131">For more information about how to work with direct bound ports, see [Working with Direct Bound Ports in Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea16a-132">使用直接繫結時，您無法在一個要求-回應連接埠和兩個單向連接埠間交換訊息。</span><span class="sxs-lookup"><span data-stu-id="ea16a-132">When you use direct binding, you cannot exchange messages between one request-response port and two one-way ports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea16a-133">直接繫結和「Web 服務商務程序工程語言」(BPEL4WS) 的標準不相容。</span><span class="sxs-lookup"><span data-stu-id="ea16a-133">Direct binding is not compliant with the standards of the Business Process Engineering Language for Web Services (BPEL4WS).</span></span> <span data-ttu-id="ea16a-134">若您需要 BPEL4WS 相容規範，請使用另一種繫結。</span><span class="sxs-lookup"><span data-stu-id="ea16a-134">If you require BPEL4WS compliance, use another kind of binding.</span></span>  
  
## <a name="dynamic-binding"></a><span data-ttu-id="ea16a-135">動態繫結</span><span class="sxs-lookup"><span data-stu-id="ea16a-135">Dynamic Binding</span></span>  
 <span data-ttu-id="ea16a-136">若您要到執行階段才會知道通訊的目的地，您可以針對傳送埠使用動態繫結。</span><span class="sxs-lookup"><span data-stu-id="ea16a-136">If you will not know the destination of a communication until run time, you can use dynamic binding for a send port.</span></span> <span data-ttu-id="ea16a-137">位置可能、 比方說，是由傳入訊息上的屬性，並指定在**運算式**圖形，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ea16a-137">The location might, for example, be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following code:</span></span>  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
```  
  
 <span data-ttu-id="ea16a-138">如需如何以動態方式將值指派給連接埠資訊，請參閱[如何指派值給動態連接埠](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="ea16a-138">For information about how to dynamically assign values to ports, see [How to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md).</span></span>  
  
## <a name="web-ports"></a><span data-ttu-id="ea16a-139">Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="ea16a-139">Web Ports</span></span>  
 <span data-ttu-id="ea16a-140">若您的專案包含 Web 服務的參考，「協調流程設計師」會偵測它，並提供可用的對應 Web 連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="ea16a-140">If your project contains a reference to a Web service, Orchestration Designer will detect it and will make available a corresponding Web port type.</span></span> <span data-ttu-id="ea16a-141">若要建立 Web 連接埠，您只要新增連接埠到您的協調流程，並為它指派現有的 Web 連接埠類型即可。</span><span class="sxs-lookup"><span data-stu-id="ea16a-141">To create a Web port, you simply add a port to your orchestration and assign it an existing Web port type.</span></span> <span data-ttu-id="ea16a-142">如需詳細資訊，請參閱[建立 Web 連接埠](../core/creating-web-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="ea16a-142">For more information, see [Creating Web Ports](../core/creating-web-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea16a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea16a-143">See Also</span></span>  
 <span data-ttu-id="ea16a-144">[如何使用連接埠類型](../core/how-to-work-with-port-types.md) </span><span class="sxs-lookup"><span data-stu-id="ea16a-144">[How to Work with Port Types](../core/how-to-work-with-port-types.md) </span></span>  
 <span data-ttu-id="ea16a-145">[通訊模式](../core/communication-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="ea16a-145">[Communication Pattern](../core/communication-pattern.md) </span></span>  
 <span data-ttu-id="ea16a-146">[通訊方向](../core/communication-direction.md) </span><span class="sxs-lookup"><span data-stu-id="ea16a-146">[Communication Direction](../core/communication-direction.md) </span></span>  
 <span data-ttu-id="ea16a-147">[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="ea16a-147">[Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md) </span></span>  
 <span data-ttu-id="ea16a-148">[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="ea16a-148">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="ea16a-149">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="ea16a-149">Consuming Web Services</span></span>](../core/consuming-web-services.md)