---
title: SAP 配接器中設定動態連接埠 |Microsoft Docs
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
ms.assetid: 4d6569f9-e513-47f3-b2c1-4c21bafb2bf2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de45553cfad2db19cfe16bbcd55420019b4971e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971503"
---
# <a name="configure-dynamic-ports-in-the-sap-adapter"></a><span data-ttu-id="70ba7-102">SAP 配接器中設定動態連接埠</span><span class="sxs-lookup"><span data-stu-id="70ba7-102">Configure dynamic ports in the SAP adapter</span></span>
## <a name="use-message-context-properties"></a><span data-ttu-id="70ba7-103">使用訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="70ba7-103">Use message context properties</span></span>
<span data-ttu-id="70ba7-104">在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ba7-104">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="70ba7-105">因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 架構配接器時，您可以動態設定的連接埠[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="70ba7-105">Because [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="70ba7-106">針對[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，URI、 動作和繫結可能會決定從傳入訊息上的屬性，則指定在運算式圖形中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="70ba7-106">For the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the URI, action, and binding might be determined from a property on an incoming message, and then specified in the Expression shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET";  
Request2(WCF.BindingType)="sapBinding";  
Request2(WCF.UserName)="YourUserName";  
Request2(WCF.Password)="YourPassword";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="sap://CLIENT=800;LANG=EN;@A/YourSAPHost/00";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="70ba7-107">如果您使用中的 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SAPAdapter"`，其中**SAPAdapter**是您加入中的 WCF SAP 配接器名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="70ba7-107">If you are using a WCF-SAP adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SAPAdapter"`, where **SAPAdapter** is the name with which you added the WCF-SAP adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="70ba7-108">在上述範例中：</span><span class="sxs-lookup"><span data-stu-id="70ba7-108">In the preceding example:</span></span>  
  
- <span data-ttu-id="70ba7-109">正在從 Request1 訊息建立要求 2 訊息。</span><span class="sxs-lookup"><span data-stu-id="70ba7-109">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="70ba7-110">兩個訊息對應至作業的結構描述，產生使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ba7-110">Both the messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
- <span data-ttu-id="70ba7-111">傳送埠是在 BizTalk 協調流程中的邏輯傳送連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="70ba7-111">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
  <span data-ttu-id="70ba7-112">「 運算式 」 圖形是 BizTalk 協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="70ba7-112">The Expression shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="70ba7-113">當您部署協調流程時，也會建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="70ba7-113">When you deploy the orchestration, the WCF-Custom send port is also created.</span></span>  
  
  <span data-ttu-id="70ba7-114">如需有關如何設定動態連接埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="70ba7-114">For more information on configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70ba7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ba7-115">See Also</span></span>  
[<span data-ttu-id="70ba7-116">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="70ba7-116">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)