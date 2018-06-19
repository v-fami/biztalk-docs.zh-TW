---
title: CIDX 訊息標準 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, RosettaNet
- RosettaNet, CIDX
ms.assetid: 6f70fa56-1fc3-4016-ac9e-6af18026292a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d37cd02f92a8a13857071d0b3d84ab40c480787
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207254"
---
# <a name="cidx-messaging-standards"></a>CIDX 訊息標準
CIDX (Chemical Industry Data Exchange，化學產業資料交換) 為一標準組織，支援及維護 Chem eStandards 標準化訊息交換。 化學工業公司使用這些標準，因應其業界特有的訊息傳送需求。  
  
 CIDX 在訊息傳送層已採用 RosettaNet 實作架構 (RNIF)，以便進行 XML 文件的交換。 CIDX 尚未採用 RNIF 標準的公開程序層。  
  
 Chem eStandards 定義了 XML 文件類型定義 (DTD)，描述了系統交換的訊息服務內容。 訊息在結構上與 RNIF 1.1 RosettaNet 物件相同，差別在於服務內容及部分標頭值。 當 CIDX 標準與 RosettaNet 訊息相符時，CIDX 標準會採用 RosettaNet 項目名稱及資料結構。  
  
 CIDX 之前都是使用電子文件交換 (EDI) 格式來交換訊息，但如今已形成一組以 XML 技術為主的新文件。 Chem eStandards 提供 EDI 訊息的 XML 複本。  
  
 Chem eStandards 為每個商務交易建立個別的訊息。 Chem eStandards 使用兩種類型的訊息回應： 技術回應與交易回應。 為了達到安全且可靠的訊息傳送，Chem eStandards 只會使用 RNIF 1.1 的通知 (Notification) 類型程序， 而不會使用交易夥伴介面程序 (PIP) 0A1。  
  
## <a name="cidx-and-rosettanet-differences"></a>CIDX 與 RosettaNet 之間的差異  
 下表顯示 RosettaNet 與 CIDX 之間的一些差異。  
  
|RosettaNet 實作|CIDX 實作|  
|-------------------------------|-------------------------|  
|RosettaNet 會將「Application/x-RosettaNet」當做「多用途網際網路郵件延伸標準」(Multipurpose Internet Mail Extensions，MIME) 類型使用。|CIDX 會將「Application/x-ChemXML」當做 MIME 類型使用。|  
|對於 RosettaNet 標頭，RosettaNet 會使用 GlobalAdministeringAuthorityCode = RosettaNet|CIDX 會使用 GlobalAdministeringAuthorityCode = CIDX|  
|RosettaNet 支援單向動作和雙向動作訊息。|CIDX 僅支援單向動作訊息。|  
|RosettaNet 支援 PIP 0A1 (失敗通知)。|CIDX 不支援 PIP 0A1。|  
|RosettaNet 訊息可以是「交易」(Transaction) 或「通知」(Notification) 類型。|所有 CIDX 訊息都屬於「通知」類型。|  
|在 RosettaNet 中，必須從 PIP 規格衍生 PIP 組態設定。|在 CIDX 中，必須從 CIDX Chem eStandards 規格衍生 PIP 組態設定。|  
  
## <a name="see-also"></a>另請參閱  
 [RosettaNet 與 CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [RNIF 標準](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)   
 [RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)   
 [CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)