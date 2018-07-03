---
title: 使用 Oracle E-business Suite 配接器處理交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b443be9d-a93d-4836-8717-5ee9dad4442f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9d5bc59cdce4b78a01dc867e12a84eac3b3469d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010911"
---
# <a name="handle-transactions-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="dceed-102">使用 Oracle E-business Suite 配接器處理交易</span><span class="sxs-lookup"><span data-stu-id="dceed-102">Handle transactions with the Oracle E-Business Suite adapter</span></span>
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="dceed-103"> 不會啟動交易，以執行 Oracle E-business Suite 中的作業時。</span><span class="sxs-lookup"><span data-stu-id="dceed-103"> does not initiate a transaction while performing an operation in Oracle E-Business Suite.</span></span> <span data-ttu-id="dceed-104">相反地，配接器會執行使用配接器用戶端所提供的異動內容的作業。</span><span class="sxs-lookup"><span data-stu-id="dceed-104">Instead, the adapter performs the operations using the transaction context provided by the adapter clients.</span></span> <span data-ttu-id="dceed-105">若要執行作業在交易中使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須：</span><span class="sxs-lookup"><span data-stu-id="dceed-105">In order to perform operations in a transaction using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must:</span></span>  
  
-   <span data-ttu-id="dceed-106">啟用配接器用戶端中的交易。</span><span class="sxs-lookup"><span data-stu-id="dceed-106">Enable transactions in the adapter clients.</span></span> <span data-ttu-id="dceed-107">例如，若要啟用 BizTalk Server 中的交易，您必須選取**Use Transaction**中的核取方塊**交易**區域**訊息**WCF 自訂 索引標籤或Wcf-oracleebs 連接埠。</span><span class="sxs-lookup"><span data-stu-id="dceed-107">For example, to enable transactions in BizTalk Server, you must select the **Use Transaction** check box in the **Transactions** area of the **Messages** tab for a WCF-Custom or WCF-OracleEBS port.</span></span>  
  
-   <span data-ttu-id="dceed-108">設定的值**UseAmbientTransaction**屬性來繫結 **，則為 True**配接器中。</span><span class="sxs-lookup"><span data-stu-id="dceed-108">Set the value of the **UseAmbientTransaction** binding property to **True** in the adapter.</span></span> <span data-ttu-id="dceed-109">如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="dceed-109">For more information about the binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dceed-110">若要使用配接器執行 Oracle E-business Suite 中的交易，您必須安裝**Oracle Microsoft Transaction Services Server**元件，同時執行配接器的電腦上安裝 Oracle 用戶端用戶端。</span><span class="sxs-lookup"><span data-stu-id="dceed-110">To use the adapter to perform transactions in Oracle E-Business Suite, you must have installed the **Oracle Services For Microsoft Transaction Server** component, while installing the Oracle client, on the computer running the adapter client.</span></span>  
  
## <a name="transactions-in-the-outbound-operations"></a><span data-ttu-id="dceed-111">在輸出的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="dceed-111">Transactions in the Outbound Operations</span></span>  
 <span data-ttu-id="dceed-112">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]單一交易中執行輸出作業。</span><span class="sxs-lookup"><span data-stu-id="dceed-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] performs an outbound operation in a single transaction.</span></span> <span data-ttu-id="dceed-113">對於複合作業，所有作業將會在單一交易，但使用不同的 ODP.NET 連線。</span><span class="sxs-lookup"><span data-stu-id="dceed-113">For composite operations, all the operations are performed in a single transaction but using different ODP.NET connections.</span></span> <span data-ttu-id="dceed-114">如需詳細資訊，呈現的輸出作業的相關[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dceed-114">For more information about the outbound operations surfaced by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [How Does the Adapter Surface Oracle E-Business Suite Metadata?](https://msdn.microsoft.com/library/dd788431.aspx).</span></span>  
  
## <a name="transactions-in-the-inbound-operations"></a><span data-ttu-id="dceed-115">輸入的作業中的交易</span><span class="sxs-lookup"><span data-stu-id="dceed-115">Transactions in the Inbound Operations</span></span>  
 <span data-ttu-id="dceed-116">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開下列兩項輸入的作業：</span><span class="sxs-lookup"><span data-stu-id="dceed-116">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the following two inbound operations:</span></span>  
  
- <span data-ttu-id="dceed-117">**輪詢**： 輪詢陳述式和後輪詢陳述式 （如果有指定） 會在交易中執行，而不同的交易中執行輪詢的資料提供陳述式。</span><span class="sxs-lookup"><span data-stu-id="dceed-117">**Polling**: The polling statement and the post-poll statement (if specified) are executed in a transaction, whereas, the polled data available statement is executed in a different transaction.</span></span> <span data-ttu-id="dceed-118">同樣地，輪詢陳述式後輪詢陳述式執行和使用相同的 ODP.NET 連線，而使用不同的 ODP.NET 連接 」 來執行 「 輪詢的資料提供陳述式。</span><span class="sxs-lookup"><span data-stu-id="dceed-118">Similarly, the polling statement and the post-poll statement are executed using the same ODP.NET connection, whereas, the polled data available statement is executed using a different ODP.NET connection.</span></span>  
  
- <span data-ttu-id="dceed-119">**通知**： 通知作業中使用單一的 ODP.NET 連接的交易。</span><span class="sxs-lookup"><span data-stu-id="dceed-119">**Notification**: The notification operation is performed in a transaction using a single ODP.NET connection.</span></span>  
  
  <span data-ttu-id="dceed-120">如需詳細資訊，呈現輸入作業的相關[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 配接器介面 Oracle E-business Suite 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788431.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dceed-120">For more information about the inbound operations surfaced by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [How Does the Adapter Surface Oracle E-Business Suite Metadata?](https://msdn.microsoft.com/library/dd788431.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dceed-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dceed-121">See Also</span></span>  
[<span data-ttu-id="dceed-122">了解 BizTalk Adapter for Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="dceed-122">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)