---
title: 使用 Oracle E-business Suite 中設定動態連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75a150ea-d957-4a37-81cf-c043a0a7d5cb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2f960560a631dd2eaf36f43522513242c240e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981911"
---
# <a name="configure-dynamic-ports-with-oracle-e-business-suite"></a><span data-ttu-id="31ed2-102">使用 Oracle E-business Suite 中設定動態連接埠</span><span class="sxs-lookup"><span data-stu-id="31ed2-102">Configure dynamic ports with Oracle E-Business Suite</span></span>
<span data-ttu-id="31ed2-103">在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31ed2-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="31ed2-104">因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 架構配接器時，您可以動態設定的連接埠[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="31ed2-104">Because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by using message context properties.</span></span>  
  
 <span data-ttu-id="31ed2-105">針對[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]、 URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定中**運算式**圖形，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31ed2-105">For the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], the URI, action, and binding may be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="InterfaceTables/Insert/OFA/FA/FA_BOOKS";  
Request2(WCF.BindingType)="oracleEBSBinding";  
Request2(WCF.UserName)="myuser";  
Request2(WCF.Password)="mypass";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="oracleebs://ebs_instance";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
> [!NOTE]
>  <span data-ttu-id="31ed2-106">如果您使用 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleEBSAdapter"`，其中**OracleEBSAdapter**新增 Wcf-oracleebs 配接器中的名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="31ed2-106">If you are using a WCF-OracleEBS adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleEBSAdapter"`, where **OracleEBSAdapter** is the name with which you added the WCF-OracleEBS adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="31ed2-107">在上述範例中，</span><span class="sxs-lookup"><span data-stu-id="31ed2-107">In the preceding example,</span></span>  
  
- <span data-ttu-id="31ed2-108">正在從 Request1 訊息建立要求 2 訊息。</span><span class="sxs-lookup"><span data-stu-id="31ed2-108">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="31ed2-109">這兩個訊息對應至作業的結構描述，產生使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31ed2-109">Both messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
- <span data-ttu-id="31ed2-110">傳送埠是在 BizTalk 協調流程中的邏輯傳送連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="31ed2-110">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
  <span data-ttu-id="31ed2-111">**運算式**圖形是 BizTalk 協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="31ed2-111">The **Expression** shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="31ed2-112">部署協調流程時，也會建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="31ed2-112">Deploying the orchestration also creates a WCF-Custom send port.</span></span>  
  
  <span data-ttu-id="31ed2-113">如需有關如何設定動態連接埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="31ed2-113">For more information about configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="31ed2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31ed2-114">See Also</span></span>  
[<span data-ttu-id="31ed2-115">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="31ed2-115">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)