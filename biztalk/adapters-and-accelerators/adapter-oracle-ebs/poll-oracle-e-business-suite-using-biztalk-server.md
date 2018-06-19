---
title: 使用 BizTalk Server 輪詢 Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9b5d0743d39dfcf6cbab7e1da20a8a3fb1382fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218006"
---
# <a name="poll-oracle-e-business-suite-using-biztalk-server"></a><span data-ttu-id="35ca8-102">使用 BizTalk Server 輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="35ca8-102">Poll Oracle E-Business Suite using BizTalk Server</span></span>
<span data-ttu-id="35ca8-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 資料庫接收輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="35ca8-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from Oracle database.</span></span> <span data-ttu-id="35ca8-104">配接器會提供兩種輪詢 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="35ca8-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
-   <span data-ttu-id="35ca8-105">**使用 SELECT 陳述式**。</span><span class="sxs-lookup"><span data-stu-id="35ca8-105">**Using SELECT statements**.</span></span> <span data-ttu-id="35ca8-106">您可以指定簡單的 SELECT 陳述式，以輪詢 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="35ca8-106">You can specify a simple SELECT statement to poll the Oracle database.</span></span> <span data-ttu-id="35ca8-107">配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="35ca8-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
-   <span data-ttu-id="35ca8-108">**使用預存程序**。</span><span class="sxs-lookup"><span data-stu-id="35ca8-108">**Using stored procedures**.</span></span> <span data-ttu-id="35ca8-109">您可以指定輪詢 Oracle 資料庫的預存程序。</span><span class="sxs-lookup"><span data-stu-id="35ca8-109">You can specify a stored procedure to poll the Oracle database.</span></span> <span data-ttu-id="35ca8-110">配接器指定的間隔執行預存程序，並將結果傳回至配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="35ca8-110">The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.</span></span>  
  
 <span data-ttu-id="35ca8-111">兩種方法中的主要差異是方式配接器用戶端指定配接器輪詢 Oracle 資料庫所使用的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="35ca8-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="35ca8-112">簡單的 SELECT 陳述式的第一個方法的輪詢陳述式時，預存程序方法的輪詢陳述式是執行預存程序的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="35ca8-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure.</span></span> <span data-ttu-id="35ca8-113">配接器用戶端指定輪詢陳述式，兩種方法，如**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35ca8-113">Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property.</span></span> <span data-ttu-id="35ca8-114">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="35ca8-114">For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
 <span data-ttu-id="35ca8-115">此章節的主題提供如何輪詢使用 SELECT 陳述式和預存程序的指示。</span><span class="sxs-lookup"><span data-stu-id="35ca8-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35ca8-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="35ca8-116">In This Section</span></span>  
  
-   [<span data-ttu-id="35ca8-117">輪詢 Oracle E-business Suite 使用 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="35ca8-117">Poll Oracle E-Business Suite Using SELECT Statement</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [<span data-ttu-id="35ca8-118">輪詢 Oracle E-business Suite 使用預存程序</span><span class="sxs-lookup"><span data-stu-id="35ca8-118">Poll Oracle E-Business Suite Using Stored Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## <a name="see-also"></a><span data-ttu-id="35ca8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35ca8-119">See Also</span></span>  
[<span data-ttu-id="35ca8-120">開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器</span><span class="sxs-lookup"><span data-stu-id="35ca8-120">Develop BizTalk applications using the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)