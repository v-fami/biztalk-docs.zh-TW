---
title: 設定欄位交互驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f0c6ae8-0b8a-4826-9dfb-bf27e5ff7fa6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bde88ac82d69cdaa0dec7513e294953b7164b56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233646"
---
# <a name="configuring-cross-field-validation"></a><span data-ttu-id="d5813-102">設定欄位交互驗證</span><span class="sxs-lookup"><span data-stu-id="d5813-102">Configuring Cross-Field Validation</span></span>
<span data-ttu-id="d5813-103">本主題說明如何在 EDI 編碼訊息內的交易集資料元素，啟用欄位/區段交互驗證。</span><span class="sxs-lookup"><span data-stu-id="d5813-103">This topic describes how to enable cross field/segment validation on transaction-set data elements in EDI-encoded messages.</span></span> <span data-ttu-id="d5813-104">若要這樣做，必須進行兩種設定：</span><span class="sxs-lookup"><span data-stu-id="d5813-104">To do so, you need to make two settings:</span></span>  
  
-   <span data-ttu-id="d5813-105">設定 EDI 結構描述註解中的欄位交互驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="d5813-105">Set the cross-field validation flag in an annotation of the EDI schema.</span></span> <span data-ttu-id="d5813-106">若為 X12 或 HIPAA 結構描述，則**X12ConditionDesignator_Check**旗標。</span><span class="sxs-lookup"><span data-stu-id="d5813-106">For X12 or HIPAA schemas, this is the **X12ConditionDesignator_Check** flag.</span></span> <span data-ttu-id="d5813-107">若為 EDIFACT 結構描述，則**EdifactDependencyRule_Check**旗標。</span><span class="sxs-lookup"><span data-stu-id="d5813-107">For EDIFACT schemas, this is the **EdifactDependencyRule_Check** flag.</span></span>  
  
-   <span data-ttu-id="d5813-108">啟用 在協議屬性中的 EDI 類型驗證。</span><span class="sxs-lookup"><span data-stu-id="d5813-108">Enable EDI-type validation in the agreement properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d5813-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="d5813-109">Prerequisites</span></span>  
 <span data-ttu-id="d5813-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="d5813-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="configuring-cross-field-validation"></a><span data-ttu-id="d5813-111">設定欄位交互驗證</span><span class="sxs-lookup"><span data-stu-id="d5813-111">Configuring Cross-Field Validation</span></span>  
  
1.  <span data-ttu-id="d5813-112">在 BizTalk 編輯器中開啟結構描述。</span><span class="sxs-lookup"><span data-stu-id="d5813-112">Open your schema in BizTalk Editor.</span></span>  
  
2.  <span data-ttu-id="d5813-113">對於 X12 或 HIPAA 結構描述，尋找**X12ConditionDesignator_Check**註解的結構描述 appinfo 區段中的旗標。</span><span class="sxs-lookup"><span data-stu-id="d5813-113">For an X12 or HIPAA schema, find the **X12ConditionDesignator_Check** flag in an annotation in the appinfo section of the schema.</span></span> <span data-ttu-id="d5813-114">將它設定為**是**。</span><span class="sxs-lookup"><span data-stu-id="d5813-114">Set it to **Yes**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5813-115">設定的旗標 X12ConditionDesignator_Check**是**無法執行從 BizTalk 結構描述編輯器。</span><span class="sxs-lookup"><span data-stu-id="d5813-115">Setting the flag X12ConditionDesignator_Check to **Yes** cannot be performed from BizTalk Schema Editor.</span></span> <span data-ttu-id="d5813-116">若要設定該旗標，必須在記事本或類似的文字編輯器中開啟結構描述檔案 (.xsd)，並且在編輯後儲存。</span><span class="sxs-lookup"><span data-stu-id="d5813-116">For setting the flag, you will have to open it in a notepad or similar text editor, edit, and then save the schema file (.xsd).</span></span>  
  
3.  <span data-ttu-id="d5813-117">對於 EDIFACT 結構描述中，尋找**EdifactDependencyRule_Check**註解的結構描述 appinfo 區段中的旗標。</span><span class="sxs-lookup"><span data-stu-id="d5813-117">For an EDIFACT schema, find the **EdifactDependencyRule_Check** flag in the annotation in the appinfo section of the schema.</span></span> <span data-ttu-id="d5813-118">將它設定為**是**。</span><span class="sxs-lookup"><span data-stu-id="d5813-118">Set it to **Yes**.</span></span>  
  
4.  <span data-ttu-id="d5813-119">針對結構描述適用的區段，指定套用的關係條件 (X12 和 HIPAA) 或相依性規則 (EDIFACT)。</span><span class="sxs-lookup"><span data-stu-id="d5813-119">For the applicable segments of the schema, specify the relational conditions (X12 and HIPAA) or dependency rules (EDIFACT) that apply.</span></span> <span data-ttu-id="d5813-120">如需詳細資訊，請參閱[跨欄位區段驗證](../core/cross-field-segment-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="d5813-120">For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5813-121">針對 EDI 結構描述內的區段，輸入欄位交互驗證條件或規則。</span><span class="sxs-lookup"><span data-stu-id="d5813-121">A cross-field validation condition or rule is entered for a segment in an EDI schema.</span></span> <span data-ttu-id="d5813-122">如果您的資料元素，而不是在區段中，輸入欄位交互驗證規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行結構描述驗證時，會產生警告。</span><span class="sxs-lookup"><span data-stu-id="d5813-122">If you enter a cross-field validation rule for a data element, rather than a segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a warning when schema validation is performed.</span></span>  
  
5.  <span data-ttu-id="d5813-123">在**驗證**頁面 (下**交易集設定**區段) 的單向協議索引標籤**協議屬性**相關的協議 對話方塊請確定**EDI 類型驗證**選取屬性。</span><span class="sxs-lookup"><span data-stu-id="d5813-123">In the **Validation** page (under the **Transaction Set Settings** section) of the one-way agreement tab of the **Agreement Properties** dialog box for relevant agreement, make sure that the **EDI type Validation** property is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5813-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5813-124">See Also</span></span>  
 [<span data-ttu-id="d5813-125">開發 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="d5813-125">Developing EDI Schemas</span></span>](../core/developing-edi-schemas.md)