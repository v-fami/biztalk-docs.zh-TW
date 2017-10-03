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
ms.openlocfilehash: 9e9d3314b5564ab7619744e97f8e63df55683117
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testcrypto"></a>TestCrypto
您可使用 TestCrypto 公用程式在解密訊息失敗時進行疑難排解。 此公用程式會指出解密是否失敗。 如果解密成功，公用程式就會指出憑證為何，並顯示解密後訊息。  
  
 您可在只包含訊息之加密部分的檔案上執行 TestCrypto，不需要未加密的標頭。 請探查內送訊息或從 `MessageStorageIn` 擷取訊息，以便將訊息中加密的二進位大型物件 (BLOB) 解壓縮到文字檔中。  
  
 如需有關擷取訊息，以從`MessageStorageIn`，請參閱[GetMessages 範例](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md)。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK  
  
## <a name="running-testcrypto"></a>執行 TestCrypto  
  
#### <a name="to-run-testcrypto"></a>若要執行 TestCrypto  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下 **命令提示字元**。  
  
2.  移至\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK。  
  
3.  在命令提示字元中，輸入**TestCrypto.exe\<檔名 >**，然後按 ENTER 鍵。  
  
## <a name="remarks"></a>備註  
 如果公用程式找到的憑證不是所需且有效的憑證，或是公用程式找不到該憑證，解密就會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)