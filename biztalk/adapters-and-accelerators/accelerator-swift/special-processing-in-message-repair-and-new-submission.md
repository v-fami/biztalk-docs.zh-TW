---
title: 特殊處理 Message Repair 和 New Submission |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages, rekey verification
- repairing messages, process flow
- rekey verification
- repairing messages
- messages, templates
- messages, rekey verification
- BIC fields
- templates, messages
- BIC-12 data
- messages, process flow
- BIC-11 data
ms.assetid: 0ab729e3-4b67-47d3-84c9-f016318a4c41
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d77d518b080fd84b874c9bb79dedd5173d0a78b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214414"
---
# <a name="special-processing-in-message-repair-and-new-submission"></a>在 訊息修復和新送出的特殊處理
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 功能可讓客戶開發企業實作。 功能支援下列特殊的處理：  
  
-   重設金鑰驗證  
  
-   部門專屬的工作流程支援 (如需詳細資訊，請參閱[修復的訊息和提交新訊息](../../adapters-and-accelerators/accelerator-swift/repairing-messages-and-submitting-new-messages.md)。)  
  
-   輸入為 BIC 11 BIC 12 資料  
  
-   BIC 欄位的項目當做一個字串  
  
-   修復和重新送出剖析失敗 (如需詳細資訊，請參閱[修復未剖析訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。)  
  
-   儲存修復進行中，使用 [儲存] 命令  
  
-   使用 [另存新檔] 命令建立新的範本  
  
## <a name="rekey-verification"></a>重設金鑰驗證  
 許多金融機構中，檢查工作的主要方法是供第二個使用者重設金鑰交易的最重要的欄位。 這項作業會驗證第二個使用者具有讀取及了解，這些欄位中的資料。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復或中建立的訊息提供這項功能[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 如果需要，重設金鑰步驟[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]出 rekeyed 向使用者顯示的表單中的欄位空白。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]讓驗證器可以使用這些內容，輸入資料時，仍顯示工作窗格中，原始訊息的內容。 因為這可能會允許變更，而不驗證驗證器不應變更訊息中的其他欄位。 相反地，驗證器應該拒絕訊息修復，如果需要進行其他變更。  
  
 重設金鑰的步驟之後，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]比較結果的修復金鑰的結果。 它只在有已 rekeyed，欄位的欄位為基礎的欄位上執行這項比較。 如果您不同意以逐字元為基礎的兩個版本，必須再次修復訊息。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]表示有索引鍵的驗證不符的情況，並將錯誤加入至錯誤集合組件的訊息。 輸入由驗證器的資料不會儲存。  
  
 底下的 MRSR 資料夾中 MrsrXpathConfig.xml 檔案中指定的欄位 rekeyed[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料夾。 此檔案包含要被 rekeyed 的欄位和欄位的 xpath 所組成的名稱/值組。 您可以自訂此檔案，以變更哪些欄位會 rekeyed 每個訊息。 要被 rekeyed 欄位通常會代表最重要日期的訊息內容中，與相關聯的交易，以及交易數量的貨幣。  
  
 在 訊息修復和新送出的所有驗證步驟牽涉都到重設金鑰驗證。 使驗證被執行的核准。  
  
## <a name="entry-of-bic-12-data-as-bic-11"></a>輸入為 BIC 11 BIC 12 資料  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]適用於需要訊息的邏輯終端機 （長期） 位址中的其他字元。 LT 位址包含只 11 個字元的資料，但 SWIFT 聯盟存取 (SAA) 需要 LT 欄位位置 9 中有"X"。 這個額外的字元表示 SAA 它應該選取正確的小型  
  
 LT 位址用於傳輸的訊息中，尋找網路上。 它可以包含在 SWIFTBound 訊息 （基本的標頭區塊的 LT 位址欄位） 或目的地位址 欄位中輸入應用程式標頭區塊的兩個欄位和來自 SWIFT 的訊息的兩個欄位 (LT 位址 欄位的基本的標頭區塊或LT 位址的輸出應用程式標頭區塊訊息輸入參考資料中）。  
  
 建立或修復的訊息，或重設欄位金鑰驗證的一部分時，使用者必須輸入只 11 個字元。 即使修復或重設金鑰 LT 具有 12 個字元，使用者必須輸入只 11 個字元。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將插入的第十二個字元，並驗證 12 個字元的欄位。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]驗證對 BIC 加上資料庫中的地址的 11 個字元 LT 位址。  
  
## <a name="entry-of-bic-fields-as-one-string"></a>BIC 欄位當做一個字串的項目  
 您可以輸入 BIC 併入單一欄位[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。 BIC 包含四個子欄位，每一個都有子欄位[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。 到單一欄位中，輸入完整的 BIC 字串之後[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]填入每四個子欄位。  
  
## <a name="saving-repairs-in-progress"></a>儲存修復進行中  
 如果您要中斷的修復，您可以儲存在目前的狀態訊息回修復收件匣。 您使用 [儲存] 命令來檢查訊息中。 您可以關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成並檢查訊息之後，或其他人可以簽出以繼續修復。 訊息的歷程記錄指出儲存作業，而且第二個 repairer 可以查看您執行修復。  
  
 您可以執行 [另存新檔] 命令來儲存使用者的本機電腦上目前的狀態訊息。 如此一來執行另存的使用者簽出的訊息。 使用者可以關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單和更新版本，才能完成修復，但另一位使用者傳回無法簽出的訊息並修復問題。  
  
## <a name="creating-a-new-template"></a>建立新的範本  
 在建立新的訊息時，您可以藉由執行 [另存新檔] 命令建立新的範本。 這可讓您以開啟現有的範本，將資料加入至欄位，然後建立新的範本以現有範本，其中包含其他資料。 您將範本儲存具有新名稱，並 MRSR 站台中新的郵件資料夾的存取權的任何人都可以建立新範本為基礎的訊息。 您必須儲存 MRSR 網站提交訊息範本為依據的範本[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 否則，便會發生錯誤，或無法開啟表單。