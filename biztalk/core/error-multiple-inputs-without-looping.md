---
title: 錯誤-沒有迴圈的多個輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.multipleInputsWithoutLooping
ms.assetid: 7e55ad22-06a8-4a56-839d-a30b82819a68
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a8a11b25c3c1df52827bdbf4098f0cd37bdd8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240502"
---
# <a name="error---multiple-inputs-without-looping"></a>錯誤-多個沒有迴圈的輸入
**錯誤碼**  
  
 btm1004  
  
 **說明**  
  
 多個連結連接目的結構描述，只適用於當指定節點的祖系節點的其中一個連線到指定的節點**迴圈**運算質。  
  
 **使用者動作**  
  
 移除目的結構描述中指定之節點的所有連結，只保留一個連結，或將指定節點的其中一個上階節點連接到迴圈運算質。