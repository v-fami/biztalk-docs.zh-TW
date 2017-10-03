---
title: "如何將協調流程對應至 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, Web services
- BizTalk Web Services Publishing Wizard, naming conventions
- Web services, orchestrations
- orchestrations, naming conventions
- Web services, naming conventions
ms.assetid: e6a58978-c81c-49f3-9428-9bff60f1ded7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f101a9a9ab6c0d99e9895433401de08b1380d1e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-orchestrations-to-web-services"></a><span data-ttu-id="84ddc-102">如何將協調流程對應至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="84ddc-102">How to Map Orchestrations to Web Services</span></span>
<span data-ttu-id="84ddc-103">一個協調流程可以具有多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="84ddc-103">An orchestration can have multiple receive ports.</span></span> <span data-ttu-id="84ddc-104">使用 [BizTalk Web 服務發佈精靈]，即可選取要發佈為 Web 服務的接收埠。</span><span class="sxs-lookup"><span data-stu-id="84ddc-104">Using the BizTalk Web Services Publishing Wizard, you select receive ports to publish as Web services.</span></span> <span data-ttu-id="84ddc-105">此精靈可為每個接收埠建立一個 Web 服務 (.asmx 檔案)。</span><span class="sxs-lookup"><span data-stu-id="84ddc-105">The wizard creates one Web service (.asmx file) for each receive port.</span></span> <span data-ttu-id="84ddc-106">如果所有的接收埠都屬於相同的接收埠類型 (「單向」或「要求/回應」)，此精靈也可為所有的接收埠建立單一的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="84ddc-106">The wizard can also create one Web service for all of the receive ports if they are the same receive port type (one-way or request/response).</span></span> <span data-ttu-id="84ddc-107">作業變成函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="84ddc-107">Operations become function calls.</span></span> <span data-ttu-id="84ddc-108">接收埠中的每個作業都會變成 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="84ddc-108">Each operation in the receive port becomes a Web method.</span></span> <span data-ttu-id="84ddc-109">要求作業變成輸入參數。</span><span class="sxs-lookup"><span data-stu-id="84ddc-109">Request operations become input parameters.</span></span> <span data-ttu-id="84ddc-110">回應作業變成傳回型別。</span><span class="sxs-lookup"><span data-stu-id="84ddc-110">Response operations become return types.</span></span>  
  
 <span data-ttu-id="84ddc-111">如果要求和回應的作業相同的 Web 訊息類型，輸入的參數就會變成**ref**和傳回型別是**void**。</span><span class="sxs-lookup"><span data-stu-id="84ddc-111">If the request and response operations are the same Web message type, the input parameter becomes a **ref** and the return type is **void**.</span></span> <span data-ttu-id="84ddc-112">ASP.NET Web 用戶端可能會合併相同型別的 in 和 out 參數，以變更 Web 方法簽章。</span><span class="sxs-lookup"><span data-stu-id="84ddc-112">ASP.NET Web clients may change the Web method signature by combining the in and out parameters of the same type.</span></span> <span data-ttu-id="84ddc-113">例如，ASP.NET Web 用戶端可能會變更 BizTalk Web 方法，從**string myService （字串一部分）**至**void myService （ref 字串的一部分）**。</span><span class="sxs-lookup"><span data-stu-id="84ddc-113">For example, an ASP.NET Web client may change a BizTalk Web method from **string myService(string part)** to **void myService(ref string part)**.</span></span>  
  
 <span data-ttu-id="84ddc-114">作業訊息類型可定義 Web 方法簽章。</span><span class="sxs-lookup"><span data-stu-id="84ddc-114">The operation message types define the Web method signatures.</span></span> <span data-ttu-id="84ddc-115">每個訊息類型部分都是 Web 方法中的參數。</span><span class="sxs-lookup"><span data-stu-id="84ddc-115">Each message type part is a parameter in the Web method.</span></span>  
  
## <a name="message-type-part-names-and-target-namespaces"></a><span data-ttu-id="84ddc-116">訊息類型部分名稱和目標命名空間</span><span class="sxs-lookup"><span data-stu-id="84ddc-116">Message type part names and target namespaces</span></span>  
 <span data-ttu-id="84ddc-117">文件結構描述和使用者定義類別**XmlRootAttribute**指定是訊息類型部分定義目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="84ddc-117">Document schemas and user defined classes with **XmlRootAttribute** specified are message type parts that have defined target namespaces.</span></span> <span data-ttu-id="84ddc-118">EDI 結構描述、 使用者定義的類別，而不**XmlRootAttribute**指定和內建類型，例如**System.String**是未定義的目標命名空間的訊息類型部分。</span><span class="sxs-lookup"><span data-stu-id="84ddc-118">EDI schemas, user-defined classes without **XmlRootAttribute** specified, and built-in types, such as **System.String** are message type parts without defined target namespaces.</span></span>  
  
|<span data-ttu-id="84ddc-119">如果訊息類型部分名稱有</span><span class="sxs-lookup"><span data-stu-id="84ddc-119">If the message type part name has a</span></span>|<span data-ttu-id="84ddc-120">使用的參數名稱</span><span class="sxs-lookup"><span data-stu-id="84ddc-120">Parameter Name Used</span></span>|  
|-----------------------------------------|-------------------------|  
|<span data-ttu-id="84ddc-121">定義的目標命名空間</span><span class="sxs-lookup"><span data-stu-id="84ddc-121">Defined target namespace</span></span>|<span data-ttu-id="84ddc-122">根項目名稱</span><span class="sxs-lookup"><span data-stu-id="84ddc-122">Root element name</span></span>|  
|<span data-ttu-id="84ddc-123">沒有定義的目標命名空間</span><span class="sxs-lookup"><span data-stu-id="84ddc-123">No defined target namespace</span></span>|<span data-ttu-id="84ddc-124">訊息類型部分名稱</span><span class="sxs-lookup"><span data-stu-id="84ddc-124">Message type part name</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="84ddc-125">在回應訊息使用 multipart 訊息類型時，[BizTalk Web 服務發佈精靈] 會使用第一個訊息部分做為傳回值，並會使用其餘的訊息部分做為 out 參數。</span><span class="sxs-lookup"><span data-stu-id="84ddc-125">When a multipart message type is used for the response message, the BizTalk Web Services Publishing Wizard uses the first message part for the return value and the remaining message parts are used as out parameters.</span></span>  
  
## <a name="orchestrations-with-multiple-operations"></a><span data-ttu-id="84ddc-126">具有多重作業的協調流程</span><span class="sxs-lookup"><span data-stu-id="84ddc-126">Orchestrations with multiple operations</span></span>  
 <span data-ttu-id="84ddc-127">如果您的協調流程具有多重作業，此協調流程應該設計為使用一個接收埠，而非多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="84ddc-127">If your orchestration has multiple operations, you should design your orchestrations to have one receive port instead of several receive ports.</span></span> <span data-ttu-id="84ddc-128">這種設計可防止「BizTalk Web 服務發佈精靈」建立多個 Web 服務 (.asmx) 檔案，而只在所有的作業都具有相同的呼叫模式 (全都是單向作業，或者全都是要求-回應作業) 情況下運作。</span><span class="sxs-lookup"><span data-stu-id="84ddc-128">This design prevents the BizTalk Web Services Publishing Wizard from creating multiple Web service (.asmx) files and only works when all the operations have the same calling pattern—all one-way operations or all request-response operations.</span></span> <span data-ttu-id="84ddc-129">單一的接收埠不能同時包含單向和要求/回應作業。</span><span class="sxs-lookup"><span data-stu-id="84ddc-129">A single receive port cannot contain both one-way and request/response operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84ddc-130">[BizTalk Web 服務發佈精靈] 會顯示公用的接收埠。</span><span class="sxs-lookup"><span data-stu-id="84ddc-130">The BizTalk Web Services Publishing Wizard displays public receive ports.</span></span> <span data-ttu-id="84ddc-131">公用的接收埠屬於具有公用型別修飾詞的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="84ddc-131">Public receive ports are port types with a public type modifier.</span></span> <span data-ttu-id="84ddc-132">您只能將公用連接埠發佈為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="84ddc-132">You can publish only public ports as a Web service.</span></span> <span data-ttu-id="84ddc-133">預設的連接埠類型為「內部」。</span><span class="sxs-lookup"><span data-stu-id="84ddc-133">The default port type is internal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84ddc-134">如果您收到定義為單向連接埠、 Web 方法回應型別是**void**和 Web 用戶端傳回任何資訊。</span><span class="sxs-lookup"><span data-stu-id="84ddc-134">If your receive port is defined as one-way, the Web method response type is **void** and no information is returned to the Web client.</span></span> <span data-ttu-id="84ddc-135">SOAP 配接器或協調流程所擲回的例外狀況，都不會傳回到 Web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="84ddc-135">Exceptions thrown by the SOAP adapter or an orchestration are not returned to the Web client.</span></span>  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a><span data-ttu-id="84ddc-136">已發佈協調流程的 Web 服務命名慣例</span><span class="sxs-lookup"><span data-stu-id="84ddc-136">Web services naming conventions for published orchestrations</span></span>  
 <span data-ttu-id="84ddc-137">BizTalk Web 服務發佈精靈產生 Web 服務 (.asmx) 檔案名稱，而根據協調流程命名空間，後面接著底線 (_)，後面接著類型名稱，後面接著底線 (\_)，後面接著接收名稱和連接埠。</span><span class="sxs-lookup"><span data-stu-id="84ddc-137">The BizTalk Web Services Publishing Wizard generates Web service (.asmx) file names based on the orchestrations namespace, followed by an underscore (_), followed by the type name, followed by an underscore (\_), and followed by the name of the receive port.</span></span> <span data-ttu-id="84ddc-138">底線 (\_) 會取代任何包含句號的組件。</span><span class="sxs-lookup"><span data-stu-id="84ddc-138">An underscore (\_) replaces any of the parts that contain periods.</span></span> <span data-ttu-id="84ddc-139">Web 服務的名稱永遠都會加上該連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="84ddc-139">The name of the Web service always has the port name appended.</span></span>  
  
 <span data-ttu-id="84ddc-140">下表顯示「BizTalk Web 服務發佈精靈」如何產生 Web 服務名稱。</span><span class="sxs-lookup"><span data-stu-id="84ddc-140">The following table shows how the BizTalk Web Services Publishing Wizard generates Web service names.</span></span>  
  
|<span data-ttu-id="84ddc-141">協調流程與 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="84ddc-141">Orchestration(s) with Web port(s)</span></span>|<span data-ttu-id="84ddc-142">產生的 Web 服務名稱</span><span class="sxs-lookup"><span data-stu-id="84ddc-142">Generated Web service name</span></span>|  
|-------------------------------------------|--------------------------------|  
|<span data-ttu-id="84ddc-143">具有一個 Web 連接埠的一個協調流程</span><span class="sxs-lookup"><span data-stu-id="84ddc-143">One orchestration with one Web port</span></span>|<span data-ttu-id="84ddc-144">orchestration1_port1.asmx</span><span class="sxs-lookup"><span data-stu-id="84ddc-144">orchestration1_port1.asmx</span></span>|  
|<span data-ttu-id="84ddc-145">具有兩個 Web 連接埠的一個協調流程</span><span class="sxs-lookup"><span data-stu-id="84ddc-145">One orchestration with two Web ports</span></span>|<span data-ttu-id="84ddc-146">orchestration1_port1.asmx 和 orchestration1_port2.asmx</span><span class="sxs-lookup"><span data-stu-id="84ddc-146">orchestration1_port1.asmx and orchestration1_port2.asmx</span></span>|  
|<span data-ttu-id="84ddc-147">各有一個 Web 連接埠的兩個協調流程</span><span class="sxs-lookup"><span data-stu-id="84ddc-147">Two orchestrations with one Web port each</span></span>|<span data-ttu-id="84ddc-148">orchestration1_port1.asmx 和 orchestration2_port2.asmx</span><span class="sxs-lookup"><span data-stu-id="84ddc-148">orchestration1_port1.asmx and orchestration2_port2.asmx</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84ddc-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84ddc-149">See Also</span></span>  
 <span data-ttu-id="84ddc-150">[協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="84ddc-150">[Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md) </span></span>  
 [<span data-ttu-id="84ddc-151">如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="84ddc-151">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)