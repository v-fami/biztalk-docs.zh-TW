---
title: BizTalk Server 2010 效能最佳化指南 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a56b27f-3e57-47db-a776-520f2d67d65e
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de3d6f1da478ae65d9bf7ed6862a0b13de36e288
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987047"
---
# <a name="biztalk-server-2010-performance-optimization-guide"></a>BizTalk Server 2010 效能最佳化指南
歡迎使用 Microsoft® BizTalk® Server 2010 效能最佳化指南。 我們建立了本指南，以提供 BizTalk Server 解決方案的效能最佳化的深入資訊。 企業應用程式部署期間，經常忽略完整端對端效能測試。 使用 BizTalk Server 的許多組織得知 Microsoft 已建置可調整的傳訊基礎結構中，花費少量或沒有時間進行效能測試自己的應用程式。 BizTalk Server 應用程式包含許多組件，其中可能包含自訂建置的元件，以及 Microsoft 所提供。 針對 Microsoft 效能測試每個可能的組合，這些元件，就不可能。 因此，完整而正確地執行您的應用程式的效能測試是任何部署的重要步驟。  

 本指南的目的是要合併及提供的最佳作法和技巧，將 BizTalk Server 效能最佳化時應該遵循的規範指引。  

 若要下載一份本指南中的 chm、 pdf 或 docx 表單，請前往[Microsoft BizTalk Server 2010 效能最佳化指南](http://go.microsoft.com/fwlink/?LinkId=210870)(http://go.microsoft.com/fwlink/?LinkId=210870)。  

## <a name="whats-in-it"></a>什麼是在它？  
 一般來說，伺服器的效能取決於效能最低的元件，在系統中的瓶頸。 若要改善效能的索引鍵能夠找出瓶頸，判斷其原因，並套用適當的更正動作。  

 當您規劃 BizTalk Server 部署，請使用本指南來協助設計及最佳化您的環境。 概念的效能與延展性的概念密切相關。 當您有充分的了解影響系統元件的效能因素時，您可以部署元件，以調整為支援的高需求的方式。  

 本指南提供最佳化效能，根據實際操作經驗的 IT 專業人員已廣泛使用 BizTalk Server 的指引。 具體來說，本指南包含四個主要部分：  

- **尋找並消除瓶頸**:[尋找並消除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)章節描述各種類型的效能瓶頸，在與 BizTalk Server 方案和如何資訊解決瓶頸。  

- **最佳化效能**:[最佳化效能](../technical-guides/optimizing-performance.md)一節提供最佳化的效能指引[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與效能的平台緊密相關效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。 本節提供最佳化的效能建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]而[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]平台。  

- **調整生產 BizTalk Server 環境**:[調整生產 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)章節提供的 BizTalk Server 效能測試完成 BizTalk 產品小組的詳細的結果. 這些測試著重於延展性，以及測量的加入 BizTalk Server 電腦，新增的影響影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫，並將 BizTalk Server 電腦和 BizTalk Server MessageBox 資料庫新增至解決方案的影響同時。  

  - 時增加的數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中，這些測試只有一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫設有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試著重於新增的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  

  - 時增加的數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試著重於新增的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  

  - 時增加兩者的數字[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦並[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試會測量新增這兩個新增的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦並[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  

- **BizTalk Server 效能測試方法**: [BizTalk Server 效能測試方法](../technical-guides/biztalk-server-performance-testing-methodology.md)一節提供如何測試和最佳化的詳細的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。 它包含資訊的效能準則，將重點放在和評量時應套用的基本階段[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。  

## <a name="additions-to-this-version-of-the-guide"></a>本指南的這個版本的新增項目  
 [使用 Visual Studio 促進自動化測試](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)– 說明如何使用 Visual Studio 負載測試，以評估 BizTalk Server 應用程式的效能。  

## <a name="acknowledgments"></a>致謝  
 我們在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]User Education 小組高度認可下列人員傑出貢獻的 BizTalk Server 效能最佳化指南提供技術的意見反應以及優惠的內容：  

 **作者**  

- Tim Wieman Microsoft  

- Paolo Salvatori、 Microsoft  

- Trace Young，Microsoft  

  **檢閱者**  

- Tim Wieman Microsoft  

- Paolo Salvatori、 Microsoft
