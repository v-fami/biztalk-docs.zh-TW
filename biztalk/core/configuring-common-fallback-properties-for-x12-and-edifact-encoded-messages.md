---
title: "設定通用的後援屬性的 X12 和 EDIFACT 編碼訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7393d6ac-b901-43ef-a8d6-c5b0b3033257
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd66c9ce3bb104cfb471e725778faab2c4e9528
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-common-fallback-properties-for-x12-and-edifact-encoded-messages"></a><span data-ttu-id="f7a96-102">設定通用的後援屬性的 X12 和 EDIFACT 編碼的訊息</span><span class="sxs-lookup"><span data-stu-id="f7a96-102">Configuring Common Fallback Properties for X12 and EDIFACT Encoded Messages</span></span>
<span data-ttu-id="f7a96-103">後援屬性套用至 （包括 HIPAA）-X12 和 EDIFACT 編碼交換。</span><span class="sxs-lookup"><span data-stu-id="f7a96-103">Fallback properties apply to both X12 (including HIPAA) - and EDIFACT-encoded interchanges.</span></span> <span data-ttu-id="f7a96-104">當所有後援協議屬性，這些屬性會套用時，才[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]尚未判斷出協議的外寄訊息解析為傳入。</span><span class="sxs-lookup"><span data-stu-id="f7a96-104">As with all fallback agreement properties, these properties apply only when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has not determined the agreement to which an incoming our outgoing message resolves to.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7a96-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f7a96-105">Prerequisites</span></span>  
 <span data-ttu-id="f7a96-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="f7a96-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-common-global-properties"></a><span data-ttu-id="f7a96-107">若要設定通用全域屬性</span><span class="sxs-lookup"><span data-stu-id="f7a96-107">To set common global properties</span></span>  
  
1.  <span data-ttu-id="f7a96-108">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**或**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="f7a96-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings** or **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="f7a96-109">在**後援設定一般頁面**索引標籤**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f7a96-109">In the **Fallback Settings General Pages** tab, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="f7a96-110">按一下**啟用後援設定**啟用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]沒有協議為解析內送或外寄訊息時使用後援協議設定。</span><span class="sxs-lookup"><span data-stu-id="f7a96-110">Click **Enable Fallback Settings** to enable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use the fallback agreement settings if no agreement is resolved for incoming or outgoing messages.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="f7a96-111">如果不勾選此選項，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將不會使用後援協議中設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7a96-111">If this option is not checked, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will not use the properties set in the fallback agreement.</span></span>  
  
    2.  <span data-ttu-id="f7a96-112">按一下**啟動 EDI 報告**啟動報告所有 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="f7a96-112">Click **Activate EDI Reporting** to activate reporting for all EDI messages.</span></span> <span data-ttu-id="f7a96-113">這可確保訊息會顯示在狀態報告畫面底部的連結即可顯示**群組中樞**窗格[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f7a96-113">This ensures messages are displayed in the status reporting screens displayed by clicking the links at the bottom of the **Group Hub** pane of the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console.</span></span>  
  
    3.  <span data-ttu-id="f7a96-114">如果您按下**啟動 EDI 報告**，按一下 **儲存交易集/內容 reporting** ，將交易集儲存在追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f7a96-114">If you clicked **Activate EDI Reporting**, click **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span>  
  
    4.  <span data-ttu-id="f7a96-115">按一下**EDI 錯誤和記錄到 Windows 事件記錄檔的 EDI 引擎產生的警告**記錄產生 EDI 引擎 （EDI 管線、 批次處理協調流程、 路由協調流程等），與內容相關的錯誤/警告訊息Windows 事件檢視器的資訊。</span><span class="sxs-lookup"><span data-stu-id="f7a96-115">Click **Log EDI errors and warnings generated by EDI engine to Windows event log** to log error/warnings messages generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span> <span data-ttu-id="f7a96-116">取消選取時，這些錯誤/警告訊息就不會記錄至事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="f7a96-116">If cleared, these error/warning messages will not be logged to the Event Viewer.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f7a96-117">不論是否選取此核取方塊，系統/處理錯誤都會記錄在事件檢視器中。</span><span class="sxs-lookup"><span data-stu-id="f7a96-117">System/processing errors are logged in the Event Viewer whether or not this checkbox is selected.</span></span>  
  
3.  <span data-ttu-id="f7a96-118">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證並接受變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f7a96-118">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate and accept the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a96-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a96-119">See Also</span></span>  
 [<span data-ttu-id="f7a96-120">設定全域或後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="f7a96-120">Configuring Global or Fallback Agreement Properties</span></span>](../core/configuring-global-or-fallback-agreement-properties.md)