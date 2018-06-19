---
title: EDI 群組結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 100a7118-9c02-474e-8685-9e4bb6f52e81
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555d7b86e069adda4f7761b698793fd4ec2af721
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242518"
---
# <a name="edi-group-structural-element"></a><span data-ttu-id="0a623-102">EDI 群組結構元素</span><span class="sxs-lookup"><span data-stu-id="0a623-102">EDI Group Structural Element</span></span>
<span data-ttu-id="0a623-103">群組包含一或多個交易集。</span><span class="sxs-lookup"><span data-stu-id="0a623-103">The group contains one or more transaction sets.</span></span> <span data-ttu-id="0a623-104">EDIFACT 群組必須包含相同類型的交易集。</span><span class="sxs-lookup"><span data-stu-id="0a623-104">An EDIFACT group must contain transaction sets of the same type.</span></span> <span data-ttu-id="0a623-105">X12 群組包含交易集類似類型的 （根據交易集 – 群組對應 (GS01 ST01)） 或型別相同的交易集。</span><span class="sxs-lookup"><span data-stu-id="0a623-105">An X12 group may contain transaction sets of similar type (based on the transaction set – group (GS01-ST01) mapping) or transaction sets of the same type.</span></span> <span data-ttu-id="0a623-106">下表列出類似 X12 交易集 (ST01)，可以在單一群組 (GS01) 一起出現。</span><span class="sxs-lookup"><span data-stu-id="0a623-106">The table below lists similar X12 transaction sets (ST01), which can occur together in a single group (GS01).</span></span>  
  
|<span data-ttu-id="0a623-107">GS01</span><span class="sxs-lookup"><span data-stu-id="0a623-107">GS01</span></span>|<span data-ttu-id="0a623-108">ST01</span><span class="sxs-lookup"><span data-stu-id="0a623-108">ST01</span></span>|  
|----------|----------|  
|<span data-ttu-id="0a623-109">CF</span><span class="sxs-lookup"><span data-stu-id="0a623-109">CF</span></span>|<span data-ttu-id="0a623-110">844</span><span class="sxs-lookup"><span data-stu-id="0a623-110">844</span></span>|  
|<span data-ttu-id="0a623-111">CF</span><span class="sxs-lookup"><span data-stu-id="0a623-111">CF</span></span>|<span data-ttu-id="0a623-112">849</span><span class="sxs-lookup"><span data-stu-id="0a623-112">849</span></span>|  
|<span data-ttu-id="0a623-113">DX</span><span class="sxs-lookup"><span data-stu-id="0a623-113">DX</span></span>|<span data-ttu-id="0a623-114">894</span><span class="sxs-lookup"><span data-stu-id="0a623-114">894</span></span>|  
|<span data-ttu-id="0a623-115">DX</span><span class="sxs-lookup"><span data-stu-id="0a623-115">DX</span></span>|<span data-ttu-id="0a623-116">895</span><span class="sxs-lookup"><span data-stu-id="0a623-116">895</span></span>|  
|<span data-ttu-id="0a623-117">FR</span><span class="sxs-lookup"><span data-stu-id="0a623-117">FR</span></span>|<span data-ttu-id="0a623-118">821</span><span class="sxs-lookup"><span data-stu-id="0a623-118">821</span></span>|  
|<span data-ttu-id="0a623-119">FR</span><span class="sxs-lookup"><span data-stu-id="0a623-119">FR</span></span>|<span data-ttu-id="0a623-120">827</span><span class="sxs-lookup"><span data-stu-id="0a623-120">827</span></span>|  
|<span data-ttu-id="0a623-121">GC</span><span class="sxs-lookup"><span data-stu-id="0a623-121">GC</span></span>|<span data-ttu-id="0a623-122">920</span><span class="sxs-lookup"><span data-stu-id="0a623-122">920</span></span>|  
|<span data-ttu-id="0a623-123">GC</span><span class="sxs-lookup"><span data-stu-id="0a623-123">GC</span></span>|<span data-ttu-id="0a623-124">924</span><span class="sxs-lookup"><span data-stu-id="0a623-124">924</span></span>|  
|<span data-ttu-id="0a623-125">GC</span><span class="sxs-lookup"><span data-stu-id="0a623-125">GC</span></span>|<span data-ttu-id="0a623-126">925</span><span class="sxs-lookup"><span data-stu-id="0a623-126">925</span></span>|  
|<span data-ttu-id="0a623-127">GC</span><span class="sxs-lookup"><span data-stu-id="0a623-127">GC</span></span>|<span data-ttu-id="0a623-128">926</span><span class="sxs-lookup"><span data-stu-id="0a623-128">926</span></span>|  
|<span data-ttu-id="0a623-129">HC</span><span class="sxs-lookup"><span data-stu-id="0a623-129">HC</span></span>|<span data-ttu-id="0a623-130">837</span><span class="sxs-lookup"><span data-stu-id="0a623-130">837</span></span>|  
|<span data-ttu-id="0a623-131">HC</span><span class="sxs-lookup"><span data-stu-id="0a623-131">HC</span></span>|<span data-ttu-id="0a623-132">837_D</span><span class="sxs-lookup"><span data-stu-id="0a623-132">837_D</span></span>|  
|<span data-ttu-id="0a623-133">HC</span><span class="sxs-lookup"><span data-stu-id="0a623-133">HC</span></span>|<span data-ttu-id="0a623-134">837_I</span><span class="sxs-lookup"><span data-stu-id="0a623-134">837_I</span></span>|  
|<span data-ttu-id="0a623-135">HC</span><span class="sxs-lookup"><span data-stu-id="0a623-135">HC</span></span>|<span data-ttu-id="0a623-136">837_P</span><span class="sxs-lookup"><span data-stu-id="0a623-136">837_P</span></span>|  
|<span data-ttu-id="0a623-137">採用 IA-64</span><span class="sxs-lookup"><span data-stu-id="0a623-137">IA</span></span>|<span data-ttu-id="0a623-138">110</span><span class="sxs-lookup"><span data-stu-id="0a623-138">110</span></span>|  
|<span data-ttu-id="0a623-139">採用 IA-64</span><span class="sxs-lookup"><span data-stu-id="0a623-139">IA</span></span>|<span data-ttu-id="0a623-140">980</span><span class="sxs-lookup"><span data-stu-id="0a623-140">980</span></span>|  
|<span data-ttu-id="0a623-141">IO</span><span class="sxs-lookup"><span data-stu-id="0a623-141">IO</span></span>|<span data-ttu-id="0a623-142">310</span><span class="sxs-lookup"><span data-stu-id="0a623-142">310</span></span>|  
|<span data-ttu-id="0a623-143">IO</span><span class="sxs-lookup"><span data-stu-id="0a623-143">IO</span></span>|<span data-ttu-id="0a623-144">312</span><span class="sxs-lookup"><span data-stu-id="0a623-144">312</span></span>|  
|<span data-ttu-id="0a623-145">我</span><span class="sxs-lookup"><span data-stu-id="0a623-145">ME</span></span>|<span data-ttu-id="0a623-146">198</span><span class="sxs-lookup"><span data-stu-id="0a623-146">198</span></span>|  
|<span data-ttu-id="0a623-147">我</span><span class="sxs-lookup"><span data-stu-id="0a623-147">ME</span></span>|<span data-ttu-id="0a623-148">200</span><span class="sxs-lookup"><span data-stu-id="0a623-148">200</span></span>|  
|<span data-ttu-id="0a623-149">我</span><span class="sxs-lookup"><span data-stu-id="0a623-149">ME</span></span>|<span data-ttu-id="0a623-150">201</span><span class="sxs-lookup"><span data-stu-id="0a623-150">201</span></span>|  
|<span data-ttu-id="0a623-151">我</span><span class="sxs-lookup"><span data-stu-id="0a623-151">ME</span></span>|<span data-ttu-id="0a623-152">245</span><span class="sxs-lookup"><span data-stu-id="0a623-152">245</span></span>|  
|<span data-ttu-id="0a623-153">我</span><span class="sxs-lookup"><span data-stu-id="0a623-153">ME</span></span>|<span data-ttu-id="0a623-154">261</span><span class="sxs-lookup"><span data-stu-id="0a623-154">261</span></span>|  
|<span data-ttu-id="0a623-155">我</span><span class="sxs-lookup"><span data-stu-id="0a623-155">ME</span></span>|<span data-ttu-id="0a623-156">262</span><span class="sxs-lookup"><span data-stu-id="0a623-156">262</span></span>|  
|<span data-ttu-id="0a623-157">我</span><span class="sxs-lookup"><span data-stu-id="0a623-157">ME</span></span>|<span data-ttu-id="0a623-158">263</span><span class="sxs-lookup"><span data-stu-id="0a623-158">263</span></span>|  
|<span data-ttu-id="0a623-159">我</span><span class="sxs-lookup"><span data-stu-id="0a623-159">ME</span></span>|<span data-ttu-id="0a623-160">833</span><span class="sxs-lookup"><span data-stu-id="0a623-160">833</span></span>|  
|<span data-ttu-id="0a623-161">我</span><span class="sxs-lookup"><span data-stu-id="0a623-161">ME</span></span>|<span data-ttu-id="0a623-162">872</span><span class="sxs-lookup"><span data-stu-id="0a623-162">872</span></span>|  
|<span data-ttu-id="0a623-163">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-163">MG</span></span>|<span data-ttu-id="0a623-164">203</span><span class="sxs-lookup"><span data-stu-id="0a623-164">203</span></span>|  
|<span data-ttu-id="0a623-165">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-165">MG</span></span>|<span data-ttu-id="0a623-166">206</span><span class="sxs-lookup"><span data-stu-id="0a623-166">206</span></span>|  
|<span data-ttu-id="0a623-167">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-167">MG</span></span>|<span data-ttu-id="0a623-168">259</span><span class="sxs-lookup"><span data-stu-id="0a623-168">259</span></span>|  
|<span data-ttu-id="0a623-169">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-169">MG</span></span>|<span data-ttu-id="0a623-170">260</span><span class="sxs-lookup"><span data-stu-id="0a623-170">260</span></span>|  
|<span data-ttu-id="0a623-171">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-171">MG</span></span>|<span data-ttu-id="0a623-172">264</span><span class="sxs-lookup"><span data-stu-id="0a623-172">264</span></span>|  
|<span data-ttu-id="0a623-173">MG</span><span class="sxs-lookup"><span data-stu-id="0a623-173">MG</span></span>|<span data-ttu-id="0a623-174">266</span><span class="sxs-lookup"><span data-stu-id="0a623-174">266</span></span>|  
|<span data-ttu-id="0a623-175">OG</span><span class="sxs-lookup"><span data-stu-id="0a623-175">OG</span></span>|<span data-ttu-id="0a623-176">875</span><span class="sxs-lookup"><span data-stu-id="0a623-176">875</span></span>|  
|<span data-ttu-id="0a623-177">OG</span><span class="sxs-lookup"><span data-stu-id="0a623-177">OG</span></span>|<span data-ttu-id="0a623-178">876</span><span class="sxs-lookup"><span data-stu-id="0a623-178">876</span></span>|  
|<span data-ttu-id="0a623-179">PK</span><span class="sxs-lookup"><span data-stu-id="0a623-179">PK</span></span>|<span data-ttu-id="0a623-180">196</span><span class="sxs-lookup"><span data-stu-id="0a623-180">196</span></span>|  
|<span data-ttu-id="0a623-181">PK</span><span class="sxs-lookup"><span data-stu-id="0a623-181">PK</span></span>|<span data-ttu-id="0a623-182">839</span><span class="sxs-lookup"><span data-stu-id="0a623-182">839</span></span>|  
|<span data-ttu-id="0a623-183">QG</span><span class="sxs-lookup"><span data-stu-id="0a623-183">QG</span></span>|<span data-ttu-id="0a623-184">878</span><span class="sxs-lookup"><span data-stu-id="0a623-184">878</span></span>|  
|<span data-ttu-id="0a623-185">QG</span><span class="sxs-lookup"><span data-stu-id="0a623-185">QG</span></span>|<span data-ttu-id="0a623-186">879</span><span class="sxs-lookup"><span data-stu-id="0a623-186">879</span></span>|  
|<span data-ttu-id="0a623-187">QG</span><span class="sxs-lookup"><span data-stu-id="0a623-187">QG</span></span>|<span data-ttu-id="0a623-188">888</span><span class="sxs-lookup"><span data-stu-id="0a623-188">888</span></span>|  
|<span data-ttu-id="0a623-189">QG</span><span class="sxs-lookup"><span data-stu-id="0a623-189">QG</span></span>|<span data-ttu-id="0a623-190">889</span><span class="sxs-lookup"><span data-stu-id="0a623-190">889</span></span>|  
|<span data-ttu-id="0a623-191">QG</span><span class="sxs-lookup"><span data-stu-id="0a623-191">QG</span></span>|<span data-ttu-id="0a623-192">896</span><span class="sxs-lookup"><span data-stu-id="0a623-192">896</span></span>|  
|<span data-ttu-id="0a623-193">QO</span><span class="sxs-lookup"><span data-stu-id="0a623-193">QO</span></span>|<span data-ttu-id="0a623-194">313</span><span class="sxs-lookup"><span data-stu-id="0a623-194">313</span></span>|  
|<span data-ttu-id="0a623-195">QO</span><span class="sxs-lookup"><span data-stu-id="0a623-195">QO</span></span>|<span data-ttu-id="0a623-196">315</span><span class="sxs-lookup"><span data-stu-id="0a623-196">315</span></span>|  
|<span data-ttu-id="0a623-197">RO</span><span class="sxs-lookup"><span data-stu-id="0a623-197">RO</span></span>|<span data-ttu-id="0a623-198">300</span><span class="sxs-lookup"><span data-stu-id="0a623-198">300</span></span>|  
|<span data-ttu-id="0a623-199">RO</span><span class="sxs-lookup"><span data-stu-id="0a623-199">RO</span></span>|<span data-ttu-id="0a623-200">301</span><span class="sxs-lookup"><span data-stu-id="0a623-200">301</span></span>|  
|<span data-ttu-id="0a623-201">RO</span><span class="sxs-lookup"><span data-stu-id="0a623-201">RO</span></span>|<span data-ttu-id="0a623-202">303</span><span class="sxs-lookup"><span data-stu-id="0a623-202">303</span></span>|  
|<span data-ttu-id="0a623-203">RQ</span><span class="sxs-lookup"><span data-stu-id="0a623-203">RQ</span></span>|<span data-ttu-id="0a623-204">836</span><span class="sxs-lookup"><span data-stu-id="0a623-204">836</span></span>|  
|<span data-ttu-id="0a623-205">RQ</span><span class="sxs-lookup"><span data-stu-id="0a623-205">RQ</span></span>|<span data-ttu-id="0a623-206">840</span><span class="sxs-lookup"><span data-stu-id="0a623-206">840</span></span>|  
|<span data-ttu-id="0a623-207">RS</span><span class="sxs-lookup"><span data-stu-id="0a623-207">RS</span></span>|<span data-ttu-id="0a623-208">869</span><span class="sxs-lookup"><span data-stu-id="0a623-208">869</span></span>|  
|<span data-ttu-id="0a623-209">RS</span><span class="sxs-lookup"><span data-stu-id="0a623-209">RS</span></span>|<span data-ttu-id="0a623-210">870</span><span class="sxs-lookup"><span data-stu-id="0a623-210">870</span></span>|  
|<span data-ttu-id="0a623-211">SL</span><span class="sxs-lookup"><span data-stu-id="0a623-211">SL</span></span>|<span data-ttu-id="0a623-212">135</span><span class="sxs-lookup"><span data-stu-id="0a623-212">135</span></span>|  
|<span data-ttu-id="0a623-213">SL</span><span class="sxs-lookup"><span data-stu-id="0a623-213">SL</span></span>|<span data-ttu-id="0a623-214">139</span><span class="sxs-lookup"><span data-stu-id="0a623-214">139</span></span>|  
|<span data-ttu-id="0a623-215">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-215">SO</span></span>|<span data-ttu-id="0a623-216">302</span><span class="sxs-lookup"><span data-stu-id="0a623-216">302</span></span>|  
|<span data-ttu-id="0a623-217">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-217">SO</span></span>|<span data-ttu-id="0a623-218">311</span><span class="sxs-lookup"><span data-stu-id="0a623-218">311</span></span>|  
|<span data-ttu-id="0a623-219">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-219">SO</span></span>|<span data-ttu-id="0a623-220">317</span><span class="sxs-lookup"><span data-stu-id="0a623-220">317</span></span>|  
|<span data-ttu-id="0a623-221">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-221">SO</span></span>|<span data-ttu-id="0a623-222">319</span><span class="sxs-lookup"><span data-stu-id="0a623-222">319</span></span>|  
|<span data-ttu-id="0a623-223">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-223">SO</span></span>|<span data-ttu-id="0a623-224">322</span><span class="sxs-lookup"><span data-stu-id="0a623-224">322</span></span>|  
|<span data-ttu-id="0a623-225">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-225">SO</span></span>|<span data-ttu-id="0a623-226">323</span><span class="sxs-lookup"><span data-stu-id="0a623-226">323</span></span>|  
|<span data-ttu-id="0a623-227">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-227">SO</span></span>|<span data-ttu-id="0a623-228">324</span><span class="sxs-lookup"><span data-stu-id="0a623-228">324</span></span>|  
|<span data-ttu-id="0a623-229">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-229">SO</span></span>|<span data-ttu-id="0a623-230">325</span><span class="sxs-lookup"><span data-stu-id="0a623-230">325</span></span>|  
|<span data-ttu-id="0a623-231">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-231">SO</span></span>|<span data-ttu-id="0a623-232">326</span><span class="sxs-lookup"><span data-stu-id="0a623-232">326</span></span>|  
|<span data-ttu-id="0a623-233">因此</span><span class="sxs-lookup"><span data-stu-id="0a623-233">SO</span></span>|<span data-ttu-id="0a623-234">361</span><span class="sxs-lookup"><span data-stu-id="0a623-234">361</span></span>|  
|<span data-ttu-id="0a623-235">TO</span><span class="sxs-lookup"><span data-stu-id="0a623-235">TO</span></span>|<span data-ttu-id="0a623-236">197</span><span class="sxs-lookup"><span data-stu-id="0a623-236">197</span></span>|  
|<span data-ttu-id="0a623-237">TO</span><span class="sxs-lookup"><span data-stu-id="0a623-237">TO</span></span>|<span data-ttu-id="0a623-238">199</span><span class="sxs-lookup"><span data-stu-id="0a623-238">199</span></span>|  
|<span data-ttu-id="0a623-239">TO</span><span class="sxs-lookup"><span data-stu-id="0a623-239">TO</span></span>|<span data-ttu-id="0a623-240">265</span><span class="sxs-lookup"><span data-stu-id="0a623-240">265</span></span>|  
|<span data-ttu-id="0a623-241">TO</span><span class="sxs-lookup"><span data-stu-id="0a623-241">TO</span></span>|<span data-ttu-id="0a623-242">485</span><span class="sxs-lookup"><span data-stu-id="0a623-242">485</span></span>|  
|<span data-ttu-id="0a623-243">TO</span><span class="sxs-lookup"><span data-stu-id="0a623-243">TO</span></span>|<span data-ttu-id="0a623-244">486</span><span class="sxs-lookup"><span data-stu-id="0a623-244">486</span></span>|  
|<span data-ttu-id="0a623-245">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-245">TP</span></span>|<span data-ttu-id="0a623-246">460</span><span class="sxs-lookup"><span data-stu-id="0a623-246">460</span></span>|  
|<span data-ttu-id="0a623-247">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-247">TP</span></span>|<span data-ttu-id="0a623-248">463</span><span class="sxs-lookup"><span data-stu-id="0a623-248">463</span></span>|  
|<span data-ttu-id="0a623-249">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-249">TP</span></span>|<span data-ttu-id="0a623-250">466</span><span class="sxs-lookup"><span data-stu-id="0a623-250">466</span></span>|  
|<span data-ttu-id="0a623-251">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-251">TP</span></span>|<span data-ttu-id="0a623-252">468</span><span class="sxs-lookup"><span data-stu-id="0a623-252">468</span></span>|  
|<span data-ttu-id="0a623-253">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-253">TP</span></span>|<span data-ttu-id="0a623-254">490</span><span class="sxs-lookup"><span data-stu-id="0a623-254">490</span></span>|  
|<span data-ttu-id="0a623-255">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-255">TP</span></span>|<span data-ttu-id="0a623-256">492</span><span class="sxs-lookup"><span data-stu-id="0a623-256">492</span></span>|  
|<span data-ttu-id="0a623-257">TP</span><span class="sxs-lookup"><span data-stu-id="0a623-257">TP</span></span>|<span data-ttu-id="0a623-258">494</span><span class="sxs-lookup"><span data-stu-id="0a623-258">494</span></span>|  
|<span data-ttu-id="0a623-259">WA</span><span class="sxs-lookup"><span data-stu-id="0a623-259">WA</span></span>|<span data-ttu-id="0a623-260">140</span><span class="sxs-lookup"><span data-stu-id="0a623-260">140</span></span>|  
|<span data-ttu-id="0a623-261">WA</span><span class="sxs-lookup"><span data-stu-id="0a623-261">WA</span></span>|<span data-ttu-id="0a623-262">141</span><span class="sxs-lookup"><span data-stu-id="0a623-262">141</span></span>|  
|<span data-ttu-id="0a623-263">WA</span><span class="sxs-lookup"><span data-stu-id="0a623-263">WA</span></span>|<span data-ttu-id="0a623-264">142</span><span class="sxs-lookup"><span data-stu-id="0a623-264">142</span></span>|  
|<span data-ttu-id="0a623-265">WA</span><span class="sxs-lookup"><span data-stu-id="0a623-265">WA</span></span>|<span data-ttu-id="0a623-266">143</span><span class="sxs-lookup"><span data-stu-id="0a623-266">143</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0a623-267">HIPAA 5010 群組也可讓單一群組內的不同版本的交易集。</span><span class="sxs-lookup"><span data-stu-id="0a623-267">A HIPAA 5010 group also allows transaction sets of different versions within a single group.</span></span>  
  
 <span data-ttu-id="0a623-268">若設定處理異動時遇到例外狀況時，會擱置 EDI 合作對象屬性用來判斷整個交換或只失敗的交易設定。</span><span class="sxs-lookup"><span data-stu-id="0a623-268">If an exception is encountered when processing a transaction set, EDI party properties are used to determine if the entire interchange or only the failing transaction set is suspended.</span></span>  
  
 <span data-ttu-id="0a623-269">群組必須以功能群組標頭 (X12 中的 GS 或 EDIFACT 中的 UNG) 做為開頭，而且必須以功能群組結尾 (X12 中的 GE 或 EDIFACT 中的 UNE) 做為結尾。</span><span class="sxs-lookup"><span data-stu-id="0a623-269">A group must start with a Functional Group Header (GS in X12 or UNG in EDIFACT), and it must end with a Functional Group Trailer (GE in X12 or UNE in EDIFACT).</span></span> <span data-ttu-id="0a623-270">群組標頭中包含傳送者和接收者代碼、與標頭和結尾相符的日期和時間、定義可包含在功能群組內之交易集集合的群組識別碼，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="0a623-270">The Group Header contains sender and receiver codes, a date and time, a control number that matches the header and trailer, a group identifier that defines the collection of transaction sets that may be included within the functional group, and other information.</span></span> <span data-ttu-id="0a623-271">群組結尾則具有指出群組內部交易集數目的元素。</span><span class="sxs-lookup"><span data-stu-id="0a623-271">The Group Trailer has an element that indicates the number of transaction sets within the group.</span></span>  
  
 <span data-ttu-id="0a623-272">群組是 EDIFACT 交換中的選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="0a623-272">A group is optional in an EDIFACT interchange.</span></span> <span data-ttu-id="0a623-273">即使沒有任何群組 (UNG 區段不存在)，EDIFACT 交換也可以包含多個交易集.</span><span class="sxs-lookup"><span data-stu-id="0a623-273">An EDIFACT interchange can contain multiple transaction sets even if no group is present (the UNG segment is not present).</span></span> <span data-ttu-id="0a623-274">在這種情況下，這些交易集全都必須屬於同一種類型，因為單一群組中的交易集必須屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="0a623-274">In this case, the transaction sets must all be of the same type, as transaction sets in a single group must be of the same type.</span></span> <span data-ttu-id="0a623-275">例如，APERAK 和 ORDERS 交易集不能同時存在單一群組或是沒有多個群組的交換中。</span><span class="sxs-lookup"><span data-stu-id="0a623-275">For example, APERAK and ORDERS transaction sets could not both be present in a single group or in an interchange that does not have multiple groups.</span></span>  
  
 <span data-ttu-id="0a623-276">群組在 X12 交換中是必要的項目。</span><span class="sxs-lookup"><span data-stu-id="0a623-276">A group is required in an X12 interchange.</span></span>