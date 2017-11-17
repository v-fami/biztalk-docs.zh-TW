---
title: "變更欄位 Rekeyed |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rekeyed fields
- Message Repair and New Submission, modifying fields
- Message Repair and New Submission, rekeyed fields
ms.assetid: aaf353f7-0e43-403e-b72a-88e5dd07f4ac
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc47d080b43b7679e76b9c6f8a0d8de1216daeaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="changing-fields-to-be-rekeyed"></a><span data-ttu-id="f698e-102">變更 Rekeyed 的欄位</span><span class="sxs-lookup"><span data-stu-id="f698e-102">Changing Fields to Be Rekeyed</span></span>
<span data-ttu-id="f698e-103">在 訊息修復工作流程執行驗證步驟[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]移除資料的欄位數目，讓驗證器必須重新輸入，或重設金鑰，該資料。</span><span class="sxs-lookup"><span data-stu-id="f698e-103">In the verification step of a message repair workflow, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] removes the data from a number of fields so that the verifier must re-enter, or rekey, that data.</span></span> <span data-ttu-id="f698e-104">您可以自訂 RekeyVerify 中的哪些欄位[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]需要 rekeyed 表單。</span><span class="sxs-lookup"><span data-stu-id="f698e-104">You can customize which fields in the RekeyVerify [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form need to be rekeyed.</span></span> <span data-ttu-id="f698e-105">這麼做在 MrsrXpathConfig.xml 檔案中，位於\<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\MRSR 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f698e-105">You do so in the MrsrXpathConfig.xml file, which is located in the \<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\MRSR folder.</span></span>  
  
 <span data-ttu-id="f698e-106">MrsrXpathConfig.xml 檔案包含一系列處理的訊息類型的節點。</span><span class="sxs-lookup"><span data-stu-id="f698e-106">The MrsrXpathConfig.xml file contains a series of nodes for the message type processed.</span></span> <span data-ttu-id="f698e-107">每個訊息類型節點包含一系列的欄位節點，其中每個欄位。</span><span class="sxs-lookup"><span data-stu-id="f698e-107">Each message-type node contains a series of field nodes, one for each field.</span></span> <span data-ttu-id="f698e-108">您可以變更的欄位由在文字編輯器中，例如 記事本 開啟 MrsrXpathConfig.xml 以及加入或移除 rekeyed\<路徑 > 欄位 節點。</span><span class="sxs-lookup"><span data-stu-id="f698e-108">You can change the fields to be rekeyed by opening MrsrXpathConfig.xml in a text editor, such as Notepad, and adding or removing a \<path> node for the field.</span></span>  
  
 <span data-ttu-id="f698e-109">\<路徑 > 節點包含訊息類型和欄位的路徑。</span><span class="sxs-lookup"><span data-stu-id="f698e-109">The \<path> node contains paths for the message type and the field.</span></span> <span data-ttu-id="f698e-110">例如，目的地路徑 MT103 訊息的輸入應用程式標頭區塊中的項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="f698e-110">For example, the entry for the Destination Path in the Input Application Header Block of an MT103 message is the following:</span></span>  
  
```  
<path>/*[local-name()='SWIFT_CATEGORY1_MT103_Interchange' and namespace-uri()'http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category1/MT103']/*[local-name()='SWIFTHeader' and namespace-uri=']'']/*[local-name()='ApplicationHeaderBlock_Input' and namespace-uri90='']/*[local-name()='DestinationAddress' and namespace-uri()='']</path>  
```  
  
 <span data-ttu-id="f698e-111">它是最簡單的方式加入新欄位，以複製，然後貼上現有的項目，然後變更 相關的路徑 rekeyed。</span><span class="sxs-lookup"><span data-stu-id="f698e-111">It is easiest to add a new field to be rekeyed by copying and then pasting an existing entry, and then changing the relevant paths.</span></span> <span data-ttu-id="f698e-112">例如，若要強制重設金鑰 MT103 訊息的值，日期貨幣 Interbank 結算量 32A 區段中的日期欄位，進行下列三個取代上述程式碼。</span><span class="sxs-lookup"><span data-stu-id="f698e-112">For example, to force rekey of the Date field in the Value Date Currency Interbank Settled Amount 32A section of an MT103 message, make the following three replacements to the preceding code.</span></span> <span data-ttu-id="f698e-113">程式碼的其餘部分維持不變。</span><span class="sxs-lookup"><span data-stu-id="f698e-113">The rest of the code remains the same.</span></span>  
  
|<span data-ttu-id="f698e-114">取代此項</span><span class="sxs-lookup"><span data-stu-id="f698e-114">Replace this</span></span>|<span data-ttu-id="f698e-115">與這個</span><span class="sxs-lookup"><span data-stu-id="f698e-115">With this</span></span>|  
|------------------|---------------|  
|`SWIFTHeader`|`SWIFT_CATEGORY1_MT103`|  
|`ApplicationHeaderBlock_Input`|`ValueDateCurrencyInterbankSettledAmount_32A`|  
|`DestinationAddress`|`Date`|  
  
 <span data-ttu-id="f698e-116">如需重設金鑰欄位的詳細資訊，請參閱[Message Repair 和 New Submission 中的特殊處理](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="f698e-116">For more information about rekeying fields, see [Special Processing in Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).</span></span>