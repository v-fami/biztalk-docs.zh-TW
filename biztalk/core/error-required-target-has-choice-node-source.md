---
title: 錯誤-必要的目標有選擇節點來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdTargetHasChoiceNodeSource
ms.assetid: 5b5af999-d100-4e5d-a959-c8b11d574d3b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91c9ad912b03bbb475efcc9eb8207a388400b43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240622"
---
# <a name="error---required-target-has-choice-node-source"></a>錯誤-必要的目標有選擇節點來源
**錯誤碼**  
  
 btm1029  
  
 **說明**  
  
 目的結構描述中指定的節點指定為必要，但連結至來源結構描述內的節點**選擇**節點。 因為來源結構描述中指定的節點可能不會出現在輸入執行個體訊息中，有可能無法用來建立必要的節點與目的結構描述的來源。  
  
 **使用者動作**  
  
 視需要，將目的結構描述中的指定節點變更為選擇性，或在目的結構描述中提供不同來源給指定的節點，此結構描述必須發生於所有有效的輸入執行個體訊息。