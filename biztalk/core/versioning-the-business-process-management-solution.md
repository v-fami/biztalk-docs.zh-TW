---
title: "版本控制商務程序管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, process management solutions
- process management solution tutorial, modifying
- process management solution tutorial, versioning
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 501b2162-821f-44e1-87c0-8628cc5bd9c3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af8afd3666a35b827ff25b243c1bfb4c81262273
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="versioning-the-business-process-management-solution"></a>版本控制商務程序管理解決方案
商務程序管理解決方案的設計目的是讓您可在需要時取代階段。 此設計也提供更容易管理結構描述版本的方法。  
  
 如需將商務程序分成階段資訊，請參閱[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
> [!NOTE]
>  解決方案的項目會與訊息結構高度相依。 變更訊息結構需要大幅變更協調流程。  
  
 如需有關更新中已部署的方案和編寫指令碼的指導方針來處理更新的組件的一般指示，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。  
  
## <a name="adding-replacing-or-removing-stages"></a>新增、取代或移除階段  
 訂單處理階段協調流程包含兩種類型的程式碼： 實作商務程序和提供的基礎結構，讓它可以在方案中運作的程式碼的程式碼。 在這兩個階段協調流程**CableOrder1**和**CableOrder2**，商務程序程式碼會在 「 群組 」 圖形內標示為 「 商務處理 」。  
  
 最容易建立新階段的方法是複製其中一個階段，以您的程式碼取代「商務處理」群組中的程式碼，並使基礎結構程式碼保持不變。  
  
> [!NOTE]
>  **CableOrder2**協調流程有兩個 「 商務處理 」 群組，第二個 「 更新歷程記錄傳送 」 圖形周圍。 「傳送」圖形是有效傳送範圍的一部分。 (如需詳細資訊，請參閱 < 改善效能與巢狀範圍 」 中的[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。)由於「群組」圖形無法與範圍圖形的一部分重疊，因此會標示第二個群組，以指出它是商務程序程式碼的一部分。  
  
 您必須將新協調流程上的篩選條件運算式設定成它在順序中的號碼。 **OrderManager**假設階段號碼以 1 開始，並增加一個 （1、 2、 3 …） 的每個下列階段。 若要篩選第三個階段，您需要將篩選條件運算式設定如下：  
  
 `(Microsoft.Samples.BizTalk.SouthridgeVidoe.Schemas.Stage == 3)`  
  
 解決方案會使用 BAM API 來追蹤解決方案中的事件，包括訂單處理階段。 第一個階段會啟動 BAM 活動，最後一個階段會結束它。 若有例外狀況，解決方案中的處理常式會結束相關的 BAM 活動。 BAM 會將不連續的作業有效地重新組合成連續的檢視以進行監控。  
  
## <a name="changing-configuration"></a>變更組態  
 若您的變更會增加或減少階段數目，則必須變更儲存在「企業單一登入」(SSO) 密碼存放區中的組態資訊。  
  
 如果您尚未部署應用程式，您可以修改的組態設定**TotalStages** CreateSouthridgeVideoApplication.cmd 指令碼檔案中。 當指令碼於部署期間執行時，值將會變更。  
  
 若您已部署應用程式，則可以執行 SDK\Common\SsoApplicationConfig 資料夾中的命令列公用程式 BTSScnSSOApplicationConfig 以變更值。 若要將階段總數設定為 3，需要使用下列的命令列：  
  
 `BTSScnSSOApplicationConfig -set SouthRidgeVideo.CableOrder ConfigProperties TotalStages 3`  
  
 因為解決方案會快取組態值，所以您必須等到重新整理間隔過去，新值才會生效。  
  
## <a name="versioning-schemas"></a>管理結構描述版本  
 BizTalk 會從最新版本包含它的組件的結構描述。 這表示若您建立結構描述的新版本，則它會完全取代結構描述的所有先前版本。 這在交易期間很短時是可行的。 不過，在商務程序管理解決方案中的交易期間較長： 訂單可能需要一年才能完成。  
  
 為了同時使用某個結構描述的多個版本，解決方案中的每個結構描述會在其命名空間中包含版本號碼。 例如，Order 結構描述的命名空間如下所示：  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 因為命名空間會識別結構描述，而且版本號碼的包含使得命名空間在結構描述中是唯一，所以新結構描述將可與較舊的版本區別。 因此，可以不取代舊的結構描述，即可使用新的結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [開發商務程序管理解決方案](../core/developing-a-business-process-management-solution.md)