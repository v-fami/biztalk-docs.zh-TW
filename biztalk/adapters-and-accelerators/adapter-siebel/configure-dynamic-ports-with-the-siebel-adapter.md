---
title: 使用 Siebel 配接器設定動態連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
- configuring, dynamic ports
ms.assetid: a3516c2c-d40e-426b-bf3f-f9dc3de105ef
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80a568880aaf8b11cc79e04c7eaee5a5c9e512a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000849"
---
# <a name="configure-dynamic-ports-with-the-siebel-adapter"></a><span data-ttu-id="b0019-102">使用 Siebel 配接器設定動態連接埠</span><span class="sxs-lookup"><span data-stu-id="b0019-102">Configure dynamic ports with the Siebel adapter</span></span>
<span data-ttu-id="b0019-103">在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0019-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="b0019-104">因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 架構配接器時，您可以動態設定的連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b0019-104">Because [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="b0019-105">針對[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]、 URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定中**運算式**圖形，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b0019-105">For the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the URI, action, and binding might be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert";  
Request2(WCF.BindingType)="siebelBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="siebel://mySiebelServer:1234?SiebelObjectManager=SSEObjMgr&SiebelEnterpriseServer=myEnterpriseServer&Language=enu";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="b0019-106">如果您使用 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SiebelAdapter"`，其中**SiebelAdapter**是的名稱與您新增 Wcf-siebel 配接器，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b0019-106">If you are using a WCF-Siebel adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SiebelAdapter"`, where **SiebelAdapter** is the name with which you added the WCF-Siebel adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="b0019-107">在上述範例中：</span><span class="sxs-lookup"><span data-stu-id="b0019-107">In the preceding example:</span></span>  
  
- <span data-ttu-id="b0019-108">正在從 Request1 訊息建立要求 2 訊息。</span><span class="sxs-lookup"><span data-stu-id="b0019-108">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="b0019-109">兩個訊息對應至作業的結構描述，產生使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0019-109">Both the messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
- <span data-ttu-id="b0019-110">傳送埠是在 BizTalk 協調流程中的邏輯傳送連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0019-110">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
  <span data-ttu-id="b0019-111">「 運算式 」 圖形是 BizTalk 協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="b0019-111">The Expression shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="b0019-112">當您部署協調流程時，也會建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b0019-112">When you deploy the orchestration, the WCF-Custom send port is also created.</span></span>  
  
  <span data-ttu-id="b0019-113">如需有關如何設定動態連接埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b0019-113">For more information on configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b0019-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0019-114">See Also</span></span>  
[<span data-ttu-id="b0019-115">若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="b0019-115">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)