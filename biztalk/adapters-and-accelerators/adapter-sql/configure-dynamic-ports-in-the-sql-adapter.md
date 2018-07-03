---
title: SQL 配接器中設定動態連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c98b66ed-0bf7-4b24-9d16-9792d033b818
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c23bce67dbc4eaca8441e6e7d07573724225cc45
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976231"
---
# <a name="configure-dynamic-ports-in-the-sql-adapter"></a><span data-ttu-id="6d676-102">SQL 配接器中設定動態連接埠</span><span class="sxs-lookup"><span data-stu-id="6d676-102">Configure dynamic ports in the SQL adapter</span></span>
<span data-ttu-id="6d676-103">在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6d676-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="6d676-104">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 架構配接器時，您可以動態設定的連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="6d676-104">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by using message context properties.</span></span>  

## <a name="use-an-expression-shape"></a><span data-ttu-id="6d676-105">使用 「 運算式 」 圖形</span><span class="sxs-lookup"><span data-stu-id="6d676-105">Use an expression shape</span></span>  
 <span data-ttu-id="6d676-106">針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後指定中**運算式**圖形，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6d676-106">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], the URI, action, and binding may be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
```  
Request2=Request1;  
Request2(WCF.Action)="TableOp/Insert/dbo/CustomerTable";  
Request2(WCF.BindingType)="sqlBinding";  
Request2(WCF.UserName)="myuser";  
Request2(WCF.Password)="mypass";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="mssql://sql_server/my_instance/my_database";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="6d676-107">如果您使用中的 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SQLAdapter"`，其中**SQLAdapter**加入中的 WCF-SQL 配接器名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6d676-107">If you are using a WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SQLAdapter"`, where **SQLAdapter** is the name with which you added the WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="6d676-108">在上述範例中，</span><span class="sxs-lookup"><span data-stu-id="6d676-108">In the preceding example,</span></span>  
  
- <span data-ttu-id="6d676-109">正在從 Request1 訊息建立要求 2 訊息。</span><span class="sxs-lookup"><span data-stu-id="6d676-109">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="6d676-110">這兩個訊息對應至作業的結構描述，產生使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6d676-110">Both messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
- <span data-ttu-id="6d676-111">傳送埠是在 BizTalk 協調流程中的邏輯傳送連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d676-111">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
  <span data-ttu-id="6d676-112">**運算式**圖形是 BizTalk 協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="6d676-112">The **Expression** shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="6d676-113">部署協調流程時，也會建立 Wcf-custom 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6d676-113">Deploying the orchestration also creates a WCF-Custom send port.</span></span>  
  
  <span data-ttu-id="6d676-114">如需有關如何設定動態連接埠的詳細資訊，請參閱 <<c0> [ 設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6d676-114">For more information about configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6d676-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d676-115">See Also</span></span>  
[<span data-ttu-id="6d676-116">若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="6d676-116">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)