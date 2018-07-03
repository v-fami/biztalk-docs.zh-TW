---
title: 輪詢 Oracle E-business Suite 使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96670a39-4fec-49bf-85d1-947b1a1bc750
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2f8c9f16ed93e2866da0cbd55021edfdb2bd863
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995343"
---
# <a name="poll-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="b563c-102">使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="b563c-102">Poll Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="b563c-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 資料庫接收以輪詢為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="b563c-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from the Oracle database.</span></span> <span data-ttu-id="b563c-104">配接器會提供兩種輪詢 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b563c-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
- <span data-ttu-id="b563c-105">**使用 SELECT 陳述式**。</span><span class="sxs-lookup"><span data-stu-id="b563c-105">**Using SELECT statements**.</span></span> <span data-ttu-id="b563c-106">您可以指定要輪詢 Oracle 資料庫的簡單 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b563c-106">You can specify a simple SELECT statement to poll the Oracle database.</span></span> <span data-ttu-id="b563c-107">配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="b563c-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
- <span data-ttu-id="b563c-108">**使用預存程序**。</span><span class="sxs-lookup"><span data-stu-id="b563c-108">**Using stored procedures**.</span></span> <span data-ttu-id="b563c-109">您可以指定要輪詢 Oracle 資料庫的預存程序。</span><span class="sxs-lookup"><span data-stu-id="b563c-109">You can specify a stored procedure to poll the Oracle database.</span></span> <span data-ttu-id="b563c-110">配接器會在指定的時間間隔執行預存程序，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="b563c-110">The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.</span></span>  
  
  <span data-ttu-id="b563c-111">中的兩種方法的主要差異是方式配接器用戶端指定用來輪詢 Oracle 資料庫的配接器輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="b563c-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="b563c-112">簡單的 SELECT 陳述式的第一個方法的輪詢陳述式時，預存程序方法的輪詢陳述式就會是執行預存程序的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b563c-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure.</span></span> <span data-ttu-id="b563c-113">配接器用戶端指定任一種方法，輪詢陳述式，如**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b563c-113">Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property.</span></span> <span data-ttu-id="b563c-114">如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b563c-114">For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
  <span data-ttu-id="b563c-115">在本節中的主題會提供指示，有關如何使用 SELECT 陳述式和預存程序進行輪詢。</span><span class="sxs-lookup"><span data-stu-id="b563c-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b563c-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="b563c-116">In This Section</span></span>  
  
-   [<span data-ttu-id="b563c-117">使用 SELECT 陳述式使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="b563c-117">Poll Oracle E-Business Suite using SELECT statement with the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="b563c-118">預存程序使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="b563c-118">Poll Oracle E-Business Suite using stored procedures with the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="b563c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b563c-119">See Also</span></span>  
 [<span data-ttu-id="b563c-120">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="b563c-120">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)