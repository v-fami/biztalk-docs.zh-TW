---
title: "ResolverDictionary 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46deb8a0-0523-4a5c-ac6b-45c506de7a72
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dfe0082ffc7f7b68c5c56811a28d5ccd20e93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolverdictionary-class"></a>ResolverDictionary 類別
**ResolverDictionary**類別是**字典**-基礎類別，可以儲存的執行個體**解析程式**類別做為**字串**名稱 /值組。 建立的執行個體時**ResolverDictionary**類別，您必須提供現有參考**字典**執行個體。 **ResolverDictionary**類別提供資料的**解析程式**類別會使用執行執行階段解析時。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**具有組件**ResolverDictionary**在全域組件快取中的類別。  
  
 **ResolverDictionary**類別會公開其中一種方法和一個屬性：  
  
-   **項目 (**金鑰**)**。 這個方法會採用包含索引鍵名稱的字串值。 如果，則傳回對應的字串值或空字串項目不存在於基礎**字典**執行個體。  
  
-   **BaseDictionary**。 這個屬性會傳回參考基礎**字典**執行個體。