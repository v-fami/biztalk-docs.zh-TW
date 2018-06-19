---
title: 函式和預存的 Procedures1 上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e6bdaa7-ed3c-43bc-bed5-70fe43f9c2d1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe5f705c8e432c920c8fae41a2b2f050c188047
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216350"
---
# <a name="operations-on-functions-and-stored-procedures"></a><span data-ttu-id="9c469-102">函式和預存程序的作業</span><span class="sxs-lookup"><span data-stu-id="9c469-102">Operations on Functions and Stored Procedures</span></span>
<span data-ttu-id="9c469-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函式和程序。</span><span class="sxs-lookup"><span data-stu-id="9c469-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports Oracle functions and procedures.</span></span>

## <a name="functions-and-procedures"></a><span data-ttu-id="9c469-104">函數和程序</span><span class="sxs-lookup"><span data-stu-id="9c469-104">Functions and procedures</span></span>

<span data-ttu-id="9c469-105">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援 Oracle 函數和程序如下：</span><span class="sxs-lookup"><span data-stu-id="9c469-105">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports Oracle functions and procedures in the following manner:</span></span>  
  
-   <span data-ttu-id="9c469-106">**函式**當成作業。</span><span class="sxs-lookup"><span data-stu-id="9c469-106">**Functions** are surfaced as operations.</span></span> <span data-ttu-id="9c469-107">作業名稱是 Oracle 函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c469-107">The name of the operation is the name of the Oracle function.</span></span> <span data-ttu-id="9c469-108">在 OUT、 出參數都有支援，以及，傳回值。</span><span class="sxs-lookup"><span data-stu-id="9c469-108">IN, OUT, and IN OUT parameters are supported, as well as, RETURN values.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9c469-109">如果您的函式中傳遞了無效的參數 （也就是傳遞的數值欄位的字串值），[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可能會擲回例外狀況根據 ODP.NET 的行為。</span><span class="sxs-lookup"><span data-stu-id="9c469-109">If you pass an invalid parameter in a function (that is, pass a string value for a numeric field), the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] might throw an exception depending on the ODP.NET behavior.</span></span> <span data-ttu-id="9c469-110">這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 ODP.NET Oracle E-business Suite 與通訊。</span><span class="sxs-lookup"><span data-stu-id="9c469-110">This is because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses ODP.NET to communicate with Oracle E-Business Suite.</span></span>  
  
-   <span data-ttu-id="9c469-111">**程序**當成作業。</span><span class="sxs-lookup"><span data-stu-id="9c469-111">**Procedures** are surfaced as operations.</span></span> <span data-ttu-id="9c469-112">作業名稱是 Oracle 程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c469-112">The name of the operation is the name of the Oracle procedure.</span></span> <span data-ttu-id="9c469-113">OUT、] 和 [出支援參數。</span><span class="sxs-lookup"><span data-stu-id="9c469-113">IN, OUT, and IN OUT parameters are supported.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9c469-114">在程序，如果您插入或更新的介面資料表或資料庫資料表中數值欄位的十進位值 (例如，15.2)[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9c469-114">As part of a procedure, if you insert or update a decimal value (for example, 15.2) into a numeric field of an interface table or database table, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] will throw an exception.</span></span> <span data-ttu-id="9c469-115">這是因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用利用 Oracle E-business Suite，通訊 ODP.NET 和 ODP.NET 不支援接受的數值欄位的十進位值。</span><span class="sxs-lookup"><span data-stu-id="9c469-115">This is because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses ODP.NET to communicate with Oracle E-Business Suite, and ODP.NET does not support accepting decimal values for the numeric fields.</span></span>  
  
-   <span data-ttu-id="9c469-116">**REF CURSOR 類型**支援 IN 和 OUT 參數的程序和函式，以及函式傳回值。</span><span class="sxs-lookup"><span data-stu-id="9c469-116">**REF CURSOR types** are supported for IN and OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="9c469-117">如需詳細資訊，請參閱[函式和有 REF CURSOR 參數的程序上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。</span><span class="sxs-lookup"><span data-stu-id="9c469-117">For more information, see [Operations on Functions and Procedures with REF CURSOR Parameters](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).</span></span>  
  
-   <span data-ttu-id="9c469-118">**記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。</span><span class="sxs-lookup"><span data-stu-id="9c469-118">**RECORD types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="9c469-119">支援簡單和複雜 （巢狀） 的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="9c469-119">Both simple and complex (nested) RECORD types are supported.</span></span> [<span data-ttu-id="9c469-120">函數和程序的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="9c469-120">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
> [!NOTE]
>  <span data-ttu-id="9c469-121">您也可以設定函式和預存程序中的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9c469-121">You can also set the application context for functions and stored procedures in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="9c469-122">應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="9c469-122">For information about application context, and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c469-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c469-123">See Also</span></span>  
 <span data-ttu-id="9c469-124">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="9c469-124">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>