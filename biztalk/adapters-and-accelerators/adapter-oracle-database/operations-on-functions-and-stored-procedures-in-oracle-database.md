---
title: 函式和 Oracle 資料庫中的預存程序上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- REF CURSOR
- packaged functions and procedures
- operations, on functions and stored procedures
- stored procedure
- RECORD type
- overloaded functions and procedures
ms.assetid: 18072b58-65b2-4da5-9433-ea0da4e2d4f4
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78181aae7921cad3996e4bd408e604857a2bd15e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214950"
---
# <a name="operations-on-functions-and-stored-procedures-in-oracle-database"></a><span data-ttu-id="f79b2-102">函式和 Oracle 資料庫中的預存程序的作業</span><span class="sxs-lookup"><span data-stu-id="f79b2-102">Operations on functions and stored procedures in Oracle Database</span></span>
<span data-ttu-id="f79b2-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 函數、 程序和封裝，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="f79b2-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports Oracle functions, procedures, and packages in the following manner:</span></span>  
  
-   <span data-ttu-id="f79b2-104">**函式**當成作業。</span><span class="sxs-lookup"><span data-stu-id="f79b2-104">**Functions** are surfaced as operations.</span></span> <span data-ttu-id="f79b2-105">作業名稱是 Oracle 函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="f79b2-105">The name of the operation is the name of the Oracle function.</span></span> <span data-ttu-id="f79b2-106">在 OUT、 出參數都有支援，以及，傳回值。</span><span class="sxs-lookup"><span data-stu-id="f79b2-106">IN, OUT, and IN OUT parameters are supported, as well as, RETURN values.</span></span>  
  
-   <span data-ttu-id="f79b2-107">**程序**當成作業。</span><span class="sxs-lookup"><span data-stu-id="f79b2-107">**Procedures** are surfaced as operations.</span></span> <span data-ttu-id="f79b2-108">作業名稱是 Oracle 程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="f79b2-108">The name of the operation is the name of the Oracle procedure.</span></span> <span data-ttu-id="f79b2-109">OUT、] 和 [出支援參數。</span><span class="sxs-lookup"><span data-stu-id="f79b2-109">IN, OUT, and IN OUT parameters are supported.</span></span>  
  
-   <span data-ttu-id="f79b2-110">**包裝函數和程序**當成作業。</span><span class="sxs-lookup"><span data-stu-id="f79b2-110">**Packaged functions and procedures** are surfaced as operations.</span></span> <span data-ttu-id="f79b2-111">Oracle 封裝的名稱限定的名稱和命名空間的作業 （函式或程序）。</span><span class="sxs-lookup"><span data-stu-id="f79b2-111">The name and namespace of the operation (function or procedure) is qualified by the name of the Oracle package.</span></span> <span data-ttu-id="f79b2-112">多載支援 （請參閱下一個項目符號） 的封裝中。</span><span class="sxs-lookup"><span data-stu-id="f79b2-112">Overloads are supported in packages (see next bullet).</span></span>  
  
-   <span data-ttu-id="f79b2-113">**多載函式和程序**在封裝中當成作業。</span><span class="sxs-lookup"><span data-stu-id="f79b2-113">**Overloaded functions and procedures** in packages are surfaced as operations.</span></span> <span data-ttu-id="f79b2-114">每個多載函式或程序會顯示與字串附加至其識別的多載的名稱。</span><span class="sxs-lookup"><span data-stu-id="f79b2-114">Each overloaded function or procedure is surfaced with a string appended to its name that identifies the overload.</span></span> <span data-ttu-id="f79b2-115">此字串是組件的順序"overload1"、"overload2"、"overload3"，等等。</span><span class="sxs-lookup"><span data-stu-id="f79b2-115">This string is part of the sequence "overload1", "overload2", "overload3", and so on.</span></span>  
  
-   <span data-ttu-id="f79b2-116">**REF CURSOR 類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。</span><span class="sxs-lookup"><span data-stu-id="f79b2-116">**REF CURSOR types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="f79b2-117">如需詳細資訊，請參閱[函式和有 REF CURSOR 參數的程序上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。</span><span class="sxs-lookup"><span data-stu-id="f79b2-117">For more information, see [Operations on Functions and Procedures with REF CURSOR Parameters](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).</span></span>  
  
-   <span data-ttu-id="f79b2-118">**記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式傳回值。</span><span class="sxs-lookup"><span data-stu-id="f79b2-118">**RECORD types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="f79b2-119">支援簡單和複雜 （巢狀） 的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="f79b2-119">Both simple and complex (nested) RECORD types are supported.</span></span> [<span data-ttu-id="f79b2-120">函數和程序的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="f79b2-120">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
 <span data-ttu-id="f79b2-121">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="f79b2-121">For more information about:</span></span>  
  
-   <span data-ttu-id="f79b2-122">透過使用叫用 Oracle 程序或函數[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[叫用函數及使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)和[叫用多載函式和 Oracle 資料庫中的程序BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f79b2-122">Invoking an Oracle procedure or function by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md) and [Invoke Overload Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f79b2-123">叫用 Oracle 程序或函式使用 WCF 服務模型，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="f79b2-123">Invoking an Oracle procedure or function by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="f79b2-124">叫用 Oracle 程序或函式使用 WCF 通道模型，請參閱[叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="f79b2-124">Invoking an Oracle procedure or function by using the WCF channel model, see [Invoke a Function in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
-   <span data-ttu-id="f79b2-125">訊息結構和用來叫用 Oracle 程序和函式，請參閱的 SOAP 動作[函數和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f79b2-125">Message structure and SOAP actions used to invoke Oracle procedures and functions, see [Message Schemas for Functions and Procedures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79b2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f79b2-126">See Also</span></span>  
 <span data-ttu-id="f79b2-127">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="f79b2-127">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>