---
title: "通知產生失敗，因為已達到上限的 Edifact 交易集控制編號之全域設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6adc02d7-ebc4-4da0-a19a-3a423d63499d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 252f0fd6dbe77eb83018e2bb34d4a6cd07cdbdf2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-global-settings"></a><span data-ttu-id="d130a-102">通知產生失敗，因為全域設定已達到可接受 Edifact 交易集控制編號的上限</span><span class="sxs-lookup"><span data-stu-id="d130a-102">Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for global settings</span></span>
## <a name="details"></a><span data-ttu-id="d130a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d130a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d130a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d130a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d130a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d130a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d130a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d130a-106">Event ID</span></span>|-|  
|<span data-ttu-id="d130a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d130a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="d130a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d130a-108"> EDI</span></span>|  
|<span data-ttu-id="d130a-109">元件</span><span class="sxs-lookup"><span data-stu-id="d130a-109">Component</span></span>|<span data-ttu-id="d130a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d130a-110">EDI Engine</span></span>|  
|<span data-ttu-id="d130a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d130a-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d130a-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d130a-112">Message Text</span></span>|<span data-ttu-id="d130a-113">通知產生失敗，因為最大的可接受 Edifact 交易集控制編號已達到 Guest 設定的限制。</span><span class="sxs-lookup"><span data-stu-id="d130a-113">Acknowledgement generation has failed as max limit of acceptable Edifact transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="d130a-114">瀏覽至 通用設定寄件者角色畫面，欄位 UNH 1 在夥伴協議管理員 中，重設計數器。</span><span class="sxs-lookup"><span data-stu-id="d130a-114">Reset counter by navigating to Global configuration sender role screen, field UNH 1 in Partner Agreement manager.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d130a-115">說明</span><span class="sxs-lookup"><span data-stu-id="d130a-115">Explanation</span></span>  
 <span data-ttu-id="d130a-116">這個錯誤/警告/資訊事件表示，BizTalk Server 無法產生 EDIFACT 交換通知因為高於它進入交易集參考編號 (UNH1) 的通知控制編號UNH1 允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="d130a-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the EDIFACT interchange because the control number that it entered in the Transaction set reference number (UNH1) of the acknowledgment is greater than the maximum value allowed for UNH1.</span></span> <span data-ttu-id="d130a-117">在本例中，BizTalk Server 會使用 EDI 全域屬性，若要建立通知。</span><span class="sxs-lookup"><span data-stu-id="d130a-117">In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="d130a-118">交易集參考編號的最大值取決於用來參考編號的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="d130a-118">The maximum value of the transaction set reference number depends upon the number of digits used for the reference number.</span></span> <span data-ttu-id="d130a-119">參考編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。</span><span class="sxs-lookup"><span data-stu-id="d130a-119">The maximum number of characters is 14 for the reference number, 13 for the prefix and suffix, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d130a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d130a-120">User Action</span></span>  
 <span data-ttu-id="d130a-121">若要解決這個錯誤，重設為低於最大限制值的交易集參考編號 (UNH1) 的 UNG 和 UNH 區段定義頁面中的參考編號欄位 (UNH1.2)。</span><span class="sxs-lookup"><span data-stu-id="d130a-121">To resolve this error, reset the reference number field (UNH1.2) of the Transaction set reference number (UNH1) in the UNG and UNH Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="d130a-122">在 [EDI 全域屬性] 對話方塊中設定此屬性[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d130a-122">Set this property in the EDI Global Properties dialog box in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console.</span></span>