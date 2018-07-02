---
title: 網路組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, network configuration
ms.assetid: fb6265b8-2e6d-4344-bb44-4f4fd995382d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fb693b9718b7c92e24f3537bea7ef27267f9a05
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967439"
---
# <a name="network-configuration"></a>網路組態
本節中的指引可用於在您的部署中設定網路。 如需詳細資訊，請參閱 <<c0> [ 準備部署](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md)。  

 您在參數中定義虛擬區域網路 (Vlan)，然後連接適當的纜線 藉由定義 Vlan，您會指定針對每個網路區段或層交換器連接埠。 您必須建立 VLAN 的每個下列環境：  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 接收和傳送層  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 協調流程和資料庫層  

- 公司網路  

  定義虛擬區域網路之後，您可以從伺服器連線的網路纜線到交換器上的適當連接埠。  

  此部分包含：  

- [實體圖表](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  

- [網路負載平衡](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)
