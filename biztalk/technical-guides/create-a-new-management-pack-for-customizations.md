---
title: 建立用於自訂的新管理組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ce1ffa0-57c7-41ce-b459-48c36522889e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3108696e89e6a411049c11929c8e7dcb7f48db34
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016795"
---
# <a name="create-a-new-management-pack-for-customizations"></a>建立用於自訂的新管理組件
大部分的廠商管理組件是密封格式，因此您無法變更任何管理組件檔案中的原始設定。 不過，您可以建立自訂，例如覆寫或新的監視物件，並將它們儲存至不同的管理組件。 根據預設，Operations Manager 2007 R2/2012年會將所有自訂都儲存至預設管理組件。 最佳做法，您應該改為建立您想要自訂每個密封的管理組件的不同管理組件。  
  
 建立新的管理組件以儲存覆寫有下列好處：  
  
- 簡化將測試環境和預先生產環境中所建立的自訂匯出至生產環境的程序。 比方說，而不要匯出包含來自多個管理組件的預設管理組件，您可以匯出只包含單一管理組件的自訂管理組件。  
  
- 您可以刪除原始管理組件，而不需要先刪除預設管理組件。 包含自訂的管理組件相依於原始管理組件。 此相依性需要先刪除含自訂的管理組件，才能刪除原始管理組件。 如果所有自訂都儲存至預設管理組件，您必須先刪除預設管理組件，才能刪除原始管理組件。  
  
- 更容易追蹤及更新個別管理組件的自訂。  
  
  如需詳細資訊有關密封與未密封管理組件，請參閱[管理組件格式](http://go.microsoft.com/fwlink/?LinkID=198193)(http://go.microsoft.com/fwlink/?LinkId=198193)。 如需有關管理組件自訂的詳細資訊，請參閱 <<c0> [ 自訂管理組件](http://go.microsoft.com/fwlink/?LinkID=198194)(http://go.microsoft.com/fwlink/?LinkID=198194)。