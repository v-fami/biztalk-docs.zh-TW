---
title: 錯誤-無效的根節點類別名稱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.rootNodeClassNameNotValid
ms.assetid: 48b4f7e4-8c20-4e94-86be-1425ea62f8c5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff170609ef37b1d7f2b00a4d4ca3952b89eef9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240966"
---
# <a name="error---root-node-class-name-not-valid"></a>錯誤-無效的根節點類別名稱
**錯誤碼**  
  
 BEC2012  
  
 **說明**  
  
 **RootNode TypeName**根節點，此結構描述中的其中一個屬性是無效的。 因為值**RootNode TypeName**屬性做為自動產生的 C# 類別名稱的名稱時，它必須是有效的 C# 識別項，且不能是 BizTalk 保留的關鍵字。  
  
 **使用者動作**  
  
 選取指定的根節點，然後在 Microsoft®[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性視窗中，變更**RootNode TypeName**屬性的值，是有效的 C# 識別項並不是 BizTalk 保留的關鍵字。