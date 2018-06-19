---
title: 資料型別對應自訂 Rfc |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom RFCs, data type mapping
ms.assetid: 33539a5a-bdfc-423f-8026-436f69a20c70
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cac254734a35658e3aa635b086f765e8f06494a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217414"
---
# <a name="data-type-mapping-for-custom-rfcs"></a><span data-ttu-id="4a853-102">自訂 Rfc 的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="4a853-102">Data Type Mapping for Custom RFCs</span></span>
<span data-ttu-id="4a853-103">下表提供有關 SAP 資料類型和其如何對應至.NET 資料型別 Z_EXTRACT_DATA_OO RFC 的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a853-103">The following table provides information about SAP data types and how they are mapped to .NET data types for the Z_EXTRACT_DATA_OO RFC.</span></span> <span data-ttu-id="4a853-104">使用這個自訂 RFC [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a853-104">This custom RFC is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a853-105">如 Z_EXECUTE_SAP_QUERY，這由[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]執行 EXECQUERY 命令，所有的 SAP 資料類型會轉換為.NET 字串類型。</span><span class="sxs-lookup"><span data-stu-id="4a853-105">For the Z_EXECUTE_SAP_QUERY, which is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to execute the EXECQUERY command, all SAP data types are converted to .NET string types.</span></span>  
  
|<span data-ttu-id="4a853-106">SAP 資料類型</span><span class="sxs-lookup"><span data-stu-id="4a853-106">SAP Data Type</span></span>|<span data-ttu-id="4a853-107">.NET 資料類型</span><span class="sxs-lookup"><span data-stu-id="4a853-107">.NET Data Type</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="4a853-108">ACCP</span><span class="sxs-lookup"><span data-stu-id="4a853-108">ACCP</span></span>|<span data-ttu-id="4a853-109">-Int32</span><span class="sxs-lookup"><span data-stu-id="4a853-109">-   Int32</span></span><br /><span data-ttu-id="4a853-110">的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。</span><span class="sxs-lookup"><span data-stu-id="4a853-110">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="4a853-111">CHAR</span><span class="sxs-lookup"><span data-stu-id="4a853-111">CHAR</span></span>|<span data-ttu-id="4a853-112">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-112">String</span></span>|  
|<span data-ttu-id="4a853-113">CLNT</span><span class="sxs-lookup"><span data-stu-id="4a853-113">CLNT</span></span>|<span data-ttu-id="4a853-114">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-114">String</span></span>|  
|<span data-ttu-id="4a853-115">CUKY</span><span class="sxs-lookup"><span data-stu-id="4a853-115">CUKY</span></span>|<span data-ttu-id="4a853-116">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-116">String</span></span>|  
|<span data-ttu-id="4a853-117">目前</span><span class="sxs-lookup"><span data-stu-id="4a853-117">CURR</span></span>|<span data-ttu-id="4a853-118">Decimal、 有效位數小於或等於 28 時</span><span class="sxs-lookup"><span data-stu-id="4a853-118">Decimal, if precision less than or equal to 28</span></span><br /><br /> <span data-ttu-id="4a853-119">字串，如果有效位數大於 28</span><span class="sxs-lookup"><span data-stu-id="4a853-119">String, if precision greater than 28</span></span>|  
|<span data-ttu-id="4a853-120">DATS</span><span class="sxs-lookup"><span data-stu-id="4a853-120">DATS</span></span>|<span data-ttu-id="4a853-121">日期時間</span><span class="sxs-lookup"><span data-stu-id="4a853-121">-   DateTime</span></span><br /><span data-ttu-id="4a853-122">的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。</span><span class="sxs-lookup"><span data-stu-id="4a853-122">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="4a853-123">DEC</span><span class="sxs-lookup"><span data-stu-id="4a853-123">DEC</span></span>|<span data-ttu-id="4a853-124">Decimal</span><span class="sxs-lookup"><span data-stu-id="4a853-124">Decimal</span></span>|  
|<span data-ttu-id="4a853-125">FLTP</span><span class="sxs-lookup"><span data-stu-id="4a853-125">FLTP</span></span>|<span data-ttu-id="4a853-126">Double</span><span class="sxs-lookup"><span data-stu-id="4a853-126">Double</span></span>|  
|<span data-ttu-id="4a853-127">INT1</span><span class="sxs-lookup"><span data-stu-id="4a853-127">INT1</span></span>|<span data-ttu-id="4a853-128">Byte</span><span class="sxs-lookup"><span data-stu-id="4a853-128">Byte</span></span>|  
|<span data-ttu-id="4a853-129">INT2</span><span class="sxs-lookup"><span data-stu-id="4a853-129">INT2</span></span>|<span data-ttu-id="4a853-130">Int16</span><span class="sxs-lookup"><span data-stu-id="4a853-130">Int16</span></span>|  
|<span data-ttu-id="4a853-131">INT4</span><span class="sxs-lookup"><span data-stu-id="4a853-131">INT4</span></span>|<span data-ttu-id="4a853-132">Int32</span><span class="sxs-lookup"><span data-stu-id="4a853-132">Int32</span></span>|  
|<span data-ttu-id="4a853-133">LANG</span><span class="sxs-lookup"><span data-stu-id="4a853-133">LANG</span></span>|<span data-ttu-id="4a853-134">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-134">String</span></span>|  
|<span data-ttu-id="4a853-135">NUMC</span><span class="sxs-lookup"><span data-stu-id="4a853-135">NUMC</span></span>|<span data-ttu-id="4a853-136">-Int32，如果欄位長度小於或等於到 9</span><span class="sxs-lookup"><span data-stu-id="4a853-136">-   Int32, if field length less than or equal to 9</span></span><br /><span data-ttu-id="4a853-137">-Int64，如果欄位長度大於 9 且小於或等於 19</span><span class="sxs-lookup"><span data-stu-id="4a853-137">-   Int64, if field length greater than 9 and less than or equal to 19</span></span><br /><span data-ttu-id="4a853-138">字串，如果大於 19</span><span class="sxs-lookup"><span data-stu-id="4a853-138">-   String, if greater than 19</span></span><br /><span data-ttu-id="4a853-139">的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。</span><span class="sxs-lookup"><span data-stu-id="4a853-139">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="4a853-140">PREC</span><span class="sxs-lookup"><span data-stu-id="4a853-140">PREC</span></span>|<span data-ttu-id="4a853-141">Int16</span><span class="sxs-lookup"><span data-stu-id="4a853-141">Int16</span></span>|  
|<span data-ttu-id="4a853-142">QUAN</span><span class="sxs-lookup"><span data-stu-id="4a853-142">QUAN</span></span>|<span data-ttu-id="4a853-143">Decimal</span><span class="sxs-lookup"><span data-stu-id="4a853-143">Decimal</span></span>|  
|<span data-ttu-id="4a853-144">RAW</span><span class="sxs-lookup"><span data-stu-id="4a853-144">RAW</span></span>|<span data-ttu-id="4a853-145">Byte]</span><span class="sxs-lookup"><span data-stu-id="4a853-145">Byte []</span></span>|  
|<span data-ttu-id="4a853-146">RSTR</span><span class="sxs-lookup"><span data-stu-id="4a853-146">RSTR</span></span>|<span data-ttu-id="4a853-147">Byte]</span><span class="sxs-lookup"><span data-stu-id="4a853-147">Byte []</span></span>|  
|<span data-ttu-id="4a853-148">SSTR</span><span class="sxs-lookup"><span data-stu-id="4a853-148">SSTR</span></span>|<span data-ttu-id="4a853-149">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-149">String</span></span>|  
|<span data-ttu-id="4a853-150">STRG</span><span class="sxs-lookup"><span data-stu-id="4a853-150">STRG</span></span>|<span data-ttu-id="4a853-151">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-151">String</span></span>|  
|<span data-ttu-id="4a853-152">TIMS</span><span class="sxs-lookup"><span data-stu-id="4a853-152">TIMS</span></span>|<span data-ttu-id="4a853-153">-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="4a853-153">-   TimeSpan</span></span><br /><span data-ttu-id="4a853-154">的字串，如果**disabledatavalidation**選項在 SELECT 或 EXEC 陳述式中設定。</span><span class="sxs-lookup"><span data-stu-id="4a853-154">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="4a853-155">單位</span><span class="sxs-lookup"><span data-stu-id="4a853-155">UNIT</span></span>|<span data-ttu-id="4a853-156">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-156">String</span></span>|  
|<span data-ttu-id="4a853-157">LCHR</span><span class="sxs-lookup"><span data-stu-id="4a853-157">LCHR</span></span>|<span data-ttu-id="4a853-158">字串</span><span class="sxs-lookup"><span data-stu-id="4a853-158">String</span></span>|  
|<span data-ttu-id="4a853-159">LRAW</span><span class="sxs-lookup"><span data-stu-id="4a853-159">LRAW</span></span>|<span data-ttu-id="4a853-160">Byte]</span><span class="sxs-lookup"><span data-stu-id="4a853-160">Byte []</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a853-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a853-161">See Also</span></span>  
 [<span data-ttu-id="4a853-162">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="4a853-162">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)