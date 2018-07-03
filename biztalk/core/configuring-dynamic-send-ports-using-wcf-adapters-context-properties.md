---
title: 設定動態傳送埠使用 WCF 配接器內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services, send ports
- send ports, WCF services
- dynamic send ports, WCF services
- send ports, dynamic
ms.assetid: 2a7e2cd2-fa2d-45da-bb8e-eb8bab21bfa3
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca781dc1d101e3eef0976229b3d1b986c2f4498d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995271"
---
# <a name="configuring-dynamic-send-ports-using-wcf-adapters-context-properties"></a><span data-ttu-id="a0b63-102">使用 WCF 配接器內容屬性設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="a0b63-102">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>
<span data-ttu-id="a0b63-103">您可以為 WCF 配接器設定動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0b63-103">You can configure dynamic send ports for WCF adapters.</span></span> <span data-ttu-id="a0b63-104">URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定 在**運算式**圖形，如下列 Wcf-nettcp 配接器中所示：</span><span class="sxs-lookup"><span data-stu-id="a0b63-104">The URI, action, and binding might be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following WCF-NetTcp adapter:</span></span>  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.SecurityMode)="Transport";  
MessageOut(WCF.TransportClientCredentialType)="Windows";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/netTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-NetTcp";  
```  
  
 <span data-ttu-id="a0b63-105">下列程式碼顯示如何指定 WCF 內容屬性中的範例**運算式**Wcf-custom 配接器的圖形：</span><span class="sxs-lookup"><span data-stu-id="a0b63-105">The following code shows an example of how to specify the WCF context properties in the **Expression** shape for a WCF-Custom adapter:</span></span>  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.BindingType)="customBinding";  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.BindingConfiguration)=@"<binding name=""customBinding""><binaryMessageEncoding /><tcpTransport /></binding>";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/customNetTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
 <span data-ttu-id="a0b63-106">指定 WCF 內容屬性時的考量如下：</span><span class="sxs-lookup"><span data-stu-id="a0b63-106">Considerations when specifying WCF context properties are as follows:</span></span>  
  
- <span data-ttu-id="a0b63-107">有些位址可對應至多個配接器。</span><span class="sxs-lookup"><span data-stu-id="a0b63-107">There are addresses that can be mapped to multiple adapters.</span></span> <span data-ttu-id="a0b63-108">例如，http:// 或 https:// 開頭的位址可以由 HTTP 配接器和 WCF-BasicHttp、WCF-WsHttp 或 WCF-Custom 配接器處理。</span><span class="sxs-lookup"><span data-stu-id="a0b63-108">For example, an address that starts with http:// or https:// can be handled by the HTTP adapter as well as by the WCF-BasicHttp, WCF-WsHttp, or WCF-Custom adapters.</span></span> <span data-ttu-id="a0b63-109">上方範例程式碼的另一個範例為：這兩種配接器都使用開頭為 net.tcp:// 的位址，不過因為第二個範例程式碼使用自訂繫結，所以應該使用 WCF-Custom 處理位址。</span><span class="sxs-lookup"><span data-stu-id="a0b63-109">For another example, in the above sample code, both of them are using the address starts with net.tcp://, yet because the second sample code uses custom binding, WCF-Custom adapter should be used to handle the address.</span></span> <span data-ttu-id="a0b63-110">因此，若要識別正確的配接器，您必須設定選擇性**Microsoft.XLANGs.BaseTypes.TransportType**欄位中**運算式**您想要使用的配接器的圖形。</span><span class="sxs-lookup"><span data-stu-id="a0b63-110">Therefore, to identify the correct adapter, you must configure the optional **Microsoft.XLANGs.BaseTypes.TransportType** field in an **Expression** shape with the adapter that you want to use.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="a0b63-111">如果位址開頭為 http:// 或 https://，而且如果您未指定**Microsoft.XLANGs.BaseTypes.TransportType**  欄位中，根據預設，BizTalk 引擎會使用 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="a0b63-111">If the address starts with http:// or https://, and if you do not specify the **Microsoft.XLANGs.BaseTypes.TransportType** field, by default, the BizTalk engine will use the HTTP adapter.</span></span>  
  
- <span data-ttu-id="a0b63-112">**WCF。BindingType**依名稱識別繫結。</span><span class="sxs-lookup"><span data-stu-id="a0b63-112">The **WCF.BindingType** identifies the binding by name.</span></span> <span data-ttu-id="a0b63-113">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a0b63-113">It can be one of the following:</span></span>  
  
  - <span data-ttu-id="a0b63-114">basicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-114">basicHttpBinding</span></span>  
  
  - <span data-ttu-id="a0b63-115">customBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-115">customBinding</span></span>  
  
  - <span data-ttu-id="a0b63-116">netMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-116">netMsmqBinding</span></span>  
  
  - <span data-ttu-id="a0b63-117">netNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-117">netNamedPipeBinding</span></span>  
  
  - <span data-ttu-id="a0b63-118">netTcpBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-118">netTcpBinding</span></span>  
  
  - <span data-ttu-id="a0b63-119">wsFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-119">wsFederationHttpBinding</span></span>  
  
  - <span data-ttu-id="a0b63-120">wsHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a0b63-120">wsHttpBinding</span></span>  
  
    <span data-ttu-id="a0b63-121">上方的清單可以擴充。</span><span class="sxs-lookup"><span data-stu-id="a0b63-121">The above list can be extended.</span></span> <span data-ttu-id="a0b63-122">例如，您可以將自己的繫結新增至清單中，例如 FtpBinding。</span><span class="sxs-lookup"><span data-stu-id="a0b63-122">For example, you can add your own binding to it such as FtpBinding.</span></span>  
  
- <span data-ttu-id="a0b63-123">**WCF。BindingConfiguration**指定繫結類型的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="a0b63-123">The **WCF.BindingConfiguration** specifies the binding configuration for the binding type.</span></span> <span data-ttu-id="a0b63-124">它會採用在電腦組態檔中註冊的任何繫結。</span><span class="sxs-lookup"><span data-stu-id="a0b63-124">It takes any binding that are registered in the machine configuration file.</span></span> <span data-ttu-id="a0b63-125">此外還會以與 WCF 組態檔的繫結組態中使用的相同格式採用 XML 組態。</span><span class="sxs-lookup"><span data-stu-id="a0b63-125">It also takes the XML configuration in the same format as used in the binding configuration in the WCF configuration file.</span></span>  
  
- <span data-ttu-id="a0b63-126">您可能需要指定額外的 WCF 屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b63-126">You may need to specify additional WCF properties.</span></span> <span data-ttu-id="a0b63-127">您可以輸入**WCF**中運算式編輯器中和 IntelliSense 功能應該會列出所有可用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b63-127">You can type **WCF** in the Expression Editor, and the IntelliSense feature should list all the available context properties.</span></span> <span data-ttu-id="a0b63-128">如需有關 WCF 內容屬性的詳細資訊，請參閱 < [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b63-128">For more information about WCF context properties, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).</span></span>  
  
  <span data-ttu-id="a0b63-129">上述範例示範如何設定**WCF。動作**以單一動作。</span><span class="sxs-lookup"><span data-stu-id="a0b63-129">The preceding examples show how to configure **WCF.Action** with a single action.</span></span> <span data-ttu-id="a0b63-130">在多個動作對應實例中，WCF 配接器不支援使用多個動作對應搭配動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0b63-130">For multiple actions mapping scenarios, WCF adapter do not support using multiple actions mapping with dynamic send ports.</span></span> <span data-ttu-id="a0b63-131">您只可以在設定的實際動作**WCF。動作**與上述中顯示的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b63-131">You can just set the actual action in the **WCF.Action** context property as showing in above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b63-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b63-132">See Also</span></span>  
 <span data-ttu-id="a0b63-133">[指定的 SOAP 動作，wcf 傳送配接器](../core/specifying-soap-actions-for-wcf-send-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="a0b63-133">[Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md) </span></span>  
 <span data-ttu-id="a0b63-134">[如何使用運算式來將值指派給動態連接埠](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md) </span><span class="sxs-lookup"><span data-stu-id="a0b63-134">[How to Use Expressions to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md) </span></span>  
 [<span data-ttu-id="a0b63-135">連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="a0b63-135">Port Bindings</span></span>](../core/port-bindings.md)