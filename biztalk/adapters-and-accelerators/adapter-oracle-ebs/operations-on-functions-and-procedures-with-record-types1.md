---
title: 函數和程序的記錄 Types1 上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afc1c84f-2e36-493c-9ea8-4bc2248331db
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43974d1c392a357b9781ff7f6fae5286e282513a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216078"
---
# <a name="operations-on-functions-and-procedures-with-record-types"></a><span data-ttu-id="a2673-102">函數和程序的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="a2673-102">Operations on Functions and Procedures with RECORD Types</span></span>
<span data-ttu-id="a2673-103">Oracle 記錄類型可用來代表階層式參數傳遞至 PL/SQL 函數和程序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2673-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="a2673-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現記錄類型為複雜的 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="a2673-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> 

## <a name="supported-record-types"></a><span data-ttu-id="a2673-105">支援的記錄類型</span><span class="sxs-lookup"><span data-stu-id="a2673-105">Supported RECORD types</span></span>
<span data-ttu-id="a2673-106">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援下列幾種記錄類型：</span><span class="sxs-lookup"><span data-stu-id="a2673-106">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="a2673-107">記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="a2673-107">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="a2673-108">宣告類型的記錄中當做參數的 PL/SQL 封裝的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="a2673-108">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages.</span></span> <span data-ttu-id="a2673-109">例如，輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));</span><span class="sxs-lookup"><span data-stu-id="a2673-109">For example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));</span></span>  
  
-   <span data-ttu-id="a2673-110">包含巢狀的記錄的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="a2673-110">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="a2673-111">記錄中出現的類型為，逾時或在 OUT 參數的程序或函式。</span><span class="sxs-lookup"><span data-stu-id="a2673-111">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="a2673-112">傳回值的函式的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="a2673-112">RECORD types that are RETURN values of functions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2673-113">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 BFILE 做為記錄成員的類型。</span><span class="sxs-lookup"><span data-stu-id="a2673-113">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2673-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2673-114">See Also</span></span>  
 <span data-ttu-id="a2673-115">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="a2673-115">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>