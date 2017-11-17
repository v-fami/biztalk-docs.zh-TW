---
title: "X12 TA1 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68568a1a-3669-46f4-8edc-8d057b012544
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8547175461732e41248e1e94bf961f95e655890f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="x12-ta1-acknowledgment"></a><span data-ttu-id="71c90-102">X12 TA1 通知</span><span class="sxs-lookup"><span data-stu-id="71c90-102">X12 TA1 Acknowledgment</span></span>
<span data-ttu-id="71c90-103">X12 TA1 技術通知會報告位址接收者對交換標頭和結尾的處理狀態。</span><span class="sxs-lookup"><span data-stu-id="71c90-103">The X12 TA1 technical acknowledgment reports the status of the processing of an interchange header and trailer by the address receiver.</span></span> <span data-ttu-id="71c90-104">包括 X12 編碼訊息的 ISA 和 IEA 何時有效，何時有傳出正的 TA1 ACK，以及任何的其他內容狀態。</span><span class="sxs-lookup"><span data-stu-id="71c90-104">When the ISA and IEA of the X12-encoded message are valid, a positive TA1 ACK is sent, whatever the status of the other content is.</span></span> <span data-ttu-id="71c90-105">若結果為否，就會傳送包含錯誤碼的 TA1 ACK。</span><span class="sxs-lookup"><span data-stu-id="71c90-105">If not, TA1 ACK with an error code is sent.</span></span>  
  
 <span data-ttu-id="71c90-106">X12 TA1 通知會與 x12_<\<版本號碼 > _TA1.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="71c90-106">The X12 TA1 acknowledgment conforms to the X12_\<version number>_TA1.xsd schema.</span></span> <span data-ttu-id="71c90-107">此 TA1 ACK 會以 ISA/IEA 信封傳送。</span><span class="sxs-lookup"><span data-stu-id="71c90-107">The TA1 ACK is sent inside an ISA/IEA envelope.</span></span> <span data-ttu-id="71c90-108">其中的 ISA 和 IEA 與任何其他交換的 ISA 和 IEA 完全相同。</span><span class="sxs-lookup"><span data-stu-id="71c90-108">The ISA and IEA are no different than any other interchange.</span></span>  
  
 <span data-ttu-id="71c90-109">下表列出在 TA1 ACK 交換內的區段。</span><span class="sxs-lookup"><span data-stu-id="71c90-109">The segments within the interchange of a TA1 ACK are shown in the following table.</span></span>  
  
|<span data-ttu-id="71c90-110">TA1 中的欄位</span><span class="sxs-lookup"><span data-stu-id="71c90-110">Field in TA1</span></span>|<span data-ttu-id="71c90-111">欄位的名稱</span><span class="sxs-lookup"><span data-stu-id="71c90-111">Name of Field</span></span>|<span data-ttu-id="71c90-112">對應至內送交換</span><span class="sxs-lookup"><span data-stu-id="71c90-112">Mapped to Incoming Interchange</span></span>|<span data-ttu-id="71c90-113">值</span><span class="sxs-lookup"><span data-stu-id="71c90-113">Value</span></span>|  
|------------------|-------------------|------------------------------------|-----------|  
|<span data-ttu-id="71c90-114">TA101</span><span class="sxs-lookup"><span data-stu-id="71c90-114">TA101</span></span>|<span data-ttu-id="71c90-115">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="71c90-115">Interchange control number</span></span>|<span data-ttu-id="71c90-116">ISA13 - 交換控制編號</span><span class="sxs-lookup"><span data-stu-id="71c90-116">ISA13 - Interchange control number</span></span>|-|  
|<span data-ttu-id="71c90-117">TA102</span><span class="sxs-lookup"><span data-stu-id="71c90-117">TA102</span></span>|<span data-ttu-id="71c90-118">交換日期</span><span class="sxs-lookup"><span data-stu-id="71c90-118">Interchange Date</span></span>|<span data-ttu-id="71c90-119">ISA09 - 交換日期</span><span class="sxs-lookup"><span data-stu-id="71c90-119">ISA09 Interchange Date</span></span>|-|  
|<span data-ttu-id="71c90-120">TA103</span><span class="sxs-lookup"><span data-stu-id="71c90-120">TA103</span></span>|<span data-ttu-id="71c90-121">交換時間</span><span class="sxs-lookup"><span data-stu-id="71c90-121">Interchange Time</span></span>|<span data-ttu-id="71c90-122">ISA10 - 交換時間</span><span class="sxs-lookup"><span data-stu-id="71c90-122">ISA10 – Interchange Time</span></span>|-|  
|<span data-ttu-id="71c90-123">TA104</span><span class="sxs-lookup"><span data-stu-id="71c90-123">TA104</span></span>|<span data-ttu-id="71c90-124">交換通知代碼*</span><span class="sxs-lookup"><span data-stu-id="71c90-124">Interchange ACK Code*</span></span>|<span data-ttu-id="71c90-125">不適用</span><span class="sxs-lookup"><span data-stu-id="71c90-125">N/A</span></span>|<span data-ttu-id="71c90-126">引擎行為： A、 E 或 R</span><span class="sxs-lookup"><span data-stu-id="71c90-126">Engine behavior: A, E, or R</span></span><br /><br /> <span data-ttu-id="71c90-127">A = 接受</span><span class="sxs-lookup"><span data-stu-id="71c90-127">A = Accept</span></span><br /><br /> <span data-ttu-id="71c90-128">E = 交換已接受，發生錯誤</span><span class="sxs-lookup"><span data-stu-id="71c90-128">E = Interchange accepted with errors</span></span><br /><br /> <span data-ttu-id="71c90-129">R = 交換已拒絕/已擱置</span><span class="sxs-lookup"><span data-stu-id="71c90-129">R = Interchange rejected/suspended</span></span>|  
|<span data-ttu-id="71c90-130">TA105</span><span class="sxs-lookup"><span data-stu-id="71c90-130">TA105</span></span>|<span data-ttu-id="71c90-131">交換說明碼</span><span class="sxs-lookup"><span data-stu-id="71c90-131">Interchange Note Code</span></span>|<span data-ttu-id="71c90-132">不適用</span><span class="sxs-lookup"><span data-stu-id="71c90-132">N/A</span></span>|<span data-ttu-id="71c90-133">正在處理結果錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="71c90-133">Processing result error code.</span></span> <span data-ttu-id="71c90-134">**注意：**中的，請參閱資料表[X12 TA1 通知錯誤碼](../core/x12-ta1-acknowledgment-error-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="71c90-134">**Note:**  See table in [X12 TA1 Acknowledgment Error Codes](../core/x12-ta1-acknowledgment-error-codes.md).</span></span>|  
  
 <span data-ttu-id="71c90-135">\*引擎行為根據資料元素驗證;除了安全性和驗證資訊，會依據其組態資訊的字串比較。</span><span class="sxs-lookup"><span data-stu-id="71c90-135">\* Engine behavior is based off data element validation; except for security and authentication information, which will be based off string comparisons in configuration information.</span></span>