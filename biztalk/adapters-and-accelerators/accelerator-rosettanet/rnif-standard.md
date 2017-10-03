---
title: "RNIF 標準 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNIF, message definitions
- RNIF, messaging framework patterns
- messages, message definitions
- RNIF, standards
- messages, messaging framework patterns
ms.assetid: d39a9683-1ef5-462b-9472-4e30fe873f7d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6b29d8c9c770893fd78769b86266ce33e31a336
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rnif-standard"></a>RNIF 標準
RosettaNet 實作架構 (RNIF) 標準定義系統傳送 RosettaNet 訊息的方式。 RNIF 標準是穩固的傳輸、傳送、封裝及安全性標準。 所有 RosettaNet 訊息系統必須遵循 RNIF 標準才能通過 RosettaNet 憑證。  
  
 標準定義了訊息結構、通知的需要、多用途網際網路郵件延伸標準 (MIME) 編碼及數位簽章。 核心標準包含對驗證、授權、加密及不可否認性的要求。 RNIF 標準是以 HTTP、MIME、和 XML 標準為基礎， 不會指定平台或啟用應用程式。  
  
 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會實作兩種 RNIF 版本： RNIF Specification v02.00.01 與 RNIF Specification v1.1。 RNIF 2.01 已新增支援 RNIF 1.1 中，包括加密、 附件和同步交易的重要功能。 RNIF 2.0 對 RNIF 1.1 不具有回溯相容性。  
  
## <a name="messaging-framework-patterns"></a>傳訊架構模式  
 下表顯示 RNIF 支援的訊息傳送架構模式及同步訊息交換。 單向動作訊息是指不會涉及回應的訊息，而雙向動作訊息則會包括要求和回應。  
  
|架構|模式|同步 /<br />非同步的|  
|---------------|-------------|---------------------------------|  
|RNIF 1.1|通知|非同步|  
|RNIF 1.1|Transaction|非同步|  
|RNIF 2.0|雙向動作|同步|  
|RNIF 2.0|雙向動作|非同步|  
|RNIF 2.0|單向動作|同步|  
|RNIF 2.0|單向動作|非同步|  
  
## <a name="message-definitions"></a>訊息定義  
 RNIF 1.1 與 RNIF 2.01 對 RosettaNet 訊息的定義並不相同。 這些差異包括兩者對於附件、安全多用途網際網路郵件延伸 (Secure/Multipurpose Internet Mail Extensions，SMIME) 信封、傳遞標頭以及 MIME 封裝方法的處理方式。 RNIF 2.01 特別加入了附件，因為 RNIF 2.01 新增了傳遞標頭，而 RNIF 1.1 沒有。  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不支援*Technical Recommendations for RNIF 1.1*發佈的 RosettaNet 組織 （一個是附件支援，一個是同步回應）。  
  
 系統使用部分的 RNIF 1.1 與 RNIF 2.01 訊息，做為合作對象識別、傳送及服務層級識別目的。 在讀取及回覆服務內容本文 (即訊息的主要內容) 之前，每一個合作對象必須成功地填入或解譯標頭值。  
  
 下圖描述 RNIF 1.1 與 RNIF 2.01 訊息定義。  
  
 ![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-rnif-message-definitions.gif "RN3_RNIF_Message_Definitions")  
  
 在 RNIF 1.1 訊息中，版本號碼代表 RNIF 版本。 內容長度等於 RosettaNet 服務訊息 (Service Message) 的長度。 「服務訊息」包含了前序、服務標頭以及服務內容，是 multipart/related 的 MIME 實體。 簽章長度等於簽章的長度 (以位元組為單位)。 如果有簽章，即為服務訊息欄位上的「公開金鑰加密標準」(Public-Key Cryptography Standards，PKCS) #7 簽章。  
  
 RNIF 2.01 包括獨立於傳輸通訊協定的容器，將系統要在封裝中交換的商務承載、標頭元件及其他元素包裝在一起。 RosettaNet 商務訊息 (如 RNIF 2.01 的定義) 包含前序、傳遞標頭、服務標頭及服務內容。 系統必須根據 RosettaNet 標準文件類型定義 (DTD) 文法驗證規則，對文件類型的結構描述驗證所有元素。 服務內容可以是動作訊息或信號訊息。 如果服務內容是動作訊息，則訊息可以包含一或多個附件。  
  
 RosettaNet 商務訊息是 multipart/related 的 MIME 實體。 如上圖所示，標頭及服務內容會以 MIME multipart/related 建構封裝在一起，這與 RNIF 1.1 封裝結構描述類似。 系統可以選擇數位簽署 RosettaNet 商務訊息。 在 RNIF 1.1 中，您可以使用 RosettaNet 物件 (RNO) 格式達到相同目的。 RNIF 2.0 捨棄了 RNO 格式，改用標準 S/MIME 編碼。  
  
 系統可以加密 RNIF 2.01 承載或承載容器。 為了達成上述目的，您必須將要加密的部分組合在一個 multipart/related MIME 實體，再進行加密。 接著，封裝產生的 S/MIME 物件，做為 RosettaNet 商務訊息中的一部分。  
  
 信號訊息必須永遠是 RosettaNet 定義的信號訊息執行個體。 對於動作訊息，RNIF 2.01 規格提供了以協力廠商定義的格式送出商務動作訊息的選項。 RNIF 2.01 服務標頭為此目的包含了額外的欄位，例如識別「標準內文」的欄位，以及識別動作訊息遵守之規格版本的欄位。  
  
 只有動作訊息 (亦稱為商務內容) 可以是非 RosettaNet 來源。 系統必須以 RosettaNet 定義的 PIP 交換這些訊息。 RosettaNet 必須明確識別 PIP 規格中已認可的協力廠商動作訊息，藉以認可這些訊息。 此外，交易夥伴必須同意其交易夥伴協議才能交換協力廠商的商務內容。 協議中必須包含 PIP 承載繫結資訊，該資訊識別您可以使用哪個協力廠商商務內容取代 PIP 中的特定動作訊息。  
  
## <a name="see-also"></a>另請參閱  
 [RosettaNet 與 CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)