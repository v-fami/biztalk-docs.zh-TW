---
title: 設定後援信封屬性 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a951f70-07d5-4a58-b1ea-e7117a45c545
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa7898d1e1a83da879400a89d5cd089ef2d4069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233166"
---
# <a name="configuring-fallback-envelope-properties-x12-transaction-set-settings"></a><span data-ttu-id="a35ec-102">設定後援信封屬性 (X12-交易集設定)</span><span class="sxs-lookup"><span data-stu-id="a35ec-102">Configuring Fallback Envelope Properties (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="a35ec-103">在**信封**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 X12 編碼交換的 GS 區段。</span><span class="sxs-lookup"><span data-stu-id="a35ec-103">In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS segments for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="a35ec-104">GS 區段可識別並指定 X12 編碼交換的功能群組。</span><span class="sxs-lookup"><span data-stu-id="a35ec-104">A GS segment identifies and specifies a functional group for an X12-encoded interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a35ec-105">這個主題也適用於 HIPAA 相關設定。</span><span class="sxs-lookup"><span data-stu-id="a35ec-105">This topic applies also to HIPAA-related settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a35ec-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="a35ec-106">Prerequisites</span></span>  
 <span data-ttu-id="a35ec-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="a35ec-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-gs-segments"></a><span data-ttu-id="a35ec-108">定義 GS 區段</span><span class="sxs-lookup"><span data-stu-id="a35ec-108">To define the GS segments</span></span>  
  
1.  <span data-ttu-id="a35ec-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="a35ec-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="a35ec-110">在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**信封**.</span><span class="sxs-lookup"><span data-stu-id="a35ec-110">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="a35ec-111">如**功能代碼 (GS01)**，從下拉式清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="a35ec-111">For **Functional code (GS01)**, select a value from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="a35ec-112">如**應用程式傳送者 (GS02)**，輸入最少 2 個，最多 15 個英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a35ec-112">For **Application sender (GS02)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15.</span></span> <span data-ttu-id="a35ec-113">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a35ec-113">This is a required field.</span></span>  
  
5.  <span data-ttu-id="a35ec-114">如**應用程式接收者 (GS03)**，輸入最少 2 個，最多 15 個英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a35ec-114">For **Application receiver (GS03)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15.</span></span> <span data-ttu-id="a35ec-115">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a35ec-115">This is a required field.</span></span>  
  
6.  <span data-ttu-id="a35ec-116">如**日期格式 (GS04)**，從下拉式清單中選取 CCYYMMDD 或 YYMMDD。</span><span class="sxs-lookup"><span data-stu-id="a35ec-116">For **Date format (GS04)**, select CCYYMMDD or YYMMDD from the drop-down list.</span></span> <span data-ttu-id="a35ec-117">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a35ec-117">This is a required field.</span></span>  
  
7.  <span data-ttu-id="a35ec-118">如**時間格式 (GS05)**，從下拉式清單中選取 HHMM、 HHMMSS 或 HHMMSSdd。</span><span class="sxs-lookup"><span data-stu-id="a35ec-118">For **Time format (GS05)**, select HHMM, HHMMSS, or HHMMSSdd from the drop-down list.</span></span> <span data-ttu-id="a35ec-119">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a35ec-119">This is a required field.</span></span>  
  
8.  <span data-ttu-id="a35ec-120">如**負責單位 (GS07)**，從下拉式清單選取值。</span><span class="sxs-lookup"><span data-stu-id="a35ec-120">For **Responsible agency (GS07)**, select the value from the drop-down list.</span></span>  
  
9. <span data-ttu-id="a35ec-121">如**文件識別項 (GS08)**，輸入最少 1 個，最多 12 個英數字元值。</span><span class="sxs-lookup"><span data-stu-id="a35ec-121">For **Document identifier (GS08)**, enter an alphanumeric value with a minimum of 1 and a maximum of 12.</span></span> <span data-ttu-id="a35ec-122">這是選擇性欄位。</span><span class="sxs-lookup"><span data-stu-id="a35ec-122">This is an optional field.</span></span>  
  
10. <span data-ttu-id="a35ec-123">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a35ec-123">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35ec-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a35ec-124">See Also</span></span>  
 [<span data-ttu-id="a35ec-125">設定 X12 後援協議屬性的交易設定。</span><span class="sxs-lookup"><span data-stu-id="a35ec-125">Configuring X12 Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)