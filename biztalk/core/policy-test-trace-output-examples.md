---
title: "原則測試追蹤輸出範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- policies, testing
- testing, examples
ms.assetid: 92e1dc7f-1a8d-41a5-84b6-46d5ad9f2ef2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3678769dffa03bb77c3e86fef02998a354b1fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-examples"></a><span data-ttu-id="93425-102">原則測試追蹤輸出範例</span><span class="sxs-lookup"><span data-stu-id="93425-102">Policy Test Trace Output Examples</span></span>
<span data-ttu-id="93425-103">本章節包含不同事實類型的原則測試輸出範例。</span><span class="sxs-lookup"><span data-stu-id="93425-103">This section contains examples of the policy test output for different types of facts.</span></span>  
  
## <a name="net-class"></a><span data-ttu-id="93425-104">.Net 類別</span><span class="sxs-lookup"><span data-stu-id="93425-104">.Net Class</span></span>  
 <span data-ttu-id="93425-105">原則 "LoanProcessing" 中的範例規則 "TestRule1"：</span><span class="sxs-lookup"><span data-stu-id="93425-105">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF test.get_ID > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="93425-106">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="93425-106">**Output:**</span></span>  
  
 <span data-ttu-id="93425-107">規則集的規則引擎追蹤： LoanProcessing 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-107">RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-108">事實活動 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-108">FACT ACTIVITY 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-109">規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="93425-109">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="93425-110">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-110">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-111">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-111">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-112">物件類型：MyTest.test</span><span class="sxs-lookup"><span data-stu-id="93425-112">Object Type: MyTest.test</span></span>  
  
 <span data-ttu-id="93425-113">物件執行個體識別碼： 872</span><span class="sxs-lookup"><span data-stu-id="93425-113">Object Instance Identifier: 872</span></span>  
  
 <span data-ttu-id="93425-114">條件評估測試 （符合） 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-114">CONDITION EVALUATION TEST (MATCH) 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-115">規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="93425-115">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="93425-116">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-116">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-117">測試運算式： MyTest.test.get_ID > 0</span><span class="sxs-lookup"><span data-stu-id="93425-117">Test Expression: MyTest.test.get_ID > 0</span></span>  
  
 <span data-ttu-id="93425-118">左運算元值： 100</span><span class="sxs-lookup"><span data-stu-id="93425-118">Left Operand Value: 100</span></span>  
  
 <span data-ttu-id="93425-119">右運算元值： 0</span><span class="sxs-lookup"><span data-stu-id="93425-119">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="93425-120">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-120">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-121">議程更新 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-121">AGENDA UPDATE 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-122">規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="93425-122">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="93425-123">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-123">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-124">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-124">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-125">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-125">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-126">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-126">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-127">規則被引發 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-127">RULE FIRED 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-128">規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="93425-128">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="93425-129">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-129">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-130">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-130">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-131">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-131">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-132">事實活動 3/16/2004年上午 9:50:28</span><span class="sxs-lookup"><span data-stu-id="93425-132">FACT ACTIVITY 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="93425-133">規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="93425-133">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="93425-134">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-134">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-135">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-135">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-136">物件類型：MyTest.test</span><span class="sxs-lookup"><span data-stu-id="93425-136">Object Type: MyTest.test</span></span>  
  
 <span data-ttu-id="93425-137">物件執行個體識別碼： 872</span><span class="sxs-lookup"><span data-stu-id="93425-137">Object Instance Identifier: 872</span></span>  
  
## <a name="dataconnectiontypeddatarow"></a><span data-ttu-id="93425-138">DataConnection/TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="93425-138">DataConnection/TypedDataRow</span></span>  
 <span data-ttu-id="93425-139">原則 "LoanProcessing" 中的範例規則 "TestRule1"：</span><span class="sxs-lookup"><span data-stu-id="93425-139">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="93425-140">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="93425-140">**Output:**</span></span>  
  
 <span data-ttu-id="93425-141">規則集的規則引擎追蹤： LoanProcessing 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-141">RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-142">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-142">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-143">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-143">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-144">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-144">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-145">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-145">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-146">物件類型： DataConnection:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-146">Object Type: DataConnection:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-147">物件執行個體識別碼： 874</span><span class="sxs-lookup"><span data-stu-id="93425-147">Object Instance Identifier: 874</span></span>  
  
 <span data-ttu-id="93425-148">條件評估測試 （符合） 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-148">CONDITION EVALUATION TEST (MATCH) 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-149">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-149">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-150">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-150">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-151">測試運算式： 選取 * 從 [CustInfo]，[CreditCardBalance] > 0</span><span class="sxs-lookup"><span data-stu-id="93425-151">Test Expression: select * from [CustInfo] where [CreditCardBalance] > 0</span></span>  
  
 <span data-ttu-id="93425-152">左運算元值：</span><span class="sxs-lookup"><span data-stu-id="93425-152">Left Operand Value:</span></span>  
  
 <span data-ttu-id="93425-153">右運算元值：</span><span class="sxs-lookup"><span data-stu-id="93425-153">Right Operand Value:</span></span>  
  
 <span data-ttu-id="93425-154">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-154">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-155">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-155">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-156">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-156">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-157">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-157">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-158">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-158">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-159">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-159">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-160">物件執行個體識別碼： 177556</span><span class="sxs-lookup"><span data-stu-id="93425-160">Object Instance Identifier: 177556</span></span>  
  
 <span data-ttu-id="93425-161">議程更新 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-161">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-162">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-162">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-163">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-163">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-164">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-164">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-165">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-165">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-166">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-166">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-167">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-167">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-168">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-168">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-169">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-169">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-170">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-170">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-171">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-171">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-172">物件執行個體識別碼： 177559</span><span class="sxs-lookup"><span data-stu-id="93425-172">Object Instance Identifier: 177559</span></span>  
  
 <span data-ttu-id="93425-173">議程更新 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-173">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-174">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-174">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-175">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-175">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-176">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-176">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-177">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-177">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-178">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-178">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-179">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-179">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-180">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-180">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-181">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-181">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-182">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-182">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-183">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-183">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-184">物件執行個體識別碼： 177558</span><span class="sxs-lookup"><span data-stu-id="93425-184">Object Instance Identifier: 177558</span></span>  
  
 <span data-ttu-id="93425-185">議程更新 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-185">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-186">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-186">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-187">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-187">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-188">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-188">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-189">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-189">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-190">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-190">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-191">規則被引發 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-191">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-192">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-192">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-193">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-193">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-194">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-194">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-195">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-195">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-196">規則被引發 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-196">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-197">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-197">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-198">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-198">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-199">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-199">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-200">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-200">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-201">規則被引發 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-201">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-202">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-202">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-203">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-203">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-204">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-204">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-205">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-205">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-206">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-206">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-207">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-207">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-208">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-208">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-209">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-209">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-210">物件類型： DataConnection:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-210">Object Type: DataConnection:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-211">物件執行個體識別碼： 874</span><span class="sxs-lookup"><span data-stu-id="93425-211">Object Instance Identifier: 874</span></span>  
  
 <span data-ttu-id="93425-212">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-212">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-213">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-213">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-214">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-214">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-215">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-215">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-216">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-216">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-217">物件執行個體識別碼： 177559</span><span class="sxs-lookup"><span data-stu-id="93425-217">Object Instance Identifier: 177559</span></span>  
  
 <span data-ttu-id="93425-218">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-218">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-219">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-219">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-220">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-220">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-221">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-221">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-222">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-222">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-223">物件執行個體識別碼： 177558</span><span class="sxs-lookup"><span data-stu-id="93425-223">Object Instance Identifier: 177558</span></span>  
  
 <span data-ttu-id="93425-224">事實活動 3/16/2004年 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="93425-224">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="93425-225">規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="93425-225">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="93425-226">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-226">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-227">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-227">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-228">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-228">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-229">物件執行個體識別碼： 177556</span><span class="sxs-lookup"><span data-stu-id="93425-229">Object Instance Identifier: 177556</span></span>  
  
 <span data-ttu-id="93425-230">上述範例指出 CustInfo 表格中有三列符合規則中的條件。</span><span class="sxs-lookup"><span data-stu-id="93425-230">The example above indicates that three rows in the CustInfo table met the condition in the rule.</span></span>  <span data-ttu-id="93425-231">這導致三個唯一的 TypedDataRows 判斷提示至引擎，並造成每個執行個體發生議程更新和規則引發。</span><span class="sxs-lookup"><span data-stu-id="93425-231">This caused three unique TypedDataRows to be asserted into the engine and an agenda update and rule firing to occur for each instance.</span></span>  
  
## <a name="typedatatabletypeddatarow"></a><span data-ttu-id="93425-232">TypeDataTable/TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="93425-232">TypeDataTable/TypedDataRow</span></span>  
 <span data-ttu-id="93425-233">原則 "LoanProcessing" 中的範例規則 "TestRule1"：</span><span class="sxs-lookup"><span data-stu-id="93425-233">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="93425-234">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="93425-234">**Output:**</span></span>  
  
 <span data-ttu-id="93425-235">規則集的規則引擎追蹤： LoanProcessing 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-235">RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-236">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-236">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-237">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-237">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-238">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-238">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-239">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-239">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-240">物件類型： TypedDataTable:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-240">Object Type: TypedDataTable:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-241">物件執行個體識別碼： 377</span><span class="sxs-lookup"><span data-stu-id="93425-241">Object Instance Identifier: 377</span></span>  
  
 <span data-ttu-id="93425-242">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-242">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-243">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-243">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-244">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-244">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-245">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-245">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-246">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-246">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-247">物件執行個體識別碼： 376</span><span class="sxs-lookup"><span data-stu-id="93425-247">Object Instance Identifier: 376</span></span>  
  
 <span data-ttu-id="93425-248">條件評估測試 (符合) 3/17/2004 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-248">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-249">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-249">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-250">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-250">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-251">測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="93425-251">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="93425-252">左運算元值： 500</span><span class="sxs-lookup"><span data-stu-id="93425-252">Left Operand Value: 500</span></span>  
  
 <span data-ttu-id="93425-253">右運算元值： 0</span><span class="sxs-lookup"><span data-stu-id="93425-253">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="93425-254">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-254">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-255">議程更新 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-255">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-256">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-256">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-257">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-257">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-258">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-258">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-259">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-259">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-260">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-260">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-261">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-261">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-262">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-262">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-263">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-263">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-264">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-264">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-265">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-265">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-266">物件執行個體識別碼： 375</span><span class="sxs-lookup"><span data-stu-id="93425-266">Object Instance Identifier: 375</span></span>  
  
 <span data-ttu-id="93425-267">條件評估測試 (符合) 3/17/2004 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-267">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-268">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-268">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-269">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-269">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-270">測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="93425-270">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="93425-271">左運算元值： 1000年</span><span class="sxs-lookup"><span data-stu-id="93425-271">Left Operand Value: 1000</span></span>  
  
 <span data-ttu-id="93425-272">右運算元值： 0</span><span class="sxs-lookup"><span data-stu-id="93425-272">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="93425-273">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-273">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-274">議程更新 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-274">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-275">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-275">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-276">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-276">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-277">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-277">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-278">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-278">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-279">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-279">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-280">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-280">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-281">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-281">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-282">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-282">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-283">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-283">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-284">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-284">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-285">物件執行個體識別碼： 374</span><span class="sxs-lookup"><span data-stu-id="93425-285">Object Instance Identifier: 374</span></span>  
  
 <span data-ttu-id="93425-286">條件評估測試 (符合) 3/17/2004 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-286">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-287">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-287">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-288">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-288">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-289">測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="93425-289">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="93425-290">左運算元值： 35000</span><span class="sxs-lookup"><span data-stu-id="93425-290">Left Operand Value: 35000</span></span>  
  
 <span data-ttu-id="93425-291">右運算元值： 0</span><span class="sxs-lookup"><span data-stu-id="93425-291">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="93425-292">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-292">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-293">議程更新 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-293">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-294">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-294">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-295">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-295">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-296">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-296">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-297">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-297">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-298">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-298">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-299">規則被引發 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-299">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-300">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-300">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-301">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-301">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-302">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-302">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-303">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-303">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-304">規則被引發 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-304">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-305">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-305">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-306">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-306">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-307">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-307">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-308">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-308">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-309">規則被引發 3/17/2004年 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-309">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-310">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-310">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-311">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-311">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-312">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-312">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-313">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-313">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-314">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-314">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-315">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-315">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-316">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-316">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-317">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-317">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-318">物件類型： TypedDataTable:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-318">Object Type: TypedDataTable:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-319">物件執行個體識別碼： 377</span><span class="sxs-lookup"><span data-stu-id="93425-319">Object Instance Identifier: 377</span></span>  
  
 <span data-ttu-id="93425-320">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-320">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-321">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-321">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-322">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-322">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-323">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-323">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-324">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-324">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-325">物件執行個體識別碼： 375</span><span class="sxs-lookup"><span data-stu-id="93425-325">Object Instance Identifier: 375</span></span>  
  
 <span data-ttu-id="93425-326">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-326">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-327">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-327">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-328">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-328">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-329">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-329">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-330">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-330">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-331">物件執行個體識別碼： 374</span><span class="sxs-lookup"><span data-stu-id="93425-331">Object Instance Identifier: 374</span></span>  
  
 <span data-ttu-id="93425-332">事實活動 17.03.04 11:27:35 AM</span><span class="sxs-lookup"><span data-stu-id="93425-332">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="93425-333">規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="93425-333">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="93425-334">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-334">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-335">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-335">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-336">物件類型： TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="93425-336">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="93425-337">物件執行個體識別碼： 376</span><span class="sxs-lookup"><span data-stu-id="93425-337">Object Instance Identifier: 376</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93425-338">上述範例顯示 TypedDataTable 包含三個資料列，且會將每一個資料列判斷提示為 TypedDataRow。</span><span class="sxs-lookup"><span data-stu-id="93425-338">The example above shows that the TypedDataTable contained three rows, and each was asserted as a TypedDataRow.</span></span>  <span data-ttu-id="93425-339">每個資料列在條件中都會評估為 True，且會造成規則新增至議程並引發規則。</span><span class="sxs-lookup"><span data-stu-id="93425-339">Each evaluated to True in the condition and caused the rule to be added to the agenda and fired.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="93425-340">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="93425-340">TypedXmlDocument</span></span>  
 <span data-ttu-id="93425-341">原則 "LoanProcessing" 中的範例規則 "TestRule1"：</span><span class="sxs-lookup"><span data-stu-id="93425-341">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
THEN <do something>  
```  
  
 <span data-ttu-id="93425-342">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="93425-342">**Output:**</span></span>  
  
 <span data-ttu-id="93425-343">規則集的規則引擎追蹤： LoanProcessing 2004 年 3 月 17 日上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-343">RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-344">事實活動 2004 年 3 月 17 日上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-344">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-345">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-345">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-346">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-346">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-347">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-347">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-348">物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span><span class="sxs-lookup"><span data-stu-id="93425-348">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span></span>  
  
 <span data-ttu-id="93425-349">物件執行個體識別碼： 858</span><span class="sxs-lookup"><span data-stu-id="93425-349">Object Instance Identifier: 858</span></span>  
  
 <span data-ttu-id="93425-350">事實活動 2004 年 3 月 17 日上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-350">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-351">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-351">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-352">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-352">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-353">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-353">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-354">物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span><span class="sxs-lookup"><span data-stu-id="93425-354">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span></span>  
  
 <span data-ttu-id="93425-355">物件執行個體識別碼： 853</span><span class="sxs-lookup"><span data-stu-id="93425-355">Object Instance Identifier: 853</span></span>  
  
 <span data-ttu-id="93425-356">條件評估測試 （符合） 3/17/2004年上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-356">CONDITION EVALUATION TEST (MATCH) 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-357">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-357">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-358">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-358">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-359">測試運算式： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths > = 4</span><span class="sxs-lookup"><span data-stu-id="93425-359">Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4</span></span>  
  
 <span data-ttu-id="93425-360">左運算元值： 6</span><span class="sxs-lookup"><span data-stu-id="93425-360">Left Operand Value: 6</span></span>  
  
 <span data-ttu-id="93425-361">右運算元值： 4</span><span class="sxs-lookup"><span data-stu-id="93425-361">Right Operand Value: 4</span></span>  
  
 <span data-ttu-id="93425-362">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-362">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-363">議程更新 3/17/2004年上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-363">AGENDA UPDATE 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-364">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-364">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-365">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-365">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-366">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-366">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-367">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-367">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-368">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-368">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-369">規則被引發 3/17/2004年上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-369">RULE FIRED 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-370">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-370">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-371">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-371">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-372">規則名稱： TestRule1</span><span class="sxs-lookup"><span data-stu-id="93425-372">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="93425-373">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-373">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-374">事實活動 2004 年 3 月 17 日上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-374">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-375">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-375">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-376">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-376">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-377">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-377">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-378">物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span><span class="sxs-lookup"><span data-stu-id="93425-378">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span></span>  
  
 <span data-ttu-id="93425-379">物件執行個體識別碼： 858</span><span class="sxs-lookup"><span data-stu-id="93425-379">Object Instance Identifier: 858</span></span>  
  
 <span data-ttu-id="93425-380">事實活動 2004 年 3 月 17 日上午 9:23:05</span><span class="sxs-lookup"><span data-stu-id="93425-380">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="93425-381">規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="93425-381">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="93425-382">規則集名稱：LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="93425-382">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="93425-383">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-383">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-384">物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span><span class="sxs-lookup"><span data-stu-id="93425-384">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span></span>  
  
 <span data-ttu-id="93425-385">物件執行個體識別碼： 853</span><span class="sxs-lookup"><span data-stu-id="93425-385">Object Instance Identifier: 853</span></span>  
  
 <span data-ttu-id="93425-386">這個範例將示範**TypedXmlDocument**已判斷提示至引擎，以"microsoft.samples.biztalk.loansprocessor.case"的文件類型。</span><span class="sxs-lookup"><span data-stu-id="93425-386">This example shows that a **TypedXmlDocument** was asserted into the engine with a document type of "Microsoft.Samples.BizTalk.LoansProcessor.Case".</span></span>  <span data-ttu-id="93425-387">根據規則中定義的 XPath 選取器，引擎接著會依據文件類型與選取器字串，以 "Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType" 類型來建立和判斷提示子 TypedXmlDocument。</span><span class="sxs-lookup"><span data-stu-id="93425-387">Based on the XPath selector defined in the rule, the engine then created and asserted a child TypedXmlDocument with type  "Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType" based on the document type and selector string.</span></span>  
  
 <span data-ttu-id="93425-388">此子 TypedXmlDocument 在條件中評估為 True，造成議程更新和規則引發。</span><span class="sxs-lookup"><span data-stu-id="93425-388">This child TypedXmlDocument evaluated to True in the condition, causing an agenda update and rule firing.</span></span>  <span data-ttu-id="93425-389">父和子**TypedXmlDocument**的然後撤回。</span><span class="sxs-lookup"><span data-stu-id="93425-389">The parent and child **TypedXmlDocument**'s were then retracted.</span></span>  
  
## <a name="update-function"></a><span data-ttu-id="93425-390">更新功能</span><span class="sxs-lookup"><span data-stu-id="93425-390">Update Function</span></span>  
 <span data-ttu-id="93425-391">範例原則 "Order"</span><span class="sxs-lookup"><span data-stu-id="93425-391">Example policy "Order"</span></span>  
  
 <span data-ttu-id="93425-392">**"InventoryCheck"規則**</span><span class="sxs-lookup"><span data-stu-id="93425-392">**"InventoryCheck" Rule**</span></span>  
  
```  
IF Inventory.AllocateInventory == True  
THEN Order.inventoryAvailable == True  
   Update(Order)  
```  
  
 <span data-ttu-id="93425-393">**"Ship"規則**</span><span class="sxs-lookup"><span data-stu-id="93425-393">**"Ship" Rule**</span></span>  
  
```  
IF Order.inventoryAvailable == True  
THEN Shipment.ShipOrder  
```  
  
 <span data-ttu-id="93425-394">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="93425-394">**Output:**</span></span>  
  
 <span data-ttu-id="93425-395">規則集的規則引擎追蹤： 排序 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-395">RULE ENGINE TRACE for RULESET: Order 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-396">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-396">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-397">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-397">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-398">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-398">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-399">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-399">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-400">物件類型： TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="93425-400">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="93425-401">物件執行個體識別碼： 448</span><span class="sxs-lookup"><span data-stu-id="93425-401">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="93425-402">條件評估測試 （符合） 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-402">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-403">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-403">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-404">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-404">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-405">測試運算式： TestClasses.Order.inventoryAvailable = = True</span><span class="sxs-lookup"><span data-stu-id="93425-405">Test Expression: TestClasses.Order.inventoryAvailable == True</span></span>  
  
 <span data-ttu-id="93425-406">左運算元值： null</span><span class="sxs-lookup"><span data-stu-id="93425-406">Left Operand Value: null</span></span>  
  
 <span data-ttu-id="93425-407">右運算元值： True</span><span class="sxs-lookup"><span data-stu-id="93425-407">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="93425-408">測試結果： False</span><span class="sxs-lookup"><span data-stu-id="93425-408">Test Result: False</span></span>  
  
 <span data-ttu-id="93425-409">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-409">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-410">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-410">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-411">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-411">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-412">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-412">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-413">物件類型： TestClasses.Shipment</span><span class="sxs-lookup"><span data-stu-id="93425-413">Object Type: TestClasses.Shipment</span></span>  
  
 <span data-ttu-id="93425-414">物件執行個體識別碼： 447</span><span class="sxs-lookup"><span data-stu-id="93425-414">Object Instance Identifier: 447</span></span>  
  
 <span data-ttu-id="93425-415">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-415">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-416">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-416">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-417">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-417">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-418">作業：判斷提示</span><span class="sxs-lookup"><span data-stu-id="93425-418">Operation: Assert</span></span>  
  
 <span data-ttu-id="93425-419">物件類型： TestClasses.Inventory</span><span class="sxs-lookup"><span data-stu-id="93425-419">Object Type: TestClasses.Inventory</span></span>  
  
 <span data-ttu-id="93425-420">物件執行個體識別碼： 446</span><span class="sxs-lookup"><span data-stu-id="93425-420">Object Instance Identifier: 446</span></span>  
  
 <span data-ttu-id="93425-421">條件評估測試 （符合） 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-421">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-422">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-422">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-423">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-423">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-424">測試運算式： TestClasses.Inventory.AllocateInventory = = True</span><span class="sxs-lookup"><span data-stu-id="93425-424">Test Expression: TestClasses.Inventory.AllocateInventory == True</span></span>  
  
 <span data-ttu-id="93425-425">左運算元值： True</span><span class="sxs-lookup"><span data-stu-id="93425-425">Left Operand Value: True</span></span>  
  
 <span data-ttu-id="93425-426">右運算元值： True</span><span class="sxs-lookup"><span data-stu-id="93425-426">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="93425-427">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-427">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-428">議程更新 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-428">AGENDA UPDATE 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-429">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-429">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-430">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-430">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-431">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-431">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-432">規則名稱： InventoryCheck</span><span class="sxs-lookup"><span data-stu-id="93425-432">Rule Name: InventoryCheck</span></span>  
  
 <span data-ttu-id="93425-433">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-433">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-434">規則被引發 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-434">RULE FIRED 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-435">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-435">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-436">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-436">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-437">規則名稱： InventoryCheck</span><span class="sxs-lookup"><span data-stu-id="93425-437">Rule Name: InventoryCheck</span></span>  
  
 <span data-ttu-id="93425-438">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-438">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-439">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-439">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-440">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-440">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-441">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-441">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-442">作業： 更新</span><span class="sxs-lookup"><span data-stu-id="93425-442">Operation: Update</span></span>  
  
 <span data-ttu-id="93425-443">物件類型： TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="93425-443">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="93425-444">物件執行個體識別碼： 448</span><span class="sxs-lookup"><span data-stu-id="93425-444">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="93425-445">條件評估測試 （符合） 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-445">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-446">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-446">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-447">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-447">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-448">測試運算式： TestClasses.Order.inventoryAvailable = = True</span><span class="sxs-lookup"><span data-stu-id="93425-448">Test Expression: TestClasses.Order.inventoryAvailable == True</span></span>  
  
 <span data-ttu-id="93425-449">左運算元值： True</span><span class="sxs-lookup"><span data-stu-id="93425-449">Left Operand Value: True</span></span>  
  
 <span data-ttu-id="93425-450">右運算元值： True</span><span class="sxs-lookup"><span data-stu-id="93425-450">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="93425-451">測試結果：True</span><span class="sxs-lookup"><span data-stu-id="93425-451">Test Result: True</span></span>  
  
 <span data-ttu-id="93425-452">議程更新 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-452">AGENDA UPDATE 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-453">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-453">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-454">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-454">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-455">作業：新增</span><span class="sxs-lookup"><span data-stu-id="93425-455">Operation: Add</span></span>  
  
 <span data-ttu-id="93425-456">規則名稱： 出貨</span><span class="sxs-lookup"><span data-stu-id="93425-456">Rule Name: Ship</span></span>  
  
 <span data-ttu-id="93425-457">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-457">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-458">規則被引發 3/17/2004年 10:31:17 AM</span><span class="sxs-lookup"><span data-stu-id="93425-458">RULE FIRED 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-459">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-459">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-460">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-460">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-461">規則名稱： 出貨</span><span class="sxs-lookup"><span data-stu-id="93425-461">Rule Name: Ship</span></span>  
  
 <span data-ttu-id="93425-462">衝突解決準則： 0</span><span class="sxs-lookup"><span data-stu-id="93425-462">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="93425-463">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-463">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-464">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-464">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-465">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-465">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-466">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-466">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-467">物件類型： TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="93425-467">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="93425-468">物件執行個體識別碼： 448</span><span class="sxs-lookup"><span data-stu-id="93425-468">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="93425-469">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-469">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-470">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-470">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-471">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-471">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-472">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-472">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-473">物件類型： TestClasses.Shipment</span><span class="sxs-lookup"><span data-stu-id="93425-473">Object Type: TestClasses.Shipment</span></span>  
  
 <span data-ttu-id="93425-474">物件執行個體識別碼： 447</span><span class="sxs-lookup"><span data-stu-id="93425-474">Object Instance Identifier: 447</span></span>  
  
 <span data-ttu-id="93425-475">事實活動 2004 年 3 月 17 日上午 10:31:17</span><span class="sxs-lookup"><span data-stu-id="93425-475">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="93425-476">規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="93425-476">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="93425-477">規則集名稱： 順序</span><span class="sxs-lookup"><span data-stu-id="93425-477">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="93425-478">作業： 撤銷</span><span class="sxs-lookup"><span data-stu-id="93425-478">Operation: Retract</span></span>  
  
 <span data-ttu-id="93425-479">物件類型： TestClasses.Inventory</span><span class="sxs-lookup"><span data-stu-id="93425-479">Object Type: TestClasses.Inventory</span></span>  
  
 <span data-ttu-id="93425-480">物件執行個體識別碼： 446</span><span class="sxs-lookup"><span data-stu-id="93425-480">Object Instance Identifier: 446</span></span>  
  
 <span data-ttu-id="93425-481">在此範例中，在第一次檢查與 Ship 規則相關聯的條件時，它會評估為 False。</span><span class="sxs-lookup"><span data-stu-id="93425-481">In this example, the condition associated with the Ship rule evaluates to False the first time it is checked.</span></span>  <span data-ttu-id="93425-482">但是，當 InventoryCheck 規則引發時，Order 的 inventoryAvailable 欄位會變更，且在引擎上發出對 Order 物件更新命令。</span><span class="sxs-lookup"><span data-stu-id="93425-482">However, when the InventoryCheck rule fires, the inventoryAvailable field on the Order is changed and an Update command is issued on the engine for the Order object.</span></span>  <span data-ttu-id="93425-483">這會造成重新評估 Ship 規則。</span><span class="sxs-lookup"><span data-stu-id="93425-483">This causes the Ship rule to be reevaluated.</span></span>  <span data-ttu-id="93425-484">這一次，此條件會評估為 True，並引發 Ship 規則。</span><span class="sxs-lookup"><span data-stu-id="93425-484">This time the condition evaluates to true and the Ship rule fires.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93425-485">如果您的規則撰寫不正確，使用更新功能正向鏈結可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="93425-485">If your rules are written incorrectly, forward chaining with the Update function may cause an infinite loop.</span></span>  <span data-ttu-id="93425-486">若發生此情況，您會在商務規則編輯器中測試原則時，收到文字為「規則引擎偵測到執行迴圈」的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="93425-486">If this occurs, you will receive an error message when testing the policy in the Business Rule Composer with the text "The rule engine detected an execution loop."</span></span>