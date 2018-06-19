---
title: 設定 CIDX 解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, process configuration
- creating, CIDX solutions
- CIDX, connecting to Elemica network
- agreements, CIDX
- process configuration, CIDX
- CIDX, agreements
- PIPs, importing for CIDX
- CIDX, PIPs
- CIDX, creating solutions
- CIDX, importing PIPs
- PIPs, CIDX
ms.assetid: 7f1f159f-3b09-4efd-907b-9a75f7f3ecd1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab617efc701551f1d5bcbae2a292676cc4f33251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210910"
---
# <a name="setting-up-a-cidx-solution"></a>設定 CIDX 解決方案
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 支援 CIDX (化學產業資料交換) XML 訊息交換 (CIDX Chem eStandards 2.0 版和 3.0 版)。 本主題說明如何執行下列動作來設定 CIDX 解決方案：  
  
-   設定程序組態  
  
-   設定協議  
  
-   套用 PIP  
  
-   匯入以 XSD 為基礎的 PIP  
  
-   連線到 Elemica 網路  
  
## <a name="setting-up-a-cidx-process-configuration"></a>設定 CIDX 程序組態  
 若要設定 CIDX eStandards 訊息交換，您必須建立具有下列屬性的程序組態：  
  
-   **標準**屬性設定為處理序組態設定中的**CIDX**  
  
-   **單向動作**屬性設定為處理序組態設定中的 **，則為 True**  
  
-   **0A1 協議**屬性設定為交易夥伴協議中的**No 0A1**  
  
 如需詳細資訊，請參閱[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)。  
  
## <a name="creating-a-cidx-agreement"></a>建立 CIDX 協議  
 要設定 CIDX eStandards 訊息交換，您必須建立具有下列屬性的協議：  
  
-   **RNIF 版本**協議設定中設定為屬性**V01.10.00**  
  
-   **0A1 協議**協議設定中設定為屬性**No 0A1**  
  
 如需詳細資訊，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
## <a name="applying-a-pip-for-cidx"></a>對 CIDX 套用 PIP  
 若要將 PIP 套用至 CIDX 實作，將**標準**程序組態設定檔中的屬性**CIDX**。 當您完成之後，您將能夠輸入的值**訊息標準**，**標準版本**，和**承載繫結識別碼**。 您可以在 CIDX Chem eStandards 的規格中找到這些值。  
  
## <a name="importing-an-xsd-based-pip-for-cidx"></a>對 CIDX 匯入以 XSD 為基礎的 PIP  
 若要對 CIDX，匯入以 XSD 為基礎的 PIP，您必須從在 CIDX.org 下載 PIP 的 ZIP 檔案[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361)。 請依照下列所述匯入程序[匯入以 XSD 為基礎的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)。  
  
## <a name="connecting-to-the-elemica-network"></a>連線到 Elemica 網路  
 您可以使用 Elemica Connectivity Pack 中的專案檔，自訂 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 以連接到 Elemica。 您可以下載 Connectivity Pack 從[http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195)。 如需詳細資訊，請參閱 < 連接到 Elemica 網路利用 BizTalk Accelerator for RosettaNet 3.0 > 技術白皮書在 MSDN 上[http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539)。  
  
> [!NOTE]
>  《利用 BizTalk Accelerator for RosettaNet 3.0 連線至 Elemica 網路》白皮書 (英文) 中的資訊對 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 有效。  
  
## <a name="see-also"></a>另請參閱  
 [CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)   
 [CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)   
 [設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [匯入以 XSD 為基礎的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)