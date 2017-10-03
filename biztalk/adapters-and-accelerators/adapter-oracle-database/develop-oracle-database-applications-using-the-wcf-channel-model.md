---
title: "開發 Oracle 資料庫應用程式使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming
- channel programming, streaming
- WCF channel model, performing operations
- developing applications, by using the WCF channel model
- streaming, using the WCF channel model
- WCF channel model, developingn applications
- channel programming, performing operations
ms.assetid: cb6bf5fd-ff90-44bd-a9dd-03b00f12a78d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fb9b6ca1fc70a55b59c6708450b8d94a01eff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a><span data-ttu-id="8e383-102">開發 Oracle 資料庫應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="8e383-102">Develop Oracle Database applications using the WCF Channel Model</span></span>
<span data-ttu-id="8e383-103">您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]直接透過使用 Oracle 資料庫繫結建立通道執行個體傳送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="8e383-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] by sending XML messages directly over a channel instance created with the Oracle DB Binding.</span></span>  
  
 <span data-ttu-id="8e383-104">使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您的 Oracle 資料庫執行的作業。</span><span class="sxs-lookup"><span data-stu-id="8e383-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle database.</span></span> <span data-ttu-id="8e383-105">為什麼？</span><span class="sxs-lookup"><span data-stu-id="8e383-105">Why?</span></span> <span data-ttu-id="8e383-106">WCF 通道模型中直接控制您透過通道傳送訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="8e383-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="8e383-107">在某些情況下，控制此額外層級可能有所助益。</span><span class="sxs-lookup"><span data-stu-id="8e383-107">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="8e383-108">例如，當您執行更新作業的資料表上使用 WCF 通道模型，您可以藉由略過您傳遞的訊息中的更新範本的資料行選擇性地更新目標資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e383-108">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="8e383-109">所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中包含每個資料行中的資料表結構描述的強型別記錄參數。</span><span class="sxs-lookup"><span data-stu-id="8e383-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span> <span data-ttu-id="8e383-110">如果資料行"nillable = false 」 在 WSDL，就必須更新使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="8e383-110">If a column has “nillable=false” in the WSDL, it must be updated using the WCF service model.</span></span>  
  
 <span data-ttu-id="8e383-111">WCF 通道模型提供的 WCF 服務模型透過另一個主要優點是更廣泛支援端對端的資料流的 Oracle 大型物件 (LOB) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8e383-111">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for end-to-end streaming of Oracle large object (LOB) data types.</span></span> <span data-ttu-id="8e383-112">使用 WCF 通道模型中，您可以執行端對端資料流：</span><span class="sxs-lookup"><span data-stu-id="8e383-112">By using the WCF channel model you can perform end-to-end streaming:</span></span>  
  
-   <span data-ttu-id="8e383-113">若要更新資料表中的 LOB 資料行或檢視使用 UpdateLOB 作業。</span><span class="sxs-lookup"><span data-stu-id="8e383-113">To update an LOB column in a table or view using the UpdateLOB operation.</span></span>  
  
-   <span data-ttu-id="8e383-114">在和 IN，OUT 參數包含 LOB 程序和函數所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="8e383-114">On OUT and IN OUT parameters containing LOB data that are returned by procedures and functions.</span></span>  
  
-   <span data-ttu-id="8e383-115">SQLEXECUTE 運算的結果中包含的 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="8e383-115">On LOB data that is contained in the result of a SQLEXECUTE operation.</span></span>  
  
-   <span data-ttu-id="8e383-116">上傳回 POLLINGSTMT 作業中的 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e383-116">On LOB data columns that are returned in the POLLINGSTMT operation.</span></span>  
  
-   <span data-ttu-id="8e383-117">上傳回的資料表或檢視表上的選取作業的 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e383-117">On LOB data columns that are returned by a Select operation on a table or view.</span></span>  
  
 <span data-ttu-id="8e383-118">這是因為 WCF 通道模型中您直接控制如何於外寄訊息提供訊息內文和您要如何處理內送訊息的訊息本文。</span><span class="sxs-lookup"><span data-stu-id="8e383-118">This is because in the WCF channel model you directly control how you provide the message body on outgoing messages and how you process the message body on incoming messages.</span></span>  
  
 <span data-ttu-id="8e383-119">相反地，WCF 服務模型只會提供：</span><span class="sxs-lookup"><span data-stu-id="8e383-119">In contrast, the WCF service model only provides:</span></span>  
  
-   <span data-ttu-id="8e383-120">端對端的一項操作，ReadLOB 作業的 LOB 資料串流。</span><span class="sxs-lookup"><span data-stu-id="8e383-120">End-to-end streaming for LOB data on one operation, the ReadLOB operation.</span></span>  
  
-   <span data-ttu-id="8e383-121">若要更新 LOB 資料，以資料流處理方式的 Oracle 資料庫上沒有功能。</span><span class="sxs-lookup"><span data-stu-id="8e383-121">No capability to update LOB data on the Oracle database in a streamed fashion.</span></span>  
  
 <span data-ttu-id="8e383-122">本主題中的各節說明如何執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="8e383-122">The sections in this topic explain how to perform operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e383-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="8e383-123">In This Section</span></span>  
  
-   [<span data-ttu-id="8e383-124">使用 Oracle 資料庫配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="8e383-124">Overview of the WCF channel model with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="8e383-125">建立通道使用 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="8e383-125">Create a channel using Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [<span data-ttu-id="8e383-126">使用 WCF 通道模型之 Oracle 資料庫上叫用作業</span><span class="sxs-lookup"><span data-stu-id="8e383-126">Invoke Operations on the Oracle Database Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="8e383-127">使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 操作</span><span class="sxs-lookup"><span data-stu-id="8e383-127">Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="8e383-128">在使用 WCF 通道模型的 Oracle 資料庫執行插入作業</span><span class="sxs-lookup"><span data-stu-id="8e383-128">Run an Insert Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="8e383-129">叫用使用 WCF 通道模型的 Oracle 資料庫中的函式</span><span class="sxs-lookup"><span data-stu-id="8e383-129">Invoke a Function in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="8e383-130">使用 WCF 通道模型的 Oracle 資料庫中收到輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="8e383-130">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [<span data-ttu-id="8e383-131">資料流處理的 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="8e383-131">Streaming Oracle Database LOB Data Types Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)