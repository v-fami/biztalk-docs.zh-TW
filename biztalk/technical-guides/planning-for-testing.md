---
title: "測試規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bdf5f35d5d612ec077ebdac83339c5a6838109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-testing"></a>測試規劃
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]測試可以分成數種類別，包括單元測試、 功能測試、 負載測試，以及可用性測試。 本主題描述單位和負載測試，以及如何針對每個計劃。  
  
## <a name="planning-for-unit-testing"></a>單元測試計劃  
 單元測試是用來驗證該程式碼個別單位的程序依照設計運作。 單元測試可以視為 「 中斷/修正 「 測試： 軟體不會執行所需的功能在不同情況下，可以在這些情況下會發生軟體處理錯誤？  
  
 因為個別的元件通常會執行單元測試，關聯的測試平台不需要實際執行環境的處理功能。 基於這個理由，您應該考慮執行單元測試中的虛擬伺服器環境，可大幅較少的硬體資源。  
  
 單元測試的虛擬化環境中執行的另一個層面暫存。 臨時區域是單元測試實際部署 BizTalk 解決方案的程序。 若要充分利用可用的硬體資源，請考慮使用 Virtual Server 的執行環境。  
  
 如需有關使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[使用虛擬伺服器期間發行管理程序](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ)。 工具可能適用於單元測試 BizTalk 解決方案的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。 如需執行單元測試的考量的檢查清單，請參閱[執行單元測試](../technical-guides/performing-unit-testing.md)。  
  
## <a name="planning-for-load-testing"></a>負載測試的計劃  
 負載測試是測量最大持續性效能和最大持續性追蹤的 BizTalk 解決方案的效能，然後再移除禁止解決方案的輸送量瓶頸的程序。 如需有關負載測試，且會移除從瓶頸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
 工具可用於負載測試 BizTalk 解決方案的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。 如需負載測試的考量的檢查清單，請參閱[執行載入及輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)。  
  
## <a name="plan-to-test-for-the-lifetime-of-the-solution"></a>測試計劃的存留期方案  
 而單元測試和負載測試是特別重要之方案的早期階段存留期中的方案以找出潛在的問題，可能會發生負載增加時，或是做為新功能或元件的一般測試計劃會加入至方案。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)   
 [檢查清單： 測試操作整備](../technical-guides/checklist-testing-operational-readiness.md)