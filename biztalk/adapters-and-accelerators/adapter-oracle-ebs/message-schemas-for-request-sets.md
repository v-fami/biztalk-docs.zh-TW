---
title: 要求的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bba9677d-ee94-4da5-8611-b1e47f2f3798
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fd81ee75088b41a182c5a2aa675266420f8f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217094"
---
# <a name="message-schemas-for-request-sets"></a><span data-ttu-id="9829a-102">要求的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9829a-102">Message Schemas for Request Sets</span></span>
<span data-ttu-id="9829a-103">Oracle E-business Suite 中的 Oracle 應用程式中設定每個要求會呈現為中的作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9829a-103">Each request set in an Oracle application in Oracle E-Business Suite is surfaced as an operation in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span></span>  
  
## <a name="message-structure-of-request-set-operation"></a><span data-ttu-id="9829a-104">要求的訊息結構，設定作業</span><span class="sxs-lookup"><span data-stu-id="9829a-104">Message Structure of Request Set Operation</span></span>  
 <span data-ttu-id="9829a-105">要求設定中顯示的作業會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9829a-105">The operations surfaced for request set follow a request-response message exchange pattern.</span></span> <span data-ttu-id="9829a-106">下表顯示這些要求和回應訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="9829a-106">The following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9829a-107">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="9829a-107">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="9829a-108">作業</span><span class="sxs-lookup"><span data-stu-id="9829a-108">Operation</span></span>|<span data-ttu-id="9829a-109">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="9829a-109">XML Message</span></span>|<span data-ttu-id="9829a-110">Description</span><span class="sxs-lookup"><span data-stu-id="9829a-110">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="9829a-111">[Request_Set_Name]要求</span><span class="sxs-lookup"><span data-stu-id="9829a-111">[Request_Set_Name] Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name] xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]/">   <SetRelClassOptions>     <Application>[value]</Application>     <ClassName>[value]</ClassName>     <CancelOrHold>[value]</CancelOrHold>     <StaleDate>[value]</StaleDate>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRelClassOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <SetNlsOptions>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetNlsOptions>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_NAME1]>[value]</[CONCURRENT_PROGRAM_NAME1]>   <[CONCURRENT_PROGRAM_NAME2]>[value]</[CONCURRENT_PROGRAM_NAME2]>   … </[Request_Set_Name]>`|<span data-ttu-id="9829a-112">-[Request_Set_Name] 作業會採用標準的五個參數： `SetRelClassOptions`， `SetPrintOptions`， `SetRepeatOptions`， `SetNlsOptions`，和`StartTime`。</span><span class="sxs-lookup"><span data-stu-id="9829a-112">- The [Request_Set_Name] operation takes five standard parameters:  `SetRelClassOptions`, `SetPrintOptions`,  `SetRepeatOptions`, `SetNlsOptions`, and `StartTime`.</span></span><br /><br /> <span data-ttu-id="9829a-113">-`ContinueOnFail`參數會指出是否要求組提交事件應該繼續還是擲回例外狀況案例中的父參數 (`SetRelClassOptions`， `SetPrintOptions`，`SetRepeatOptions`或`SetNlsOptions`) 失敗。</span><span class="sxs-lookup"><span data-stu-id="9829a-113">- The `ContinueOnFail` parameter indicates whether the request set submission should continue or throw an exception in case the parent parameter (`SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions` or `SetNlsOptions`) fails.</span></span> <span data-ttu-id="9829a-114">您可以指定**True** （繼續） 或**False** （擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="9829a-114">You can specify **True** (continue) or **False** (throw an exception).</span></span><br /><br /> <span data-ttu-id="9829a-115">-若為每個參數的詳細資訊，請參閱[作業要求集](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="9829a-115">- For detailed information about each parameter, see [Operations on Request Sets](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span></span>|  
|<span data-ttu-id="9829a-116">[Request_Set_Name]回應</span><span class="sxs-lookup"><span data-stu-id="9829a-116">[Request_Set_Name] Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name]Response xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]">   <[Request_Set_Name]Result>[value]</[Request_Set_Name]Result> </[Request_Set_Name]Response>`|<span data-ttu-id="9829a-117">Oracle E-business Suite 的回應包含並行要求識別碼。</span><span class="sxs-lookup"><span data-stu-id="9829a-117">The response from Oracle E-Business Suite contains a concurrent request ID.</span></span>|  
  
 <span data-ttu-id="9829a-118">實體描述：</span><span class="sxs-lookup"><span data-stu-id="9829a-118">Entity descriptions:</span></span>  
  
 <span data-ttu-id="9829a-119">[版本] = http://schemas.microsoft.com/OracleEBS/2008/05</span><span class="sxs-lookup"><span data-stu-id="9829a-119">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05</span></span>  
  
 <span data-ttu-id="9829a-120">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="9829a-120">.</span></span>  
  
 <span data-ttu-id="9829a-121">[CONCURRENT_PROGRAM_NAME] = 並行要求集中包含的程式。</span><span class="sxs-lookup"><span data-stu-id="9829a-121">[CONCURRENT_PROGRAM_NAME] = Concurrent program included in the request set.</span></span>  
  
## <a name="message-actions-for-request-sets"></a><span data-ttu-id="9829a-122">要求的訊息動作</span><span class="sxs-lookup"><span data-stu-id="9829a-122">Message Actions for Request Sets</span></span>  
 <span data-ttu-id="9829a-123">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求組會使用下列的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="9829a-123">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for request sets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9829a-124">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="9829a-124">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="9829a-125">訊息</span><span class="sxs-lookup"><span data-stu-id="9829a-125">Message</span></span>|<span data-ttu-id="9829a-126">動作</span><span class="sxs-lookup"><span data-stu-id="9829a-126">Action</span></span>|<span data-ttu-id="9829a-127">範例</span><span class="sxs-lookup"><span data-stu-id="9829a-127">Example</span></span>|  
|-------------|------------|-------------|  
|<span data-ttu-id="9829a-128">要求設定要求</span><span class="sxs-lookup"><span data-stu-id="9829a-128">Request Set request</span></span>|<span data-ttu-id="9829a-129">RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]</span><span class="sxs-lookup"><span data-stu-id="9829a-129">RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]</span></span>|<span data-ttu-id="9829a-130">RequestSets/SQLGL/FNDRSSUB965</span><span class="sxs-lookup"><span data-stu-id="9829a-130">RequestSets/SQLGL/FNDRSSUB965</span></span>|  
|<span data-ttu-id="9829a-131">要求設定回應</span><span class="sxs-lookup"><span data-stu-id="9829a-131">Request Set response</span></span>|<span data-ttu-id="9829a-132">RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]] / 回應</span><span class="sxs-lookup"><span data-stu-id="9829a-132">RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]]/response</span></span>|<span data-ttu-id="9829a-133">RequestSets/SQLGL/FNDRSSUB965/回應</span><span class="sxs-lookup"><span data-stu-id="9829a-133">RequestSets/SQLGL/FNDRSSUB965/response</span></span>|  
  
 <span data-ttu-id="9829a-134">實體描述：</span><span class="sxs-lookup"><span data-stu-id="9829a-134">Entity descriptions:</span></span>  
  
 <span data-ttu-id="9829a-135">[APP_SHORT_NAME] = 應用程式簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="9829a-135">[APP_SHORT_NAME] = Application short name.</span></span>  
  
 <span data-ttu-id="9829a-136">[REQUESTSET_SHORT_NAME] = 要求設定的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="9829a-136">[REQUESTSET_SHORT_NAME] = Request Set short name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9829a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9829a-137">See Also</span></span>  
 [<span data-ttu-id="9829a-138">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="9829a-138">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)