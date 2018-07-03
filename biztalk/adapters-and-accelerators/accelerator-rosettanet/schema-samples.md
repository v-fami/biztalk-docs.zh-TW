---
title: 結構描述範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SDK samples, schemas
- examples, schemas
- schemas, examples
ms.assetid: 7d7e696d-935f-4582-b873-c5637673b651
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2d5397319bcf7472a0999adcfc64fd7519d10c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008407"
---
# <a name="schema-samples"></a>結構描述範例
The Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 包含一系列 RNIF 和夥伴介面程序 (PIP) 處理的 XSD 結構描述。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 您可以使用這些結構描述處理訊息。 您可以依照自己的目的修改這些結構描述，或是用來疑難排解失敗。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 提供三組結構描述。 這些結構描述與 RosettaNet PIP、RosettaNet 下一代結構描述及 RNIF 結構描述關聯。  
  
## <a name="xsd-schemas-associated-with-rosettanet-pips"></a>與 RosettaNet PIP 關聯的 XSD 結構描述  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用這些結構描述，驗證訊息執行個體的服務內容。 您可以修改這些結構描述，以變更訊息處理。 在疑難排解處理服務內容中的錯誤時，您也可以使用結構描述驗證訊息執行個體。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 已經將這些結構描述編譯至 RNPIP 組件。 您可以解除部署 RNPIP 組件，再變更結構描述，然後重新部署 RNPIP，藉以修改任何其中一個結構描述。 但是您必須小心，不要變更結構描述。 如果變更結構描述，您所做的變更可能不符合對應的 RosettaNet PIP。 您也可以在 RNPIP 中新增結構描述。 如需詳細資訊，請參閱 <<c0> [ 修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝在這些結構描述\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Schemas。  
  
## <a name="rnif-schemas"></a>RNIF 結構描述  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用這些結構描述驗證 RNIF 訊息部分，例如前序、服務標頭和傳遞標頭， 其中也包括用於通知和例外狀況的結構描述。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝在這些結構描述\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\RNIFSchemas。  
  
## <a name="rosettanet-next-generation-schemas"></a>RosettaNet 下一代結構描述  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用這些結構描述，驗證符合 RosettaNet 下一代結構描述的訊息。 這些結構描述本身支援 XSD，而非 DTD。 若要使用這些結構描述，將它們加入 Rnpip 組件中所述[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝在這些結構描述\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK\Schemas\Domain、 \Interchange 和 \Universal 資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [PIP 實作](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)   
 [使用 Pip](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [範例](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)