---
title: RosettaNet 私用程序教學課程中，BizTalk Server 中的必要條件 |Microsoft Docs
description: 若要逐步執行 RosettaNet 加速器 (BTARN) 在 BizTalk Server 中的私用程序教學課程的必要條件
caps.latest.revision: 7
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
ms.author: mandia
ms.openlocfilehash: 823788385b659f5aa26d4aa92db1e234f2773600
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010927"
---
# <a name="prepare-for-the-private-process-tutorial"></a>準備私用程序教學課程

## <a name="prerequisites"></a>必要條件
再開始本教學課程：
  
- 執行 BizTalk Server 的完整安裝和[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]兩部電腦上。 如需詳細資訊，請參閱 <<c0> [ 安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。  
  
  > [!IMPORTANT]
  >  請務必完全設定 RosettaNet 加速器，其中包括啟動 BTARN 協調流程。 請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。 您也可以在新增[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]虛擬目錄 （包含 btarnhttpreceive） 至 Microsoft Windows® SharePoint™ Services 受管理的路徑排除清單。 
  
- 本教學課程會使用兩台電腦模擬真實世界的實例，而不是搭配回送協議使用一台電腦。 每當本教學課程提到電腦名稱時，都會使用預留位置做為電腦名稱。 該預留位置取代為您選擇的實際電腦名稱。 例如，如果電腦執行您 Contoso 解決方案會命名為**Contoso**，在教學課程中的任何取代\\ \\< contoso<strong>_</strong> *電腦*\>具有該電腦名稱。  
  
  本教學課程會在 Contoso 和 Fabrikam 之間，透過使用憑證促成安全通訊。 您必須產生任何憑證，您需要，以及在個別的電腦上安裝它們。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [還原 Contoso 資料庫](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [產生並啟用憑證](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)