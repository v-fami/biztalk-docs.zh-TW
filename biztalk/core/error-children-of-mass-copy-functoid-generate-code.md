---
title: 錯誤-大量複製運算質的子系產生程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.massCopyChildtenGenCode
ms.assetid: c791009b-241b-4004-b0c6-f1536bb119c5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68183a90be46b176d13100b02cbed2798fe24b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240566"
---
# <a name="error---children-of-mass-copy-functoid-generate-code"></a>錯誤-大量複製運算質的子系產生程式碼
**錯誤碼**  
  
 btm1068  
  
 **說明**  
  
 與衝突的功能的案例**大量複製**對應中找不到運算質。 在目的結構描述，連結至的輸出之節點的下階節點**大量複製**運算質會嘗試產生其本身的 XSLT 程式碼。  
  
 **使用者動作**  
  
 藉由變更相關的使用方式，移除不相容的問題**大量複製**運算質或變更子節點，使其不再產生其本身的 XSLT 程式碼。