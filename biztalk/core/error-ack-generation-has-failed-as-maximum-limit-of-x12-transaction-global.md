---
title: 錯誤通知的產生失敗，因為 X12 全域交易的最大限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ef251a7e9af04245d1987e2d196a03f7c01b911
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980479"
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-global"></a><span data-ttu-id="3713a-102">錯誤通知的產生失敗，因為 X12 全域交易的最大限制</span><span class="sxs-lookup"><span data-stu-id="3713a-102">Error-Ack generation has failed as maximum limit of X12 transaction-global</span></span>
## <a name="details"></a><span data-ttu-id="3713a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3713a-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="3713a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3713a-104">Product Name</span></span>   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                  |
| <span data-ttu-id="3713a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3713a-105">Product Version</span></span> |                                                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                              |
|    <span data-ttu-id="3713a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3713a-106">Event ID</span></span>     |                                                                                                                          -                                                                                                                          |
|  <span data-ttu-id="3713a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3713a-107">Event Source</span></span>   |                                                                                                                 <span data-ttu-id="3713a-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="3713a-108">BizTalk Server EDI</span></span>                                                                                                                  |
|    <span data-ttu-id="3713a-109">元件</span><span class="sxs-lookup"><span data-stu-id="3713a-109">Component</span></span>    |                                                                                                                     <span data-ttu-id="3713a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3713a-110">EDI Engine</span></span>                                                                                                                      |
|  <span data-ttu-id="3713a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3713a-111">Symbolic Name</span></span>  |                                                                                                                          -                                                                                                                          |
|  <span data-ttu-id="3713a-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3713a-112">Message Text</span></span>   | <span data-ttu-id="3713a-113">通知產生失敗，因為可接受 X12 交易集控制編號已達到 Guest 設定的最大限制。</span><span class="sxs-lookup"><span data-stu-id="3713a-113">Acknowledgement generation has failed as max limit of acceptable X12 transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="3713a-114">瀏覽至 全域設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員重設計數器</span><span class="sxs-lookup"><span data-stu-id="3713a-114">Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="3713a-115">說明</span><span class="sxs-lookup"><span data-stu-id="3713a-115">Explanation</span></span>  
 <span data-ttu-id="3713a-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生 x12 交換因為它進入交易控制編號設定通知控制編號 (ST2) 大於通知允許的項目 ST2 的最大值。</span><span class="sxs-lookup"><span data-stu-id="3713a-116">This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the X12 interchange because the control number that it entered in the Transaction set control number (ST2) of the acknowledgment is greater than the maximum value allowed for ST2.</span></span> <span data-ttu-id="3713a-117">在此情況下，BizTalk Server 會使用 EDI 全域屬性，來建立通知。</span><span class="sxs-lookup"><span data-stu-id="3713a-117">In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.</span></span>  
  
 <span data-ttu-id="3713a-118">交易集控制編號的最大值取決於所使用的控制編號的數字數目。</span><span class="sxs-lookup"><span data-stu-id="3713a-118">The maximum value of the transaction set control number depends upon the number of digits used for the control number.</span></span> <span data-ttu-id="3713a-119">所有的三個欄位的長度上限是 9;在前置詞和尾碼欄位的最大長度為 8。</span><span class="sxs-lookup"><span data-stu-id="3713a-119">The maximum length of all three fields is 9; the maximum length of the prefix and suffix fields is 8.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3713a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3713a-120">User Action</span></span>  
 <span data-ttu-id="3713a-121">若要解決這個錯誤，重設控制編號 欄位 (ST2.2) 交易集控制編號 (ST2) 的 GS 和 ST 區段定義頁面為低於最大限制值的。</span><span class="sxs-lookup"><span data-stu-id="3713a-121">To resolve this error, reset the control number field (ST2.2) of the Transaction set control number (ST2) in the GS and ST Segment Definition Page to a value that is lower than the maximum limit.</span></span> <span data-ttu-id="3713a-122">在 [EDI 全域屬性] 對話方塊中，在 BizTalk Server 管理主控台中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="3713a-122">Set this property in the EDI Global Properties dialog box in the BizTalk Server Administration Console.</span></span>