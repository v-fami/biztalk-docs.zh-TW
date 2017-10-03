---
title: "案例： 更新應用程式成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, artifacts
- updating, artifacts
- artifacts, examples
- updating, examples
- examples, updating
- artifacts, updating
ms.assetid: 76833df3-2330-48af-84d8-731028b192ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e95e6a66fb0e6bccc1fcc2fb4a7664538e50d3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-updating-application-artifacts"></a>案例： 更新應用程式成品
在應用程式部署至實際執行環境後，更新應用程式中的成品有兩種基本案例：  
  
-   當協調流程處理長時間執行的交易或正在等候請求-回應連接埠的回應時，以新版本更新協調流程。  
  
-   不用考慮完成訊息處理時，例如以新版本更新結構描述或對應，這是較一般的更新案例。  
  
 在一般更新案例中，您可以用新版本更新成品，例如處理商務需求的變更。 這個案例相當單純，您可以用更新版本來覆寫原始成品。 如需所需的步驟，請參閱[檢查清單： 更新 BizTalk 應用程式中的成品](../core/checklist-update-the-artifacts-in-a-biztalk-application.md)。  
  
 另一個案例較為複雜。 在這個案例中，您必須讓現有協調流程完成訊息的處理。 同時，您必須防止現有協調流程處理任何新訊息。 相反地，您要協調流程更新版本來接管。 若要完成這項作業，您要將包含更新協調流程的組件部署到與原始版本相同的 BizTalk 應用程式中，然後同時執行兩個協調流程 (新組件的版本號碼必須與包含原始協調流程的組件不同，否則將無法部署到相同的 BizTalk 群組)。然後再停止原始的協調流程，不使新訊息路由傳送給它，並啟動更新版本，使所有新訊息都傳送給它。 在原始的版本完成所有其訊息的處理之後，即可將它解除部署。 如需執行這些工作的指示，請參閱[如何升級協調流程](../core/how-to-upgrade-an-orchestration.md)。  
  
 下圖顯示典型的並存協調流程部署。  
  
 ![並存部署案例](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md)   
 [更新應用程式的重要考量](../core/important-considerations-for-updating-applications.md)