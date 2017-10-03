---
title: "若要修復的訊息或提交新訊息使用 InfoPath 表單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- InfoPath forms, verifying messages
- submitting, messages
- InfoPath forms, repairing messages
- Bank Identifier Code (BIC)
- messages, submitting
- messages, repairing
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
- messages, modifying
- messages, InfoPath forms
- modifying, messages
- messages, approving
- repairing messages, InfoPath forms
- messages, creating
- approving messages
- messages, verifying
- verifying, messages
ms.assetid: fb1a885f-fb01-42be-88bc-f68715f689f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f89959b1900ce03717f2bb28efda7651c5008e7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-an-infopath-form-to-repair-a-message-or-submit-a-new-message"></a>若要修復的訊息或提交新訊息使用 InfoPath 表單
若要修復、 驗證、 核准，或建立一則訊息，您在工作[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]從開啟的表單[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 網站。 MRSR 站台包含[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單對於各種訊息類型和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單未剖析的訊息。 Message Repair 和 New Submission 會需要修復、 驗證或核准訊息傳送至適當的 MRSR 文件庫，而您可以開啟它。  
  
 當您在 MRSR 文件庫中，開啟郵件[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]顯示[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]填入訊息資料的表單。 在執行內部作業[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，可讓您操作加上標籤的欄位，來選取值，從下拉式清單中 （如果適用），並查看是否必要或選擇性欄位內的資料。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]可確保訊息修復和新送出程序的安全性，藉由送出要求的網域帳戶和簽章的憑證。  
  
 若要在訊息上執行作業[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 站台，您必須部署[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]該訊息類型的表單。 這會載入[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單範本文件庫所需的訊息。  
  
## <a name="repairing-a-message"></a>修復訊息  
 若要修復、 驗證、 核准，或建立訊息時，可以從開啟 MRSR SharePoint 站台內的 InfoPath 表單中。 要修復的訊息會發佈 MRSR 站台中。 Message Repair 和 New Submission 請將需要修復、 驗證或核准的訊息傳送至適當 MRSR 網站文件庫，而您可以開啟它。  
  
 當您開啟 MRSR 網站文件庫中的訊息時，A4SWIFT 顯示 InfoPath 表單會填入訊息資料。 您執行在 InfoPath 表單內，可讓您操作加上標籤的欄位，來選取值，從下拉式清單中 （如果適用），並查看是否必要或選擇性欄位內的資料作業。 A4SWIFT，可確保訊息修復和新送出程序的安全性，藉由送出要求的網域帳戶和簽章的憑證。  
  
 若要執行 MRSR 站台中的訊息上的作業，您必須部署該訊息類型的 InfoPath 表單。 這會載入到範本文件庫訊息所需的 InfoPath 表單。  
  
## <a name="verifying-a-message"></a>確認訊息  
 修復工作流程可以包含驗證階段。 在這個階段，repairer 已經修復訊息時之後, 驗證器會驗證訊息中的修復正確無誤。 若要這樣做，請您開啟中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成從\<部門名稱 > _RekeyVerify 文件庫 MRSR 站台，並確認修復對訊息進行正確無誤。 您也必須使用需要重設金鑰之特定欄位中重新鍵入資料。 所有的驗證階段需要重設金鑰，雖然您可以自訂哪些欄位 （如果有的話） 必須 rekeyed。 如需重設金鑰驗證的詳細資訊，請參閱[Message Repair 和 New Submission 中的特殊處理](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)。  
  
 所有可能的階段組成工作流程包含一個或多個驗證階段。 不過，工作流程不需要包含驗證階段。  
  
## <a name="approving-a-message"></a>核准訊息  
 修復工作流程可以包含 「 核准 」 階段。 在這個階段，驗證器已驗證訊息，或在新的訊息中，資料修復後核准者以視覺化方式確認訊息中的修復正確無誤。 請注意，驗證階段組成重設金鑰驗證，而核准階段組成 visual 驗證。  
  
## <a name="accepting-or-rejecting-the-changes-to-a-message"></a>接受或拒絕訊息中所做的變更  
 完成後階段，建立者、 repairer、 驗證器或核准者可以接受變更，取消變更，或拒絕變更。 如果提交成功時，接受將訊息移至下一個階段。 拒絕提交訊息，以拒絕的變更。 取消取消送出程序，以及訊息保留在其目前的階段。  
  
 如果您拒絕的訊息，請確認或核准階段中，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將訊息傳回至該工作流程定義的第一個階段 （建立或修復）。 工作流程會重設，因此任何 repairer 可修復的訊息。 如果工作流程的第一個階段拒絕訊息時，修復協調流程會將訊息發佈到 MessageBox，具有適當的升級屬性。 您可以撰寫自訂的處理常式，來處理這些訊息。 如需詳細資訊，請參閱[拒絕的訊息建立自訂處理常式](../../adapters-and-accelerators/accelerator-swift/creating-a-custom-handler-for-rejected-messages.md)。  
  
 如果您在建立或修復階段中，拒絕訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置訊息，而且您會收到錯誤訊息: 「 無法重設至工作流程中的第一個階段。"  
  
## <a name="repairing-an-unparsed-message"></a>修復未剖析的訊息  
 如果訊息失敗，因為剖析錯誤，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將訊息路由至 MRSR 站台中未剖析的文件庫。 如同無法通過驗證，當您按兩下訊息的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]顯示[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]填入訊息資料的表單。 您修復的訊息中的表單。 當您送出訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]訊息將直接傳送至寄件匣，而不需要驗證或核准。 如需詳細資訊，請參閱[修復未剖析訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。  
  
## <a name="creating-and-submitting-a-new-message"></a>建立及提交新的訊息  
 您可以建立新的訊息中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 藉由顯示新的郵件表單、 輸入資料，送出的站台。 如需詳細資訊，請參閱[建立及提交新訊息](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)。  
  
 若要建立新的訊息，您必須部署新的郵件表單，該訊息類型。 這會載入到您建立包含新郵件表單的文件庫訊息所需的 XML 格式。  
  
 當您從預設的新訊息形式建立一則訊息時，欄位不會擴展，要求您輸入所有欄位中的資料。 您可以藉由開啟郵件，輸入資料，然後執行儲存預先填入表單中的欄位-做為從 MRSR 站台中的 [檔案] 功能表的命令。 您可以提供[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成不同的名稱，並將它儲存到不同的文件庫。  
  
## <a name="looking-up-a-bic"></a>查閱 BIC  
 當您使用[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]中形成[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 站台，您可能需要輸入銀行識別項程式碼 (BIC)。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]提供可用來查閱 BIC 公用程式。 在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單中，在表單的右窗格中按一下 BIC 查閱。 這會顯示表單為基礎時的銀行名稱，或反之亦然 BIC 搜尋。 這個動作會搜尋的 Bicplus 資料表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫。 如需有關 Bicplus 資料表的詳細資訊，請參閱[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)和[管理 Bicplus 資料庫中的資料表 A4SWIFT](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)。