---
title: "加入新的交易夥伴介面程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, PIP schemas
- PIP schemas
- PIP schemas, deploying
- PIP schemas, downloading
- creating, PIP schemas
- PIP schemas, creating
ms.assetid: 6a5fcbcb-c6aa-40c0-bcca-dd0c391e7f42
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4874c623c80a008a4f2c1aa5382c49e37616b6af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="incorporating-a-new-partner-interface-process"></a>加入新的交易夥伴介面程序
您可以將新的 RosettaNet 夥伴介面程序 (PIP) 結構描述併入 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 組件中。 作法：  
  
-   從 RosettaNet 網站下載 PIP 結構描述[http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。  
  
-   將結構描述部署至 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 做為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIP 組件的一部分，或是不同 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組件的一部分。 如需詳細資訊，請參閱[擴充 BTARN 使用新的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)。  
  
-   在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中建立新的「程序組態設定」。 如需詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
 從 RosettaNet 組織下載的結構描述通常是 .dtd 格式，具有所附的 PIP 規格，可以當做 .doc 檔案使用。 擴充管線以使用新結構描述的程序包括將 PIP .dtd 檔轉換為 .xsd 檔。  
  
 安裝 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含一些 XSD 結構描述。 您可以找到那些結構描述中的\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\Schemas 資料夾。 BTARN 會將這些結構描述建置在 RNPIPs.dll 檔案中。 如果您要變更其中一個結構描述，則必須在同一個資料夾中開啟 RNPIP 專案，並在 BizTalk 編輯器中變更結構描述，然後重新編譯並重新部署組件。 重新部署 RNPIPs.dll 檔之後，您必須重新部署使用這個結構描述的管線。 您可以使用這個程序，在 BTARN 中整合新的結構描述，但是擴充管線以加入新結構描述的作法，會比較簡單。  
  
### <a name="to-obtain-the-pip-schema"></a>取得 PIP 結構描述  
  
-   在 Internet Explorer 中，前往 RosettaNet 網站，網址[http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。  
  
## <a name="see-also"></a>另請參閱  
 [使用新的 PIP 擴充 BTARN](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)