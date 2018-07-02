---
title: BizTalk Adapter for Oracle E-business Suite 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 149cee03-43cd-4cb3-a937-6565f5e96ce5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6de75a2955632f4f8e0daae2a2035e90f1f2fca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988391"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="8d102-102">BizTalk Adapter for Oracle E-business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="8d102-102">Limitations of BizTalk Adapter for Oracle E-Business Suite</span></span>
## <a name="general-limitations"></a><span data-ttu-id="8d102-103">一般限制</span><span class="sxs-lookup"><span data-stu-id="8d102-103">General Limitations</span></span>  
 <span data-ttu-id="8d102-104">下列已知限制[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8d102-104">The following are known limitations for [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span></span>  
  
- <span data-ttu-id="8d102-105">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 XML 閘道 」、 「 進階佇列，和 「 商務事件。</span><span class="sxs-lookup"><span data-stu-id="8d102-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support XML Gateway, Advanced Queuing, and Business Events.</span></span>  
  
   <span data-ttu-id="8d102-106">不過，您可以以下列方式取得解決商務事件限制：</span><span class="sxs-lookup"><span data-stu-id="8d102-106">However, you can get around the Business Events limitation in the following way:</span></span>  
  
  1. <span data-ttu-id="8d102-107">在 Oracle 商務事件系統中，建立商務事件發生時叫用自訂的 PL/SQL 程序的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="8d102-107">In Oracle Business Events System, create a subscription to invoke a custom PL/SQL procedure when a business event occurs.</span></span>  
  
  2. <span data-ttu-id="8d102-108">撰寫自訂的 PL/SQL 程序會接收商務事件。</span><span class="sxs-lookup"><span data-stu-id="8d102-108">Write a custom PL/SQL procedure that receives the business event.</span></span>  
  
  3. <span data-ttu-id="8d102-109">您可以使用自訂的 PL/SQL 程序，在資料表中儲存產生的資料 （事件和事件裝載）。</span><span class="sxs-lookup"><span data-stu-id="8d102-109">Use the custom PL/SQL procedure to store the resultant data (event and event payload) in a table.</span></span>  
  
  4. <span data-ttu-id="8d102-110">使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢，或從資料表中接收通知。</span><span class="sxs-lookup"><span data-stu-id="8d102-110">Use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll or receive notifications from the table.</span></span>  
  
- <span data-ttu-id="8d102-111">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援的 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="8d102-111">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support XML Types.</span></span>  
  
- <span data-ttu-id="8d102-112">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。</span><span class="sxs-lookup"><span data-stu-id="8d102-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not enable clients to set the value of the first element in a VARRAY to NULL.</span></span>  
  
- <span data-ttu-id="8d102-113">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行不支援包含的欄位的記錄類型的記錄類型的 PL/SQL 資料表。</span><span class="sxs-lookup"><span data-stu-id="8d102-113">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support records that contain fields of type PL/SQL tables of RECORD type.</span></span>  
  
- <span data-ttu-id="8d102-114">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。</span><span class="sxs-lookup"><span data-stu-id="8d102-114">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support User-Defined Types (UDTs) that have circular references.</span></span>  
  
- <span data-ttu-id="8d102-115">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援複雜類型 （例如記錄類型、 資料表類型、 UDT 和 VARRAY） 內的 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="8d102-115">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support the BFILE data type inside complex types (such as RECORD type, TABLE type, UDT, and VARRAY).</span></span>  
  
- <span data-ttu-id="8d102-116">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援巢狀只有最多兩個層級的 UDT。</span><span class="sxs-lookup"><span data-stu-id="8d102-116">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports UDT nesting only up to two levels.</span></span>  
  
- <span data-ttu-id="8d102-117">PL/SQL 資料表，除了[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援封裝內定義的 Udt。</span><span class="sxs-lookup"><span data-stu-id="8d102-117">Except for PL/SQL tables, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that are defined inside a package.</span></span>  
  
- <span data-ttu-id="8d102-118">當與 BizTalk Server 使用配接器，如果認證 wcf-custom 傳送埠不正確的時不會處理要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8d102-118">When using the adapters with BizTalk Server, if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="8d102-119">您指定正確的認證之後，將訊息傳送到 Oracle E-business Suite 和收到的回應。</span><span class="sxs-lookup"><span data-stu-id="8d102-119">After you specify the correct credentials, the message is sent to Oracle E-Business Suite and a response is received.</span></span> <span data-ttu-id="8d102-120">不過，回應訊息不適用於輸出連接埠。</span><span class="sxs-lookup"><span data-stu-id="8d102-120">However, the response message is not available to the out port.</span></span> <span data-ttu-id="8d102-121">在此情況下，您可能需要重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d102-121">In such scenarios, you may need to restart the host instance.</span></span>  
  
## <a name="limitations-due-to-odpnet"></a><span data-ttu-id="8d102-122">由於 ODP.NET 的限制</span><span class="sxs-lookup"><span data-stu-id="8d102-122">Limitations Due to ODP.NET</span></span>  
 <span data-ttu-id="8d102-123">下列已知限制[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]由於 ODP.NET 的限制：</span><span class="sxs-lookup"><span data-stu-id="8d102-123">The following are known limitations for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] due to the limitation of ODP.NET:</span></span>  
  
- <span data-ttu-id="8d102-124">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援未編製索引為數值欄位的 PL/SQL 資料表。</span><span class="sxs-lookup"><span data-stu-id="8d102-124">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support PL/SQL tables that are not indexed by a numeric field.</span></span>  
  
- <span data-ttu-id="8d102-125">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援不包含任何元素的關聯陣列。</span><span class="sxs-lookup"><span data-stu-id="8d102-125">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support associative arrays that do not contain any element.</span></span>  
  
- <span data-ttu-id="8d102-126">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含當地時間區域屬性 (TimeStampLTZ) 的時間戳記資料類型的 Udt。</span><span class="sxs-lookup"><span data-stu-id="8d102-126">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain the TimeStamp data type with local time zone attributes (TimeStampLTZ).</span></span>  
  
- <span data-ttu-id="8d102-127">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含 Udt"。"</span><span class="sxs-lookup"><span data-stu-id="8d102-127">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain a “.”</span></span> <span data-ttu-id="8d102-128">（句號） 在其名稱中。</span><span class="sxs-lookup"><span data-stu-id="8d102-128">(period) in their names.</span></span>  
  
- <span data-ttu-id="8d102-129">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含 BLOB、 CLOB、 和 NCLOB 資料類型為在 OUT 參數的 Udt。</span><span class="sxs-lookup"><span data-stu-id="8d102-129">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain BLOB, CLOB, and NCLOB data types as an IN OUT parameter.</span></span>  
  
- <span data-ttu-id="8d102-130">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] Nepodporuje Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。</span><span class="sxs-lookup"><span data-stu-id="8d102-130">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support Varray of Varray of the following simple types: BFILE, IntervalDS, IntervalYM, TimeStampLTZ, and TimeStampTZ.</span></span>  
  
- <span data-ttu-id="8d102-131">由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的任何記錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8d102-131">Due to the limitation of associative arrays, PL/SQL tables or PL/SQL tables of records that contain any of the following data types are not supported in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:</span></span>  
  
  -   <span data-ttu-id="8d102-132">BFILE</span><span class="sxs-lookup"><span data-stu-id="8d102-132">BFILE</span></span>  
  
  -   <span data-ttu-id="8d102-133">BLOB</span><span class="sxs-lookup"><span data-stu-id="8d102-133">BLOB</span></span>  
  
  -   <span data-ttu-id="8d102-134">CLOB</span><span class="sxs-lookup"><span data-stu-id="8d102-134">CLOB</span></span>  
  
  -   <span data-ttu-id="8d102-135">IntervalDS</span><span class="sxs-lookup"><span data-stu-id="8d102-135">IntervalDS</span></span>  
  
  -   <span data-ttu-id="8d102-136">IntervalYM</span><span class="sxs-lookup"><span data-stu-id="8d102-136">IntervalYM</span></span>  
  
  -   <span data-ttu-id="8d102-137">長整數</span><span class="sxs-lookup"><span data-stu-id="8d102-137">Long</span></span>  
  
  -   <span data-ttu-id="8d102-138">NCLOB</span><span class="sxs-lookup"><span data-stu-id="8d102-138">NCLOB</span></span>  
  
  -   <span data-ttu-id="8d102-139">RowID</span><span class="sxs-lookup"><span data-stu-id="8d102-139">RowID</span></span>  
  
  -   <span data-ttu-id="8d102-140">TimeStamp</span><span class="sxs-lookup"><span data-stu-id="8d102-140">TimeStamp</span></span>  
  
  -   <span data-ttu-id="8d102-141">TimeStampLTZ</span><span class="sxs-lookup"><span data-stu-id="8d102-141">TimeStampLTZ</span></span>  
  
  -   <span data-ttu-id="8d102-142">TimeStampTZ</span><span class="sxs-lookup"><span data-stu-id="8d102-142">TimeStampTZ</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d102-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d102-143">See Also</span></span>  
 [<span data-ttu-id="8d102-144">了解 BizTalk Adapter for Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="8d102-144">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)