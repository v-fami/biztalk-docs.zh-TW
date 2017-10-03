---
title: "其他疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: 6ebc1867-b5d3-46de-b3bd-69e570ed2b2c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765b32895fa76c0c77b740b76e2e6a03f0571351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="miscellaneous-troubleshooting"></a><span data-ttu-id="9e4dc-102">其他疑難排解</span><span class="sxs-lookup"><span data-stu-id="9e4dc-102">Miscellaneous Troubleshooting</span></span>
## <a name="leading-zeroes-validation-is-not-performed-for-fields-that-use-the-checkleadingzeroesinelement-method-to-validate-a-field-in-the-message-validation-policy"></a><span data-ttu-id="9e4dc-103">前置字元為零可使用 CheckLeadingZeroesInElement 方法來驗證訊息驗證原則中的欄位的欄位，不執行驗證。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-103">Leading zeroes validation is not performed for fields that use the CheckLeadingZeroesInElement method to validate a field in the message Validation Policy.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="9e4dc-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="9e4dc-104">Symptom</span></span>  
 <span data-ttu-id="9e4dc-105">如果將訊息提交前置零的欄位中，即使欄位不允許前置的零和驗證原則包含的欄位，會執行這項驗證的規則，會不傳回任何 BRE 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-105">No BRE validation error is returned if a message is submitted with leading zeroes in a field, even though leading zeroes are not permitted for the field and the validation policy includes a rule for the field that performs this validation.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="9e4dc-106">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9e4dc-106">Possible Cause</span></span>  
 <span data-ttu-id="9e4dc-107">**CheckLeadingZeroInElement**方法隨附於的商務規則中的訊息類型的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-107">The **CheckLeadingZeroInElement** method is included in a business rule in the validation policy for the message type.</span></span> <span data-ttu-id="9e4dc-108">此方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-108">This method is deprecated.</span></span> <span data-ttu-id="9e4dc-109">函式呼叫的目的是讓驗證失敗，如果沒有前置零函式呼叫中提供的項目中。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-109">The purpose of the function call is to cause validation to fail if there is a leading zero in the element provided in the function call.</span></span> <span data-ttu-id="9e4dc-110">不過，這個方法不會驗證失敗，即使沒有前置零的欄位中。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-110">However, this method does not cause validation to fail, even if there is a leading zero in the field.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="9e4dc-111">方案</span><span class="sxs-lookup"><span data-stu-id="9e4dc-111">Solution</span></span>  
 <span data-ttu-id="9e4dc-112">如果您想要檢查前置零，您必須實作**CheckLeadingZero**方法，而非**CheckLeadingZeroInElement**方法。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-112">If you want to check leading zeroes, you must implement the **CheckLeadingZero** method instead of the **CheckLeadingZeroInElement** method.</span></span> <span data-ttu-id="9e4dc-113">**CheckLeadingZero**造成驗證錯誤，如果沒有前置零的函式的字串輸入。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-113">**CheckLeadingZero** causes a validation error if there is a leading zero in the string input to the function.</span></span>  
  
 <span data-ttu-id="9e4dc-114">若要實作**CheckLeadingZero**方法，您必須建立自訂的方法叫用**CheckLeadingZero**從自訂函式內的方法並提供它做為字串的值是驗證前置字元為零。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-114">To implement the **CheckLeadingZero** method, you must create a custom method that invokes the **CheckLeadingZero** method from within the custom function and provides to it as a string the value to be validated for leading zeroes.</span></span> <span data-ttu-id="9e4dc-115">這是因為**CheckLeadingZero**不會記錄錯誤，但改為只會傳回布林值 False 如果輸入的字串不是有效的 SWIFT 數字欄位或輸入字串有前置零。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-115">This is because **CheckLeadingZero** does not log an error, but instead simply returns a Boolean False if the input string is not a valid SWIFT Number field or if the string input has a leading zero.</span></span> <span data-ttu-id="9e4dc-116">否則，它會傳回 True。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-116">Otherwise, it returns True.</span></span> <span data-ttu-id="9e4dc-117">您的自訂方法然後可以據此記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-117">Your custom method can then log errors accordingly.</span></span>  
  
## <a name="an-error-is-returned-by-the-message-validation-policy-if-the-swift-number-field-has-a-leading-zero"></a><span data-ttu-id="9e4dc-118">如果 SWIFT 數字欄位有前置零，傳回錯誤訊息驗證原則</span><span class="sxs-lookup"><span data-stu-id="9e4dc-118">An error is returned by the message validation policy if the SWIFT Number field has a leading zero</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="9e4dc-119">徵兆</span><span class="sxs-lookup"><span data-stu-id="9e4dc-119">Symptom</span></span>  
 <span data-ttu-id="9e4dc-120">如果將訊息提交欄位中的前置零即使前置零允許的欄位，會傳回 BRE 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-120">A BRE validation error is returned if a message is submitted with leading zeroes in a field even though leading zeroes are permitted for the field.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="9e4dc-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9e4dc-121">Possible Cause</span></span>  
 <span data-ttu-id="9e4dc-122">如果其中一種下列方法用來驗證 SWIFT 數字中的欄位而言，通常是在動作屬於規則的規則，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-122">This can occur if one of the following methods is used to validate a SWIFT Number field in the rule concerned, usually in the Action part of the rule.</span></span> <span data-ttu-id="9e4dc-123">這可能會發生量、 速率、 價格或數量的欄位。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-123">This may occur in an Amount, Rate, Price, or Quantity field.</span></span>  
  
-   <span data-ttu-id="9e4dc-124">**CheckCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-124">**CheckCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="9e4dc-125">**CheckValidAmount**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-125">**CheckValidAmount**</span></span>  
  
-   <span data-ttu-id="9e4dc-126">**CheckValidCurrencyAndPriceCode**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-126">**CheckValidCurrencyAndPriceCode**</span></span>  
  
-   <span data-ttu-id="9e4dc-127">**CheckValidSignCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-127">**CheckValidSignCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="9e4dc-128">**CheckValidSignDateCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-128">**CheckValidSignDateCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="9e4dc-129">**CheckValidSignRate**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-129">**CheckValidSignRate**</span></span>  
  
-   <span data-ttu-id="9e4dc-130">**IsValidTransactionDetailsCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="9e4dc-130">**IsValidTransactionDetailsCurrencyAmount**</span></span>  
  
### <a name="solution"></a><span data-ttu-id="9e4dc-131">方案</span><span class="sxs-lookup"><span data-stu-id="9e4dc-131">Solution</span></span>  
 <span data-ttu-id="9e4dc-132">如果任何上述清單中的方法除外**CheckValidSignRate**，用於在 [驗證原則] 中所述前置零的啟用規則[量欄位驗證支援前置零](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).</span><span class="sxs-lookup"><span data-stu-id="9e4dc-132">If any of the methods in the list above, except for **CheckValidSignRate**, is used in the rule in the Validation policy, enable leading zeros as described in [Supporting Leading Zeros in Amount Field Validations](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).</span></span>  
  
 <span data-ttu-id="9e4dc-133">如果**CheckValidSignRate**方法中的規則，傳回這個錯誤，則支援前置零的唯一方式是從 驗證原則移除此規則。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-133">If the **CheckValidSignRate** method is used in the rule that returned this error, the only way to support leading zeroes is to remove this rule from the Validation policy.</span></span> <span data-ttu-id="9e4dc-134">請遵循下列步驟來完成這項作業：</span><span class="sxs-lookup"><span data-stu-id="9e4dc-134">Follow the steps below to accomplish this:</span></span>  
  
1.  <span data-ttu-id="9e4dc-135">在商務規則編輯器，以滑鼠右鍵按一下**版本**已部署的原則，其中包含規則使用的節點**CheckValidSignRate**方法。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-135">In Business Rule Composer, right-click the **Version** node for the deployed policy that contains a rule using the **CheckValidSignRate** method.</span></span> <span data-ttu-id="9e4dc-136">按一下**解除部署**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-136">Click **Undeploy**.</span></span>  
  
2.  <span data-ttu-id="9e4dc-137">以滑鼠右鍵按一下**版本**節點為相同的原則，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-137">Right-click the **Version** node for the same policy, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="9e4dc-138">以滑鼠右鍵按一下**Validation_Policy**節點為相同的原則，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-138">Right-click the **Validation_Policy** node for the same policy, and then click **Paste**.</span></span>  
  
4.  <span data-ttu-id="9e4dc-139">展開新未儲存的原則版本。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-139">Expand the new unsaved version of the policy.</span></span> <span data-ttu-id="9e4dc-140">以滑鼠右鍵按一下的規則即**CheckValidSignRate**方法呼叫，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-140">Right-click the rule that has the **CheckValidSignRate** method call, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="9e4dc-141">以滑鼠右鍵按一下新的儲存原則**版本**節點，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-141">Right-click the policy's new unsaved **Version** node, and then click **Save**.</span></span> <span data-ttu-id="9e4dc-142">以滑鼠右鍵按一下相同節點，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-142">Right-click the same node, and then click **Publish**.</span></span> <span data-ttu-id="9e4dc-143">以滑鼠右鍵按一下相同節點，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-143">Right-click the same node, and then click **Deploy**.</span></span>  
  
## <a name="a4swift-database-requires-archiving"></a><span data-ttu-id="9e4dc-144">A4SWIFT 資料庫需要封存</span><span class="sxs-lookup"><span data-stu-id="9e4dc-144">A4SWIFT database requires archiving</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="9e4dc-145">徵兆</span><span class="sxs-lookup"><span data-stu-id="9e4dc-145">Symptom</span></span>  
 <span data-ttu-id="9e4dc-146">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫成長太大。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-146">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is growing too large.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="9e4dc-147">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9e4dc-147">Possible Cause</span></span>  
 <span data-ttu-id="9e4dc-148">中的歷程記錄資料表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫不會自動封存。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-148">The History table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is not automatically archived.</span></span> <span data-ttu-id="9e4dc-149">此資料表會儲存訊息修復和新送出，包括誰執行哪些工作和協調流程的相關資料的相關資料。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-149">This table stores data about message repair and new submission, including who performed which tasks and data about orchestration processes.</span></span> <span data-ttu-id="9e4dc-150">此資料表會繼續成長，當您執行訊息修復和新送出作業。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-150">This table will continue to grow as you perform message repair and new submission operations.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="9e4dc-151">方案</span><span class="sxs-lookup"><span data-stu-id="9e4dc-151">Solution</span></span>  
 <span data-ttu-id="9e4dc-152">若要限制的成長[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫中，定期封存移出歷程記錄資料表，使用您保存程序的標準的資料。</span><span class="sxs-lookup"><span data-stu-id="9e4dc-152">To limit growth of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, routinely archive data out of the History table, using your standard archiving procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4dc-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4dc-153">See Also</span></span>  
 [<span data-ttu-id="9e4dc-154">疑難排解： 問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="9e4dc-154">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)