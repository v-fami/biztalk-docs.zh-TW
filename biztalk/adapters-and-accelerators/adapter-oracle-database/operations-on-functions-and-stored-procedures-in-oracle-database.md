---
title: 函式和 Oracle 資料庫中的預存程序作業 |Microsoft Docs
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
ms.openlocfilehash: 856e6bf882605737380f0bbe6185dce8a56c5828
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979607"
---
# <a name="operations-on-functions-and-stored-procedures-in-oracle-database"></a><span data-ttu-id="e3e66-102">函式和 Oracle 資料庫中的預存程序作業</span><span class="sxs-lookup"><span data-stu-id="e3e66-102">Operations on functions and stored procedures in Oracle Database</span></span>
<span data-ttu-id="e3e66-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 函式、 程序，以及套件以下列方式：</span><span class="sxs-lookup"><span data-stu-id="e3e66-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports Oracle functions, procedures, and packages in the following manner:</span></span>  
  
- <span data-ttu-id="e3e66-104">**函式**當成作業。</span><span class="sxs-lookup"><span data-stu-id="e3e66-104">**Functions** are surfaced as operations.</span></span> <span data-ttu-id="e3e66-105">作業的名稱是 Oracle 函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3e66-105">The name of the operation is the name of the Oracle function.</span></span> <span data-ttu-id="e3e66-106">在外，和 OUT 參數都有支援，以及，傳回值。</span><span class="sxs-lookup"><span data-stu-id="e3e66-106">IN, OUT, and IN OUT parameters are supported, as well as, RETURN values.</span></span>  
  
- <span data-ttu-id="e3e66-107">**程序**當成作業。</span><span class="sxs-lookup"><span data-stu-id="e3e66-107">**Procedures** are surfaced as operations.</span></span> <span data-ttu-id="e3e66-108">作業的名稱是 Oracle 程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3e66-108">The name of the operation is the name of the Oracle procedure.</span></span> <span data-ttu-id="e3e66-109">在外，和 OUT 參數支援。</span><span class="sxs-lookup"><span data-stu-id="e3e66-109">IN, OUT, and IN OUT parameters are supported.</span></span>  
  
- <span data-ttu-id="e3e66-110">**包裝函式和程序**當成作業。</span><span class="sxs-lookup"><span data-stu-id="e3e66-110">**Packaged functions and procedures** are surfaced as operations.</span></span> <span data-ttu-id="e3e66-111">Oracle 封裝的名稱被限定的名稱和命名空間的作業 （函式或程序）。</span><span class="sxs-lookup"><span data-stu-id="e3e66-111">The name and namespace of the operation (function or procedure) is qualified by the name of the Oracle package.</span></span> <span data-ttu-id="e3e66-112">（請參閱下一步 的項目符號） 的套件支援多載。</span><span class="sxs-lookup"><span data-stu-id="e3e66-112">Overloads are supported in packages (see next bullet).</span></span>  
  
- <span data-ttu-id="e3e66-113">**多載的函式和程序**在封裝中顯示為作業。</span><span class="sxs-lookup"><span data-stu-id="e3e66-113">**Overloaded functions and procedures** in packages are surfaced as operations.</span></span> <span data-ttu-id="e3e66-114">每個多載函式或程序的呈現與識別此多載其名稱後面附加的字串。</span><span class="sxs-lookup"><span data-stu-id="e3e66-114">Each overloaded function or procedure is surfaced with a string appended to its name that identifies the overload.</span></span> <span data-ttu-id="e3e66-115">此字串是組件的順序 」 overload1"、"overload2 」、 「 overload3"，等等。</span><span class="sxs-lookup"><span data-stu-id="e3e66-115">This string is part of the sequence "overload1", "overload2", "overload3", and so on.</span></span>  
  
- <span data-ttu-id="e3e66-116">**REF CURSOR 類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="e3e66-116">**REF CURSOR types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="e3e66-117">如需詳細資訊，請參閱 <<c0> [ 函式和含有 REF CURSOR 參數的程序作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e66-117">For more information, see [Operations on Functions and Procedures with REF CURSOR Parameters](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).</span></span>  
  
- <span data-ttu-id="e3e66-118">**記錄類型**IN、 支援，而在 OUT 參數的程序和函式，以及函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="e3e66-118">**RECORD types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values.</span></span> <span data-ttu-id="e3e66-119">支援簡單和複雜 （巢狀） 的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="e3e66-119">Both simple and complex (nested) RECORD types are supported.</span></span> [<span data-ttu-id="e3e66-120">函式和含有 RECORD 類型之程序的相關作業</span><span class="sxs-lookup"><span data-stu-id="e3e66-120">Operations on Functions and Procedures with RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
  <span data-ttu-id="e3e66-121">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="e3e66-121">For more information about:</span></span>  
  
- <span data-ttu-id="e3e66-122">使用叫用 Oracle 程序或函式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 叫用函式與使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)和[叫用多載函式和 Oracle Database 中的程序BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e66-122">Invoking an Oracle procedure or function by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md) and [Invoke Overload Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="e3e66-123">叫用 Oracle 程序或函式，使用 WCF 服務模型，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e66-123">Invoking an Oracle procedure or function by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
- <span data-ttu-id="e3e66-124">叫用 Oracle 程序或函式使用 WCF 通道模型，請參閱[叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e66-124">Invoking an Oracle procedure or function by using the WCF channel model, see [Invoke a Function in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
- <span data-ttu-id="e3e66-125">訊息結構和 SOAP 動作，用來叫用 Oracle 程序和函數，請參閱 <<c0> [ 函式和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e66-125">Message structure and SOAP actions used to invoke Oracle procedures and functions, see [Message Schemas for Functions and Procedures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e66-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e66-126">See Also</span></span>  
 <span data-ttu-id="e3e66-127">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e3e66-127">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>