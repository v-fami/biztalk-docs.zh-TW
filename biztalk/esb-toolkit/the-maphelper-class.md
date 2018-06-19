---
title: MapHelper 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c552c066-835f-4515-939f-dd465a7a5ed0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de74610c40b37560abcbce040d80320525f0a21c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295110"
---
# <a name="the-maphelper-class"></a>MapHelper 類別
使用**MapHelper**類別以執行轉換，直接不使用 Web 服務的轉換。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝程式會安裝並註冊組件**Microsof.Practices.ESB.Transform.dll**與**MapHelper**在全域組件快取中的類別。  
  
 **MapHelper**類別會公開兩個公用方法：  
  
-   **TransformMessage**。 包含要轉換之訊息的字串，包含部署在 BizTalk 對應的完整的名稱的字串，這個方法會接受做為參數。 方法會傳回字串，包含已轉換的文件。  
  
-   **TransformMessageStream**。 包含要轉換的訊息資料流和字串，包含完整部署在 BizTalk 對應的名稱，這個方法會接受做為參數。 方法會傳回字串，包含已轉換的文件。