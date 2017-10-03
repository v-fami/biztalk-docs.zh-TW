---
title: "導入 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06a4a31a-eefe-4b1b-89ca-2cba2b6fa587
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 544522fd2761cf12702ce517116bfaac84830084
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="introducing-biztalk-server"></a>介紹的 BizTalk Server
沒有一個應用程式會像孤島， 是否我們喜歡，一起繫結系統變成範數。 尚未軟體的連接更單純的交換位元組。 當組織走向服務導向的世界，真正的目標，建立有效的商務程序的不同系統結合成一體 — 恢復得以實現。  
  
 Microsoft[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]支援此目標。 如同舊版的應用程式，最新版可連接各種不同的軟體，然後以圖形方式建立並修改使用該軟體的處理程序邏輯。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也可讓資訊工作者監視執行中處理序、 與企業合作夥伴互動並執行其他業務相關的工作。  
  
 索引鍵中的新功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是：  
  
-   提供部署、監控及管理應用程式方面更好的支援  
  
-   更為簡化的安裝  
  
-   加強的商務活動監控 (BAM) 功能  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也會使用其他 Microsoft 技術的最新版本。 例如，建置在.NET framework 3.5 版和開發人員工具所裝載的 Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]。 針對儲存體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以使用[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]，Microsoft 頭號資料庫產品的最新版本。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]也可以執行 64 位元 Windows 伺服器上，利用較大的記憶體和其他優點，此新一代硬體能提供。  
  
## <a name="what-is-biztalk-server"></a>什麼是 BizTalk Server？  
 將不同的系統結合到有效的商務程序中是一項具有挑戰性的任務。 因此，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含數種技術。 下圖說明此產品的主要元件。  
  
 ![BizTalk Server 元件概觀](../core/media/d167608e-7c51-4d52-b8fa-9d4149242934.gif "d167608e-7c51-4d52-b8fa-9d4149242934")  
  
 如圖所示，產品的核心是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎。 引擎有兩個主要部分：  
  
-   提供與不同系統溝通之能力的傳訊元件。 藉由依賴配接器來進行不同的通訊，引擎可以支援各種不同的通訊協定及資料格式，包含 Web 服務及其他等等。  
  
-   支援建立及執行圖形式定義程序，稱為協調流程。 協調流程建置在引擎的傳訊元件最上方，因此可實作驅動所有或部分商務程序的邏輯。  
  
 其他數個 BizTalk 元件可以也用於搭配使用引擎，包括：  
  
-   評估複合規則集的商務規則引擎。  
  
-   群組中樞，可讓開發人員和管理員監視及管理引擎和協調流程會執行。  
  
-   「企業單一登入」(SSO) 功能，提供對應 Windows 與非 Windows 系統間驗證資訊的能力。  
  
 在這項基礎之上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含商務活動監控 」，資訊工作者可用來監視執行中的商務處理。 資訊會以商務而非技術的形式來顯示，且商務使用者可判定所顯示的資訊為何。  
  
## <a name="biztalk-server-and-the-challenge-of-connecting-diverse-systems"></a>BizTalk Server 及連線不同系統的挑戰  
 目前大多數的商務程序至少有一部分都要仰賴軟體。 有些程序由單一應用程式支援，有些則依賴數個不同的軟體系統。 在許多情況中，這個軟體是已經在不同時間、使用不同技術、在不同平台上建立。 自動化這些商務程序需要連接不同的系統。  
  
 解決這項挑戰會透過各種名稱： 商務程序自動化 (BPA)、 商務程序管理 (BPM) 等等。 不管名稱為何，在應用程式整合上有兩個最重要的案例。 一個是連接單一組織內的應用程式，一般是指企業應用程式整合 (EAI)。 另一個是連接不同組織內的應用程式，稱為企業對企業 (B2B) 整合。  
  
 下圖顯示套用到 EAI 問題之核心 BizTalk Server 引擎的簡單範例。 在此案例中，庫存應用程式，也許在 IBM 大型主機上執行，注意到某一項目的庫存不足，然後發出要求訂購更多該項目。 此要求會傳送到 BizTalk Server 協調流程 (步驟 1)，然後發出要求給組織的 ERP 應用程式以要求訂單 (步驟 2)。 ERP 應用程式可能在 Unix 系統上執行，且會傳回要求的 PO (步驟 3)，而 BizTalk Server 協調流程則會通知履行應用程式 (可能使用 .NET Framework 建置在 Windows 上) 應該訂購該項目 (步驟 4)。  
  
 ![BizTalk 引擎中實作的 EAI。] (../core/media/7d8558da-03cf-494b-8334-efe0ea15a6a7.gif "7d8558da-03cf-494b-8334-efe0ea15a6a7")  
  
 在此範例中，每一個應用程式都使用不同的通訊協定進行溝通。 因此，BizTalk Server 引擎的傳訊元件必須可以用原生通訊樣式與每一個應用程式溝通。 另外，注意不只單一應用程式知道完整的商務程序。 協調所有相關軟體所需的情報實作於 BizTalk Server 協調流程中。  
  
 連線組織內的應用程式十分重要，但是連線跨越數個組織的應用程式，有時會有更多商務價值。 下圖顯示此種企業對企業 (B2B) 整合的簡單範例。 在此案例中，在圖示上方的採購組織執行 BizTalk Server 協調流程，該協調流程會與兩個供應組織互動。 供應商 A 也使用 BizTalk Server，提供其「供應」應用程式的間接存取。 供應商 B 則使用其他廠商的整合平台，並使用 Web 服務連線到採購組織的 BizTalk Server 協調流程。  
  
 ![企業 &#45; 若要 &#45; 商務整合圖](../core/media/b1d8787d-e842-468e-96c5-b68875d9abc3.gif "b1d8787d-e842-468e-96c5-b68875d9abc3")  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Server](../core/understanding-biztalk-server.md)