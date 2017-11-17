---
title: "輪詢 Oracle E-business Suite 使用 WCF 服務模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96670a39-4fec-49bf-85d1-947b1a1bc750
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0122bceddbfd902f31549efe9bc8819f108b6f57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="dc4bc-102">使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="dc4bc-102">Poll Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="dc4bc-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 資料庫接收輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from the Oracle database.</span></span> <span data-ttu-id="dc4bc-104">配接器會提供兩種輪詢 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="dc4bc-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
-   <span data-ttu-id="dc4bc-105">**使用 SELECT 陳述式**。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-105">**Using SELECT statements**.</span></span> <span data-ttu-id="dc4bc-106">您可以指定簡單的 SELECT 陳述式，以輪詢 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-106">You can specify a simple SELECT statement to poll the Oracle database.</span></span> <span data-ttu-id="dc4bc-107">配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
-   <span data-ttu-id="dc4bc-108">**使用預存程序**。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-108">**Using stored procedures**.</span></span> <span data-ttu-id="dc4bc-109">您可以指定輪詢 Oracle 資料庫的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-109">You can specify a stored procedure to poll the Oracle database.</span></span> <span data-ttu-id="dc4bc-110">配接器指定的間隔執行預存程序，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-110">The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.</span></span>  
  
 <span data-ttu-id="dc4bc-111">兩種方法中的主要差異是方式配接器用戶端指定配接器輪詢 Oracle 資料庫所使用的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="dc4bc-112">簡單的 SELECT 陳述式的第一個方法的輪詢陳述式時，預存程序方法的輪詢陳述式是執行預存程序的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure.</span></span> <span data-ttu-id="dc4bc-113">配接器用戶端指定輪詢陳述式，兩種方法，如**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-113">Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property.</span></span> <span data-ttu-id="dc4bc-114">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-114">For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
 <span data-ttu-id="dc4bc-115">此章節的主題提供如何輪詢使用 SELECT 陳述式和預存程序的指示。</span><span class="sxs-lookup"><span data-stu-id="dc4bc-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc4bc-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="dc4bc-116">In This Section</span></span>  
  
-   [<span data-ttu-id="dc4bc-117">輪詢 Oracle E-business Suite 與 WCF 服務模型中使用 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="dc4bc-117">Poll Oracle E-Business Suite using SELECT statement with the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="dc4bc-118">輪詢 Oracle E-business Suite 使用 WCF 服務模型中的預存程序</span><span class="sxs-lookup"><span data-stu-id="dc4bc-118">Poll Oracle E-Business Suite using stored procedures with the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc4bc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4bc-119">See Also</span></span>  
 [<span data-ttu-id="dc4bc-120">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="dc4bc-120">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)