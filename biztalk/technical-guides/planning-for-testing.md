---
title: 規劃測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b386ee074538af7960ca39bfb50c25ac59df1dbb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010279"
---
# <a name="planning-for-testing"></a>規劃測試
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 測試可以分成幾個類別，包括單元測試、 功能性測試、 負載測試，及可用性測試。 本主題描述單位與負載測試，以及如何針對每個計劃。  
  
## <a name="planning-for-unit-testing"></a>單元測試計劃  
 單元測試是用來驗證該個別程式碼單位的程序依照設計運作。 單元測試可以視為 「 協助修正 」 測試： 軟體不會執行所需的功能，在不同情況下，可以在這些情況下會發生軟體處理錯誤？  
  
 單元測試通常在個別的元件上執行，因為相關聯的測試平台不需要實際的生產環境的處理能力。 基於這個理由，您應該考慮執行單元測試在虛擬伺服器環境中，這需要大幅較少的硬體資源。  
  
 單元測試的可能執行虛擬化環境中的另一個層面預備環境。 預備環境是單元測試實際部署 BizTalk 解決方案的程序。 若要充分利用可用的硬體資源，請考慮使用 Virtual Server 進行您的預備環境。  
  
 如需使用詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[使用虛擬伺服器期間發行管理程序](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ)。 可能是適用於單元測試 BizTalk 解決方案的工具的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。 如需執行單元測試的考量事項的檢查清單，請參閱[執行單元測試](../technical-guides/performing-unit-testing.md)。  
  
## <a name="planning-for-load-testing"></a>規劃負載測試  
 負載測試是測量的最大持續性效能和最大持續性追蹤的 BizTalk 解決方案的效能，然後再移除禁止解決方案的輸送量的瓶頸的程序。 如需有關負載測試，並移除從瓶頸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 < [BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(<http://go.microsoft.com/fwlink/?LinkID=150492>)。  
  
 可能是適用於負載測試 BizTalk 解決方案的工具的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。 如需負載測試的考量的檢查清單[執行載入和輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)。  
  
## <a name="plan-to-test-for-the-lifetime-of-the-solution"></a>規劃測試解決方案的存留期  
 雖然單元測試和負載測試是特別重要之方案的早期階段存留期的方案，以找出潛在的問題，可能會發生負載增加時，或為新功能或元件的一般測試計劃會加入至方案。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)   
 [檢查清單：測試作業整備](../technical-guides/checklist-testing-operational-readiness.md)