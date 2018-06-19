---
title: 要求的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0537354d-821e-4cf9-a4d1-f4e7d1643df9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8051a94df28df4090f78287070c5143e6f866ed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217294"
---
# <a name="operations-on-request-sets"></a><span data-ttu-id="40b9e-102">要求的作業</span><span class="sxs-lookup"><span data-stu-id="40b9e-102">Operations on Request Sets</span></span>
<span data-ttu-id="40b9e-103">在 Oracle E-business Suite 中設定的要求是一組報表和並行會組織成不同階段的程式。</span><span class="sxs-lookup"><span data-stu-id="40b9e-103">A request set in Oracle E-Business Suite is a set of reports and concurrent programs that are organized into various stages.</span></span> <span data-ttu-id="40b9e-104">您可以使用單一要求設定為執行一組報表和並行程式。</span><span class="sxs-lookup"><span data-stu-id="40b9e-104">You can use a single request set to run a set of reports and concurrent programs.</span></span> <span data-ttu-id="40b9e-105">要求集劃分為一個或多個階段，而且每個階段包含一組報表和並行程式。</span><span class="sxs-lookup"><span data-stu-id="40b9e-105">Request sets are divided into one or more stages, and each stage contains a set of reports and concurrent programs.</span></span> <span data-ttu-id="40b9e-106">這些階段會彼此連結，而且每個階段執行的順序定義。</span><span class="sxs-lookup"><span data-stu-id="40b9e-106">These stages are linked with each other, and the order of the execution of each stage is defined.</span></span> <span data-ttu-id="40b9e-107">如需要求集的多個 Oracle 特定資訊，請移至[http://go.microsoft.com/fwlink/p/?LinkId=129539](http://go.microsoft.com/fwlink/p/?LinkId=129539)。</span><span class="sxs-lookup"><span data-stu-id="40b9e-107">For more Oracle-specific information about request sets, go to [http://go.microsoft.com/fwlink/p/?LinkId=129539](http://go.microsoft.com/fwlink/p/?LinkId=129539).</span></span>  
  
 [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="40b9e-108">可讓您執行 Oracle E-business Suite 中要求集合。</span><span class="sxs-lookup"><span data-stu-id="40b9e-108"> enables you to execute request sets in Oracle E-Business Suite.</span></span> <span data-ttu-id="40b9e-109">要求會公開為中的作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="40b9e-109">The request sets are exposed as operations in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="40b9e-110">要求集只包含一組並行程式，因為這些並行程式要求設定作業，就會是輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="40b9e-110">Since a request set contains a set of concurrent programs, those concurrent programs are the input parameters for a request set operation.</span></span> <span data-ttu-id="40b9e-111">並行程式，以及要求設定作業會接受四個複雜型別參數和簡單的型別參數做為輸入。</span><span class="sxs-lookup"><span data-stu-id="40b9e-111">Along with the concurrent programs, the request set operation takes four complex type parameters and a simple type parameter as input.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40b9e-112">您必須針對要求設定中設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]才能執行任何作業要求集。</span><span class="sxs-lookup"><span data-stu-id="40b9e-112">You must set the applications context for request sets in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] before you can perform any operations on request sets.</span></span> <span data-ttu-id="40b9e-113">這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。</span><span class="sxs-lookup"><span data-stu-id="40b9e-113">This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact.</span></span> <span data-ttu-id="40b9e-114">應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="40b9e-114">For information about applications context, and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
## <a name="complex-type-parameters"></a><span data-ttu-id="40b9e-115">複雜型別參數</span><span class="sxs-lookup"><span data-stu-id="40b9e-115">Complex type parameters</span></span>
  
-   <span data-ttu-id="40b9e-116">**SetRelClassOptions**： 可讓您設定的要求組排程選項。</span><span class="sxs-lookup"><span data-stu-id="40b9e-116">**SetRelClassOptions**: Enables you to set scheduling options for the request set.</span></span> <span data-ttu-id="40b9e-117">如果已設定 SetRelClassOptions 和 SetRepeatOptions SetRelClassOptions 將享有優先權。</span><span class="sxs-lookup"><span data-stu-id="40b9e-117">If both SetRelClassOptions and SetRepeatOptions are set then SetRelClassOptions will take precedence.</span></span> <span data-ttu-id="40b9e-118">SetRelClassOptions 接受做為參數的下列選項：</span><span class="sxs-lookup"><span data-stu-id="40b9e-118">SetRelClassOptions takes the following options as parameters:</span></span>  
  
    -   <span data-ttu-id="40b9e-119">**應用程式**： 指出要求組相關的應用程式的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="40b9e-119">**Application**: Indicates the short name of the application associated with the request set.</span></span>  
  
    -   <span data-ttu-id="40b9e-120">**ClassName**： 指出要求集相關聯的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="40b9e-120">**ClassName**: Indicates the name of the class associated with the request set.</span></span>  
  
    -   <span data-ttu-id="40b9e-121">**CanceOrHold**： 指出取消 」 或 「 保留 」 旗標。</span><span class="sxs-lookup"><span data-stu-id="40b9e-121">**CanceOrHold**: Indicates the Cancel or Hold flag.</span></span>  
  
    -   <span data-ttu-id="40b9e-122">**StaleDate**： 指出日期要求組尚未執行，當天或之後這個將取消要求集。</span><span class="sxs-lookup"><span data-stu-id="40b9e-122">**StaleDate**: Indicates the date on or after which this request set will be canceled if the request set has not yet run.</span></span>  
  
    -   <span data-ttu-id="40b9e-123">**ContinueOnFail**： 指出要求組提交應該繼續還是 SetRelClassOptions 失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="40b9e-123">**ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetRelClassOptions fails.</span></span> <span data-ttu-id="40b9e-124">您可以指定"True"（繼續） 或"False"（擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="40b9e-124">You can specify “True” (continue) or “False” (throw an exception).</span></span>  
  
-   <span data-ttu-id="40b9e-125">**SetPrintOptions**： 可讓您設定要求集的列印選項。</span><span class="sxs-lookup"><span data-stu-id="40b9e-125">**SetPrintOptions**: Enables you to set the print options for the request set.</span></span> <span data-ttu-id="40b9e-126">SetPrintOptions 接受做為參數的下列選項：</span><span class="sxs-lookup"><span data-stu-id="40b9e-126">SetPrintOptions takes the following options as parameters:</span></span>  
  
    -   <span data-ttu-id="40b9e-127">**印表機**： 指出設定輸出要求應該會傳送的印表機名稱。</span><span class="sxs-lookup"><span data-stu-id="40b9e-127">**Printer**: Indicates the printer name where the request set output should be sent.</span></span>  
  
    -   <span data-ttu-id="40b9e-128">**樣式**： 指出用來列印要求設定輸出的列印樣式。</span><span class="sxs-lookup"><span data-stu-id="40b9e-128">**Style**: Indicates the print style used to print the request set output.</span></span> <span data-ttu-id="40b9e-129">例如，您可以指定方向 （「 橫印 」 或 「 縱向 」）。</span><span class="sxs-lookup"><span data-stu-id="40b9e-129">For example, you can specify the orientation (“Landscape” or “Portrait”).</span></span>  
  
    -   <span data-ttu-id="40b9e-130">**複製**： 指出要設定輸出的要求列印的份數。</span><span class="sxs-lookup"><span data-stu-id="40b9e-130">**Copies**: Indicates the number of copies to be printed of the request set output.</span></span>  
  
    -   <span data-ttu-id="40b9e-131">**SaveOutput**： 指出是否要儲存輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="40b9e-131">**SaveOutput**: Indicates whether or not to save the output file.</span></span> <span data-ttu-id="40b9e-132">您可以指定"True"False"。</span><span class="sxs-lookup"><span data-stu-id="40b9e-132">You can specify “True” or “False”.</span></span>  
  
    -   <span data-ttu-id="40b9e-133">**PrintTogether**： 只適用於子要求。</span><span class="sxs-lookup"><span data-stu-id="40b9e-133">**PrintTogether**: Applicable only for sub-requests.</span></span> <span data-ttu-id="40b9e-134">表示子要求的輸出列印的方式。</span><span class="sxs-lookup"><span data-stu-id="40b9e-134">Indicates how the output of sub-requests is printed.</span></span> <span data-ttu-id="40b9e-135">如果您指定"Y"，所有的子要求已完成之後，才列印輸出的子要求。</span><span class="sxs-lookup"><span data-stu-id="40b9e-135">If you specify “Y”, the output of sub-requests is printed only after all the sub-requests are complete.</span></span> <span data-ttu-id="40b9e-136">如果您指定完成時，會列印"N"，每項子要求的輸出。</span><span class="sxs-lookup"><span data-stu-id="40b9e-136">If you specify “N”, the output of each sub-request is printed as it completes.</span></span>  
  
    -   <span data-ttu-id="40b9e-137">**ContinueOnFail**： 指出要求組提交應該繼續還是 SetPrintOptions 失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="40b9e-137">**ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetPrintOptions fails.</span></span> <span data-ttu-id="40b9e-138">您可以指定"True"（繼續） 或"False"（擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="40b9e-138">You can specify “True” (continue) or “False” (throw an exception).</span></span>  
  
-   <span data-ttu-id="40b9e-139">**SetRepeatOptions**： 可讓您設定要求集的重複選項。</span><span class="sxs-lookup"><span data-stu-id="40b9e-139">**SetRepeatOptions**: Enables you to set the repeat options for the request set.</span></span> <span data-ttu-id="40b9e-140">SetRepeatOptions 接受做為參數的下列選項：</span><span class="sxs-lookup"><span data-stu-id="40b9e-140">SetRepeatOptions takes the following options as parameters:</span></span>  
  
    -   <span data-ttu-id="40b9e-141">**RepeatTime**： 指出要重複的要求集合的當日時間。</span><span class="sxs-lookup"><span data-stu-id="40b9e-141">**RepeatTime**: Indicates the time of day to repeat the request set.</span></span>  
  
    -   <span data-ttu-id="40b9e-142">**RepeatInterval**： 這是參數時才適用**RepeatTime**是 NULL。</span><span class="sxs-lookup"><span data-stu-id="40b9e-142">**RepeatInterval**: This parameter is applicable only when **RepeatTime** is NULL.</span></span> <span data-ttu-id="40b9e-143">表示要求的 resubmissions 之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="40b9e-143">Indicates the interval between resubmissions of the request.</span></span> <span data-ttu-id="40b9e-144">使用此選項，連同**RepeatUnit**指定 resubmissions 之間的時間。</span><span class="sxs-lookup"><span data-stu-id="40b9e-144">Use this option along with **RepeatUnit** to specify the time between resubmissions.</span></span>  
  
    -   <span data-ttu-id="40b9e-145">**RepeatUnit**： 這是參數時才適用**RepeatTime**是 NULL。</span><span class="sxs-lookup"><span data-stu-id="40b9e-145">**RepeatUnit**: This parameter is applicable only when **RepeatTime** is NULL.</span></span> <span data-ttu-id="40b9e-146">時間與單位**RepeatInterval**若要指定要求的 resubmissions 之間的時間。</span><span class="sxs-lookup"><span data-stu-id="40b9e-146">The unit of time used along with **RepeatInterval** to specify the time between resubmissions of the request.</span></span> <span data-ttu-id="40b9e-147">您可以指定"Minutes"、"Hours"、"Days"或"Months"。</span><span class="sxs-lookup"><span data-stu-id="40b9e-147">You can specify “Minutes”, “Hours”, “Days” or “Months”.</span></span>  
  
    -   <span data-ttu-id="40b9e-148">**RepeatType**： 這是參數時才適用**RepeatTime**是 NULL。</span><span class="sxs-lookup"><span data-stu-id="40b9e-148">**RepeatType**: This parameter is applicable only when **RepeatTime** is NULL.</span></span> <span data-ttu-id="40b9e-149">指出是否將重複間隔會套用前一個要求 「 開始 」 設定執行後，或者在前一個要求 「 結束 」 設定執行。</span><span class="sxs-lookup"><span data-stu-id="40b9e-149">Indicates whether the repeat interval is applied after the “start” of a previous request set execution or after the “end” of a previous request set execution.</span></span>  
  
    -   <span data-ttu-id="40b9e-150">**RepeatEndTime**： 指出停止重新提交要求集的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="40b9e-150">**RepeatEndTime**: Indicates the date and time to stop resubmitting the request set.</span></span>  
  
    -   <span data-ttu-id="40b9e-151">**ContinueOnFail**： 指出要求組提交應該繼續還是 SetRepeatOptions 失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="40b9e-151">**ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetRepeatOptions fails.</span></span> <span data-ttu-id="40b9e-152">您可以指定"True"（繼續） 或"False"（擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="40b9e-152">You can specify “True” (continue) or “False” (throw an exception).</span></span>  
  
-   <span data-ttu-id="40b9e-153">**SetNlsOptions**： 可讓您設定要求集 NLS 選項。</span><span class="sxs-lookup"><span data-stu-id="40b9e-153">**SetNlsOptions**: Enables you to set the NLS options for the request set.</span></span> <span data-ttu-id="40b9e-154">SetNlsOptions 接受做為參數的下列選項：</span><span class="sxs-lookup"><span data-stu-id="40b9e-154">SetNlsOptions takes the following options as parameters:</span></span>  
  
    -   <span data-ttu-id="40b9e-155">**語言**： 表示 NLS 語言。</span><span class="sxs-lookup"><span data-stu-id="40b9e-155">**Language**: Indicates the NLS language.</span></span>  
  
    -   <span data-ttu-id="40b9e-156">**語言**： 指出語言領域。</span><span class="sxs-lookup"><span data-stu-id="40b9e-156">**Language**: Indicates the language territory.</span></span>  
  
    -   <span data-ttu-id="40b9e-157">**ContinueOnFail**： 指出要求組提交應該繼續還是 SetNlsOptions 失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="40b9e-157">**ContinueOnFail**: Indicates whether the request set submission should continue or throw an exception in case SetNlsOptions fails.</span></span> <span data-ttu-id="40b9e-158">您可以指定"True"（繼續） 或"False"（擲回例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="40b9e-158">You can specify “True” (continue) or “False” (throw an exception).</span></span>  
  
## <a name="simple-type-parameter"></a><span data-ttu-id="40b9e-159">簡單的型別參數</span><span class="sxs-lookup"><span data-stu-id="40b9e-159">Simple type parameter</span></span>
  
 <span data-ttu-id="40b9e-160">**StartTime**： 表示要求集應該開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="40b9e-160">**StartTime**: Indicates the time at which the request set should start running.</span></span>  
  
 <span data-ttu-id="40b9e-161">如果要求設定已經順利完成，會傳回識別碼的並行要求。</span><span class="sxs-lookup"><span data-stu-id="40b9e-161">If the request set completes successfully, a concurrent request ID is returned.</span></span> <span data-ttu-id="40b9e-162">否則，會傳回"0"。</span><span class="sxs-lookup"><span data-stu-id="40b9e-162">Otherwise, “0” is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b9e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40b9e-163">See Also</span></span>  
 <span data-ttu-id="40b9e-164">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="40b9e-164">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>