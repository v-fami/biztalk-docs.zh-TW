---
title: 有些設計商務程序管理解決方案中的原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business processes, design principals
- designing, design principals
- process management solution tutorial, dividing business processes
- patterns [process management solutions], design principals
ms.assetid: 688b970f-8e64-4a47-bcc5-bdb9c5195902
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b975f94853c155da41f09b2b0ff76a681c1df075
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279358"
---
# <a name="some-design-principles-in-the-business-process-management-solution"></a>商務程序管理解決方案中的部分設計原則
本主題開頭分割商務程序為階段有關的一般指導方針。 接著考量與這些指導方針和商務需求相關的部分解決方案之協調流程、組件以及應用程式的結構。 如需商務需求的詳細資訊，請參閱 < 商務需求 > 中[了解商務程序管理解決方案](../core/understanding-the-business-process-management-solution.md)。  
  
## <a name="dividing-business-processes"></a>分割商務程序  
 通常在考量商務程序時，最直接的想法是將它視為單一龐大的程序。 這並不一定是最佳設計。 對 Southridge Video 而言，訂單是一個長時間執行的商務程序，此程序可能需要一年時間來完成。 在此期間，商務程序本身可能會變更。 為了讓商務程序在不中斷處理中訂單的狀況下更新，Southridge Video 訂單處理將分割為階段。  
  
 分割程序的位置對於可訂定版本的部分和您允許未完成訂單中斷的類型而言很重要。 Southridge Video 解決方案使用四個一般準則來判斷階段：  
  
-   商務程序中步驟的邏輯群組。  
  
-   協調流程內的作業範圍。  
  
-   項目，很有幫助的版本，提供商務程序的程序。  
  
-   協調流程應該在完成長期作業之後結束。  
  
 在四個準則中，第一和第三個最重要，因為通常其作業範圍遠大於邏輯群組或要訂定版本的明顯項目之作業範圍。 不過，請注意，不要在範圍的中間結束協調流程。  
  
 如果您看一下協調流程的第一個階段中，以**CableOrder1.odx**，您會看到它，有效地結束與要求-回應順序以設備系統。 這是結束階段的好位置，因為它是涉及完成訂單實際實體工作的程序之一部分。 讓長時間處理步驟接近協調流程結尾可保證當解除凍結時，協調流程可快速結束。 如此可加速整個解決方案移動至協調流程的較新版本。  
  
> [!NOTE]
>  雖然解決方案將程序分割成不連續的階段，不過，解決方案監控可讓您透過使用 BAM 以連續地檢視查看項目。  
  
## <a name="order-action-broker-and-manager-orchestrations"></a>訂單動作、仲介以及管理員協調流程  
 除了將訂單處理分成各個階段，您也會發現每個訂單動作 — 例如，分析訂單、 訂單驗證、 訂單取消 — 個別的協調流程中。 將每個動作放在個別的協調流程中，可將動作從階段的結構分離。 如此可以使訂單處理階段的設計和訂定版本更有彈性。  
  
 基於相似的原因，訂單仲介和訂單管理員也在個別的協調流程中。 解決方案設計可使用多個訂單管理員來處理其他種類的訂單。 將仲介和管理員分離也可允許這些項目位在不同位置。 如需訂單仲介之設計工具的詳細資訊，請參閱 「 為什麼訂單仲介？ 」 在[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。 如需訂單管理員的詳細資訊，請參閱[程序管理員邏輯](../core/process-manager-logic.md)。  
  
## <a name="assemblies"></a>組件  
 解決方案中的組件是有組織的，可支援元件的訂定版本，並支援移動元件到其他伺服器。 例如，結構描述便在個別組件中。 尤其，訂單仲介的結構描述就在自己的組件中。 如此，可讓它們不需變更解決方案的其他項目即可訂定版本。 也可以更簡單地移動訂單仲介到個別群組或伺服器。 如需版本控制應用程式和結構描述組件的詳細資訊，請參閱[版本設定商務程序管理解決方案](../core/versioning-the-business-process-management-solution.md)。  
  
## <a name="applications"></a>應用程式  
 若您查看「BizTalk 管理主控台」，會看到由三個個別應用程式組成的建置方案：  
  
-   **BTSScn.BPM.OrderBrokerApp**包含訂單仲介的應用程式  
  
-   **BTSScn.BPM.CableOrderApp**包含訂單處理元件的應用程式  
  
-   **BTSScn.BPM.MessagingApp**，收集其他兩個應用程式所共用的成品的應用程式  
  
 由於 BizTalk 應用程式具有使用相同 BizTalk 群組中其他應用程式之成品的能力，所以解決方案的三部分結構是可能的。 若要使用另一個應用程式的成品，請您從參考的應用程式新增參考至其他應用程式。 如需參考其他應用程式資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
 將一般成品放在個別應用程式中，讓您有可能僅在一個地方更新元件。 共用元件可以是任何項目，包括連接埠。 例如，解決方案中的協調流程傳送錯誤至錯誤報告連接埠。 該連接埠位在傳訊應用程式 BTSScn.BPM.MessagingApp 中，整個解決方案可在其中使用它。  
  
 將解決方案結構化為三個應用程式，也可讓您更輕鬆地移動解決方案的部分到其他伺服器上。 您可以將每個應用程式及其參考的應用程式轉換為 MSI 檔案。 然後您可以在另一台電腦上安裝該 MSI 檔案。 如需將應用程式轉換為 MSI 檔案資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
### <a name="the-test-solution"></a>測試解決方案  
 您將會在 BizTalk 管理主控台中也有三個測試應用程式： **BTSScn.BPM.OrderBrokerApp.Test**， **BTSScn.BPM.CableOrderApp.Test**，和**BTSScn.BPM.MessagingApp.Test**。 這三個應用程式僅包含測試應用程式的連接埠，而且由主要應用程式參考。 此結構允許主要應用程式使用測試連接埠來建構測試解決方案，而同時從解決方案分離測試連接埠。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md)