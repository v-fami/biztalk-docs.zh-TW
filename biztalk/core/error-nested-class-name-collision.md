---
title: 錯誤-巢狀的類別名稱衝突 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.nestedClassNameCollision
ms.assetid: dd636d25-d0c1-41be-a2ba-b38ea97b973d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a9fa7a9f57088b3fb93e2eb6024e9b6aad49c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240942"
---
# <a name="error---nested-class-name-collision"></a>錯誤-巢狀的類別名稱衝突
**錯誤碼**  
  
 BEC2017  
  
 **說明**  
  
 **型別名稱**這個結構描述的屬性找不到要與相同**RootNode TypeName**結構描述中根節點的其中一個屬性。 C# 不允許具有相同名稱的巢狀類別；因此，此情況會引起錯誤。  
  
 **使用者動作**  
  
 您必須變更一個或兩個相關的屬性值，以避免名稱衝突。 您可以執行下列動作之一：  
  
-   在 Microsoft 中選取相關結構描述檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，然後在 [屬性] 視窗中變更**型別名稱**屬性唯一有效的值。  
  
     \- 或 -  
  
-   選取指定的根節點，然後在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性視窗中，變更**RootNode TypeName**屬性唯一有效的值。