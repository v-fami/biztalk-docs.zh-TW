---
title: CIDX 支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, procedures
- CIDX, about CIDX
- CIDX, Elemica Exchange Server Provider (ESP)
- CIDX, PIPs
- CIDX
- Elemica Exchange Server Provider (ESP)
- procedures [CIDX]
- PIPs, CIDX
ms.assetid: 58b75ad3-f6b9-47c0-8dbf-506a3eaf010b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224d2b50d132efa67e1cfc24dda2df77fa7d29e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210694"
---
# <a name="cidx-support"></a>CIDX 支援
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]支援 CIDX （化學產業資料交換） XML 訊息交換。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]支援 CIDX Chem eStandards 2.0 和 3.0，兩者都使用 RosettaNet 實作架構 (RNIF) 1.1 版。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 非同步簡單公開程序 (支援單向動作和雙向動作訊息) 會使用並傳送 CIDX 服務內容。  
  
 對於採用 CIDX PIP 的協議，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將驗證訊息中的下列資訊：  
  
-   僅 RNIF 1.1 版本  
  
-   無 0A1  
  
-   僅單向動作  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不會防止您設定`Standard`屬性程序組態為 「 CIDX 」 之後您已經設定,`0A1 agreement`會使用該設定檔為 （這不支援對 CIDX） 的 「 0A1 」 協議屬性。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不會執行可能阻止此欄位交互驗證。  
  
## <a name="applying-a-pip-to-a-cidx-implementation"></a>將 PIP 套用至 CIDX 實作  
 若要將 PIP 套用至 CIDX 實作，將`Standard`程序組態設定檔中的屬性**CIDX**。 當您完成之後，您將能夠輸入訊息標準、 標準的版本，與承載繫結識別碼。 您可以在 CIDX Chem eStandards 的規格中找到這些值。  
  
## <a name="connecting-to-the-elemica-network"></a>連線到 Elemica 網路  
 您可以啟用安裝[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]以連線到 Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] Provider (ESP)。 您可以使用 CIDX 訊息交換，透過 Elemica 網路買賣化學工業產品及管理供應鏈。  
  
 您可以使用 Elemica Connectivity Pack 中的專案檔，自訂 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 以連線到 Elemica。 您可以下載 Connectivity Pack 從[http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195)。 如需詳細資訊，請參閱 < 連接到 Elemica 網路利用 BizTalk Accelerator for RosettaNet 3.0 > 技術白皮書在 MSDN 上[http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539)。  
  
> [!NOTE]
>  《利用 BizTalk Accelerator for RosettaNet 3.0 連線至 Elemica 網路》白皮書 (英文) 中的資訊對 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 有效。  
  
## <a name="cidx-procedures"></a>CIDX 程序  
 下列章節說明如何設定 CIDX 訊息交換：  
  
-   [設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)  
  
-   [建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)  
  
-   [匯入以 XSD 為基礎的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)