---
title: 教學課程 1： 企業應用程式整合 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial
- getting started tutorials, integrating enterprise applications
- enterprise application integration tutorial, about the tutorial
ms.assetid: aca5fc97-0fd6-4964-9cf1-482aa4f444b8
caps.latest.revision: 37
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb6ddbd6c2a3e25619c684036eee3fb0fa46a18f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287510"
---
# <a name="tutorial-1-enterprise-application-integration"></a>教學課程 1：企業應用程式整合
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供應用程式整合及商務程序管理 (BPM) 的開發與執行階段環境。 此教學課程提供您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定和部署企業應用程式整合 (EAI) 解決方案的端對端練習。  
  
##  <a name="BKMK_Tut1_scenario"></a>商務案例  
 Contoso 是一間銷售電腦軟硬體的線上商店。  這家公司最近購買一套企業資源規劃 (ERP) 系統來管理資源。  在此教學課程中，您將使用 BizTalk Server 開發企業應用程式整合 (EAI) 解決方案，將現有的倉儲系統整合到 ERP 系統中，並自動化倉儲要求程序。  
  
 此整合解決方案有一些挑戰：  
  
-   **訊息傳輸**。  倉儲系統和 ERP 系統可以位於兩個不同的平台上，並使用不同的傳輸通訊協定來傳送和接收訊息。 此解決方案必須能夠使用傳送端系統所支援的通訊協定來接收訊息，並使用接收端系統所支援的通訊協定來轉寄訊息。  BizTalk Server 會使用*配接器*的傳輸訊息。  BizTalk Server 安裝和 BizTalk Adapter Pack 隨附許多原生配接器。  如需其他配接器，您可以向廠商購買或使用 BizTalk Server 提供的配接器架構來開發自己的配接器。 如需配接器的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=191131](http://go.microsoft.com/fwlink/?LinkId=191131)。  
  
-   **訊息轉換**。 訊息有許多類型，例如可延伸標記語言 (XML)、電子資料交換 (EDI)、字元分隔檔等等。 BizTalk Server 以 XML 為主。 在大部分情況下，您可以先將輸入訊息轉換為 XML。  此程序稱為*剖析*。  到了輸出端，您可以再將 XML 訊息轉換為其他類型。  此程序稱為*序列化*。  
  
-   **商務程序管理**。 大部分的 EAI 實例並不是只有將訊息從一個系統轉寄至另一個系統這麼簡單。  通常涉及更多的系統和更複雜的工作流程。  在此實例中，倉儲會傳送訊息來要求補貨；您的解決方案會收到訊息，然後檢查要求的總計。  如果總計超過一定數量，解決方案就自動拒絕要求，並傳送拒絕訊息；否則，解決方案會將要求轉寄至 ERP 系統。  
  
     下圖說明此商務程序：  
  
     ![教學課程 1 訊息流程](../core/media/tut1-msg-flow.gif "tut1_msg_flow")  
  
 在此教學課程中，您會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具來設計和部署商務程序。  
  
## <a name="preparation"></a>準備  
 沒有建立 BizTalk Server 的整合方案之前，您必須收集一些基本資訊：  
  
-   BizTalk Server 解決方案需要整合多少應用程式/系統？  在本案例中，有兩個系統：ERP 和倉儲。  
  
-   每一個應用程式都支援哪些傳輸通訊協定？  為了簡化解決方案，我們假設這兩個應用程式都使用檔案。  倉儲系統會將要求以檔案的形式放入檔案資料夾中。 BizTalk Server 解決方案從資料夾挑出檔案、處理檔案，然後將要求放入 ERP 系統所監視的另一個資料夾。  
  
-   應用程式使用何種訊息類型？  為了簡化解決方案，我們假設兩個應用程式都使用 XML 類型。 BizTalk 結構描述是指用於定義 BizTalk 訊息中之 XML 資料結構的文件，目的是建立範本來處理和驗證 XML 訊息。 BizTalk Server 隨附可用於建立 BizTalk 結構描述的 [BizTalk 編輯器]。  
  
-   商務程序為何？  本文稍早已解釋過這個程序。  
  
## <a name="biztalk-server-architecture"></a>BizTalk Server 架構  
 瞭解 BizTalk Server 執行此解決方案的方式會很有幫助。  下圖顯示資料流經 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的情形。  
  
 ![教學課程 1 實例資料流程](../core/media/tut1-dataflow.gif "Tut1_Dataflow")  
  
-   (倉儲系統將要求放入檔案資料夾中。)  
  
-   BizTalk Server 接收位置設為使用 File 配接器和 XML 傳輸管線。  File 配接器定期從檔案資料夾中輪詢檔案。 收到訊息後，BizTalk Server 傳輸引擎將訊息推入管線中。  因為要求訊息是 XML 格式，所以此實例中使用 XML 傳輸管線。  XML 傳輸管線確定訊息是格式正確的 XML 檔案。  然後，將訊息儲存到 MessageBox 資料庫。  
  
-   協調流程引擎會在發現有訊息等待協調流程處理時，產生協調流程的執行個體。  根據訊息的總計而定，協調流程引擎將要求訊息或要求拒絕訊息儲存至 MessageBox 資料庫。  
  
-   同樣地，根據要求訊息或要求拒絕訊息而定，傳訊引擎使用其中一個傳送埠來處理訊息。  傳訊引擎先將訊息推入 XML 傳輸管線中，接著根據傳送埠組態而定，使用 FILE 配接器將訊息傳送至不同的檔案資料夾。  
  
-   (倉儲系統和 ERP 系統監視指定的資料夾來取得訊息。)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [開始本教學課程之前](../core/before-you-begin-the-tutorial.md) 
  
-   [第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md) 
  
-   [第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)  
  
-   [第 3 課： 部署方案](../core/lesson-3-deploy-the-solution.md)