---
title: 開發自訂累計運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ea2c5fa-ed50-4b76-aee9-0d4adf9e6d8c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8763f557c5bacb13b3fbc1542216d9eb9be8d319
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008527"
---
# <a name="developing-a-custom-cumulative-functoid"></a><span data-ttu-id="daf1f-102">開發自訂累計運算質</span><span class="sxs-lookup"><span data-stu-id="daf1f-102">Developing a Custom Cumulative Functoid</span></span>
<span data-ttu-id="daf1f-103">使用自訂累計運算質以執行在執行個體訊息中發生多次之值的累積運算。</span><span class="sxs-lookup"><span data-stu-id="daf1f-103">Use a custom cumulative functoid to perform accumulation operations for values that occur multiple times within an instance message.</span></span>  
  
 <span data-ttu-id="daf1f-104">在開發累計運算質時，您必須實作三個函式。</span><span class="sxs-lookup"><span data-stu-id="daf1f-104">You must implement three functions when developing a cumulative functoid.</span></span> <span data-ttu-id="daf1f-105">此三個函式對應至對應執行累積所需的初始化、累計和取得動作。</span><span class="sxs-lookup"><span data-stu-id="daf1f-105">The three functions correspond to the initialize, cumulate, and get actions that the map needs to perform the accumulation.</span></span> <span data-ttu-id="daf1f-106">在討論這些函式之前，必須先討論執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="daf1f-106">Before discussing these functions it is important to discuss thread safety.</span></span>  
  
## <a name="writing-a-thread-safe-functoid"></a><span data-ttu-id="daf1f-107">撰寫安全執行緒運算質</span><span class="sxs-lookup"><span data-stu-id="daf1f-107">Writing a Thread-Safe Functoid</span></span>  
 <span data-ttu-id="daf1f-108">運算質程式碼必須為安全執行緒，因為在承受壓力的狀況下，對應的多個執行個體可能會同時執行。</span><span class="sxs-lookup"><span data-stu-id="daf1f-108">The functoid code must be thread-safe because under stress conditions multiple instances of a map may be running concurrently.</span></span> <span data-ttu-id="daf1f-109">有些重點必須熟記：</span><span class="sxs-lookup"><span data-stu-id="daf1f-109">Some of the points to remember include:</span></span>  
  
- <span data-ttu-id="daf1f-110">靜態狀態必須為安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="daf1f-110">Static state must be thread-safe.</span></span>  
  
- <span data-ttu-id="daf1f-111">執行個體狀態並不一定要是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="daf1f-111">Instance state does not always need to be thread-safe.</span></span>  
  
- <span data-ttu-id="daf1f-112">設計時請考量在高壓力狀況下執行。</span><span class="sxs-lookup"><span data-stu-id="daf1f-112">Design with consideration for running under high-stress conditions.</span></span> <span data-ttu-id="daf1f-113">儘可能避免鎖定。</span><span class="sxs-lookup"><span data-stu-id="daf1f-113">Avoid taking locks whenever possible.</span></span>  
  
- <span data-ttu-id="daf1f-114">儘可能避免同步化需求。</span><span class="sxs-lookup"><span data-stu-id="daf1f-114">Avoid the need for synchronization if possible.</span></span>  
  
  <span data-ttu-id="daf1f-115">BizTalk Server 提供一個簡單的機制，以降低撰寫安全執行緒累計運算質的複雜性。</span><span class="sxs-lookup"><span data-stu-id="daf1f-115">BizTalk Server provides a simple mechanism to reduce the complexity of writing a thread-safe cumulative functoid.</span></span> <span data-ttu-id="daf1f-116">這三個函式皆具有相同的第一個參數，該參數為整數索引值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-116">All three functions have the same first parameter, an integer index value.</span></span> <span data-ttu-id="daf1f-117">在呼叫初始化函式時，BizTalk Server 會指派唯一的編號給索引值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-117">BizTalk Server assigns a unique number to the index value when it calls your initialization function.</span></span> <span data-ttu-id="daf1f-118">您可以使用此值做為保存累積值之陣列中的索引，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="daf1f-118">You can use this value as an index into an array that holds accumulating values, as shown in the following code:</span></span>  
  
```  
private HashTable cumulativeArray = new HashTable();  
…  
// Initialization function  
public string InitCumulativeMultiply(int index)  
{  
    cumulativeArray[index] = 1.0;  
    return string.Empty;  
}  
```  
  
 <span data-ttu-id="daf1f-119">此範例使用 HashTable 代替 ArrayList。</span><span class="sxs-lookup"><span data-stu-id="daf1f-119">This example uses a HashTable instead of an ArrayList.</span></span> <span data-ttu-id="daf1f-120">這是因為初始化函式可能不是以排序索引值呼叫。</span><span class="sxs-lookup"><span data-stu-id="daf1f-120">This is because the initialization function might not be called with in-order index values.</span></span>  
  
## <a name="implementing-the-three-cumulative-functions"></a><span data-ttu-id="daf1f-121">實作三個累計函式</span><span class="sxs-lookup"><span data-stu-id="daf1f-121">Implementing the Three Cumulative Functions</span></span>  
 <span data-ttu-id="daf1f-122">您將需要為所開發的每個自訂累計運算質實作三個函式。</span><span class="sxs-lookup"><span data-stu-id="daf1f-122">You will need to implement three functions for each custom cumulative functoid you develop.</span></span> <span data-ttu-id="daf1f-123">下表摘要說明您必須在建構函式中呼叫以設定的函式與方法。</span><span class="sxs-lookup"><span data-stu-id="daf1f-123">The functions and the methods you must call in the constructor to set them are summarized in the following table.</span></span> <span data-ttu-id="daf1f-124">所有函式均傳回字串值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-124">All of the functions return string values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daf1f-125">您可以為每個函式決定最適當的名稱，不過每個函式都必須具有指定引數的數目和類型。</span><span class="sxs-lookup"><span data-stu-id="daf1f-125">You determine the best name for each function, but each function must have the number and type of arguments specified.</span></span>  
  
|<span data-ttu-id="daf1f-126">函式目的</span><span class="sxs-lookup"><span data-stu-id="daf1f-126">Function Purpose</span></span>|<span data-ttu-id="daf1f-127">引數</span><span class="sxs-lookup"><span data-stu-id="daf1f-127">Arguments</span></span>|<span data-ttu-id="daf1f-128">設定參考</span><span class="sxs-lookup"><span data-stu-id="daf1f-128">To set a reference</span></span>|<span data-ttu-id="daf1f-129">設定內嵌指令碼</span><span class="sxs-lookup"><span data-stu-id="daf1f-129">To set inline script</span></span>|  
|----------------------|---------------|------------------------|--------------------------|  
|<span data-ttu-id="daf1f-130">初始化</span><span class="sxs-lookup"><span data-stu-id="daf1f-130">Initialization</span></span>|<span data-ttu-id="daf1f-131">**int 索引**</span><span class="sxs-lookup"><span data-stu-id="daf1f-131">**int index**</span></span>|<span data-ttu-id="daf1f-132">**SetExternalFunctionName**</span><span class="sxs-lookup"><span data-stu-id="daf1f-132">**SetExternalFunctionName**</span></span>|<span data-ttu-id="daf1f-133">**SetScriptBuffer**與`functionNumber`= 0</span><span class="sxs-lookup"><span data-stu-id="daf1f-133">**SetScriptBuffer** with `functionNumber` = 0</span></span>|  
|<span data-ttu-id="daf1f-134">累計</span><span class="sxs-lookup"><span data-stu-id="daf1f-134">Cumulation</span></span>|<span data-ttu-id="daf1f-135">**int 索引、 字串 val、 字串範圍**</span><span class="sxs-lookup"><span data-stu-id="daf1f-135">**int index, string val, string scope**</span></span>|<span data-ttu-id="daf1f-136">**SetExternalFunctionName2**</span><span class="sxs-lookup"><span data-stu-id="daf1f-136">**SetExternalFunctionName2**</span></span>|<span data-ttu-id="daf1f-137">**SetScriptBuffer**與`functionNumber`= 1</span><span class="sxs-lookup"><span data-stu-id="daf1f-137">**SetScriptBuffer** with `functionNumber` = 1</span></span>|  
|<span data-ttu-id="daf1f-138">Get</span><span class="sxs-lookup"><span data-stu-id="daf1f-138">Get</span></span>|<span data-ttu-id="daf1f-139">**int 索引**</span><span class="sxs-lookup"><span data-stu-id="daf1f-139">**int index**</span></span>|<span data-ttu-id="daf1f-140">**SetExternalFunctionName3**</span><span class="sxs-lookup"><span data-stu-id="daf1f-140">**SetExternalFunctionName3**</span></span>|<span data-ttu-id="daf1f-141">**SetScriptBuffer**與`functionNumber`= 2</span><span class="sxs-lookup"><span data-stu-id="daf1f-141">**SetScriptBuffer** with `functionNumber` = 2</span></span>|  
  
### <a name="initialization"></a><span data-ttu-id="daf1f-142">初始化</span><span class="sxs-lookup"><span data-stu-id="daf1f-142">Initialization</span></span>  
 <span data-ttu-id="daf1f-143">初始化可讓您準備將用來執行累積的機制。</span><span class="sxs-lookup"><span data-stu-id="daf1f-143">Initialization enables you to prepare the mechanisms you will use to perform accumulation.</span></span> <span data-ttu-id="daf1f-144">您可以初始化陣列、重設一或多個值，或視需要載入其他資源。</span><span class="sxs-lookup"><span data-stu-id="daf1f-144">You can initialize an array, reset one or more values, or load other resources as needed.</span></span> <span data-ttu-id="daf1f-145">不會使用字串傳回值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-145">The string return value is not used.</span></span>  
  
### <a name="cumulation"></a><span data-ttu-id="daf1f-146">累計</span><span class="sxs-lookup"><span data-stu-id="daf1f-146">Cumulation</span></span>  
 <span data-ttu-id="daf1f-147">您在此為運算質執行適當的累積運算。</span><span class="sxs-lookup"><span data-stu-id="daf1f-147">This is where you perform the accumulation operation appropriate for your functoid.</span></span> <span data-ttu-id="daf1f-148">BizTalk Server 會傳入下列三個參數：</span><span class="sxs-lookup"><span data-stu-id="daf1f-148">BizTalk Server passes in the following three parameters:</span></span>  
  
- <span data-ttu-id="daf1f-149">**索引。**</span><span class="sxs-lookup"><span data-stu-id="daf1f-149">**Index.**</span></span> <span data-ttu-id="daf1f-150">代表對應執行個體的整數值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-150">An integer value representing a map instance.</span></span> <span data-ttu-id="daf1f-151">可能會有多個對應執行個體同時執行。</span><span class="sxs-lookup"><span data-stu-id="daf1f-151">There may be multiple map instances running concurrently.</span></span>  
  
- <span data-ttu-id="daf1f-152">**Val。**</span><span class="sxs-lookup"><span data-stu-id="daf1f-152">**Val.**</span></span> <span data-ttu-id="daf1f-153">包含應累積之值的字串。</span><span class="sxs-lookup"><span data-stu-id="daf1f-153">A string containing the value that should be accumulated.</span></span> <span data-ttu-id="daf1f-154">除非您正在撰寫字串累計運算質，否則此值為數字值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-154">Unless you are writing a string Cumulate functoid it is a numeric value.</span></span>  
  
- <span data-ttu-id="daf1f-155">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="daf1f-155">**Scope.**</span></span> <span data-ttu-id="daf1f-156">包含指示應累積哪些項目或屬性值之數字的字串。</span><span class="sxs-lookup"><span data-stu-id="daf1f-156">A string containing a number indicating which element or attribute value should be accumulated.</span></span> <span data-ttu-id="daf1f-157">實際的值由實作決定。</span><span class="sxs-lookup"><span data-stu-id="daf1f-157">Actual values are determined by an implementation.</span></span>  
  
  <span data-ttu-id="daf1f-158">您可以決定要累積哪些值以及忽略哪些值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-158">You decide which values to accumulate and which values to ignore.</span></span> <span data-ttu-id="daf1f-159">例如，您可以忽略不是低於 0 的值，但是當某個值不是數字時，擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="daf1f-159">For example, you may ignore values that are not below 0 but throw an exception when a value is not numeric.</span></span> <span data-ttu-id="daf1f-160">**BaseFunctoid**提供兩個函式 —**IsDate**並**IsNumeric**— 以協助驗證。</span><span class="sxs-lookup"><span data-stu-id="daf1f-160">**BaseFunctoid** supplies two functions—**IsDate** and **IsNumeric**—to assist with validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daf1f-161">如果您使用**IsDate**或是**IsNumeric**中的內嵌指令碼，請務必設定**RequiredGlobalHelperFunctions**以便函式都會提供給您的指令碼。</span><span class="sxs-lookup"><span data-stu-id="daf1f-161">If you use **IsDate** or **IsNumeric** in an inline script, be sure to set **RequiredGlobalHelperFunctions** so that the functions are made available to your script.</span></span>  
  
 <span data-ttu-id="daf1f-162">不會使用字串傳回值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-162">The string return value is not used.</span></span>  
  
### <a name="get"></a><span data-ttu-id="daf1f-163">Get</span><span class="sxs-lookup"><span data-stu-id="daf1f-163">Get</span></span>  
 <span data-ttu-id="daf1f-164">當 BizTalk Server 完成重複處理由對應中的運算質設定所決定的所有值時，會要求累積值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-164">When BizTalk Server finishes iterating through all of the values determined by the functoid settings in the map, it requests the accumulated value.</span></span> <span data-ttu-id="daf1f-165">Get 函式具有一個 `Index` 引數，該引數為一個代表對應執行個體的整數值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-165">The get function has one argument, `Index`, which is an integer value representing a map instance.</span></span> <span data-ttu-id="daf1f-166">您的函式應使用索引值以尋找並傳回字串格式的累積值。</span><span class="sxs-lookup"><span data-stu-id="daf1f-166">Your function should use the index value to find and return the accumulated value as a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daf1f-167">範例</span><span class="sxs-lookup"><span data-stu-id="daf1f-167">Example</span></span>  
 <span data-ttu-id="daf1f-168">下列範例說明如何建立自訂運算質執行累計乘法。</span><span class="sxs-lookup"><span data-stu-id="daf1f-168">The following example illustrates how to create a custom functoid for performing cumulative multiplication.</span></span> <span data-ttu-id="daf1f-169">它依賴包含三個字串資源以及一個 16x16 像素點陣圖資源的資源檔案。</span><span class="sxs-lookup"><span data-stu-id="daf1f-169">It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
using System.Collections;  
using System.Globalization;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    public class CumulativeMultiplyFunctoid : BaseFunctoid  
    {  
        private ArrayList myCumulativeArray = new ArrayList();  
  
        public CumulativeMultiplyFunctoid() : base()  
        {  
            //ID for this functoid  
            ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUMULATIVEMULTIPLYFUNCTOID_NAME");  
            SetTooltip("IDS_CUMULATIVEMULTIPLYFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUMULATIVEMULTIPLYFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUMULATIVEMULTIPLYFUNCTOID_BITMAP");  
  
            // Put this string handling function under the Cumulative  
            // Functoid tab in the Visual Studio toolbox for functoids  
            Category = FunctoidCategory.Cumulative;  
  
            // 2 required parameters, no optional parameters  
            SetMinParams(1);  
            SetMaxParams(2);  
  
            // Functoid accepts three inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType((~ConnectionType.FunctoidCount) & (~ConnectionType.FunctoidIndex) & (~ConnectionType.FunctoidIteration) & (~ConnectionType.FunctoidCumulative) & (~ConnectionType.FunctoidLooping) & (~ConnectionType.Record));  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the Initialize, Cumulative and Get functions  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CumulativeMultiplyFunctoid", "InitCumulativeMultiply");  
            SetExternalFunctionName2("AddToCumulativeMultiply");  
            SetExternalFunctionName3("GetCumulativeMultiply");  
        }  
  
        // Initialization function  
        public string InitCumulativeMultiply(int index)  
        {  
            if (index >= 0)  
            {  
                if (index >= myCumulativeArray.Count)  
                {  
                    myCumulativeArray.Add(1.0);  
                }  
                else  
                {  
                    myCumulativeArray[index] = 1.0;  
                }  
            }  
  
            return "";  
        }  
  
        // Cumulative function  
        public string AddToCumulativeMultiply(int index, string val, string reserved)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            if (IsNumeric(val))  
            {  
                double dval = Convert.ToDouble(val, CultureInfo.InvariantCulture);  
                myCumulativeArray[index] = (double)(myCumulativeArray[index]) * dval;  
            }  
            return myCumulativeArray[index].ToString();  
        }  
  
        // Get Function  
        public string GetCumulativeMultiply(int index)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            return myCumulativeArray[index].ToString();  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="daf1f-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daf1f-170">See Also</span></span>  
 <span data-ttu-id="daf1f-171">[使用 BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="daf1f-171">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 <span data-ttu-id="daf1f-172">[開發自訂內嵌運算質](../core/developing-a-custom-inline-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="daf1f-172">[Developing a Custom Inline Functoid](../core/developing-a-custom-inline-functoid.md) </span></span>  
 [<span data-ttu-id="daf1f-173">自訂運算質 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="daf1f-173">Custom Functoid (BizTalk Server Sample)</span></span>](../core/custom-functoid-biztalk-server-sample.md)