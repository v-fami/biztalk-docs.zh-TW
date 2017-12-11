---
title: "如何偵測運算質組態問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32afc333-934c-4ffb-b1b5-61af07157200
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8561156091c992e9329ef7d9627589eff9e0ed6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-detect-configuration-issues-for-a-functoid"></a>如何偵測運算質的組態問題
使用對應時，您可能會遇到運算質和/或連結組態的問題。 BizTalk 對應工具使用虛擬化機制，有助於快速識別和運算質組態相關的問題。 此視覺化指示會呈現為運算質圖示上的警告註解 (如例如![運算質 IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) 關聯性檢視中。 本主題提供有關如何偵測運算質組態問題的資訊。  
  
 當對應工具偵測到運算質未正確設定時，就會顯示警告狀態圖示。 將滑鼠指標移到運算質上方也會顯示對應工具識別之問題的簡短資訊。 例如，如果運算質未達到有效輸入數目下限，運算值的工具提示會說明需要的輸入參數數目。  
  
## <a name="prerequisites"></a>必要條件  
 此作業需要執行中的 BizTalk 對應工具。  
  
### <a name="to-detect-configuration-issues-for-a-functoid"></a>偵測運算質的組態問題  
  
1.  將必要的運算質從工具箱拖曳到格線頁。 您會看到運算質帶有警告圖示。  
  
2.  您可以執行下列其中一個動作：  
  
    -   將滑鼠指標移到運算質上方。 工具提示會顯示關於錯誤和您必須採取之動作的資訊。  
  
         下圖顯示設定「加法」運算質時所出現含錯誤資訊的工具提示。  
  
         ![運算質組態中的錯誤偵測](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")  
  
    -   按兩下運算質。 **設定\<運算質\>運算質**對話方塊會顯示針對輸入參數的警告圖示。 這表示所選運算質未設定輸入參數。  
  
         下圖顯示關於「加法」運算質之輸入參數的錯誤資訊。  
  
         ![運算質未設定時顯示的警告](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")  
  
## <a name="see-also"></a>請參閱  
 [在 BizTalk 對應工具中使用增強功能](../core/using-enhanced-features-in-biztalk-mapper.md)