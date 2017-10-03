---
title: "協調流程引擎的執行階段驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, assemblies
- orchestrations, validating
- validating, orchestration engine
- schemas, validating
- correlations, validating
- validating, schemas
- orchestration engine, runtime validation
- assemblies, validating
- validating, correlations
- validating, orchestrations
- validating
ms.assetid: f6085889-05d6-4eba-a528-9d034c4e4225
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e53adb5aa42c7dfe23df50707754bde200ea838a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-validation-for-the-orchestration-engine"></a>協調流程引擎的執行階段驗證
您可以設定協調流程引擎以執行各種執行階段驗證，以協助您測試協調流程和診斷可能發生的組態或資料錯誤。  
  
 您可以在 BTSNTSvc.exe.config 中設定旗標，而您可以在與 BTSNTSvc.exe 相同的目錄中建立或編輯 BTSNTSvc.exe.config 組態檔 (通常是在 BizTalk 部署目錄中)。 您可在 BTSNTSvc.exe.config 檔案中設定下列旗標：  
  
-   如果您設定**ValidateAssemblies**旗標設為`True`，引擎嘗試載入立即依存組件的協調流程，並在失敗會擲回後所參考的所有組件Microsoft.XLANGs.Core.AssemblyValidationException。  
  
-   如果您設定**ValidateSchemas**旗標設為`True`，此引擎會使用 System.Xml.XmlValidatingReader 來驗證代表訊息部分類型的每個結構描述，並在失敗時擲回 System.Xml.XmlException。  
  
-   如果您設定**ValidateCorrelations**旗標設為`True`，引擎就會確認，在平行群組的符合其中一個群組會收到具有相同的相互關聯屬性值，並在失敗時擲回的所有訊息Microsoft.XLANGs.Core.CorrelationValidationException。  
  
-   如果您設定**ExtendedLogging**旗標設為`True`，引擎在 Microsoft.XLANGs.BaseTypes.PublishMessageException 的資訊無法發行之訊息中顯示的升級的屬性。  
  
 若要停用驗證，可以從組態檔整個移除旗標。 當所有驗證都開啟時，引擎將會驗證組件、結構描述和相互關聯。 如需詳細資訊和 BTSNTSvc.exe.config 的範例，請參閱[協調流程引擎組態](../core/orchestration-engine-configuration.md)。  
  
## <a name="validate-assemblies"></a>驗證組件  
 協調流程引擎將會驗證協調流程參考的所有組件是否為可用。 若要讓驗證成功，在協調流程的第一個執行個體啟動時，所有參考的組件都必須在「全域組件快取」(GAC) 中。 若驗證失敗，會在應用程式記錄檔中記錄錯誤並擱置協調流程。  
  
## <a name="validate-schemas"></a>驗證結構描述  
 不論何時指派 XSD 部分，協調流程引擎都會依照其結構描述驗證該部分的資料。 如果驗證失敗，錯誤會記錄應用程式記錄檔，並將擲回例外狀況。  
  
## <a name="validate-correlation"></a>驗證相互關聯  
 協調流程引擎將會確認使用協調流程的指定執行個體為相互關聯指定的屬性值，是否反映在從協調流程執行個體傳送的任何訊息中。 如果**validateCorrelation**未設定，引擎會假設傳送的訊息會包含正確的相互關聯值，並且將會執行任何檢查。  
  
 如果任何相互關聯驗證失敗，引擎會應用程式記錄檔中記錄錯誤並擲回例外狀況型別的**CorrelationValidationException**。  
  
 根據預設， **validateCorrelation**未設定。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯協調流程](../core/debugging-orchestrations.md)   
 [協調流程引擎組態](../core/orchestration-engine-configuration.md)