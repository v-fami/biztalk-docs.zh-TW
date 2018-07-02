---
title: 支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afdd1a5b-2a6b-48b8-a659-afd81f43f34b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592c61fd821920656cc12744f290505828cadcd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981367"
---
# <a name="support-for-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="25c16-102">支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業</span><span class="sxs-lookup"><span data-stu-id="25c16-102">Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>
<span data-ttu-id="25c16-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開下列的輸出作業的根層級：</span><span class="sxs-lookup"><span data-stu-id="25c16-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes the following outbound operations at the root level:</span></span>  
  
-   <span data-ttu-id="25c16-104">**ExecuteNonQuery**： 使用任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要傳回多個結果集的這項作業。</span><span class="sxs-lookup"><span data-stu-id="25c16-104">**ExecuteNonQuery**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want to return multiple result sets.</span></span> <span data-ttu-id="25c16-105">此函式的輸入的參數包含字串參數 （整個 PL/SQL 區塊執行） 和字串 (OutRefCursorNames) 陣列。</span><span class="sxs-lookup"><span data-stu-id="25c16-105">The input parameters of this function include a string parameter (the entire PL/SQL block to be executed) and an array of strings (OutRefCursorNames).</span></span> <span data-ttu-id="25c16-106">OutRefCursorNames 中指定每個字串值會假設為與具有相同名稱傳回 REF CURSOR 的 PL/SQL 區塊的 REF CURSOR 輸出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="25c16-106">Each string value specified in OutRefCursorNames is assumed to be the parameter name of an output REF CURSOR with the PL/SQL block returning REF CURSORS with the same names.</span></span> <span data-ttu-id="25c16-107">此函式也會為 OUT 參數 (OutRefCursors)，也就是資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="25c16-107">This function also takes an OUT parameter (OutRefCursors), which is an array of DataSets.</span></span> <span data-ttu-id="25c16-108">資料集的相關資訊，請參閱 Oracle 文件[ http://go.microsoft.com/fwlink/?LinkId=124538 ](http://go.microsoft.com/fwlink/?LinkId=124538)。</span><span class="sxs-lookup"><span data-stu-id="25c16-108">For information about DataSet, consult the Oracle documentation at [http://go.microsoft.com/fwlink/?LinkId=124538](http://go.microsoft.com/fwlink/?LinkId=124538).</span></span> <span data-ttu-id="25c16-109">這項作業的傳回值是整數資料類型，並指出受影響的資料列數。</span><span class="sxs-lookup"><span data-stu-id="25c16-109">The return value of this operation is of integer data type, and indicates the number of affected rows.</span></span>  
  
-   <span data-ttu-id="25c16-110">**ExecuteReader**： 任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要的結果集傳回的資料集使用此作業。</span><span class="sxs-lookup"><span data-stu-id="25c16-110">**ExecuteReader**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want the result set to be returned as DataSet.</span></span> <span data-ttu-id="25c16-111">此作業會接受字串參數做為輸入，並傳回資料集。</span><span class="sxs-lookup"><span data-stu-id="25c16-111">This operation takes a string parameter as input, and returns a DataSet.</span></span>  
  
-   <span data-ttu-id="25c16-112">**ExecuteScalar**： 使用此操作將任何任意的 SQL 陳述式或 PL/SQL 區塊執行 Oracle E-business Suite 中，如果您想要傳回的只有一個值。</span><span class="sxs-lookup"><span data-stu-id="25c16-112">**ExecuteScalar**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want only one value to be returned.</span></span> <span data-ttu-id="25c16-113">如果結果集傳回的值，只有第一個資料列的第一個資料行中的值會傳回 XML 字串格式。</span><span class="sxs-lookup"><span data-stu-id="25c16-113">If the return value is a result set, only the value in the first column of the first row is returned in a XML string format.</span></span>  
  
> [!NOTE]
> - <span data-ttu-id="25c16-114">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業不支援使用者定義型別 (Udt)。</span><span class="sxs-lookup"><span data-stu-id="25c16-114">The ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations are not supported for the User Defined Types (UDTs).</span></span>  
>   - <span data-ttu-id="25c16-115">您也可以設定中的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="25c16-115">You can also set the applications context for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="25c16-116">它是必要設定的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容，如果任一項作業的目標 （介面資料表、 介面檢視、 同時執行的程式或要求，Oracle E-business Suite 中的成品設定）。</span><span class="sxs-lookup"><span data-stu-id="25c16-116">It is mandatory to set the applications context for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations if any of the operation is targeted on an artifact in Oracle E-Business Suite (interface table, interface view, concurrent programs or request sets).</span></span> <span data-ttu-id="25c16-117">應用程式內容，以及如何將它設定的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="25c16-117">For information about applications context, and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c16-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25c16-118">See Also</span></span>  
 <span data-ttu-id="25c16-119">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="25c16-119">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>