---
title: 設定後援本機主機設定 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68511199-a7ed-45b3-807d-70378b2c6ebb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fa9e1fcc8bf1764a16142d38058e14878341fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233390"
---
# <a name="configuring-fallback-local-host-settngs-x12-transaction-set-settings"></a><span data-ttu-id="20c69-102">設定後援本機主機設定 (X12-交易集設定)</span><span class="sxs-lookup"><span data-stu-id="20c69-102">Configuring Fallback Local Host Settngs (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="20c69-103">為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="20c69-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="20c69-104">這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="20c69-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="20c69-105">在後援協議的這個頁面中，您要指定後援目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="20c69-105">In this page of the fallback agreement, you specify the fallback target namespace.</span></span> <span data-ttu-id="20c69-106">如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]判斷結構描述所述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="20c69-106">How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20c69-107">這個主題也適用於 HIPAA 相關設定。</span><span class="sxs-lookup"><span data-stu-id="20c69-107">This topic applies also to HIPAA-related settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="20c69-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="20c69-108">Prerequisites</span></span>  
 <span data-ttu-id="20c69-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="20c69-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="20c69-110">若要設定交易集的本機主機設定</span><span class="sxs-lookup"><span data-stu-id="20c69-110">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="20c69-111">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="20c69-111">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="20c69-112">在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**本機主機設定**.</span><span class="sxs-lookup"><span data-stu-id="20c69-112">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="20c69-113">選取**轉換隱含的小數格式 Nn 10 進制數值**来轉換成 BizTalk Server 中的中繼 XML 中的基底 10 數值將格式 Nn 指定的 EDI 數字。</span><span class="sxs-lookup"><span data-stu-id="20c69-113">Select **Convert implied decimal format Nn to base 10 numeric value** to convert an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20c69-114">轉換後，中繼 XML 可能會在長度驗證時失敗。</span><span class="sxs-lookup"><span data-stu-id="20c69-114">After this conversion, the intermediate XML may fail length validation.</span></span> <span data-ttu-id="20c69-115">這是因為以 10 為基底的數值格式包含小數點，這使得它的長度比 Nn 格式數字大一。</span><span class="sxs-lookup"><span data-stu-id="20c69-115">This occurs because the number in the base-10 numeric format includes a decimal, making its length one greater than the number in Nn format.</span></span> <span data-ttu-id="20c69-116">您可以藉由新增的值來解決這個問題**1**最小/最大長度值。</span><span class="sxs-lookup"><span data-stu-id="20c69-116">You can resolve this issue by adding a value of **1** to the minimum/maximum length value.</span></span>  
  
4.  <span data-ttu-id="20c69-117">選取**建立針對尾端分隔符號的空 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="20c69-117">Select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
5.  <span data-ttu-id="20c69-118">如**目標命名空間**、 輸入 （或從下拉式清單中選取） 目標命名空間的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用來決定處理所接收的訊息之結構描述。</span><span class="sxs-lookup"><span data-stu-id="20c69-118">For **Target Namespace**, enter (or select from the drop-down list) the target namespace that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to determine the schema to process the received message with.</span></span>  
  
6.  <span data-ttu-id="20c69-119">按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="20c69-119">Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c69-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20c69-120">See Also</span></span>  
 [<span data-ttu-id="20c69-121">設定 X12 後援協議屬性的交易設定。</span><span class="sxs-lookup"><span data-stu-id="20c69-121">Configuring X12 Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)