---
title: 訊息與執行個體追蹤規劃 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HAT, planning
- planning, HAT
ms.assetid: 69b0d30e-77df-4847-9a59-6dd806152b71
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506dcd8342b016b325544f63f95c76c87dcc0772
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263558"
---
# <a name="planning-for-message-and-instance-tracking"></a>訊息與執行個體追蹤規劃
您應該在規劃階段決定需要追蹤哪些資訊，如此在您部署專案之後便可設定追蹤選項，並限制追蹤資料量，僅取得您所需的資訊。  
  
 我們建議您不要追蹤所有訊息，因為每次觸及訊息時，BizTalk Server 訊息及伺服器執行個體追蹤可以讓另一份複本。 例如，您可以藉由僅追蹤特定連接埠以縮小範圍。 如此可協助您將系統的效能最大化，並保持資料庫的整齊。  
  
## <a name="see-also"></a>另請參閱  
 [管理與追蹤架構](../core/management-and-tracking-architecture.md)