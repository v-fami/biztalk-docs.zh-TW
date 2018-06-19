---
title: 使用 SQL 配接器的 SQL Server 中執行純量函數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ef70114-215e-49ed-87d2-7590db605a2c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbd039039535f87ef32ec86bfc6bc982ced4210
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222166"
---
# <a name="execute-scalar-functions-in-sql-server-using-the-sql-adapter"></a><span data-ttu-id="07999-102">使用 SQL 配接器的 SQL Server 中執行純量函數</span><span class="sxs-lookup"><span data-stu-id="07999-102">Execute Scalar Functions in SQL Server using the SQL adapter</span></span>
<span data-ttu-id="07999-103">SQL Server 中的 TRANSACT-SQL 和 CLR 純量函數當成作業[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07999-103">The Transact-SQL and CLR scalar functions in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="07999-104">中的作業名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL Server 中的純量函式名稱相同。</span><span class="sxs-lookup"><span data-stu-id="07999-104">The operation name in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the name of the scalar function in SQL Server.</span></span>  
  
 <span data-ttu-id="07999-105">純量函數中的所有參數會都公開在對應的作業。</span><span class="sxs-lookup"><span data-stu-id="07999-105">All the parameters in the scalar function are exposed in the corresponding operation.</span></span> <span data-ttu-id="07999-106">傳回值中的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL Server 中的純量函式中定義的傳回值相同。</span><span class="sxs-lookup"><span data-stu-id="07999-106">The return value of the operation in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the return value defined in the scalar function in SQL Server.</span></span>  
  
 <span data-ttu-id="07999-107">如需執行純量函數的詳細資訊，請參閱[叫用使用 BizTalk Server 的 SQL Server 中的純量函式](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07999-107">For more information about executing scalar functions, see [Invoke Scalar Functions in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07999-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07999-108">See Also</span></span>  
 [<span data-ttu-id="07999-109">連接至 SAP 系統使用配接器</span><span class="sxs-lookup"><span data-stu-id="07999-109">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)