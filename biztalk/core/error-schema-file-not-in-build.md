---
title: 錯誤-結構描述檔案不在組建 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.schemaFileNotInBuild
ms.assetid: 9190868d-a1ae-48bf-ac85-510086805887
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3b5d6d11bec6b9f263e2f204f004a9a162de471
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241598"
---
# <a name="error---schema-file-not-in-build"></a>錯誤-結構描述檔案不在組建中
**說明**  
  
 命令 (**驗證執行個體**，**產生執行個體**，或**驗證結構描述**) 無法執行，因為**建置動作**結構描述檔案的屬性設定為**無**，這些命令時，防止此結構描述。  
  
 **使用者動作**  
  
 在 Microsoft 中選取相關結構描述檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，然後在 [屬性] 視窗中變更**建置動作**屬性**編譯**。 然後嘗試**驗證執行個體**，**產生執行個體**，或**驗證結構描述**命令一次。