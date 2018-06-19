---
title: 變更欄位 Rekeyed |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- rekeyed fields
- Message Repair and New Submission, modifying fields
- Message Repair and New Submission, rekeyed fields
ms.assetid: aaf353f7-0e43-403e-b72a-88e5dd07f4ac
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04693bf4c4d441487a3ce38f886bc680b1db368b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964492"
---
# <a name="changing-fields-to-be-rekeyed"></a>變更 Rekeyed 的欄位
在 訊息修復工作流程執行驗證步驟[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]移除資料的欄位數目，讓驗證器必須重新輸入，或重設金鑰，該資料。 您可以自訂 RekeyVerify 中的哪些欄位[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]需要 rekeyed 表單。 這麼做在 MrsrXpathConfig.xml 檔案中，位於\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\MRSR 資料夾。  
  
 MrsrXpathConfig.xml 檔案包含一系列處理的訊息類型的節點。 每個訊息類型節點包含一系列的欄位節點，其中每個欄位。 您可以變更的欄位由在文字編輯器中，例如 [記事本] 開啟 MrsrXpathConfig.xml 以及加入或移除 rekeyed\<路徑\>欄位的節點。  
  
 \<路徑\>節點包含訊息類型和欄位的路徑。 例如，目的地路徑 MT103 訊息的輸入應用程式標頭區塊中的項目如下所示：  
  
```  
<path>/*[local-name()='SWIFT_CATEGORY1_MT103_Interchange' and namespace-uri()'http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category1/MT103']/*[local-name()='SWIFTHeader' and namespace-uri=']'']/*[local-name()='ApplicationHeaderBlock_Input' and namespace-uri90='']/*[local-name()='DestinationAddress' and namespace-uri()='']</path>  
```  
  
 它是最簡單的方式加入新欄位，以複製，然後貼上現有的項目，然後變更 相關的路徑 rekeyed。 例如，若要強制重設金鑰 MT103 訊息的值，日期貨幣 Interbank 結算量 32A 區段中的日期欄位，進行下列三個取代上述程式碼。 程式碼的其餘部分維持不變。  
  
|取代此項|與這個|  
|------------------|---------------|  
|`SWIFTHeader`|`SWIFT_CATEGORY1_MT103`|  
|`ApplicationHeaderBlock_Input`|`ValueDateCurrencyInterbankSettledAmount_32A`|  
|`DestinationAddress`|`Date`|  
  
 如需重設金鑰欄位的詳細資訊，請參閱[Message Repair 和 New Submission 中的特殊處理](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)。