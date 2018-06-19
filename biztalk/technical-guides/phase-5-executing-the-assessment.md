---
title: 第 5 個階段： 執行評定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d40fc64-b6cb-448b-8ea1-a6ad7302ab8b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fba6d49d8d69276af4282ad0a941ee1fc4d8068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302686"
---
# <a name="phase-5-executing-the-assessment"></a>第 5 個階段： 執行評估
執行階段是透過自動化的負載測試和其中的效能瓶頸會探索及定址，產生的效能資料的位置。 這個階段中具有反覆的程序效能瓶頸是減少或消除藉由測試，藉此評估效能、 最佳化及測試一次。  
  
 本主題說明通常會遵循 BizTalk Server 效能評估的執行階段的步驟：  
  
## <a name="step-1-run-automated-tests"></a>步驟 1： 執行自動化的測試  
 開始執行階段執行自動化的測試。 BizTalk Server 效能評估通常著重於輸送量和/或延遲的測試，但可能會包含組建驗證和功能測試。 完整執行自動化測試的詳細資訊，請參閱[實作自動化的測試](../technical-guides/implementing-automated-testing.md)。  
  
## <a name="step-2-document-and-evaluate-test-results"></a>步驟 2： 文件，並評估測試結果  
 在每個測試結束時，請徹底測試結果的文件，並評估是否已符合規定的效能目標。  
  
## <a name="step-3-modify-the-configuration-of-biztalk-server-third-party-systems-or-solution-artifacts-to-tune-for-performance-based-on-the-test-results"></a>步驟 3： 修改 BizTalk Server、 第三方系統或方案成品，若要根據測試結果的效能微調的組態  
 使用測試結果來決定如何將環境最佳化到達所述的輸送量或延遲的目標。  
  
## <a name="step-4-record-all-changes-made-to-the-environment"></a>步驟 4： 對環境的所有變更的都記錄  
 請確定對環境進行任何變更都完整記錄。 變更的記錄可讓您輕鬆地套用實際執行環境中的變更，並將納變更的復原，如果需要。  
  
## <a name="step-5-repeat-this-cycle-until-goals-are-achieved"></a>步驟 5： 重複這個循環，直到達到目標是  
 繼續測試、 評估和記錄結果、 最佳化環境，以及撰寫環境的變更，直到到達所要的效能目標的週期。  
  
## <a name="step-6-summarize-test-results-at-the-end-of-each-day"></a>步驟 6： 彙總的每一天結束測試結果  
 完成測試結果和結尾的每一天的進度 」 執行的摘要 」。 編譯包含摘要的電子郵件，並讓每個人所針對的進度的通知傳送給所有專案關係人的效能評估中。  
  
## <a name="step-7-update-the-project-plan-as-timeline-goals-are-met"></a>步驟 7： 更新專案計劃符合目標的時間軸  
 在計劃階段開發時間表是效能評定的整體進度的良好參考。 更新這個時間軸在必要時，所有專案關係人溝通進度。  
  
## <a name="see-also"></a>另請參閱  
 [效能評定階段](../technical-guides/phases-of-a-performance-assessment.md)