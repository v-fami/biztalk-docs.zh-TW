---
title: PIP 實作 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs
- PIPs, element-level constraints
- Document Type Definitions (DTDs)
- PIPs, schemas
- examples, schemas
- schemas, examples
- PIPs, about PIPs
- element-level constraints
- PIPs, DTDs
- schemas, PIPs
- XML Schema Definition files (XSDs)
- Partner Interface Processes (PIPs)
- DTDs, XSDs
- schemas, XSDs
ms.assetid: 0d964223-e0b6-4377-b26a-5fdc89ec81f4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba85938e2e0da2b8ee09de476c81acdf202b449c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982999"
---
# <a name="pip-implementation"></a>PIP 實作
RosettaNet Partner Interface Process (Pip) 會定義在供應鏈中的交易夥伴之間的商務程序。 Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]提供一組 Pip 的立即可用，您可以建立其他的 Pip。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 支援 RosettaNet 組織所定義的所有 Pip。  
  
 如需詳細資訊，請參閱 < [RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)。  
  
## <a name="schemas-in-btarn"></a>BTARN 中的結構描述  
 RosettaNet 以「文件類型定義」(DTD) 形式定義所有的 PIP 訊息結構描述。 在商務文件交換過程中參與的交易夥伴必須遵循這些 DTD。 不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]為 XML 結構描述定義檔案 (Xsd)，實作這些 Dtd，因為 Microsoft BizTalk Server 使用 Xsd 而非 Dtd 來代表文件。 就功能而言，XSD 會取代 DTD，並且可以自然呈現訊息指導方針所提供的大部分資訊。  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 也支援 RosettaNet 組織最近所發佈，使用 XSD 規格的下一代 PIP。  
  
 若要實作新的 PIP，您必須將 PIP 的 DTD 轉換為 XSD。 下載從 RosettaNet 網站，PIP 相關聯的 DTD [ http://go.microsoft.com/fwlink/?linkid=33859 ](http://go.microsoft.com/fwlink/?linkid=33859)。 然後，您可以根據 PIP 建立 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 程序組態設定檔。 如需詳細資訊，請參閱 <<c0> [ 併入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。  
  
 您可以根據現有的設定檔建立新的程序組態設定檔。 如需詳細資訊，請參閱 <<c0> [ 如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。 您可以在相同交易夥伴之間根據相同的程序組態設定檔建立多重協議。 然而，您一次只能啟動其中一個協議。 若要建立和啟動協議，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用下列 RosettaNet 標頭的 RosettaNet 訊息指導方針條件約束實作 XSD：  
  
-   RNIF 1.1 及 RNIF 2.01 的前序  
  
-   RNIF 1.1 及 RNIF 2.0 的服務標頭  
  
-   RNIF 2.0 的傳遞標頭  
  
-   RNIF 1.1 及 RNIF 2.01 所有信號訊息的服務內容。  
  
## <a name="sample-schemas"></a>範例結構描述  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式會安裝一組中的 Pip \<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\schemas。 這些僅當做範例使用。 實際運用在執行環境之前，我們強烈建議您將這些結構描述與最近發佈的 RosettaNet PIP 規格和訊息指導方針進行比較。 BTARN 支援所有 RosettaNet PIP 的實作。  
  
## <a name="element-level-constraints-in-btarn"></a>BTARN 中的元素階層條件約束  
 在 BTARN 中，您可以將 PIP 訊息指導方針文件中指定的元素階層條件約束實作為程序組態設定。 執行階段元件會使用程序組態決定處理特定 PIP 的方式。  
  
 若要實作新的 PIP，您必須建立新的程序組態設定檔，以套用 PIP 的訊息指導方針條件約束。 您可以在 BTARN 管理主控台中執行這個動作。 如需詳細資訊，請參閱 <<c0> [ 如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
 程序組態設定檔對應至 RosettaNet PIP 規格中所示[使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md)   
 [RosettaNet PIP](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)
