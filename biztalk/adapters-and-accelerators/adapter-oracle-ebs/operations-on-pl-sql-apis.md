---
title: PL-SQL Api 上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d47b894d-1047-48ed-8f8c-865c343a12db
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5462bc4b4d6ee6a55e0e14d3ca9fccabc4dc2daf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216006"
---
# <a name="operations-on-plsql-apis"></a><span data-ttu-id="e4505-102">PL/SQL 應用程式開發介面作業</span><span class="sxs-lookup"><span data-stu-id="e4505-102">Operations on PL/SQL APIs</span></span>
<span data-ttu-id="e4505-103">Oracle E-business Suite 提供一組的 PL/SQL 封裝函式和預存程序的形式的 Api。</span><span class="sxs-lookup"><span data-stu-id="e4505-103">Oracle E-Business Suite provides a set of PL/SQL APIs in the form of packaged functions and stored procedures.</span></span> <span data-ttu-id="e4505-104">這些封裝函式，並且顯示程序中的作業為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e4505-104">These packaged functions and procedures are surfaced as operations in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span></span> 

## <a name="plsql-apis-are-grouped-by-schema-names"></a><span data-ttu-id="e4505-105">依結構描述名稱分組的 PL/SQL 應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="e4505-105">PL/SQL APIs are grouped by schema names</span></span> 
<span data-ttu-id="e4505-106">PL/SQL 應用程式開發介面會依照下的結構描述名稱**成品為基礎的檢視**和**結構描述為基礎的檢視**節點，當您連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4505-106">The PL/SQL APIs are grouped by schema names under the **Artifact-Based View** and **Schema-Based View** nodes when you connect to Oracle E-Business Suite using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="e4505-107">如需有關瀏覽中的 PL/SQL Api 資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[瀏覽、 搜尋和 Oracle E-business 作業取得中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="e4505-107">For information about browsing the PL/SQL APIs in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Browse, Search, and get Metadata for Oracle E-Business Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).</span></span>  
  
 <span data-ttu-id="e4505-108">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示與 Oracle 資料庫，以及在 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL Api**成品為基礎的檢視**和**結構描述為基礎的檢視**節點。</span><span class="sxs-lookup"><span data-stu-id="e4505-108">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] displays the PL/SQL APIs associated with the Oracle database as well as the applications in Oracle E-Business Suite under the **Artifact-Based View** and **Schema-Based View** nodes.</span></span>  
  
## <a name="important-info"></a><span data-ttu-id="e4505-109">重要資訊</span><span class="sxs-lookup"><span data-stu-id="e4505-109">Important info</span></span>
  -   <span data-ttu-id="e4505-110">您可以執行 PL/SQL 應用程式開發介面與 Oracle E-business Suite 中的應用程式相關聯的作業之前，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="e4505-110">Before you can perform operations on PL/SQL APIs associated with applications in Oracle E-Business Suite, you must set the applications context.</span></span> <span data-ttu-id="e4505-111">這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。</span><span class="sxs-lookup"><span data-stu-id="e4505-111">This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact.</span></span> <span data-ttu-id="e4505-112">不過，它是選擇性設定適用於 Oracle 資料庫與相關聯的 PL/SQL Api 的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="e4505-112">However, it is optional to set the applications context for PL/SQL APIs associated with Oracle database.</span></span> <span data-ttu-id="e4505-113">請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="e4505-113">See [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  

-   <span data-ttu-id="e4505-114">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]無法確定不論是否在使用 oracle 的 PL/SQL 應用程式開發介面中之參數指派預設值。</span><span class="sxs-lookup"><span data-stu-id="e4505-114">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] cannot ascertain whether or not a default value is assigned for a parameter in a PL/SQL API in Oracle.</span></span>  <span data-ttu-id="e4505-115">此外，配接器也無法確定是否要將參數定義為強制性或選擇性在 Oracle 的 PL/SQL 應用程式開發介面中。</span><span class="sxs-lookup"><span data-stu-id="e4505-115">Moreover, the adapter also cannot ascertain whether a parameter is defined as mandatory or optional in a PL/SQL API in Oracle.</span></span> <span data-ttu-id="e4505-116">配接器會將每個參數視為選擇性參數，而且如果未指定值參數的：</span><span class="sxs-lookup"><span data-stu-id="e4505-116">The adapter treats every parameter as an optional parameter, and if no value is specified for a parameter that:</span></span>  

    -   <span data-ttu-id="e4505-117">有了 default 值中指定的 Oracle，則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="e4505-117">Has a default value specified in Oracle then the default value is used.</span></span>  
    -   <span data-ttu-id="e4505-118">被定義為必要參數，在 Oracle 中的例外狀況就會擲回。</span><span class="sxs-lookup"><span data-stu-id="e4505-118">Is defined as a mandatory parameter in Oracle then an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4505-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4505-119">See Also</span></span>  
 <span data-ttu-id="e4505-120">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e4505-120">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>