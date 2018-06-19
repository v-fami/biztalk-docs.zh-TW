---
title: SQL 配接器中設定動態連接埠 |Microsoft 文件
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
ms.openlocfilehash: 0bb1417280706399728f7bfd59bc4c5ee7a7cc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222190"
---
# <a name="configure-dynamic-ports-in-the-sql-adapter"></a><span data-ttu-id="33c40-102">SQL 配接器中設定動態連接埠</span><span class="sxs-lookup"><span data-stu-id="33c40-102">Configure dynamic ports in the SQL adapter</span></span>
<span data-ttu-id="33c40-103">在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定動態連接埠[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33c40-103">In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can configure dynamic ports for a [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)].</span></span> <span data-ttu-id="33c40-104">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 架構的配接器，您可以動態設定的連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="33c40-104">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF-based adapter, you can dynamically configure a port for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by using message context properties.</span></span>  

## <a name="use-an-expression-shape"></a><span data-ttu-id="33c40-105">使用 「 運算式 」 圖形</span><span class="sxs-lookup"><span data-stu-id="33c40-105">Use an expression shape</span></span>  
 <span data-ttu-id="33c40-106">如[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，URI、 動作和繫結可能會決定從傳入訊息上的屬性，然後以指定**運算式**圖形，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="33c40-106">For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], the URI, action, and binding may be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following example:</span></span>  
  
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
>  <span data-ttu-id="33c40-107">如果您使用 WCF SQL 配接器在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定做為傳輸類型`SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SQLAdapter"`，其中**SQLAdapter**新增 WCF-SQL 配接器中的名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="33c40-107">If you are using a WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can also specify the transport type as `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="SQLAdapter"`, where **SQLAdapter** is the name with which you added the WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="33c40-108">在上述範例中，</span><span class="sxs-lookup"><span data-stu-id="33c40-108">In the preceding example,</span></span>  
  
-   <span data-ttu-id="33c40-109">正在從 Request1 訊息建立 Request2 訊息。</span><span class="sxs-lookup"><span data-stu-id="33c40-109">Request2 message is being created from Request1 message.</span></span> <span data-ttu-id="33c40-110">這兩個訊息對應至作業結構描述，產生使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33c40-110">Both messages map to an operation schema, which is generated using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
-   <span data-ttu-id="33c40-111">傳送埠是 BizTalk 協調流程中的邏輯傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="33c40-111">SendPort is the name of the logical send port in the BizTalk orchestration.</span></span>  
  
 <span data-ttu-id="33c40-112">**運算式**圖形是 BizTalk 協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="33c40-112">The **Expression** shape is part of the BizTalk orchestration.</span></span> <span data-ttu-id="33c40-113">部署協調流程也會建立一個 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="33c40-113">Deploying the orchestration also creates a WCF-Custom send port.</span></span>  
  
 <span data-ttu-id="33c40-114">如需設定動態連接埠的詳細資訊，請參閱[設定動態傳送埠使用 WCF 配接器內容屬性](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="33c40-114">For more information about configuring dynamic ports, see [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="33c40-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33c40-115">See Also</span></span>  
[<span data-ttu-id="33c40-116">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="33c40-116">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)