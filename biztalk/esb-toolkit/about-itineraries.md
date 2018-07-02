---
title: 關於路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d34632f-8652-49dd-97b7-2513aacc1bd7
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd41dcfc1c5b6a090d48411956b19986aa2d676
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001087"
---
# <a name="about-itineraries"></a>關於路線
路線是一種執行一連串的處理指示為基礎的 ESB 中繼原則[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]可擴充的格式。 路線可以視為一種高層級的中繼語言，描述一連串的宣告式路線服務的組態與中繼元件相關聯的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎。 您可以設計中繼流程，以描述訊息應該如何處理，以及您可以將組織的整個流程，為 visual 的繪圖。 在執行階段，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎執行路線設計工具所產生的路線。  
  
## <a name="the-itinerary-designer-surface"></a>在路線設計工具介面  
 在路線設計工具介面是用來建立視覺化設計工具[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線並為執行時期格式匯出這些路線。 圖 1 所示，它會為要您可以從 工具箱 拖曳項目的畫布。  
  
 ![路線設計工具](../esb-toolkit/media/ch5-itinerarydesigner.gif "Ch5 ItineraryDesigner")  
  
 **圖 1**  
  
 **路線設計工具介面**  
  
 路線的名稱會顯示在路線設計工具和 Microsoft Visual Studio 標題列中 [top] 索引標籤上。 設計介面本身是單一區域，並包含說明路線的實際的訊息流程的模型項目。 ItineraryDSL 可讓您修改模型項目屬性，使用 Visual Studio 屬性 視窗。  
  
## <a name="itinerary-designer-toolbox"></a>路線設計工具的工具箱  
 Visual Studio [工具箱] 包含索引標籤，其代表的工具集。 當您開啟使用路線設計工具的 Visual Studio 專案時，[工具箱] 包含兩個索引標籤：**一般**索引標籤和**ItineraryDsl**索引標籤。 **ItineraryDsl**  索引標籤包含下列工具：  
  
-   **路線服務工具**。 這個模型項目對應至路線中繼服務，並且表示處理指示。  
  
-   **連接器工具**。 這個模型項目會定義在路線設計工具介面上的個別模型項目之間的關聯性。  
  
-   **出口匝工具**。 這個模型項目會對應至出口匝會傳送訊息。 在路線設計工具可讓多個出口每個模型。  
  
-   **匝道工具**。 這個模型項目會對應至匝道接收訊息。 在路線設計工具可讓您只有一個匝道每個模型。  
  
-   **路線的 Broker 服務工具**。 這個模型項目會對應至路線中繼服務，可讓多個輸入和多個輸出的已定義的訊息流程。  
  
-   **路線的 Broker 輸出連接埠**。 這個模型項目對應至單一輸出連接埠的路線 Broker 服務。 路線 Broker 服務的模型項目可讓多個輸出連接埠。  
  
## <a name="steps-in-itinerary-development"></a>路線的開發中的步驟  
 若要開發路線，它代表 ESB 中繼流程，您通常應該執行下列動作：  
  
- 加入模型項目，來代表訊息處理步驟，為您的路線。 在路線設計工具提供 [工具箱] 包含用來代表不同的動作或關鍵抽象概念的圖形。  
  
- 指定路線的模型屬性，其中包括 Microsoft BizTalk Server 管理資料庫和模型工具匯出設定的連接字串。  
  
- 入口和出口匝模型項目繫結實體的 BizTalk 接收位置和傳送埠產生關聯，這些模型項目對應的技術擴充項。  
  
- 路線服務的模型項目相關聯的擴充項，以及定義擴充項所需的技術專屬屬性。 這些屬性可能會不同的特定類型的擴充性;它們可以代表路線的中繼服務屬性和執行階段元件與成品相關聯的 BizTalk 特定屬性。  
  
- 找出要作為路線中繼服務所參考的自訂元件。 例如，您可以開發協調流程作為路線服務。  
  
- 確認 解析程式模型項目設定，以免[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]叫用從設計工具介面的解析程式服務的執行階段組態。  
  
- 驗證並匯出路線使用匯出工具的執行階段原則。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]與路線設計工具提供兩個匯出工具： 檔案匯出工具和資料庫匯出工具。 或者，您可以實作自訂匯出工具。  
  
- 測試使用測試用戶端應用程式或 BizUnit framework 您路線。  
  
## <a name="security-considerations-for-developing-itineraries"></a>開發路線的安全性考量  
 當您設計路線時，您應該考慮的潛在安全性問題：  
  
-   避免指定使用者認證，而不使用模型屬性的憑證。  
  
-   未參考 BizTalk 接收埠與接收 允許匿名存取的位置。  
  
-   如果路線的訊息包含敏感性資料，請保護訊息或傳輸通道。  
  
-   如果訊息包含需要保護傳輸中的敏感性資料，請保護的訊息方塊具有管線元件中的訊息。