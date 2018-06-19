---
title: 解析程式類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9ebd6c2-fd86-471a-bc50-b1b89f701fab
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1359bcbb9c6c918fc0ee6d5e67bacb8e3559c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294846"
---
# <a name="the-resolver-class"></a>解析程式類別
**解析程式**類別會公開 （expose） 的名稱/值組的簡單結構。 解析程式的 Web 服務會傳回這個類別的執行個體的泛型集合，從它的方法。  
  
 ESB 核心安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**與全域組件快取中的解析程式類別的組件。  
  
 以字典為基礎名稱/值的使用方法的可輕鬆地在未來加入新項目釋出，並藉由避免包含不相關的屬性來解析方法和目前的解析程式類型而定，解析結果的大小降到最低。  
  
 **解析程式**類別會公開兩個屬性：  
  
-   **名稱**。 這是包含資訊之後已解決的連接字串所傳回的名稱/值組的名稱。  
  
-   **值**。 這是對應名稱的名稱/值組的值。