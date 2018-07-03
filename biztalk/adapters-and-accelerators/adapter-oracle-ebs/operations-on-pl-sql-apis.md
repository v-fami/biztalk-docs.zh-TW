---
title: PL-SQL Api 作業 |Microsoft Docs
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
ms.openlocfilehash: 5719d74517331b30de986424bc14e7d01d128cf3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999343"
---
# <a name="operations-on-plsql-apis"></a><span data-ttu-id="ce77d-102">PL/SQL Api 的作業</span><span class="sxs-lookup"><span data-stu-id="ce77d-102">Operations on PL/SQL APIs</span></span>
<span data-ttu-id="ce77d-103">Oracle E-business Suite 會提供一組的 PL/SQL Api 中的封裝函式和預存程序的形式。</span><span class="sxs-lookup"><span data-stu-id="ce77d-103">Oracle E-Business Suite provides a set of PL/SQL APIs in the form of packaged functions and stored procedures.</span></span> <span data-ttu-id="ce77d-104">這些封裝函式，並顯示程序中的作業為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ce77d-104">These packaged functions and procedures are surfaced as operations in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span></span> 

## <a name="plsql-apis-are-grouped-by-schema-names"></a><span data-ttu-id="ce77d-105">PL/SQL Api 被依據結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="ce77d-105">PL/SQL APIs are grouped by schema names</span></span> 
<span data-ttu-id="ce77d-106">PL/SQL Api 按下的結構描述名稱分組**成品的檢視形式**並**結構描述為基礎的檢視**節點，當您連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce77d-106">The PL/SQL APIs are grouped by schema names under the **Artifact-Based View** and **Schema-Based View** nodes when you connect to Oracle E-Business Suite using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="ce77d-107">如需瀏覽中的 PL/SQL Api [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 瀏覽、 搜尋及取得 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ce77d-107">For information about browsing the PL/SQL APIs in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Browse, Search, and get Metadata for Oracle E-Business Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).</span></span>  
  
 <span data-ttu-id="ce77d-108">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示與 Oracle 資料庫，以及在 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL Api**成品的檢視形式**並**結構描述為基礎的檢視**節點。</span><span class="sxs-lookup"><span data-stu-id="ce77d-108">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] displays the PL/SQL APIs associated with the Oracle database as well as the applications in Oracle E-Business Suite under the **Artifact-Based View** and **Schema-Based View** nodes.</span></span>  
  
## <a name="important-info"></a><span data-ttu-id="ce77d-109">重要資訊</span><span class="sxs-lookup"><span data-stu-id="ce77d-109">Important info</span></span>
  -   <span data-ttu-id="ce77d-110">您可以執行 Oracle E-business Suite 中的應用程式相關聯的 PL/SQL api 的作業之前，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="ce77d-110">Before you can perform operations on PL/SQL APIs associated with applications in Oracle E-Business Suite, you must set the applications context.</span></span> <span data-ttu-id="ce77d-111">這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定和成品的存取控制有助於安全 Oracle E-business Suite 中的交易。</span><span class="sxs-lookup"><span data-stu-id="ce77d-111">This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact.</span></span> <span data-ttu-id="ce77d-112">不過，它是選擇性的以設定適用於 Oracle 資料庫與相關聯的 PL/SQL Api 的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="ce77d-112">However, it is optional to set the applications context for PL/SQL APIs associated with Oracle database.</span></span> <span data-ttu-id="ce77d-113">請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="ce77d-113">See [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  

- <span data-ttu-id="ce77d-114">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]無法確定是否在 Oracle 的 PL/SQL API 中的參數指派預設值。</span><span class="sxs-lookup"><span data-stu-id="ce77d-114">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] cannot ascertain whether or not a default value is assigned for a parameter in a PL/SQL API in Oracle.</span></span>  <span data-ttu-id="ce77d-115">此外，配接器也無法確定是否為強制或選擇性在 Oracle 的 PL/SQL API 中定義的參數。</span><span class="sxs-lookup"><span data-stu-id="ce77d-115">Moreover, the adapter also cannot ascertain whether a parameter is defined as mandatory or optional in a PL/SQL API in Oracle.</span></span> <span data-ttu-id="ce77d-116">配接器會將每個參數視為選擇性參數，而且如果未不指定任何值，參數的：</span><span class="sxs-lookup"><span data-stu-id="ce77d-116">The adapter treats every parameter as an optional parameter, and if no value is specified for a parameter that:</span></span>  

  -   <span data-ttu-id="ce77d-117">具有預設值中指定的 Oracle，則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="ce77d-117">Has a default value specified in Oracle then the default value is used.</span></span>  
  -   <span data-ttu-id="ce77d-118">定義為必要參數在 Oracle 中的例外狀況會擲回。</span><span class="sxs-lookup"><span data-stu-id="ce77d-118">Is defined as a mandatory parameter in Oracle then an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce77d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce77d-119">See Also</span></span>  
 <span data-ttu-id="ce77d-120">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ce77d-120">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>