---
title: "BizTalk Server 2010 效能最佳化指南 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a56b27f-3e57-47db-a776-520f2d67d65e
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6a16d47f88be211b376f54d0f7116346771d136
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-server-2010-performance-optimization-guide"></a>BizTalk Server 2010 效能最佳化指南
歡迎使用 Microsoft® BizTalk® Server 2010 效能最佳化指南。 我們建立了本指南提供的最佳化 BizTalk Server 解決方案的效能的深入資訊。 企業應用程式部署期間經常忽略完整端對端效能測試。 了解 Microsoft 已建置可擴充的傳訊基礎結構，使用 BizTalk Server 的許多組織縮短對幾乎不執行效能測試的自己的應用程式的時間。 BizTalk Server 應用程式含有許多部分，其中可能包含自訂元件，以及 Microsoft 所提供。 Microsoft 在效能測試所有可能組合，這些元件，所以不可能。 因此，完整及正確執行程式的效能測試是應用的任何部署的重要步驟。  
  
 本指南的目的是要合併及提供最佳的作法和最佳化 BizTalk Server 效能，應遵循的技術的指引。  
  
 若要下載這份指南的 chm、 pdf 或 docx 表單中，移至[Microsoft BizTalk Server 2010 效能最佳化指南](http://go.microsoft.com/fwlink/?LinkId=210870)(http://go.microsoft.com/fwlink/?LinkId=210870)。  
  
## <a name="whats-in-it"></a>什麼是在它？  
 一般來說，伺服器的效能取決於有效能最低的元件，在系統中的瓶頸。 改善效能的關鍵能夠找出瓶頸，請判斷其原因，並套用適當的更正動作。  
  
 當您規劃 BizTalk Server 部署，請使用本指南說明設計及最佳化您的環境。 效能的概念與延展性的概念密切相關。 當您有充分的了解影響系統元件的效能的因素時，您可以部署的方式調整為支援週期需求較高的元件。  
  
 本指南提供指引來最佳化效能，根據實際操作經驗的 IT 專業人員已廣泛使用 BizTalk Server。 具體來說，本指南包含四個主要部分：  
  
-   **尋找並消除瓶頸**:[尋找並消除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)章節描述各種類型的效能瓶頸，BizTalk Server 方案和如何的相關資訊與相關解決瓶頸。  
  
-   **最佳化效能**:[最佳化效能](../technical-guides/optimizing-performance.md)> 一節提供最佳化的效能指引[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與效能的平台緊密相關效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。 本節提供這兩者的效能最佳化的建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]平台。  
  
-   **調整實際執行 BizTalk Server 環境**:[調整實際執行 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)章節提供詳細的 BizTalk Server 效能 BizTalk 產品團隊所完成的測試結果. 這些測試著重於延展性，且以新增 BizTalk Server 電腦，新增的影響的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫，並加入方案中的 BizTalk Server 電腦和 BizTalk Server MessageBox 資料庫的影響同時。  
  
    -   數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，這些測試群組只有一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫已設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試僅著重於新增的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
    -   數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試僅著重於新增的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
    -   兩者的數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試以測量新增這兩個加入的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
-   **BizTalk Server 效能測試方法**: [BizTalk 伺服器效能測試的方法](../technical-guides/biztalk-server-performance-testing-methodology.md)章節提供有關如何測試和最佳化的詳細的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。 它還包含有關將重點放在哪些效能準則，且應在評估時套用的基本階段[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。  
  
## <a name="additions-to-this-version-of-the-guide"></a>本指南的這個版本的新增項目  
 [使用 Visual Studio，有助於自動化測試](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)– 說明如何使用 Visual Studio 負載測試中，評估 BizTalk Server 應用程式的效能。  
  
## <a name="acknowledgments"></a>致謝  
 我們在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用者教育小組非常感謝認可未處理的下列人員比重的 BizTalk Server 效能最佳化指南提供技術意見以及大量內容：  
  
 **作者**  
  
-   Tim Wieman、 Microsoft  
  
-   Paolo Salvatori、 Microsoft  
  
-   Microsoft trace Young  
  
 **檢閱者**  
  
-   Tim Wieman、 Microsoft  
  
-   Paolo Salvatori、 Microsoft