---
title: ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援 |Microsoft 文件
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
ms.openlocfilehash: 40bad547627669bb22a6b32f05d96c6c7b2f68c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215718"
---
# <a name="support-for-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="fb5a5-102">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的支援</span><span class="sxs-lookup"><span data-stu-id="fb5a5-102">Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>
<span data-ttu-id="fb5a5-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開下列的輸出作業根層級：</span><span class="sxs-lookup"><span data-stu-id="fb5a5-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes the following outbound operations at the root level:</span></span>  
  
-   <span data-ttu-id="fb5a5-104">**ExecuteNonQuery**： 使用這項作業，任何任意的 SQL 陳述式或 PL/SQL 封鎖執行 Oracle E-business Suite 中，如果您想要傳回多個結果集。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-104">**ExecuteNonQuery**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want to return multiple result sets.</span></span> <span data-ttu-id="fb5a5-105">此函式的輸入的參數會包含字串參數 （整個 PL/SQL 區塊執行） 和字串 (OutRefCursorNames) 的陣列。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-105">The input parameters of this function include a string parameter (the entire PL/SQL block to be executed) and an array of strings (OutRefCursorNames).</span></span> <span data-ttu-id="fb5a5-106">每個 OutRefCursorNames 中指定的字串值會假設與具有相同名稱傳回 REF CURSOR 的 PL/SQL 區塊的 REF CURSOR 輸出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-106">Each string value specified in OutRefCursorNames is assumed to be the parameter name of an output REF CURSOR with the PL/SQL block returning REF CURSORS with the same names.</span></span> <span data-ttu-id="fb5a5-107">此函式也會為 OUT 參數 (OutRefCursors)，也就是資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-107">This function also takes an OUT parameter (OutRefCursors), which is an array of DataSets.</span></span> <span data-ttu-id="fb5a5-108">資料集的相關資訊，請參閱 Oracle 文件，網址[http://go.microsoft.com/fwlink/?LinkId=124538](http://go.microsoft.com/fwlink/?LinkId=124538)。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-108">For information about DataSet, consult the Oracle documentation at [http://go.microsoft.com/fwlink/?LinkId=124538](http://go.microsoft.com/fwlink/?LinkId=124538).</span></span> <span data-ttu-id="fb5a5-109">這項作業的傳回值是整數資料類型，並指出受影響的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-109">The return value of this operation is of integer data type, and indicates the number of affected rows.</span></span>  
  
-   <span data-ttu-id="fb5a5-110">**ExecuteReader**： 使用這項作業，任何任意的 SQL 陳述式或 PL/SQL 封鎖執行 Oracle E-business Suite 中，如果您想要做為資料集傳回的結果集。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-110">**ExecuteReader**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want the result set to be returned as DataSet.</span></span> <span data-ttu-id="fb5a5-111">這項作業接受字串參數做為輸入，並傳回資料集。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-111">This operation takes a string parameter as input, and returns a DataSet.</span></span>  
  
-   <span data-ttu-id="fb5a5-112">**ExecuteScalar**： 使用這項作業，任何任意的 SQL 陳述式或 PL/SQL 封鎖執行 Oracle E-business Suite 中，如果您想要傳回只有一個值。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-112">**ExecuteScalar**: Use this operation to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite if you want only one value to be returned.</span></span> <span data-ttu-id="fb5a5-113">如果結果集傳回的值，第一個資料列的第一個資料行中的值會傳回 XML 字串格式。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-113">If the return value is a result set, only the value in the first column of the first row is returned in a XML string format.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="fb5a5-114">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業不支援使用者定義型別 (Udt)。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-114">The ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations are not supported for the User Defined Types (UDTs).</span></span>  
> -   <span data-ttu-id="fb5a5-115">您也可以設定應用程式內容中的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-115">You can also set the applications context for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="fb5a5-116">它是強制設定 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的應用程式內容，如果任何作業的目標 （介面資料表、 檢視介面、 同時執行的程式或要求 Oracle E-business Suite 中的成品設定）。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-116">It is mandatory to set the applications context for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations if any of the operation is targeted on an artifact in Oracle E-Business Suite (interface table, interface view, concurrent programs or request sets).</span></span> <span data-ttu-id="fb5a5-117">應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="fb5a5-117">For information about applications context, and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5a5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb5a5-118">See Also</span></span>  
 <span data-ttu-id="fb5a5-119">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="fb5a5-119">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>