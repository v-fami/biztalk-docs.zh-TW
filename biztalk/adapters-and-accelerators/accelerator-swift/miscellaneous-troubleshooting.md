---
title: 其他疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 6ebc1867-b5d3-46de-b3bd-69e570ed2b2c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765b32895fa76c0c77b740b76e2e6a03f0571351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211174"
---
# <a name="miscellaneous-troubleshooting"></a>其他疑難排解
## <a name="leading-zeroes-validation-is-not-performed-for-fields-that-use-the-checkleadingzeroesinelement-method-to-validate-a-field-in-the-message-validation-policy"></a>前置字元為零可使用 CheckLeadingZeroesInElement 方法來驗證訊息驗證原則中的欄位的欄位，不執行驗證。  
  
### <a name="symptom"></a>徵兆  
 如果將訊息提交前置零的欄位中，即使欄位不允許前置的零和驗證原則包含的欄位，會執行這項驗證的規則，會不傳回任何 BRE 驗證錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 **CheckLeadingZeroInElement**方法隨附於的商務規則中的訊息類型的驗證原則。 此方法已被取代。 函式呼叫的目的是讓驗證失敗，如果沒有前置零函式呼叫中提供的項目中。 不過，這個方法不會驗證失敗，即使沒有前置零的欄位中。  
  
### <a name="solution"></a>方案  
 如果您想要檢查前置零，您必須實作**CheckLeadingZero**方法，而非**CheckLeadingZeroInElement**方法。 **CheckLeadingZero**造成驗證錯誤，如果沒有前置零的函式的字串輸入。  
  
 若要實作**CheckLeadingZero**方法，您必須建立自訂的方法叫用**CheckLeadingZero**從自訂函式內的方法並提供它做為字串的值是驗證前置字元為零。 這是因為**CheckLeadingZero**不會記錄錯誤，但改為只會傳回布林值 False 如果輸入的字串不是有效的 SWIFT 數字欄位或輸入字串有前置零。 否則，它會傳回 True。 您的自訂方法然後可以據此記錄錯誤。  
  
## <a name="an-error-is-returned-by-the-message-validation-policy-if-the-swift-number-field-has-a-leading-zero"></a>如果 SWIFT 數字欄位有前置零，傳回錯誤訊息驗證原則  
  
### <a name="symptom"></a>徵兆  
 如果將訊息提交欄位中的前置零即使前置零允許的欄位，會傳回 BRE 驗證錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 如果其中一種下列方法用來驗證 SWIFT 數字中的欄位而言，通常是在動作屬於規則的規則，也可能會發生。 這可能會發生量、 速率、 價格或數量的欄位。  
  
-   **CheckCurrencyAmount**  
  
-   **CheckValidAmount**  
  
-   **CheckValidCurrencyAndPriceCode**  
  
-   **CheckValidSignCurrencyAmount**  
  
-   **CheckValidSignDateCurrencyAmount**  
  
-   **CheckValidSignRate**  
  
-   **IsValidTransactionDetailsCurrencyAmount**  
  
### <a name="solution"></a>方案  
 如果任何上述清單中的方法除外**CheckValidSignRate**，用於在 [驗證原則] 中所述前置零的啟用規則[量欄位驗證支援前置零](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).  
  
 如果**CheckValidSignRate**方法中的規則，傳回這個錯誤，則支援前置零的唯一方式是從 驗證原則移除此規則。 請遵循下列步驟來完成這項作業：  
  
1.  在商務規則編輯器，以滑鼠右鍵按一下**版本**已部署的原則，其中包含規則使用的節點**CheckValidSignRate**方法。 按一下**解除部署**。  
  
2.  以滑鼠右鍵按一下**版本**節點為相同的原則，然後按一下**複製**。  
  
3.  以滑鼠右鍵按一下**Validation_Policy**節點為相同的原則，然後按一下**貼上**。  
  
4.  展開新未儲存的原則版本。 以滑鼠右鍵按一下的規則即**CheckValidSignRate**方法呼叫，然後按一下**刪除**。  
  
5.  以滑鼠右鍵按一下新的儲存原則**版本**節點，然後再按一下**儲存**。 以滑鼠右鍵按一下相同節點，然後按一下**發行**。 以滑鼠右鍵按一下相同節點，然後按一下**部署**。  
  
## <a name="a4swift-database-requires-archiving"></a>A4SWIFT 資料庫需要封存  
  
### <a name="symptom"></a>徵兆  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫成長太大。  
  
### <a name="possible-cause"></a>可能的原因  
 中的歷程記錄資料表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫不會自動封存。 此資料表會儲存訊息修復和新送出，包括誰執行哪些工作和協調流程的相關資料的相關資料。 此資料表會繼續成長，當您執行訊息修復和新送出作業。  
  
### <a name="solution"></a>方案  
 若要限制的成長[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫中，定期封存移出歷程記錄資料表，使用您保存程序的標準的資料。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解： 問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)