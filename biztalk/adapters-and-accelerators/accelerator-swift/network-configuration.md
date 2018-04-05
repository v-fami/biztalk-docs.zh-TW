---
title: 網路設定 |Microsoft 文件
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
ms.openlocfilehash: 83a9e8ffe6b278c91429835c3ae32c96d45ef22e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="network-configuration"></a>網路組態
本章節提供您的部署中設定網路的指引。 如需詳細資訊，請參閱[準備部署](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md)。  
  
 您定義在交換器的虛擬區域網路 (Vlan)，並連接適當的纜線，然後。 藉由定義 Vlan，您會指定針對每個網路區段或層交換器連接埠。 您必須在下列環境的每個建立 VLAN:  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收和傳送層  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程和資料庫層  
  
-   公司網路  
  
 定義虛擬區域網路之後，您可以從伺服器連接的網路纜線到交換器上的適當連接埠。  
  
 此部分包含：  
  
-   [實體的圖表](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  
  
-   [網路負載平衡](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)