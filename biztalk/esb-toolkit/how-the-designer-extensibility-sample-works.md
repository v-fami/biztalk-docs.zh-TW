---
title: 設計工具擴充性範例的運作方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f4dc622-28b8-498d-961f-df969cff9dcb
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f78e5ab2c8a274b53b3cc580b37842772924af94
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975869"
---
# <a name="how-the-designer-extensibility-sample-works"></a>設計工具擴充性範例的運作方式
每個專案，在設計工具擴充性範例包含兩個類別： **Extender**類別和**擴充提供者**類別。 這些類別設計用來擴充功能，以及定義屬性的**ItineraryDsl**模型項目。  
  
 **擴充提供者**類別衍生自**ExtensionProviderBase**類別，並有**ExtensionProviderAttribute**套用這些屬性，找出擴充功能和其用途。 這些值將顯示在設計工具中的使用者，當使用者正在設定**Extender**模型項目的屬性。 當**擴充提供者**它們呼叫的建構函式的類別初始化**ExtensionProviderBase**並將擴充項類別的類型傳遞給它。  
  
 **Extender**類別具有**ObjectExtender**屬性套用至它們; 若要**ObjectExtender**屬性，傳遞中物件的型別**ItineraryDsl**它們所擴充。 這些類別的基底類別會因擴充項的類型而異。 基底類別的解析程式 extender **ObjectExtender\<解析程式\>**。 路線服務的擴充項的基底類別是**ItineraryServiceExtenderBase**。 在**Extender**類別，下列屬性會套用至屬性： 所需的正確地顯示在屬性方格中，屬性進行驗證時，Microsoft 企業程式庫中包含屬性所需的適當的序列化屬性和/或屬性，以決定如何保存內容。  
  
 當這些組件，編譯並放置在 Lib 資料夾中時，載入及快取設計工具在執行階段。 視需要擴充項**ItineraryDsl**使用反映來從快取載入適用的組件，藉由檢查匯出之型別的和在這些類型的屬性。