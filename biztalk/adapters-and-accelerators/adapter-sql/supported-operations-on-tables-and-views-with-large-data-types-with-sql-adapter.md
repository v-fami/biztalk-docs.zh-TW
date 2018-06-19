---
title: 資料表和檢視表包含使用 SQL 配接器的大型資料類型上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70f3b863-da3c-45b0-98f2-469a62286ebf
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1d6d2c52ce0772297bb2834c13f31a55d7b7a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223862"
---
# <a name="operations-on-tables-and-views-that-contain-large-data-types-using-the-sql-adapter"></a><span data-ttu-id="d96ce-102">資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業</span><span class="sxs-lookup"><span data-stu-id="d96ce-102">Operations on tables and views that contain large data types using the SQL adapter</span></span>
<span data-ttu-id="d96ce-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]提供支援下列 SQL Server 的大型資料類型：</span><span class="sxs-lookup"><span data-stu-id="d96ce-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] provides supports for the following SQL Server large data types:</span></span>  
  
-   <span data-ttu-id="d96ce-104">Varchar （max)</span><span class="sxs-lookup"><span data-stu-id="d96ce-104">Varchar(Max)</span></span>  
  
-   <span data-ttu-id="d96ce-105">Nvarchar （max)</span><span class="sxs-lookup"><span data-stu-id="d96ce-105">Nvarchar(Max)</span></span>  
  
-   <span data-ttu-id="d96ce-106">Varbinary （max)</span><span class="sxs-lookup"><span data-stu-id="d96ce-106">Varbinary(Max)</span></span>  
  
 <span data-ttu-id="d96ce-107">若要從 SQL Server，讀取大型資料值[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開選取的作業。</span><span class="sxs-lookup"><span data-stu-id="d96ce-107">To read large data values from SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Select operation.</span></span>  
  
 <span data-ttu-id="d96ce-108">若要將大型資料值寫入至 SQL Server[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開組 < column_name > 作業，其中 < column_name > 是類型 varchar （max）、 nvarchar （max） 或 varbinary （max） 資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="d96ce-108">To write large data values to SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Set<column_name> operation, where <column_name> is the name of the column of type Varchar(Max), Nvarchar(Max) or Varbinary(Max).</span></span> <span data-ttu-id="d96ce-109">設定 < column_name > 作業也可讓配接器來寫入 SQL Server 2008 中的 FILESTREAM 資料的用戶端。</span><span class="sxs-lookup"><span data-stu-id="d96ce-109">The Set<column_name> operation also allows adapter clients to write FILESTREAM data in SQL Server 2008.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d96ce-110">設定 < column_name > 作業是僅供那些資料表和檢視表包含與任何先前所述的三種大型資料類型資料行。</span><span class="sxs-lookup"><span data-stu-id="d96ce-110">The Set<column_name> operation is available only for those tables and views that contain columns with any of the three large data types mentioned earlier.</span></span>  
  
 <span data-ttu-id="d96ce-111">如需執行包含大型資料類型的 SQL Server 中的資料表和檢視表上的作業的詳細資訊，請參閱[資料表和檢視表包含使用 SQL 配接器的大型資料類型上的作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d96ce-111">For detailed information about performing operations on tables and views in SQL Server that contain large data types, see [Operations on tables and views that contain large data types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d96ce-112">See Also</span></span>  
 [<span data-ttu-id="d96ce-113">連接至 SAP 系統使用配接器</span><span class="sxs-lookup"><span data-stu-id="d96ce-113">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)