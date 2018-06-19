---
title: 叫用預存程序，在 SQL 中使用 WCF 服務模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4edd2fac-0b54-4406-932e-e3044a66b2e6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2d707c37ba92fb6f1d1608ae43d02d1e964cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222286"
---
# <a name="invoke-stored-procedures-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="2137f-102">叫用預存程序，在 SQL 中使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="2137f-102">Invoke Stored Procedures in SQL using the WCF Service Model</span></span>
<span data-ttu-id="2137f-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]探索預存程序做為配接器用戶端可以叫用預存程序將 WCF 用戶端上叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="2137f-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers the stored procedures as operations that the adapter clients can invoke on the WCF client to invoke the stored procedure.</span></span> <span data-ttu-id="2137f-104">根據預存程序傳回結果集的方式，配接器來分類做為所有預存程序：</span><span class="sxs-lookup"><span data-stu-id="2137f-104">Based on how the stored procedure returns the result set, the adapter categorizes all the stored procedures as:</span></span>  
  
-   <span data-ttu-id="2137f-105">**程序**。</span><span class="sxs-lookup"><span data-stu-id="2137f-105">**Procedures**.</span></span> <span data-ttu-id="2137f-106">叫用預存程序從**程序**節點會傳回資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="2137f-106">Invoking stored procedures from the **Procedures** node returns an array of DataSet.</span></span>  
  
-   <span data-ttu-id="2137f-107">**強型別程序**。</span><span class="sxs-lookup"><span data-stu-id="2137f-107">**Strongly-Typed Procedures**.</span></span> <span data-ttu-id="2137f-108">叫用預存程序從**Strongly-Typed 程序**節點會傳回強型別之結果集。</span><span class="sxs-lookup"><span data-stu-id="2137f-108">Invoking stored procedures from the **Strongly-Typed Procedures** node returns a strongly-typed result set.</span></span>  
  
 <span data-ttu-id="2137f-109">請注意，同一組連接到資料庫中的預存程序將會列出兩下**程序**和**Strongly-Typed 程序**節點。</span><span class="sxs-lookup"><span data-stu-id="2137f-109">Note that the same set of stored procedures in the database you connected to will be listed both under the **Procedures** and **Strongly-Typed Procedures** node.</span></span> <span data-ttu-id="2137f-110">根據您想要的結果集類型，您必須叫用預存程序，從相關的節點。</span><span class="sxs-lookup"><span data-stu-id="2137f-110">Based on the kind of result set you want, you must invoke the stored procedure from the relevant node.</span></span> <span data-ttu-id="2137f-111">如需有關如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援預存程序，請參閱[使用 BizTalk Server 的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2137f-111">For more information about how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports stored procedures, see [Execute Stored Procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="2137f-112">本節說明如何叫用預存程序，同時從**程序**和**Strongly-Typed 程序**使用 WCF 用戶端的節點。</span><span class="sxs-lookup"><span data-stu-id="2137f-112">This section provides instructions on how to invoke stored procedures from both the **Procedures** and **Strongly-Typed Procedures** node by using a WCF client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2137f-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="2137f-113">In This Section</span></span>  
  
-   [<span data-ttu-id="2137f-114">Involk 弱型別中使用 WCF 服務模型的 SQL 預存程序</span><span class="sxs-lookup"><span data-stu-id="2137f-114">Involk Weakly-typed Stored Procedures in SQL Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="2137f-115">叫用強型別使用 WCF 服務模型的 SQL 中的預存程序</span><span class="sxs-lookup"><span data-stu-id="2137f-115">Invoke Strongly-typed Stored Procedure in SQL Using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="2137f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2137f-116">See Also</span></span>  
[<span data-ttu-id="2137f-117">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="2137f-117">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)