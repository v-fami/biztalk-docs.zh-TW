---
title: "開發 SQL 應用程式使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11df5cc2-b532-45a8-9055-d05f4704a6e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b503b0766a4848e05c9361fb151196ee43afd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sql-applications-using-the-wcf-channel-model"></a><span data-ttu-id="1e29f-102">開發 SQL 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="1e29f-102">Develop SQL applications using the WCF Channel Model</span></span>
<span data-ttu-id="1e29f-103">您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]直接透過使用 SQL Server 繫結建立通道執行個體傳送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="1e29f-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] by sending XML messages directly over a channel instance created with the SQL Server Binding.</span></span>  
  
 <span data-ttu-id="1e29f-104">使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您在 SQL database 執行的作業。</span><span class="sxs-lookup"><span data-stu-id="1e29f-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the SQL database.</span></span> <span data-ttu-id="1e29f-105">此控制項是來自事實，在 WCF 通道模型中，您直接控制您透過通道傳送訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="1e29f-105">This control comes from the fact that in the WCF channel model, you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="1e29f-106">在某些情況下，控制此額外層級可能有所助益。</span><span class="sxs-lookup"><span data-stu-id="1e29f-106">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="1e29f-107">例如，當您執行更新作業的資料表上使用 WCF 通道模型，您可以藉由略過您傳遞的訊息中的更新範本的資料行選擇性地更新目標資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1e29f-107">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="1e29f-108">所需的唯一資料行是那些與"nillable = false 」 在 WSDL 中。</span><span class="sxs-lookup"><span data-stu-id="1e29f-108">The only columns that are required are those with “nillable=false” in the WSDL.</span></span> <span data-ttu-id="1e29f-109">所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中包含每個資料行中的資料表結構描述的強型別記錄參數。</span><span class="sxs-lookup"><span data-stu-id="1e29f-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span>  
  
 <span data-ttu-id="1e29f-110">本主題中的各節說明如何執行作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="1e29f-110">The sections in this topic explain how to perform operations on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e29f-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="1e29f-111">In This Section</span></span>  
  
-   [<span data-ttu-id="1e29f-112">SQL 配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="1e29f-112">Overview of the WCF channel model with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="1e29f-113">建立使用 SQL 配接器的通道</span><span class="sxs-lookup"><span data-stu-id="1e29f-113">Create a channel using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="1e29f-114">在使用 WCF 通道模型的 SQL 執行插入作業的資料表</span><span class="sxs-lookup"><span data-stu-id="1e29f-114">Run an Insert Operation on a Table in SQL using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="1e29f-115">從 SQL Server 接收輪詢基礎資料變更的訊息，使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="1e29f-115">Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e29f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e29f-116">See Also</span></span>  
[<span data-ttu-id="1e29f-117">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="1e29f-117">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)