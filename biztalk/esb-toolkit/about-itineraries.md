---
title: 關於旅 |Microsoft 文件
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
ms.openlocfilehash: 66a9a759a6afdd55c3c1646d02c480aa193261aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290606"
---
# <a name="about-itineraries"></a>有關行程
路線是表示，執行一連串的處理指示為基礎的 ESB 中繼原則[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]可擴充的格式。 行程都可視為說明宣告式路線服務的組態與中繼元件相關聯的一系列的高層級的中繼語言[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎。 您可以設計中繼流程，以描述訊息應該如何處理，以及您可以將組織為視覺繪圖的整個流程。 在執行階段，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎會執行路線設計工具所產生的路線。  
  
## <a name="the-itinerary-designer-surface"></a>在路線設計工具介面  
 在路線設計工具介面是用來建立的視覺化設計工具[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]行程並為執行時期格式匯出這些行程。 圖 1 所示，它是的畫布，您可以從 [工具箱] 拖曳項目。  
  
 ![路線設計工具](../esb-toolkit/media/ch5-itinerarydesigner.gif "Ch5 ItineraryDesigner")  
  
 **圖 1**  
  
 **路線設計工具介面**  
  
 路線的名稱會顯示在路線設計工具和 Microsoft Visual Studio 標題列中的最上層索引標籤上。 在設計介面本身是單一區域，並包含描述路線的實際訊息流程的模型項目。 ItineraryDSL 可讓您修改模型項目屬性，使用 Visual Studio 屬性 視窗。  
  
## <a name="itinerary-designer-toolbox"></a>路線設計工具的工具箱  
 Visual Studio [工具箱] 包含索引標籤，其代表的工具集。 當您開啟使用路線設計工具的 Visual Studio 專案時，工具箱 包含兩個索引標籤：**一般** 索引標籤和**ItineraryDsl**索引標籤。 **ItineraryDsl**  索引標籤包含下列工具：  
  
-   **路線服務工具**。 這個模型項目對應至路線中繼服務，並且表示處理指示。  
  
-   **連接器工具**。 這個模型項目定義在路線設計工具介面上的個別模型項目之間的關聯性。  
  
-   **匝道工具**。 這個模型項目會對應至匝道傳送訊息。 路線設計工具可讓多個關閉-坡道提升每個模型。  
  
-   **上手工具**。 這個模型項目會對應至上手接收訊息。 路線設計工具可讓您只有一個上手每個模型。  
  
-   **路線 Broker 服務工具**。 這個模型項目對應至路線中繼服務，可讓具有多個輸入和多個輸出的已定義的訊息流程。  
  
-   **路線 Broker 輸出連接埠**。 這個模型項目對應至單一輸出連接埠的行程 Broker 服務。 行程 Broker 服務的模型項目可讓多個輸出連接埠。  
  
## <a name="steps-in-itinerary-development"></a>路線開發的步驟  
 若要開發的路線，代表 ESB 中繼流程，您通常應該執行下列動作：  
  
-   加入模型項目來代表訊息處理步驟，為您的路線。 路線設計工具提供 [工具箱] 包含用來表示不同的動作或索引鍵的抽象圖案。  
  
-   指定路線模型屬性，其中包括 Microsoft BizTalk Server 管理資料庫和模型匯出工具設定的連接字串。  
  
-   上手和匝道模型項目繫結實體的 BizTalk 接收位置和傳送埠將這些模型項目與對應的技術擴充項產生關聯。  
  
-   關聯 extender 路線服務的模型項目，以及定義所需的擴充項的技術專屬屬性。 這些屬性而異的特定類型的擴充性;其可代表路線中繼服務屬性和相關聯的執行階段元件和成品的 BizTalk 特定屬性。  
  
-   識別要參考為路線中繼服務自訂元件。 例如，您可能會開發為路線服務的協調流程。  
  
-   請確認針對解析程式模型項目設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]叫用從設計工具介面的解析程式服務的執行階段組態。  
  
-   驗證並匯出路線使用匯出工具的執行階段原則。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]與路線設計工具提供兩個匯出工具： 檔案匯出工具和資料庫匯出工具。 或者，您可以實作自訂匯出工具。  
  
-   測試使用測試用戶端應用程式或 BizUnit framework 您路線。  
  
## <a name="security-considerations-for-developing-itineraries"></a>開發行程的安全性考量  
 當您設計旅時，您應該考慮潛在的安全性問題：  
  
-   應避免指定使用者認證，而不使用模型內容中的憑證。  
  
-   並未參考 BizTalk 接收埠與接收 允許匿名存取的位置。  
  
-   如果路線訊息包含敏感性資料，請保護訊息或傳輸通道。  
  
-   如果訊息包含需要保護傳輸中的敏感性資料來保護訊息的訊息方塊具有管線元件中。