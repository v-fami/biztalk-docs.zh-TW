---
title: "TestCrypto |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, TestCrypto utility
- troubleshooting, TestCrypto utility
- TestCrypto utility
ms.assetid: 02768794-64ac-4d99-930c-738bed9626c5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 632ad57a8bb8a32c8f579a07980480dbd3bf0087
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="testcrypto"></a><span data-ttu-id="339bc-102">TestCrypto</span><span class="sxs-lookup"><span data-stu-id="339bc-102">TestCrypto</span></span>
<span data-ttu-id="339bc-103">您可使用 TestCrypto 公用程式在解密訊息失敗時進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="339bc-103">You use the TestCrypto utility to troubleshoot failures in decrypting messages.</span></span> <span data-ttu-id="339bc-104">此公用程式會指出解密是否失敗。</span><span class="sxs-lookup"><span data-stu-id="339bc-104">The utility indicates whether decryption fails.</span></span> <span data-ttu-id="339bc-105">如果解密成功，公用程式就會指出憑證為何，並顯示解密後訊息。</span><span class="sxs-lookup"><span data-stu-id="339bc-105">If the decryption succeeds, the utility indicates what the certificate is, and displays the decrypted message.</span></span>  
  
 <span data-ttu-id="339bc-106">您可在只包含訊息之加密部分的檔案上執行 TestCrypto，不需要未加密的標頭。</span><span class="sxs-lookup"><span data-stu-id="339bc-106">You run TestCrypto on a file that contains only the encrypted part of the message, without unencrypted headers.</span></span> <span data-ttu-id="339bc-107">請探查內送訊息或從 `MessageStorageIn` 擷取訊息，以便將訊息中加密的二進位大型物件 (BLOB) 解壓縮到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="339bc-107">Extract the encrypted binary large object (BLOB) from the message into a text file, either by sniffing the incoming message or by retrieving the message from `MessageStorageIn`.</span></span>  
  
 <span data-ttu-id="339bc-108">如需有關擷取訊息，以從`MessageStorageIn`，請參閱[GetMessages 範例](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="339bc-108">For more information about retrieving a message from `MessageStorageIn`, see [GetMessages Sample](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md).</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="339bc-109">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="339bc-109">Location in SDK</span></span>  
 <span data-ttu-id="339bc-110">\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="339bc-110">\<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK</span></span>  
  
## <a name="running-testcrypto"></a><span data-ttu-id="339bc-111">執行 TestCrypto</span><span class="sxs-lookup"><span data-stu-id="339bc-111">Running TestCrypto</span></span>  
  
#### <a name="to-run-testcrypto"></a><span data-ttu-id="339bc-112">若要執行 TestCrypto</span><span class="sxs-lookup"><span data-stu-id="339bc-112">To run TestCrypto</span></span>  
  
1.  <span data-ttu-id="339bc-113">按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下 **命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="339bc-113">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="339bc-114">移至\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK。</span><span class="sxs-lookup"><span data-stu-id="339bc-114">Move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span></span>  
  
3.  <span data-ttu-id="339bc-115">在命令提示字元中，輸入**TestCrypto.exe \<filename\>**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="339bc-115">At the command prompt, type **TestCrypto.exe \<filename\>**, and then press ENTER.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="339bc-116">備註</span><span class="sxs-lookup"><span data-stu-id="339bc-116">Remarks</span></span>  
 <span data-ttu-id="339bc-117">如果公用程式找到的憑證不是所需且有效的憑證，或是公用程式找不到該憑證，解密就會失敗。</span><span class="sxs-lookup"><span data-stu-id="339bc-117">Decryption fails if the certificate that the utility finds is not the required and valid certificate, or if the utility cannot find the certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339bc-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="339bc-118">See Also</span></span>  
 [<span data-ttu-id="339bc-119">公用程式</span><span class="sxs-lookup"><span data-stu-id="339bc-119">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)