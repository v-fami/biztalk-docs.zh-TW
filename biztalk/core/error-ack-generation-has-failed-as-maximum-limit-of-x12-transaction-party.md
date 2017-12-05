---
title: "錯誤通知的產生失敗，因為最大限制 X12 交易合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c78a7cef-24ae-4d09-9043-2f53c301302d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e845960a85ebe2ebf90b8549634a0097676c80c5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-party"></a><span data-ttu-id="a317b-102">錯誤通知的產生失敗，因為最大限制 X12 交易合作對象</span><span class="sxs-lookup"><span data-stu-id="a317b-102">Error-Ack generation has failed as maximum limit of X12 transaction-party</span></span>
## <a name="details"></a><span data-ttu-id="a317b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a317b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a317b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a317b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a317b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a317b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a317b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a317b-106">Event ID</span></span>|-|  
|<span data-ttu-id="a317b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a317b-107">Event Source</span></span>|<span data-ttu-id="a317b-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="a317b-108">BizTalk Server EDI</span></span>|  
|<span data-ttu-id="a317b-109">元件</span><span class="sxs-lookup"><span data-stu-id="a317b-109">Component</span></span>|<span data-ttu-id="a317b-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a317b-110">EDI Engine</span></span>|  
|<span data-ttu-id="a317b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a317b-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="a317b-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a317b-112">Message Text</span></span>|<span data-ttu-id="a317b-113">通知產生失敗，因為合作對象 {0} 可接受的 X12 交易集控制編號已達到最大限制。</span><span class="sxs-lookup"><span data-stu-id="a317b-113">Acknowledgement generation has failed as max limit of acceptable X12 transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="a317b-114">請瀏覽至 [夥伴協議] 管理員中傳送者角色畫面中的 [合作對象]，欄位 [ST 2]，重設計數器</span><span class="sxs-lookup"><span data-stu-id="a317b-114">Reset counter by navigating to Party in sender role screen, field ST 2 in Partner Agreement manager.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a317b-115">說明</span><span class="sxs-lookup"><span data-stu-id="a317b-115">Explanation</span></span>  
 <span data-ttu-id="a317b-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生 x12 交換，因為它進入交易控制編號設定的通知控制編號 (ST2) 大於通知允許的項目 ST2 的最大值。</span><span class="sxs-lookup"><span data-stu-id="a317b-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the X12 interchange because the control number that it entered in the Transaction set control number (ST2) of the acknowledgment is greater than the maximum value allowed for ST2.</span></span> <span data-ttu-id="a317b-117">在這個執行個體，BizTalk Server 會使用 EDI 合作對象屬性建立通知。</span><span class="sxs-lookup"><span data-stu-id="a317b-117">In this instance, BizTalk Server used the EDI party properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="a317b-118">交易集控制編號的最大值取決於用來控制編號的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="a317b-118">The maximum value of the transaction set control number depends upon the number of digits used for the control number.</span></span> <span data-ttu-id="a317b-119">這三個欄位的最大長度為 9;前置詞和尾碼欄位的最大長度為 8。</span><span class="sxs-lookup"><span data-stu-id="a317b-119">The maximum length of all three fields is 9; the maximum length of the prefix and suffix fields is 8.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a317b-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a317b-120">User Action</span></span>  
 <span data-ttu-id="a317b-121">若要解決這個錯誤，重設控制編號欄位 (ST2.2) 的交易集控制編號 (ST2) 的 GS 和 ST 區段定義頁面的值小於最大限制。</span><span class="sxs-lookup"><span data-stu-id="a317b-121">To resolve this error, reset the control number field (ST2.2) of the Transaction set control number (ST2) in the GS and ST Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="a317b-122">在 [EDI 全域屬性] 對話方塊中設定此屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a317b-122">Set this property in the EDI Global Properties dialog box in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>