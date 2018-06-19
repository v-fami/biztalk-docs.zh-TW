---
title: 使用 Oracle 資料庫配接器處理交易 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 971c2fba-640c-4ae5-9ab3-2d8227c1627d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5072a49c9edc5dc8ce03ec819d6042b640b94a47
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005703"
---
# <a name="handle-transactions-with-the-oracle-database-adapter"></a><span data-ttu-id="3e093-102">使用 Oracle 資料庫配接器處理交易</span><span class="sxs-lookup"><span data-stu-id="3e093-102">Handle Transactions with the Oracle Database adapter</span></span>
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="3e093-103">不會啟動交易時執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="3e093-103"> does not initiate a transaction while performing an operation on the Oracle database.</span></span> <span data-ttu-id="3e093-104">相反地，配接器會執行作業使用配接器用戶端所提供的交易內容。</span><span class="sxs-lookup"><span data-stu-id="3e093-104">Instead, the adapter performs the operations using the transaction context provided by the adapter clients.</span></span> <span data-ttu-id="3e093-105">為了執行作業中使用交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須：</span><span class="sxs-lookup"><span data-stu-id="3e093-105">In order to perform operations in a transaction using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must:</span></span>  
  
-   <span data-ttu-id="3e093-106">啟用配接器用戶端中的交易。</span><span class="sxs-lookup"><span data-stu-id="3e093-106">Enable transactions in the adapter clients.</span></span> <span data-ttu-id="3e093-107">例如，若要啟用 BizTalk Server 中的交易，您必須選取**Use Transaction**中核取方塊**交易**區域**訊息**WCF 自訂 索引標籤或Wcf-oracledb 連接埠。</span><span class="sxs-lookup"><span data-stu-id="3e093-107">For example, to enable transactions in BizTalk Server, you must select the **Use Transaction** check box in the **Transactions** area of the **Messages** tab for a WCF-Custom or WCF-OracleDB port.</span></span>  
  
-   <span data-ttu-id="3e093-108">值設定**UseAmbientTransaction**內容繫結至**True**配接器中。</span><span class="sxs-lookup"><span data-stu-id="3e093-108">Set the value of the **UseAmbientTransaction** binding property to **True** in the adapter.</span></span> <span data-ttu-id="3e093-109">如需繫結屬性的詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3e093-109">For more information about the binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e093-110">若要使用配接器的 Oracle 資料庫上執行交易，您必須安裝**Oracle Microsoft Transaction Server 服務**執行配接器的電腦上安裝 Oracle 用戶端時，元件用戶端。</span><span class="sxs-lookup"><span data-stu-id="3e093-110">To use the adapter to perform transactions on the Oracle database, you must have installed the **Oracle Services For Microsoft Transaction Server** component, while installing the Oracle client, on the computer running the adapter client.</span></span>  
  
## <a name="transactions-in-the-outbound-operations"></a><span data-ttu-id="3e093-111">在輸出作業中的交易</span><span class="sxs-lookup"><span data-stu-id="3e093-111">Transactions in the Outbound Operations</span></span>  
 <span data-ttu-id="3e093-112">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在單一交易中執行的輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="3e093-112">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] performs an outbound operation in a single transaction.</span></span> <span data-ttu-id="3e093-113">複合作業，所有作業都都在單一交易，但使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="3e093-113">For composite operations, all the operations are performed in a single transaction but using different ODP.NET connections.</span></span> <span data-ttu-id="3e093-114">如需有關由顯示的輸出作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3e093-114">For more information about the outbound operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [How does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).</span></span>  
  
## <a name="transactions-in-the-inbound-operations"></a><span data-ttu-id="3e093-115">輸入的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="3e093-115">Transactions in the Inbound Operations</span></span>  
 <span data-ttu-id="3e093-116">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列兩個輸入的作業：</span><span class="sxs-lookup"><span data-stu-id="3e093-116">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes the following two inbound operations:</span></span>  
  
-   <span data-ttu-id="3e093-117">**輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 中執行的交易，而在不同交易中執行輪詢的資料的可用陳述式。</span><span class="sxs-lookup"><span data-stu-id="3e093-117">**Polling**: The polling statement and the post-poll statement (if specified) are executed in a transaction, whereas, the polled data available statement is executed in a different transaction.</span></span> <span data-ttu-id="3e093-118">同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連接，而輪詢的資料可用陳述式使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="3e093-118">Similarly, the polling statement and the post-poll statement are executed using the same ODP.NET connection, whereas, the polled data available statement is executed using a different ODP.NET connection.</span></span>  
  
-   <span data-ttu-id="3e093-119">**通知**： 通知作業使用單一 ODP.NET 連接在交易中執行。</span><span class="sxs-lookup"><span data-stu-id="3e093-119">**Notification**: The notification operation is performed in a transaction using a single ODP.NET connection.</span></span>  
  
 <span data-ttu-id="3e093-120">如需有關由顯示輸入操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3e093-120">For more information about the inbound operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [How does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e093-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e093-121">See Also</span></span>  
 [<span data-ttu-id="3e093-122">BizTalk Adapter for Oracle Database 概觀</span><span class="sxs-lookup"><span data-stu-id="3e093-122">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)