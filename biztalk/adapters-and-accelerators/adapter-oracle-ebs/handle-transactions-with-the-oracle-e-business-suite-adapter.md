---
title: "處理交易與 Oracle E-business Suite 介面卡 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b443be9d-a93d-4836-8717-5ee9dad4442f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e00b31230760d1bb811b987c3b1a926bad803b6d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handle-transactions-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="2a1b0-102">處理 Oracle E-business Suite 配接器的交易</span><span class="sxs-lookup"><span data-stu-id="2a1b0-102">Handle transactions with the Oracle E-Business Suite adapter</span></span>
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="2a1b0-103">不會啟動交易，以執行 Oracle E-business Suite 中的作業時發生。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-103"> does not initiate a transaction while performing an operation in Oracle E-Business Suite.</span></span> <span data-ttu-id="2a1b0-104">相反地，配接器會執行作業使用配接器用戶端所提供的交易內容。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-104">Instead, the adapter performs the operations using the transaction context provided by the adapter clients.</span></span> <span data-ttu-id="2a1b0-105">為了執行作業中使用交易[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須：</span><span class="sxs-lookup"><span data-stu-id="2a1b0-105">In order to perform operations in a transaction using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must:</span></span>  
  
-   <span data-ttu-id="2a1b0-106">啟用配接器用戶端中的交易。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-106">Enable transactions in the adapter clients.</span></span> <span data-ttu-id="2a1b0-107">例如，若要啟用交易中的[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，您必須選取**Use Transaction**中核取方塊**交易**區域**訊息** 索引標籤WCF 自訂 」 或 「 Wcf-oracleebs 連接埠。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-107">For example, to enable transactions in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], you must select the **Use Transaction** check box in the **Transactions** area of the **Messages** tab for a WCF-Custom or WCF-OracleEBS port.</span></span>  
  
-   <span data-ttu-id="2a1b0-108">值設定**UseAmbientTransaction**內容繫結至**True**配接器中。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-108">Set the value of the **UseAmbientTransaction** binding property to **True** in the adapter.</span></span> <span data-ttu-id="2a1b0-109">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-109">For more information about the binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a1b0-110">若要使用配接器執行 Oracle E-business Suite 中的交易，您必須安裝**Oracle Microsoft Transaction Server 服務**執行配接器的電腦上安裝 Oracle 用戶端時，元件用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-110">To use the adapter to perform transactions in Oracle E-Business Suite, you must have installed the **Oracle Services For Microsoft Transaction Server** component, while installing the Oracle client, on the computer running the adapter client.</span></span>  
  
## <a name="transactions-in-the-outbound-operations"></a><span data-ttu-id="2a1b0-111">在輸出作業中的交易</span><span class="sxs-lookup"><span data-stu-id="2a1b0-111">Transactions in the Outbound Operations</span></span>  
 <span data-ttu-id="2a1b0-112">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]在單一交易中執行的輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] performs an outbound operation in a single transaction.</span></span> <span data-ttu-id="2a1b0-113">複合作業，所有作業都都在單一交易，但使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-113">For composite operations, all the operations are performed in a single transaction but using different ODP.NET connections.</span></span> <span data-ttu-id="2a1b0-114">如需有關由顯示的輸出作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-114">For more information about the outbound operations surfaced by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [How Does the Adapter Surface Oracle E-Business Suite Metadata?](https://msdn.microsoft.com/library/dd788431.aspx).</span></span>  
  
## <a name="transactions-in-the-inbound-operations"></a><span data-ttu-id="2a1b0-115">輸入的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="2a1b0-115">Transactions in the Inbound Operations</span></span>  
 <span data-ttu-id="2a1b0-116">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開下列兩個輸入的作業：</span><span class="sxs-lookup"><span data-stu-id="2a1b0-116">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the following two inbound operations:</span></span>  
  
-   <span data-ttu-id="2a1b0-117">**輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 中執行的交易，而在不同交易中執行輪詢的資料的可用陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-117">**Polling**: The polling statement and the post-poll statement (if specified) are executed in a transaction, whereas, the polled data available statement is executed in a different transaction.</span></span> <span data-ttu-id="2a1b0-118">同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連接，而輪詢的資料可用陳述式使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-118">Similarly, the polling statement and the post-poll statement are executed using the same ODP.NET connection, whereas, the polled data available statement is executed using a different ODP.NET connection.</span></span>  
  
-   <span data-ttu-id="2a1b0-119">**通知**： 通知作業使用單一 ODP.NET 連接在交易中執行。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-119">**Notification**: The notification operation is performed in a transaction using a single ODP.NET connection.</span></span>  
  
 <span data-ttu-id="2a1b0-120">如需有關由顯示輸入操作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2a1b0-120">For more information about the inbound operations surfaced by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [How Does the Adapter Surface Oracle E-Business Suite Metadata?](https://msdn.microsoft.com/library/dd788431.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1b0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1b0-121">See Also</span></span>  
[<span data-ttu-id="2a1b0-122">瞭解 BizTalk Adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="2a1b0-122">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)