---
title: 協議屬性驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d565c26-37ef-4aee-aebb-3152880242a1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20c01ec281005cbeaffda6dcd2349c1153a531b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229870"
---
# <a name="agreement-properties-validation"></a><span data-ttu-id="47cdd-102">協議屬性驗證</span><span class="sxs-lookup"><span data-stu-id="47cdd-102">Agreement Properties Validation</span></span>
<span data-ttu-id="47cdd-103">協議屬性包含檢查交換、群組或交易集的重複控制編號。</span><span class="sxs-lookup"><span data-stu-id="47cdd-103">Agreement properties include checks for duplicate control numbers for interchanges, groups, or transaction sets.</span></span> <span data-ttu-id="47cdd-104">若已在協議屬性中啟用這些驗證，EDI 接收管線就會執行它們。</span><span class="sxs-lookup"><span data-stu-id="47cdd-104">The EDI receive pipeline will perform these validations only if they are enabled in agreement properties.</span></span> <span data-ttu-id="47cdd-105">這些驗證包括：</span><span class="sxs-lookup"><span data-stu-id="47cdd-105">These validations include:</span></span>  
  
-   <span data-ttu-id="47cdd-106">檢查重複的交換控制編號 (在 X12 中為 ISA13，在 EDIFACT 中為 UNB5)。</span><span class="sxs-lookup"><span data-stu-id="47cdd-106">Checking for a duplicate interchange control number (ISA13 in X12 or UNB5 in EDIFACT).</span></span> <span data-ttu-id="47cdd-107">您輸入時間值 (天) 來建立這個檢查的有效時間範圍。</span><span class="sxs-lookup"><span data-stu-id="47cdd-107">You enter a time value (in days) to establish the valid time range for this check.</span></span>  
  
-   <span data-ttu-id="47cdd-108">檢查交換內重複的群組控制編號 (在 X12 中為 GS6，在 EDIFACT 中為 UNG5)</span><span class="sxs-lookup"><span data-stu-id="47cdd-108">Checking for a duplicate group control number in an interchange (GS6 in X12 or UNG5 in EDIFACT)</span></span>  
  
-   <span data-ttu-id="47cdd-109">檢查功能群組中重複的交易集控制編號 (在 X12 為 ST2，在 EDIFACT 為 UNH1)</span><span class="sxs-lookup"><span data-stu-id="47cdd-109">Checking for a duplicate transaction set control number in a functional group (ST2 in X12 or UNH1 in EDIFACT)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cdd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47cdd-110">See Also</span></span>  
 [<span data-ttu-id="47cdd-111">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="47cdd-111">EDI Message Validation</span></span>](../core/edi-message-validation.md)