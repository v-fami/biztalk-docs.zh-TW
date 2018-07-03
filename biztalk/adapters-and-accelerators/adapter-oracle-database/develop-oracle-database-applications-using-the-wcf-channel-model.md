---
title: 開發使用 WCF 通道模型的 Oracle 資料庫應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4990ebb9e9aad612a82af42b3d186643da1e91ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002727"
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a><span data-ttu-id="d46d2-102">開發使用 WCF 通道模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="d46d2-102">Develop Oracle Database applications using the WCF Channel Model</span></span>
<span data-ttu-id="d46d2-103">您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]通道模型使用[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]直接透過使用 Oracle DB 繫結建立通道執行個體傳送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="d46d2-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] by sending XML messages directly over a channel instance created with the Oracle DB Binding.</span></span>  
  
 <span data-ttu-id="d46d2-104">透過使用強型別類別與 WCF 服務模型會公開的方法中使用 WCF 通道模型的優點之一是通道模型提供更精密地控制您的 Oracle 資料庫執行的作業。</span><span class="sxs-lookup"><span data-stu-id="d46d2-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle database.</span></span> <span data-ttu-id="d46d2-105">為什麼？</span><span class="sxs-lookup"><span data-stu-id="d46d2-105">Why?</span></span> <span data-ttu-id="d46d2-106">WCF 通道模型中您可以直接控制您透過通道傳送訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="d46d2-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="d46d2-107">在某些情況下，此額外控制層級能帶來好處。</span><span class="sxs-lookup"><span data-stu-id="d46d2-107">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="d46d2-108">比方說，當您使用 WCF 通道模型來執行資料表的更新作業時，您可以藉由略過資料行，從您傳遞的訊息中的更新範本選擇性地更新目標資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="d46d2-108">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="d46d2-109">所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中每個資料行包含資料表的結構描述中的強型別記錄參數。</span><span class="sxs-lookup"><span data-stu-id="d46d2-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span> <span data-ttu-id="d46d2-110">如果資料行"nillable = false"的 WSDL，就必須更新使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="d46d2-110">If a column has “nillable=false” in the WSDL, it must be updated using the WCF service model.</span></span>  
  
 <span data-ttu-id="d46d2-111">透過 WCF 服務模型的 WCF 通道模型提供的另一個主要優點是以端對端串流 Oracle 大型物件 (LOB) 資料類型的更完整支援。</span><span class="sxs-lookup"><span data-stu-id="d46d2-111">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for end-to-end streaming of Oracle large object (LOB) data types.</span></span> <span data-ttu-id="d46d2-112">使用 WCF 通道模型中，您可以執行端對端串流：</span><span class="sxs-lookup"><span data-stu-id="d46d2-112">By using the WCF channel model you can perform end-to-end streaming:</span></span>  
  
- <span data-ttu-id="d46d2-113">若要更新資料表中的 LOB 資料行，或使用 UpdateLOB 作業檢視。</span><span class="sxs-lookup"><span data-stu-id="d46d2-113">To update an LOB column in a table or view using the UpdateLOB operation.</span></span>  
  
- <span data-ttu-id="d46d2-114">在外和 IN，OUT 參數包含 LOB 程序和函式所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="d46d2-114">On OUT and IN OUT parameters containing LOB data that are returned by procedures and functions.</span></span>  
  
- <span data-ttu-id="d46d2-115">SQLEXECUTE 作業的結果中包含的 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="d46d2-115">On LOB data that is contained in the result of a SQLEXECUTE operation.</span></span>  
  
- <span data-ttu-id="d46d2-116">LOB 資料行上，會傳回 POLLINGSTMT 作業。</span><span class="sxs-lookup"><span data-stu-id="d46d2-116">On LOB data columns that are returned in the POLLINGSTMT operation.</span></span>  
  
- <span data-ttu-id="d46d2-117">在 選取資料表或檢視表上作業所傳回的 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="d46d2-117">On LOB data columns that are returned by a Select operation on a table or view.</span></span>  
  
  <span data-ttu-id="d46d2-118">這是因為 WCF 通道模型中您直接控制如何於外寄訊息提供訊息內文和訊息本文，對傳入訊息的處理方式。</span><span class="sxs-lookup"><span data-stu-id="d46d2-118">This is because in the WCF channel model you directly control how you provide the message body on outgoing messages and how you process the message body on incoming messages.</span></span>  
  
  <span data-ttu-id="d46d2-119">相反地，WCF 服務模型只提供：</span><span class="sxs-lookup"><span data-stu-id="d46d2-119">In contrast, the WCF service model only provides:</span></span>  
  
- <span data-ttu-id="d46d2-120">端對端的一項操作，ReadLOB 作業的 LOB 資料串流。</span><span class="sxs-lookup"><span data-stu-id="d46d2-120">End-to-end streaming for LOB data on one operation, the ReadLOB operation.</span></span>  
  
- <span data-ttu-id="d46d2-121">若要更新 LOB 資料，以資料流處理方式的 Oracle 資料庫上沒有功能。</span><span class="sxs-lookup"><span data-stu-id="d46d2-121">No capability to update LOB data on the Oracle database in a streamed fashion.</span></span>  
  
  <span data-ttu-id="d46d2-122">本主題中的各節說明如何執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="d46d2-122">The sections in this topic explain how to perform operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d46d2-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="d46d2-123">In This Section</span></span>  
  
-   [<span data-ttu-id="d46d2-124">使用 Oracle 資料庫配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="d46d2-124">Overview of the WCF channel model with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="d46d2-125">建立通道，使用 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="d46d2-125">Create a channel using Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [<span data-ttu-id="d46d2-126">使用 WCF 通道模型之 Oracle 資料庫上叫用作業</span><span class="sxs-lookup"><span data-stu-id="d46d2-126">Invoke Operations on the Oracle Database Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="d46d2-127">使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 作業</span><span class="sxs-lookup"><span data-stu-id="d46d2-127">Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="d46d2-128">在使用 WCF 通道模型的 Oracle 資料庫執行插入作業</span><span class="sxs-lookup"><span data-stu-id="d46d2-128">Run an Insert Operation in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="d46d2-129">叫用使用 WCF 通道模型的 Oracle 資料庫中的函式</span><span class="sxs-lookup"><span data-stu-id="d46d2-129">Invoke a Function in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="d46d2-130">使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="d46d2-130">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [<span data-ttu-id="d46d2-131">串流處理 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="d46d2-131">Streaming Oracle Database LOB Data Types Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)