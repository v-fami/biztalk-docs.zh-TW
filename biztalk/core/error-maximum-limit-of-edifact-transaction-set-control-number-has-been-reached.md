---
title: 通知產生失敗，因為合作對象設定已達到的 Edifact 交易集控制編號的最大限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcbb6374-0403-42b0-892b-b35157a2c74a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b639f80d6ad203074e0542df6672f2d7b89aa2ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001343"
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-party-settings"></a><span data-ttu-id="acb1d-102">通知產生失敗，因為合作對象設定已達到最大限制的 Edifact 交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="acb1d-102">Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for party settings</span></span>
## <a name="details"></a><span data-ttu-id="acb1d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="acb1d-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="acb1d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="acb1d-104">Product Name</span></span>   |                                                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                            |
| <span data-ttu-id="acb1d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="acb1d-105">Product Version</span></span> |                                                                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                        |
|    <span data-ttu-id="acb1d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="acb1d-106">Event ID</span></span>     |                                                                                                                    -                                                                                                                     |
|  <span data-ttu-id="acb1d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="acb1d-107">Event Source</span></span>   |                                                                                                            <span data-ttu-id="acb1d-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="acb1d-108">BizTalk Server EDI</span></span>                                                                                                            |
|    <span data-ttu-id="acb1d-109">元件</span><span class="sxs-lookup"><span data-stu-id="acb1d-109">Component</span></span>    |                                                                                                                <span data-ttu-id="acb1d-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="acb1d-110">EDI Engine</span></span>                                                                                                                |
|  <span data-ttu-id="acb1d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="acb1d-111">Symbolic Name</span></span>  |                                                                                                                    -                                                                                                                     |
|  <span data-ttu-id="acb1d-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="acb1d-112">Message Text</span></span>   | <span data-ttu-id="acb1d-113">通知產生失敗，因為最大上限為可接受 Edifact 交易集控制編號已達到合作對象{0}。</span><span class="sxs-lookup"><span data-stu-id="acb1d-113">Acknowledgement generation has failed as max limit of acceptable Edifact transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="acb1d-114">瀏覽至合作對象，傳送者角色畫面，欄位 [UNH 1 在夥伴協議] 管理員中，重設計數器。</span><span class="sxs-lookup"><span data-stu-id="acb1d-114">Reset counter by navigating to Party in sender role screen, field UNH 1 in Partner Agreement manager.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="acb1d-115">說明</span><span class="sxs-lookup"><span data-stu-id="acb1d-115">Explanation</span></span>  
 <span data-ttu-id="acb1d-116">這個錯誤/警告/資訊事件表示 BizTalk Server 可能無法產生 EDIFACT 交換通知因為它已進入通知的交易集參考編號 (UNH1) 的控制編號大於UNH1 允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="acb1d-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the EDIFACT interchange because the control number that it entered in the Transaction set reference number (UNH1) of the acknowledgment is greater than the maximum value allowed for UNH1.</span></span> <span data-ttu-id="acb1d-117">在此情況下，BizTalk Server 會使用 EDI 合作對象屬性建立通知。</span><span class="sxs-lookup"><span data-stu-id="acb1d-117">In this instance, BizTalk Server used the EDI party properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="acb1d-118">交易集參考編號的最大值取決於用來參考編號的數字數目。</span><span class="sxs-lookup"><span data-stu-id="acb1d-118">The maximum value of the transaction set reference number depends upon the number of digits used for the reference number.</span></span> <span data-ttu-id="acb1d-119">參考編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。</span><span class="sxs-lookup"><span data-stu-id="acb1d-119">The maximum number of characters is 14 for the reference number, 13 for the prefix and suffix, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="acb1d-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="acb1d-120">User Action</span></span>  
 <span data-ttu-id="acb1d-121">若要解決這個錯誤，重設為低於最大限制值的交易集參考編號 (UNH1) 的 UNG 和 UNH 區段定義頁面中的參考編號欄位 (UNH1.2)。</span><span class="sxs-lookup"><span data-stu-id="acb1d-121">To resolve this error, reset the reference number field (UNH1.2) of the Transaction set reference number (UNH1) in the UNG and UNH Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="acb1d-122">在 [EDI 屬性] 對話方塊中，在 BizTalk Server 管理主控台中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="acb1d-122">Set this property in the EDI Properties dialog box in the BizTalk Server Administration Console.</span></span>