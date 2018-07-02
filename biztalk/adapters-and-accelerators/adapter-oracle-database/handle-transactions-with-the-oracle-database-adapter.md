---
title: 使用 Oracle 資料庫配接器處理交易 |Microsoft Docs
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
ms.openlocfilehash: d94914c2f0f7bde91ea55032048e30232af60d02
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970703"
---
# <a name="handle-transactions-with-the-oracle-database-adapter"></a><span data-ttu-id="10c09-102">使用 Oracle 資料庫配接器處理交易</span><span class="sxs-lookup"><span data-stu-id="10c09-102">Handle Transactions with the Oracle Database adapter</span></span>
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="10c09-103"> 不會啟動交易時執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="10c09-103"> does not initiate a transaction while performing an operation on the Oracle database.</span></span> <span data-ttu-id="10c09-104">相反地，配接器會執行使用配接器用戶端所提供的異動內容的作業。</span><span class="sxs-lookup"><span data-stu-id="10c09-104">Instead, the adapter performs the operations using the transaction context provided by the adapter clients.</span></span> <span data-ttu-id="10c09-105">若要執行作業在交易中使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須：</span><span class="sxs-lookup"><span data-stu-id="10c09-105">In order to perform operations in a transaction using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must:</span></span>  
  
-   <span data-ttu-id="10c09-106">啟用配接器用戶端中的交易。</span><span class="sxs-lookup"><span data-stu-id="10c09-106">Enable transactions in the adapter clients.</span></span> <span data-ttu-id="10c09-107">例如，若要啟用 BizTalk Server 中的交易，您必須選取**Use Transaction**中的核取方塊**交易**區域**訊息**WCF 自訂 索引標籤或Wcf-oracledb 連接埠。</span><span class="sxs-lookup"><span data-stu-id="10c09-107">For example, to enable transactions in BizTalk Server, you must select the **Use Transaction** check box in the **Transactions** area of the **Messages** tab for a WCF-Custom or WCF-OracleDB port.</span></span>  
  
-   <span data-ttu-id="10c09-108">設定的值**UseAmbientTransaction**屬性來繫結 **，則為 True**配接器中。</span><span class="sxs-lookup"><span data-stu-id="10c09-108">Set the value of the **UseAmbientTransaction** binding property to **True** in the adapter.</span></span> <span data-ttu-id="10c09-109">如需有關繫結屬性的詳細資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="10c09-109">For more information about the binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10c09-110">若要使用配接器執行的 Oracle 資料庫上的交易，您必須安裝**Oracle Microsoft Transaction Services Server**元件，同時執行配接器的電腦上安裝 Oracle 用戶端用戶端。</span><span class="sxs-lookup"><span data-stu-id="10c09-110">To use the adapter to perform transactions on the Oracle database, you must have installed the **Oracle Services For Microsoft Transaction Server** component, while installing the Oracle client, on the computer running the adapter client.</span></span>  
  
## <a name="transactions-in-the-outbound-operations"></a><span data-ttu-id="10c09-111">在輸出的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="10c09-111">Transactions in the Outbound Operations</span></span>  
 <span data-ttu-id="10c09-112">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]單一交易中執行輸出作業。</span><span class="sxs-lookup"><span data-stu-id="10c09-112">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] performs an outbound operation in a single transaction.</span></span> <span data-ttu-id="10c09-113">對於複合作業，所有作業將會在單一交易，但使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="10c09-113">For composite operations, all the operations are performed in a single transaction but using different ODP.NET connections.</span></span> <span data-ttu-id="10c09-114">如需詳細資訊，呈現的輸出作業的相關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="10c09-114">For more information about the outbound operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [How does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).</span></span>  
  
## <a name="transactions-in-the-inbound-operations"></a><span data-ttu-id="10c09-115">輸入的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="10c09-115">Transactions in the Inbound Operations</span></span>  
 <span data-ttu-id="10c09-116">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開下列兩項輸入的作業：</span><span class="sxs-lookup"><span data-stu-id="10c09-116">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes the following two inbound operations:</span></span>  
  
- <span data-ttu-id="10c09-117">**輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 會在交易中執行，而不同的交易中執行輪詢的資料提供陳述式。</span><span class="sxs-lookup"><span data-stu-id="10c09-117">**Polling**: The polling statement and the post-poll statement (if specified) are executed in a transaction, whereas, the polled data available statement is executed in a different transaction.</span></span> <span data-ttu-id="10c09-118">同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連線，而使用不同的 ODP.NET 連接 」 來執行 「 輪詢的資料提供陳述式。</span><span class="sxs-lookup"><span data-stu-id="10c09-118">Similarly, the polling statement and the post-poll statement are executed using the same ODP.NET connection, whereas, the polled data available statement is executed using a different ODP.NET connection.</span></span>  
  
- <span data-ttu-id="10c09-119">**通知**： 通知作業中使用單一的 ODP.NET 連接的交易。</span><span class="sxs-lookup"><span data-stu-id="10c09-119">**Notification**: The notification operation is performed in a transaction using a single ODP.NET connection.</span></span>  
  
  <span data-ttu-id="10c09-120">如需詳細資訊，呈現輸入作業的相關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle 中繼資料的運作方式？](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="10c09-120">For more information about the inbound operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [How does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10c09-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10c09-121">See Also</span></span>  
 [<span data-ttu-id="10c09-122">BizTalk Adapter for Oracle Database 概觀</span><span class="sxs-lookup"><span data-stu-id="10c09-122">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)