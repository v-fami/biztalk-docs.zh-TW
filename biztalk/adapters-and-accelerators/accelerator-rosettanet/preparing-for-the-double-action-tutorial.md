---
title: RosettaNet 雙向動作教學課程中，BizTalk Server 中的必要條件 |Microsoft Docs
description: 若要逐步執行 RosettaNet 加速器 (BTARN) 在 BizTalk Server 中的雙向動作教學課程的必要條件
ms.custom: ''
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48584cf7dfee0ca4812b41e56b4e8f7c0984e4fc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979007"
---
# <a name="prepare-for-the-double-action-tutorial"></a>準備雙向動作教學課程

## <a name="prerequisites"></a>必要條件
再開始本教學課程：
  
- 執行 BizTalk Server 的完整安裝和[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]兩部電腦上。 如需詳細資訊，請參閱 <<c0> [ 安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。  
  
  > [!IMPORTANT]
  >  請務必完全設定 RosettaNet 加速器，其中包括啟動 BTARN 協調流程。 請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。
  
- 本教學課程會使用兩台電腦模擬真實世界的實例，而不是搭配回送協議使用一台電腦。 每當本教學課程提到電腦名稱時，都會使用預留位置。 該預留位置取代為您選擇的實際電腦名稱。 例如，如果電腦執行您 Contoso 解決方案會命名為**Contoso**，在教學課程中的任何取代\\ \\< contoso<strong>_</strong> *電腦*\>具有該電腦名稱。  
  
- 本教學課程會在 Contoso 和 Fabrikam 之間，透過使用憑證促成安全通訊。 您必須產生任何憑證，您需要此項目，並在其各自的電腦上安裝它們。  
  
## <a name="next-steps"></a>後續的步驟 
  
-   [步驟 1：建立憑證授權單位](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [步驟 2：建立公開憑證與私用憑證](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [步驟 3：匯入公開憑證與私用憑證](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [步驟 4：在 IIS 中啟用安全通訊端層 (SSL)](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)