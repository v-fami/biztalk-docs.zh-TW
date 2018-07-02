---
title: ValidationAdapter |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fe99350-14c0-4ddb-b257-af9a0c4258f6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbcf26ee8a3a97d2df34bb29dad5d0cf31d4db1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987903"
---
# <a name="validationadapter"></a><span data-ttu-id="e4bb0-102">ValidationAdapter</span><span class="sxs-lookup"><span data-stu-id="e4bb0-102">ValidationAdapter</span></span>
<span data-ttu-id="e4bb0-103">ValidationAdapter 範例會示範如何對回應者公開程序的訊息執行特殊驗證規則。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-103">The ValidationAdapter sample demonstrates how to run special validation rules on a message in a responder public process.</span></span> <span data-ttu-id="e4bb0-104">Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]原生執行驗證，在傳送或接收管線和協調流程中。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-104">Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] natively performs validation in the send or receive pipeline, and in orchestrations.</span></span> <span data-ttu-id="e4bb0-105">如果您想要執行其他驗證，可以建立驗證配接器。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-105">If you want to perform additional validation, you can create a validation adapter.</span></span> <span data-ttu-id="e4bb0-106">其他驗證可能包含跨欄位或特定業務的驗證規則，而您無法使用 XSD 實作這些規則。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-106">The additional validation could include cross-field validation or business-specific validation rules that you cannot implement using an XSD.</span></span>  
  
 <span data-ttu-id="e4bb0-107">您可以建立驗證配接器藉由新增[!INCLUDE[btsCSharp](../../includes/btscsharp-md.md)]ValidationAdapter 範例、 發佈介面，並將配接器輸入協議屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-107">You can create a validation adapter by adding [!INCLUDE[btsCSharp](../../includes/btscsharp-md.md)] code to the ValidationAdapter sample, publishing the interfaces, and entering the adapter into the agreement properties.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="e4bb0-108"> 接著在訊息處理期間呼叫驗證配接器。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-108"> will then call the validation adapter during message processing.</span></span>  
  
 <span data-ttu-id="e4bb0-109">由於 ValidationAdapter 是由公開程序協調流程使用的，因此，ValidationAdapter 會在與裝載該協調流程之 BizTalk 主控件服務相同的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-109">Since the ValidationAdapter is used by the public process orchestration , it runs under the same credentials as the BizTalk host service hosting that orchestration.</span></span>  
  
 <span data-ttu-id="e4bb0-110">ValidationAdapter 範例位於\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\ValidationAdapter。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-110">The ValidationAdapter sample is located in \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\ValidationAdapter.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e4bb0-111">示範</span><span class="sxs-lookup"><span data-stu-id="e4bb0-111">Demonstrates</span></span>  
 <span data-ttu-id="e4bb0-112">ValidationAdapter 範例示範服務內容中電子郵件地址的驗證。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-112">The ValidationAdapter sample demonstrates validation of the e-mail address in the service content.</span></span> <span data-ttu-id="e4bb0-113">此範例會實作 `IValidateRNIFMessageParts` 介面。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-113">The sample implements the `IValidateRNIFMessageParts` interface.</span></span> <span data-ttu-id="e4bb0-114">如果電子郵件地址的格式不正確，就會傳回 `RNIFException`。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-114">It returns an `RNIFException` if the e-mail address is not in the correct format.</span></span> <span data-ttu-id="e4bb0-115">XML 文件**preambleToValidate**， **serviceHeaderToValidate**， **deliveryHeaderToValidate**，和**serviceContentToValidate**定義的驗證。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-115">The XML documents **preambleToValidate**, **serviceHeaderToValidate**, **deliveryHeaderToValidate**, and **serviceContentToValidate** define the validation.</span></span>  
  
 <span data-ttu-id="e4bb0-116">ValidationAdapter 會使用 RNIFerror.IsOkToSendException 屬性，決定在錯誤事件下要傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-116">The ValidationAdapter uses the RNIFerror.IsOkToSendException property to determine what kind of message to send in the event of an error.</span></span> <span data-ttu-id="e4bb0-117">如果驗證不成功，ValidationAdapter 便會將 RNIFerror.ErrorCode 設定為非零值。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-117">If validation does not succeed, the ValidationAdapter sets RNIFerror.ErrorCode to a non-zero value.</span></span> <span data-ttu-id="e4bb0-118">如果 RNIFerror.IsOkToSendException 屬性為 true，則程序會傳送負值通知。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-118">If RNIFerror.IsOkToSendException property is true, the process sends a negative acknowledgment.</span></span> <span data-ttu-id="e4bb0-119">在 RNIF 2.0 中，這屬於例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-119">For RNIF 2.0, this is an exception message.</span></span> <span data-ttu-id="e4bb0-120">在 RNIF 1.1 中，則屬於接收通知的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-120">For RNIF 1.1, this is a receipt acknowledgment exception message.</span></span> <span data-ttu-id="e4bb0-121">如果 RNIFerror.IsOkToSendException 屬性為 false，並且已設定 0A1，則程序將會傳送 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-121">If RNIFerror.IsOkToSendException property is false and 0A1 is configured, the process will send a 0A1 message.</span></span> <span data-ttu-id="e4bb0-122">一旦例外狀況訊息、 接收通知的例外狀況訊息或 0A1 訊息，傳送給處理程序，它將會終止。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-122">Once the process sends an exception message, receipt acknowledgment exception message, or 0A1 message, it will terminate.</span></span>  
  
 <span data-ttu-id="e4bb0-123">如果 RNIFerror.IsOkToSendException 屬性為 false，並且未設定 0A1，則程序將不會傳送例外狀況訊息或 0A1 訊息。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-123">If RNIFerror.IsOkToSendException property is false and 0A1 is not configured, the process will send neither an exception nor a 0A1.</span></span> <span data-ttu-id="e4bb0-124">程序會記錄錯誤，然後終止。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-124">It will log the error and then terminate.</span></span>  
  
 <span data-ttu-id="e4bb0-125">如果驗證成功，ValidationAdapter 便會將 RNIFerror.ErrorCode 設定為 0，並且 BTARN 會將訊息路由傳送至私用程序。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-125">If validation succeeds, the ValidationAdapter sets RNIFerror.ErrorCode to 0, and BTARN routes the message to the private process.</span></span> <span data-ttu-id="e4bb0-126">BTARN 只有在驗證成功的情況下，才會將訊息路由傳送至私用程序。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-126">It routes the message to the private process only if validation is successful.</span></span>  
  
## <a name="to-implement-this-sample"></a><span data-ttu-id="e4bb0-127">實作這個範例</span><span class="sxs-lookup"><span data-stu-id="e4bb0-127">To Implement this Sample</span></span>  
 <span data-ttu-id="e4bb0-128">若要實作 ValidationAdapter 範例，您必須在協議中加入驗證配接器。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-128">To implement the ValidationAdapter sample, you must add the validation adapter to the agreement.</span></span>  
  
#### <a name="to-add-the-validation-adapter-to-the-agreement"></a><span data-ttu-id="e4bb0-129">在協議中加入驗證配接器</span><span class="sxs-lookup"><span data-stu-id="e4bb0-129">To add the validation adapter to the agreement</span></span>  
  
1. <span data-ttu-id="e4bb0-130">按一下 **開始**，指向**所有程式**，指向 Microsoft [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-130">Click **Start**, point to **All Programs**, point to Microsoft [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2. <span data-ttu-id="e4bb0-131">在 [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-131">In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Agreements**.</span></span>  
  
3. <span data-ttu-id="e4bb0-132">按兩下您要加入至驗證配接器的協議。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-132">Double-click the agreement to which you want to add the validation adapter.</span></span>  
  
4. <span data-ttu-id="e4bb0-133">在 **驗證配接器**對話方塊方塊中，按一下省略符號按鈕 (**...**) 按鈕右邊**組件名稱**，移至含有驗證配接器組件的位置，選取適當的.dll 檔案，，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-133">In the **Validation Adapter** dialog box, click the ellipsis button (**...**) button to the right of **Assembly name**, move to the location that contains the validation adapter assembly, select the appropriate .dll file, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="e4bb0-134">按一下向下的箭號**類別名稱**，選取 驗證配接器類別，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e4bb0-134">Click the down arrow for **Class Name**, select the validation adapter class, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bb0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4bb0-135">See Also</span></span>  
 [<span data-ttu-id="e4bb0-136">配接器範例</span><span class="sxs-lookup"><span data-stu-id="e4bb0-136">Adapter Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)