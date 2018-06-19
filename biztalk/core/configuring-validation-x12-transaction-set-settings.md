---
title: 設定驗證 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0245be7f-d212-43b1-bfef-cbcbd851b5c0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880a8d1e31cbb10f570dcf5e7422a1e61b5cc8d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234262"
---
# <a name="configuring-validation-x12-transaction-set-settings"></a><span data-ttu-id="8a176-102">設定驗證 (X12 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="8a176-102">Configuring Validation (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="8a176-103">交易集驗證設定可定義 BizTalk Server 如何驗證接收自合作對象的交易集。</span><span class="sxs-lookup"><span data-stu-id="8a176-103">The transaction set validation settings define how BizTalk Server validates the transaction sets received from a party.</span></span> <span data-ttu-id="8a176-104">在驗證設定中，您可以指定 BizTalk Server 會在內送交換上執行的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8a176-104">As part of validation settings you can specify which type of validation BizTalk Server will perform on an incoming interchange</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a176-105">本主題也適用於 HIPAA 驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8a176-105">This topic applies also to HIPAA validation settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a176-106">任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="8a176-106">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a176-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a176-107">Prerequisites</span></span>  
 <span data-ttu-id="8a176-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="8a176-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation-settings"></a><span data-ttu-id="8a176-109">若要設定驗證設定</span><span class="sxs-lookup"><span data-stu-id="8a176-109">To configure validation settings</span></span>  
  
1.  <span data-ttu-id="8a176-110">建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="8a176-110">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="8a176-111">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8a176-111">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8a176-112">在單向協議索引標籤底下**交易集設定**區段中，按一下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8a176-112">On a one-way agreement tab, under **Transaction Set Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="8a176-113">在格線中，您可以針對不同的交易集定義不同的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8a176-113">In the grid, you can define different validation settings for different transaction sets.</span></span> <span data-ttu-id="8a176-114">在**驗證**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8a176-114">In the **Validation** page, do the following:</span></span>  
  
    |<span data-ttu-id="8a176-115">使用</span><span class="sxs-lookup"><span data-stu-id="8a176-115">Use this</span></span>|<span data-ttu-id="8a176-116">動作</span><span class="sxs-lookup"><span data-stu-id="8a176-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8a176-117">**預設值**</span><span class="sxs-lookup"><span data-stu-id="8a176-117">**Default**</span></span>|<span data-ttu-id="8a176-118">選取此核取方塊可定義預設驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8a176-118">Select the check box to define a default validation setting.</span></span>|  
    |<span data-ttu-id="8a176-119">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="8a176-119">**Transaction Type**</span></span>|<span data-ttu-id="8a176-120">按一下此欄中的空白儲存格，然後從下拉式清單中選取交易類型。</span><span class="sxs-lookup"><span data-stu-id="8a176-120">Click the empty cell in the column and from the drop-down select a transaction type.</span></span>|  
    |<span data-ttu-id="8a176-121">**Edi 類型驗證**</span><span class="sxs-lookup"><span data-stu-id="8a176-121">**Edi Type Validation**</span></span>|<span data-ttu-id="8a176-122">選取此選項，啟用對交換接收者的 EDI (資料元素) 驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-122">Select this to enable EDI (data element) validation on the interchange receiver.</span></span> <span data-ttu-id="8a176-123">這項驗證會針對交易集資料元素、驗證資料型別、長度限制，以及空的資料元素和培訓分隔符號執行 EDI 驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-123">This validation performs EDI validation on transaction-set data elements, validating data types, length restrictions, and empty data elements and training separators.</span></span> <span data-ttu-id="8a176-124">如需詳細資訊，請參閱[EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="8a176-124">For more information, see [EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md).</span></span> <span data-ttu-id="8a176-125">**注意：** 如果它已在結構描述註解，即使未選取此屬性，仍執行欄位/區段交互驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-125">**Note:**  Even if this property is not selected, cross-field/segment validation will be performed if it is turned on in the schema annotation.</span></span>|  
    |<span data-ttu-id="8a176-126">**擴充的驗證**</span><span class="sxs-lookup"><span data-stu-id="8a176-126">**Extended validation**</span></span>|<span data-ttu-id="8a176-127">如果選取此選項，可針對從交換傳送者所接收的交換，啟用擴充 (BizTalk XSD) 驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-127">Select this to enable extended (BizTalk XSD) validation of interchanges received from the interchange sender.</span></span> <span data-ttu-id="8a176-128">除了 XSD 資料型別驗證外，還包括欄位長度、選用性和重複計數驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-128">This includes validation of field length, optionality, and repeat count in addition to XSD data type validation.</span></span> <span data-ttu-id="8a176-129">如需詳細資訊，請參閱[擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="8a176-129">For more information, see [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md).</span></span> <span data-ttu-id="8a176-130">**注意：** 您可以選取此核取方塊才**Edi 類型驗證**已選取。</span><span class="sxs-lookup"><span data-stu-id="8a176-130">**Note:**  You can select this check box only if **Edi Type Validation** is selected.</span></span>|  
    |<span data-ttu-id="8a176-131">**允許前置和尾端零及空格**</span><span class="sxs-lookup"><span data-stu-id="8a176-131">**Allow leading and trailing zeroes and spaces**</span></span>|<span data-ttu-id="8a176-132">如果選取此方塊，可指定如果 EDI 交換中的資料項目由於開頭或尾端有零或空格而不符合其長度需求，但在移除這些項目之後就符合長度需求時，從合作對象所接收的 EDI 交換會通過驗證。</span><span class="sxs-lookup"><span data-stu-id="8a176-132">Select to specify that an EDI interchange received from the party will not fail validation if a data element in an EDI interchange does not conform to its length requirement because of leading (or trailing) zeroes or trailing spaces, but does conform to its length requirement when they are removed.</span></span> <span data-ttu-id="8a176-133">**注意：** 您可以選取此核取方塊才**Edi 類型驗證**已選取。</span><span class="sxs-lookup"><span data-stu-id="8a176-133">**Note:**  You can select this check box only if **Edi Type Validation** is selected.</span></span>|  
    |<span data-ttu-id="8a176-134">**尾端分隔符號原則**</span><span class="sxs-lookup"><span data-stu-id="8a176-134">**Trailing Separator Policy**</span></span>|<span data-ttu-id="8a176-135">-選取**不允許**如果您不想允許在從交換傳送者所接收之交換中使用尾端分隔符號與分隔字元。</span><span class="sxs-lookup"><span data-stu-id="8a176-135">-   Select **Not Allowed** if you do not want to allow trailing delimiters and separators in an interchange received from the interchange sender.</span></span> <span data-ttu-id="8a176-136">如果此交換包含尾端分隔符號，此交換即宣告無效。</span><span class="sxs-lookup"><span data-stu-id="8a176-136">If the interchange contains trailing delimiters and separators, it will be declared invalid.</span></span><br /><span data-ttu-id="8a176-137">-選取**選擇性**接受具有或不具有結尾分隔字元的交換。</span><span class="sxs-lookup"><span data-stu-id="8a176-137">-   Select **Optional** to accept interchanges with or without trailing delimiters and separators.</span></span><br /><span data-ttu-id="8a176-138">-選取**強制**如果收到的交換必須包含尾端分隔符號與分隔字元。</span><span class="sxs-lookup"><span data-stu-id="8a176-138">-   Select **Mandatory** if the received interchange must contain trailing delimiters and separators.</span></span>|  
  
     <span data-ttu-id="8a176-139">您可以新增任意多個資料列，以定義特定交換的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8a176-139">You can add as many rows as you want to define validation settings for specific interchanges.</span></span>  
  
     <span data-ttu-id="8a176-140">若要刪除驗證設定，請選取資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="8a176-140">To delete a validation setting, select the row and click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a176-141">在格線中編輯屬性可能有點困難。</span><span class="sxs-lookup"><span data-stu-id="8a176-141">Editing the properties in the grid can be a little difficult.</span></span> <span data-ttu-id="8a176-142">相反地，您可以選取要編輯，然後編輯中的相同屬性的資料列**編輯選取的資料列**> 一節。</span><span class="sxs-lookup"><span data-stu-id="8a176-142">Instead, you can select the row to be editing and then edit the same properties in the **Edit Selected Row** section.</span></span> <span data-ttu-id="8a176-143">您在此提供的設定會反映在選取的資料列中。</span><span class="sxs-lookup"><span data-stu-id="8a176-143">The settings you provide here are reflected in the selected row.</span></span>  
  
4.  <span data-ttu-id="8a176-144">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8a176-144">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a176-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a176-145">See Also</span></span>  
 [<span data-ttu-id="8a176-146">設定交易集設定 (X12)</span><span class="sxs-lookup"><span data-stu-id="8a176-146">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)