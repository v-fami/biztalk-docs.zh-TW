---
title: "如何使用商務規則在協調流程中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- atomic transactions, business rules
- Call Rules shape [Orchestration Designer], business rules
- business rules, orchestrations
- orchestrations, business rules
ms.assetid: d20473c2-267f-4a44-93c3-df6ef655020c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346582f90cada01b2350fae227885a9e9cd71712
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-business-rules-in-orchestrations"></a><span data-ttu-id="a1d48-102">如何在協調流程中使用商務規則</span><span class="sxs-lookup"><span data-stu-id="a1d48-102">How to Use Business Rules in Orchestrations</span></span>
<span data-ttu-id="a1d48-103">您可以建立商務規則原則的執行個體，並在協調流程中執行它。</span><span class="sxs-lookup"><span data-stu-id="a1d48-103">You can create an instance of a Business Rules policy and execute it in your orchestration.</span></span> <span data-ttu-id="a1d48-104">若要這麼做，請在不可部分完成的交易範圍中新增「呼叫規則」圖形，並在此圖形上設定原則。</span><span class="sxs-lookup"><span data-stu-id="a1d48-104">To do this, add a Call Rules shape inside an atomic transaction scope, and configure a policy on it.</span></span>  
  
## <a name="examples-of-using-business-rules"></a><span data-ttu-id="a1d48-105">商務規則的使用範例</span><span class="sxs-lookup"><span data-stu-id="a1d48-105">Examples of Using Business Rules</span></span>  
  
-   [<span data-ttu-id="a1d48-106">商務規則 Hello World1 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="a1d48-106">Business Rules Hello World1 (BizTalk Server Sample)</span></span>](../core/business-rules-hello-world1-biztalk-server-sample.md)  
  
-   [<span data-ttu-id="a1d48-107">商務規則 Hello World2 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="a1d48-107">Business Rules Hello World2 (BizTalk Server Sample)</span></span>](../core/business-rules-hello-world2-biztalk-server-sample.md)  
  
-   [<span data-ttu-id="a1d48-108">貸款處理使用商務規則 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="a1d48-108">Loans Processing Using Business Rules (BizTalk Server Sample)</span></span>](../core/loans-processing-using-business-rules-biztalk-server-sample.md)  
  
-   [<span data-ttu-id="a1d48-109">醫療理賠處理和測試原則 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="a1d48-109">Medical Claims Processing and Testing Policies (BizTalk Server Sample)</span></span>](../core/medical-claims-processing-and-testing-policies-biztalk-server-sample.md)  
  
-   <span data-ttu-id="a1d48-110">從下載 SDK 範例 「 原則鏈結 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="a1d48-110">Download the SDK sample "Policy Chaining" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d48-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d48-111">See Also</span></span>  
 [<span data-ttu-id="a1d48-112">建立和使用商務規則</span><span class="sxs-lookup"><span data-stu-id="a1d48-112">Creating and Using Business Rules</span></span>](../core/creating-and-using-business-rules.md)