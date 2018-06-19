---
title: 錯誤-沒有任何連結或常數的對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.mapWithoutAnyLinksOrConstants
ms.assetid: 8d1cdbcd-4bd0-4ddc-9e94-746e82b6ec48
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d697d6d053f2c0a36d0f5cb45002dca28a92f005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240638"
---
# <a name="error---map-without-any-links-or-constants"></a>錯誤-沒有任何連結或常數的對應
**錯誤碼**  
  
 btm1000  
  
 **說明**  
  
 對應未包含結構描述間的連結，或目的結構描述中的常數值。 因此，無法從此對應建立輸出。  
  
 **使用者動作**  
  
 新增適當的連結 (若有需要，也新增運算質) 至對應格線，或新增常數至目的結構描述，以指定符合來源結構描述的執行個體訊息，如何轉換為符合目的結構描述的執行個體訊息。